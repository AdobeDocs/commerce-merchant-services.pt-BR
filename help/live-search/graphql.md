---
title: GraphQL
description: O  [!DNL Live Search] espaço de trabalho do GraphQL permite criar consultas com seus dados dinâmicos.
exl-id: f7b17c5a-a97b-4724-a50e-83e28a4c4c38
source-git-commit: cf94623fd4a87c13d15c81ac62243a508cb1d14d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# GraphQL

O espaço de trabalho *GraphQL* permite que os administradores criem e testem consultas do GraphQL usando seus próprios dados.

Este espaço de trabalho dá suporte às consultas [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) e [`attributeMetadata`](https://developer.adobe.com/commerce/services/graphql/live-search/attribute-metadata/).

![espaço de trabalho do GraphQL](assets/graphql.png)

```graphql
query productSearch {
  productSearch(phrase: "a306") {
    total_count
    items {
      product {
        sku
		name
      }
    }
    facets {
      title
    }
  }
}
```

Variáveis:

```json
{
  "Magento-Environment-Id": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
  "Magento-Website-Code": "base",
  "Magento-Store-Code": "base",
  "Magento-Store-View-Code": "default",
  "X-Api-Key": "search_gql"
}
```

