---
title: '[!DNL Catalog Service and API Mesh]'
description: '[!DNL API Mesh] O para Adobe Commerce fornece uma maneira de integrar várias fontes de dados por meio de um terminal GraphQL comum.'
source-git-commit: bdceeeeb1ed58c4ffbc87bee24c1eb3754b1cde9
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# [!DNL Catalog Service and API Mesh]

O [Mensagem de API para o Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) O permite que os desenvolvedores integrem APIs privadas ou de terceiros e outras interfaces com produtos Adobe usando o Adobe I/O Runtime.

![Diagrama de arquitetura do catálogo](assets/catalog-service-architecture-mesh.png)

A primeira etapa para usar a malha de API com o serviço de catálogo é conectar a malha de API à sua instância. Veja as instruções detalhadas em [Criar uma malha](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

Para concluir a configuração, instale o [Pacote Adobe Developer CLI](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).

Depois que a malha for configurada no Adobe I/O Runtime, execute o seguinte comando que adiciona uma `CommerceCatalogServiceGraph` origem da sua malha.

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

Onde `variables.json` é um arquivo separado que armazena valores comumente usados para o Adobe I/O Runtime.
Por exemplo, a chave da API pode ser salva no arquivo :

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

Após executar esse comando, o Serviço de catálogo deve estar sendo executado pela malha da API. Você pode executar o `aio api-mesh:get` para exibir a configuração da malha atualizada.

## Uso da malha da API

A malha da API permite que os usuários consumam fontes de dados externas para aprimorar sua instância do Adobe Commerce. Ele também pode ser usado para configurar dados existentes do Commerce para ativar uma nova funcionalidade.

Neste exemplo, a Mensagem da API é usada para habilitar preços de camada no Adobe Commerce.
Substitua o `name `, `endpoint`e `x-api-key` valores.

```json
{
  "meshConfig": {
    "sources": [
      {
        "name": "<Commerce Instance Name>",
        "handler": {
          "graphql": {
            "endpoint": "<Adobe Commerce GraphQL endpoint>"
          }
        },
        "transforms": [
            {
                "prefix": {
                    "includeRootOperations": true,
                    "value": "Core_"
                }
            }
        ]
      },
      {
        "name": "CommerceCatalogServiceGraph",
        "handler": {
          "graphql": {
            "endpoint": "https://commerce.adobe.io/catalog-service/graphql/",
            "operationHeaders": {
              "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
              "Magento-Website-Code": "{context.headers['magento-website-code']}",
              "Magento-Store-Code": "{context.headers['magento-store-code']}",
              "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
              "x-api-key": "storefront-catalog-apollo",
              "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
            },
            "schemaHeaders": {
              "x-api-key": "<YOUR API-KEY>"
            }
          }
        }
      }
    ],
    "additionalTypeDefs": "extend interface ProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type SimpleProductView {\n  price_tiers: [Core_TierPrice]\n}\n extend type ComplexProductView {\n  price_tiers: [Core_TierPrice]\n}\n",
    "additionalResolvers": [
        {  
            "targetTypeName": "ProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "SimpleProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        },
        {  
            "targetTypeName": "ComplexProductView",
            "targetFieldName": "price_tiers",
            "sourceName": "MagentoStageCore",
            "sourceTypeName": "Query",
            "sourceFieldName": "Core_products",
            "requiredSelectionSet": "{\n    items {\n  sku\n    price_tiers {\n        quantity,\n        final_price {\n          value\n          currency\n        }\n      }\n    }\n  }",
            "sourceArgs": {
                "filter.sku.eq": "{root.sku}"
            },
            "result": "items[0].price_tiers"
        }
    ]
   }
}
```

Após a configuração, consulte a Malha para obter os preços em camadas:

```json
query {
  products(skus: ["24-MB04"]) {
    sku
    description
    price_tiers {
        quantity
        final_price {
          value
          currency
        }
      }
    ... on SimpleProductView {
      id
       
      price {
        final {
          amount {
            value
          }
        }
      }
    }
  }
}
```
