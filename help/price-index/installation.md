---
title: Instalação de Indexação de Preço SaaS
description: Instalando A Indexação De Preços Do SaaS
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
source-git-commit: 3820736a25942b147d6e2c7b8820c360d6a0a535
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Instalação de Indexação de Preço SaaS

Configurar a indexação de preço do SaaS requer a instalação de novos módulos e a execução de comandos CLI. Os administradores precisam de acesso à linha de comando para concluir esta instalação.

## Pré-requisitos

* Adobe Commerce 2.4.4+
* Pelo menos um dos seguintes serviços SaaS instalados:

   * [Serviço de catálogo](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Recommendations do produto](../product-recommendations/guide-overview.md)

## Instalar os módulos necessários

Dependendo da configuração, o processo de instalação pode ser um pouco diferente.
Há extensões que adicionam os novos feeds e código de suporte e há uma extensão que remove o feed de preços padrão.

1. Adicione os seguintes módulos à sua `composer.json` arquivo:

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

Após a atualização, três novos feeds ficam disponíveis:

* `prices` - responsável pela entrega de dados sobre preços ao serviço
* `scopesCustomerGroup` - responsável por fornecer Grupos de clientes ao serviço
* `scopesWebsite` - responsável por fornecer sites, grupos de armazenamento e visualizações de loja ao serviço


1. Configure os novos feeds a serem definidos para o modo &quot;Atualizar de acordo com a programação&quot;:

   ```bash
   bin/magento indexer:set-mode schedule catalog_data_exporter_product_prices scopes_customergroup_data_exporter scopes_website_data_exporter
   ```

1. Reindexe os novos feeds:

   ```bash
   bin/magento saas:resync --feed=scopesCustomerGroup
   bin/magento saas:resync --feed=scopesWebsite
   bin/magento saas:resync --feed=prices
   ```

Execute os indexadores acima manualmente, conforme necessário. Caso contrário, os dados serão atualizados no processo de sincronização padrão. Leia mais sobre o [Sincronização do catálogo](../landing/catalog-sync.md) serviço.

Os usuários do Luma e do Adobe Commerce Core GraphQL podem instalar a variável `catalog-adapter` módulo que fornece compatibilidade Luma e Core GraphQl e desativa o indexador de preço principal PHP.
Para usar o `catalog-adapter` módulo, [!DNL Live Search] e [!DNL Catalog Service] deve primeiro ser instalado e configurado. Siga as [Instalar [!DNL Live Search]](../live-search/install.md) e [Instalação do Serviço de Catálogo](../catalog-service/installation.md) instruções antes de continuar.

Para configurar o Live Search e o Adaptador de Catálogo, siga [Conector do Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html?lang=en) instruções.

```bash
composer require adobe-commerce/catalog-adapter
```

Se necessário, o indexador de preço principal PHP pode ser reativado com o seguinte comando:

```bash
bin/magento module:disable Magento_PriceIndexerDisabler
```
