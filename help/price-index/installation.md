---
title: Instalação da indexação de preços do SaaS
description: Instalando a indexação de preços do SaaS
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
role: Admin, Developer
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '254'
ht-degree: 0%

---

# Instalação da indexação de preços do SaaS

A configuração da indexação de preços SaaS requer a instalação de novos módulos e a execução de comandos CLI. Os administradores precisam de acesso à linha de comando para concluir esta instalação.

## Pré-requisitos

* Adobe Commerce 2.4.4+
* Pelo menos um dos seguintes serviços SaaS instalados:

   * [Serviço de catálogo](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Recommendations do produto](../product-recommendations/guide-overview.md)

## Instalar os módulos necessários

Dependendo da configuração, o processo de instalação pode ser um pouco diferente.
Há extensões que adicionam os novos feeds e código de suporte e há uma extensão que remove o feed de preços padrão.

1. Adicione os seguintes módulos ao `composer.json` arquivo:

   ```json
   "magento/module-saas-price": "102.2.0",
   "magento/module-saas-scopes": "102.2.0",
   "magento/module-product-override-price-remover": "102.2.0",
   "magento/module-bundle-product-override-data-exporter": "102.2.0",
   ```

1. Execute o comando de atualização:

   ```bash
   bin/magento setup:upgrade
   ```

Depois da atualização, três novos feeds estarão disponíveis:

* `prices` - responsável pela entrega de dados de preços ao serviço
* `scopesCustomerGroup` - responsável por fornecer Grupos de Clientes ao serviço
* `scopesWebsite` - responsável por fornecer sites, grupos de lojas e visualizações de lojas ao serviço


1. Configure os novos feeds a serem definidos para o modo &quot;Atualização programada&quot;:

   ```bash
   bin/magento indexer:set-mode schedule catalog_data_exporter_product_prices scopes_customergroup_data_exporter scopes_website_data_exporter
   ```

1. Reindexe os novos feeds:

   ```bash
   bin/magento saas:resync --feed=scopesCustomerGroup
   bin/magento saas:resync --feed=scopesWebsite
   bin/magento saas:resync --feed=prices
   ```

Execute os indexadores acima manualmente, conforme necessário. Caso contrário, os dados serão atualizados no processo de sincronização padrão. Leia mais sobre o [Sincronização de catálogo](../landing/catalog-sync.md) serviço.

Os usuários do Luma e do Adobe Commerce Core GraphQL podem instalar o `catalog-adapter` módulo que fornece compatibilidade com o Luma e o Core GraphQl e desativa o indexador de preço principal do PHP.
Para usar o `catalog-adapter` módulo, [!DNL Live Search] e [!DNL Catalog Service] O deve ser instalado e configurado primeiro. Siga as [Instalar [!DNL Live Search]](../live-search/install.md) e [Instalação do serviço de catálogo](../catalog-service/installation.md) instruções antes de continuar.

Para configurar o Live Search e o Adaptador do Catálogo, siga [Conector dos Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en) instruções.

```bash
composer require adobe-commerce/catalog-adapter
```

Se necessário, o indexador de preço principal do PHP pode ser reativado com o seguinte comando:

```bash
bin/magento module:disable Magento_PriceIndexerDisabler
```
