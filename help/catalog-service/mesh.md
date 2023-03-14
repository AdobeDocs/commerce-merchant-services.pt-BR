---
title: '[!DNL Catalog Service and API Mesh]'
description: '[!DNL API Mesh] O para Adobe Commerce fornece uma maneira de integrar várias fontes de dados por meio de um endpoint comum do GraphQL.'
source-git-commit: 41d6bed30769d3864d93d6b3d077987a810890cc
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---

# [!DNL Catalog Service and API Mesh]

A variável [Malha de API para o Construtor de aplicativos Adobe Developer](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) O permite aos desenvolvedores integrar APIs privadas ou de terceiros e outras interfaces com produtos Adobe usando o Adobe I/O Runtime.

![Diagrama da arquitetura de catálogo](assets/catalog-service-architecture-mesh.png)

A primeira etapa para usar a API Mesh com o Serviço de catálogo é conectar a API Mesh à sua instância. Consulte as instruções detalhadas em [Criar uma malha](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

Para concluir a configuração, instale o [Pacote CLI do Adobe Developer](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/).

Depois que o Mesh for configurado no Adobe I/O Runtime, execute o seguinte comando, que adiciona um `CommerceCatalogServiceGraph` para sua malha.

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

Onde `variables.json` é um arquivo separado que armazena os valores usados com frequência para o Adobe I/O Runtime.
Por exemplo, a chave de API pode ser salva no arquivo:

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

Após a execução desse comando, o Serviço de catálogo deve estar em execução por meio da API Mesh. Você pode executar o `aio api-mesh:get` comando para ver a configuração da malha atualizada.

## Uso da API Mesh

A API Mesh permite que os usuários consumam fontes de dados externas para aprimorar a instância do Adobe Commerce. Ele também pode ser usado para configurar dados existentes do Commerce para habilitar novas funcionalidades.

Neste exemplo, a API Mesh é usada para ativar os preços da camada no Adobe Commerce.
Substitua o `name `, `endpoint`, e `x-api-key` valores.

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

Depois de configurado, consulte a Malha para obter preços diferenciados:

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
