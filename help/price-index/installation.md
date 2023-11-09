---
title: Instalação manual da indexação de preços do SaaS
description: Instalação de indexação de preços SaaS para versões mais antigas
seo-title: SaaS Price Indexing installation
seo-description: Installing SaaS Price indexing
exl-id: a607e852-aa04-4be3-9576-a6bf45f8751f
role: Admin, Developer
source-git-commit: b2ebf26c9a34e5e2e08b7adbabcc780f24363e3c
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 0%

---

# Instalação manual da indexação de preços do SaaS

A indexação de preços SaaS está disponível imediatamente para suporte [versão mais recente](index.md#Requirements) de Commerce Services.
Se você não tiver a versão mais recente e quiser habilitar a Indexação de preços SaaS para sua instância do Adobe Commerce, use este guia.

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
   "magento/module-saas-price": "^102.2.0",
   "magento/module-saas-scopes": ^"102.2.0",
   "magento/module-product-override-price-remover": "^102.2.0",
   "magento/module-bundle-product-override-data-exporter": "^102.2.0",
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

Os usuários do Luma e do Adobe Commerce Core GraphQL podem instalar o [`Catalog Adapter`](catalog-adapter.md) Extensão que fornece compatibilidade com o Luma e o Core GraphQl e desativa o indexador de Preço de produto do Adobe Commerce.

## Avisos

Antes `103.0.0` versão, indexação de preços SaaS suportada simples, agrupado, virtual, configurável e tipos de produtos dinâmicos de pacote.
O suporte para tipos de produto para download, cartões-presente e pacote fixo está disponível a partir de `magento/module-saas-price:103.0.0` versão e disponível imediatamente para os Commerce Services compatíveis.

Os novos feeds devem ser sincronizados manualmente com o `resync` [comando CLI](../landing/catalog-sync.md#resynccmdline). Caso contrário, os dados serão atualizados no processo de sincronização padrão. Obter mais informações sobre o [Sincronização de catálogo](../landing/catalog-sync.md) processo.
