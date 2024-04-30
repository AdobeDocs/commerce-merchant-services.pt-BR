---
title: Extensão do Adaptador de Catálogo
description: Utilização do Adaptador de catálogo para renderizar preços dos Serviços Commerce
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
exl-id: 2c9120eb-aa51-48e9-b6a4-fffe25fc31f2
source-git-commit: 7d62f8d5539cd744e98d8d6c072d77a2a7c5a256
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# Adaptador do catálogo

A variável `Catalog Adapter` A extensão do desativa o indexador de Preço de produto padrão do Adobe Commerce e, em vez disso, usa preços fornecidos pelo [Serviço de catálogo](../catalog-service/overview.md).
O indexador de Preço de Produto do Adobe Commerce está desabilitado e não pode ser ativado com esses módulos de extensão instalados. Somente com a remoção ou desabilitação dessa extensão é possível habilitar novamente a indexação padrão de preço do produto.

## Requisitos

* Adobe Commerce 2.4.4+
* Tenha ambos os seguintes serviços da Commerce instalados:

   * [Serviço de catálogo](../catalog-service/overview.md)
   * [Live Search](../live-search/overview.md)

## Instalação

Para usar o `catalog-adapter` módulo, [!DNL Live Search] e [!DNL Catalog Service] O deve ser instalado e configurado primeiro. Siga as [Instalar [!DNL Live Search]](../live-search/install.md) e [Instalação do serviço de catálogo](../catalog-service/installation.md) instruções antes de continuar.

Depois que esses serviços forem instalados, execute o seguinte comando:

```bash
composer require adobe-commerce/catalog-adapter
```

## Reative o indexador de Preço de Produto do Adobe Commerce

Se você tiver aplicativos de terceiros que dependem do indexador de preço de produto padrão do Adobe Commerce, ele poderá ser reativado com os seguintes comandos:

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# re-index Product Price indexer 
bin/magento index:reindex catalog_product_price
```

## Desabilitar indexador de preços de produto para o cenário de frente de loja headless

Se você tiver uma instância do Commerce headless, talvez seja necessário desativar o indexador de preço do produto do Adobe Commerce para reduzir a carga na instância do Adobe Commerce.
Isso é feito instalando o `magento/module-price-indexer-disabler` módulo:

```bash
composer require magento/module-price-indexer-disabler
```

## Cenários de uso

A seguir estão alguns comuns `Catalog Adapter` cenários.

### Nenhuma dependência no indexador de preço de produto do Adobe Commerce

* Você é um comerciante do Luma ou do Adobe Commerce Core GraphQL que tem um serviço necessário instalado (Live Search, Product Recommendations, Catalog Service)
* Não há extensões de terceiros que dependam do indexador de preço do produto do Adobe Commerce

1. Instale o adaptador do catálogo.

### Com dependências no indexador de preço do produto Adobe Commerce

* Você é um comerciante do Luma ou do Adobe Commerce Core GraphQL que tem um serviço compatível instalado (Live Search, Product Recommendations, Catalog Service)
* Você usa uma extensão de terceiros que depende do indexador de preço do produto do Adobe Commerce

1. Instale o adaptador do catálogo.
1. Reative o indexador padrão de Preço de produto do Adobe Commerce.

### Instâncias headless do Commerce

* Um comerciante com uma instância do Commerce headless com os serviços necessários instalados (Live Search, Recommendations de produtos, Serviço de catálogo)
* Nenhuma dependência do indexador de preço de produto padrão do Adobe Commerce

1. Instale o `magento/module-price-indexer-disabler` do pacote do adaptador do catálogo.
