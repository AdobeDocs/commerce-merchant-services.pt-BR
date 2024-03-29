---
title: 'Exibir preços tributados com a API Mesh'
description: '''Uso [!DNL API Mesh] para que o Adobe Commerce e o Serviço de catálogo exibam preços, incluindo impostos."'
role: Admin, Developer
feature: Services, API Mesh, Catalog Service
source-git-commit: d235f28c7f438fe89eb20ea7ef8bda7ae39733c0
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Exibir preços tributados com a API Mesh para o Construtor de aplicativos do Adobe Developer

[API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) O permite aos desenvolvedores integrar APIs privadas ou de terceiros e outras interfaces com produtos Adobe usando o Adobe I/O Runtime.

Neste tópico, a Malha de API é usada para exibir preços de produtos em uma Página de detalhes do produto com impostos configurados em.

## Configurar alíquotas de imposto

É necessário ter impostos configurados para que eles sejam exibidos na Página de detalhes do produto.

1. [Configurar alíquotas de imposto](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/tax-rules.html).
1. Habilitar impostos para serem [exibido no catálogo](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/display-settings.html#step-1%3A-configure-catalog-prices-display-settings)e defina-o como `Including and Excluding Tax` ou `Including Tax`.

Verifique se o Serviço de Catálogo está funcionando, marcando uma Página de detalhes do produto.

![Impostos exibidos na Página Detalhes do Produto](assets/display-tax.png)

## Configurar API Mesh

Se ainda não tiver sido feito, conecte a API Mesh com o Serviço de catálogo à sua instância. Consulte as instruções detalhadas na [Introdução](https://developer.adobe.com/graphql-mesh-gateway/gateway/getting-started/) tópico no guia do desenvolvedor do API Mesh.

No `mesh.json` arquivo, substitua o `name `, `endpoint`, e `x-api-key` valores.

```json
{
    "meshConfig": {
      "sources": [
        {
          "name": "<NAME OF MESH>",
          "handler": {
            "graphql": {
              "endpoint": "<COMMERCE INSTANCE GQL ENDPOINT URL>"
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
              "endpoint": "https://catalog-service-sandbox.adobe.io/graphql/",
              "operationHeaders": {
                "Magento-Store-View-Code": "{context.headers['magento-store-view-code']}",
                "Magento-Website-Code": "{context.headers['magento-website-code']}",
                "Magento-Store-Code": "{context.headers['magento-store-code']}",
                "Magento-Environment-Id": "{context.headers['magento-environment-id']}",
                "x-api-key": "API_KEY",
                "Magento-Customer-Group": "{context.headers['magento-customer-group']}"
              },
              "schemaHeaders": {
                "x-api-key": "<YOUR API_KEY>"
              }
            }
          }
        }
      ],
      "additionalTypeDefs": "extend type ComplexProductView {\n  priceWithTaxes: Core_PriceRange\n}\n extend type SimpleProductView {\n  priceWithTaxes: Core_PriceRange\n}\n",
      "additionalResolvers": [
            {  
              "targetTypeName": "ComplexProductView",
              "targetFieldName": "priceWithTaxes",
              "sourceName": "MagentoQACore",
              "sourceTypeName": "Query",
              "sourceFieldName": "Core_products",
              "requiredSelectionSet": "{\n items {\n sku, \n price_range {\n minimum_price {\n final_price {\n value\n currency\n }\n }\n }\n }\n }",
                "sourceArgs": {
                    "filter.sku.eq": "{root.sku}"
                },
                "result": "items[0].price_range"
            },
            {  
              "targetTypeName": "SimpleProductView",
              "targetFieldName": "priceWithTaxes",
              "sourceName": "MagentoQACore",
              "sourceTypeName": "Query",
              "sourceFieldName": "Core_products",
              "requiredSelectionSet": "{\n items {\n sku, \n price_range {\n minimum_price {\n final_price {\n value\n currency\n }\n }\n }\n }\n }",
                "sourceArgs": {
                    "filter.sku.eq": "{root.sku}"
                },
                "result": "items[0].price_range"
            }
        ]
     }
  }
```

Este `mesh.json` arquivo de configuração:

* Transforma o aplicativo principal do Commerce para exigir que &quot;Core_&quot; seja anexado a qualquer uma de suas consultas ou tipos. Isso evita possíveis conflitos de nomenclatura com o Serviço de catálogo.
* Estende o `ComplexProductView` e `SimpleProductView` tipos com um novo campo chamado `priceWithTaxes`.
* Adiciona um resolvedor personalizado ao novo campo.

Crie a malha com o [comando criar](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/#create-a-mesh-1) com o `mesh.json` arquivo.

### consulta do GraphQL

Você pode recuperar o novo `priceWithTaxes` dados usando o GraphQL.

Exemplo de consulta:

```graphql
query {
    products(skus:[MH07]) {
        __typename
        id
        sku
        name
        description
        shortDescription
        addToCartAllowed
        url
        ... on ComplexProductView {
            priceWithTaxes {
              minimum_price {
                final_price {
                  value
                }
              }
              maximum_price {
                final_price {
                  value
                }
              }
            }
            priceRange {
                maximum {
                    final {
                        amount {
                            value
                            currency
                        }
                    }
                    regular {
                        amount {
                            value
                            currency
                        }
                    }
                    roles
                }
                minimum {
                    final {
                        amount {
                            value
                            currency
                        }
                    }
                    regular {
                        amount {
                            value
                            currency
                        }
                    }
                    roles
                }
            }
        }
    }
}
```

Resposta da consulta:

```json
{
  "data": {
    "products": [
      {
        "__typename": "ComplexProductView",
        "id": "VFVnd053AFpHVm1ZWFZzZEEAWkRWa09Ua3hNVFl0WTJJd015MDBaRGMwTFRnME16a3RNak01TVRVNE9ESTBOemd4AGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSE1EQTFPRFEyTVRjeA",
        "sku": "MH07",
        "name": "Hero Hoodie13",
        "description": "<p>Gray and black color blocking sets you apart as the Hero Hoodie keeps you warm on the bus, campus or cold mean streets. Slanted outsize front pockets keep your style real . . . convenient.</p>\r\n<p>* Full-zip gray and black hoodie.<br />* Ribbed hem.<br />* Standard fit.<br />* Drawcord hood cinch.<br />* Water-resistant coating.</p>",
        "shortDescription": "",
        "addToCartAllowed": true,
        "url": "http://commerce_url/hero-hoodie.html",
        "priceWithTaxes": {
          "minimum_price": {
            "final_price": {
              "value": 8.330001
            }
          },
          "maximum_price": {
            "final_price": {
              "value": 13355.524701
            }
          }
        },
        "priceRange": {
          "maximum": {
            "final": {
              "amount": {
                "value": 39.02,
                "currency": "USD"
              }
            },
            "regular": {
              "amount": {
                "value": 54,
                "currency": "USD"
              }
            },
            "roles": [
              "visible"
            ]
          },
          "minimum": {
            "final": {
              "amount": {
                "value": 39.02,
                "currency": "USD"
              }
            },
            "regular": {
              "amount": {
                "value": 54,
                "currency": "USD"
              }
            },
            "roles": [
              "visible"
            ]
          }
        }
      }
    ]
  },
  "extensions": {}
}
```
