---
title: consulta productSearch
description: '"Um guia de referência para a consulta GraphQL do `productSearch'' para o serviço de catálogo Adobe Commerce.'''
source-git-commit: 49692cf4375ebb975b2cf132d21ac8debe609a90
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# consulta productSearch

O serviço de catálogo do Adobe Commerce `productSearch` O query pode usar o Live Search para retornar detalhes sobre os SKUs especificados como entrada. Embora esse query seja o mesmo que o [`productSearch` query](https://devdocs.magento.com//live-search/product-search.html), o Live Search retorna um `productView` objeto. Consulte a [`productSearch` query](https://devdocs.magento.com//live-search/product-search.html) tópico para informações de referência.

## Sintaxe

```graphql
productSearch(
    phrase: String!
    page_size: Int = 20
    current_page: Int = 1
    filter: [SearchClauseInput!]
    sort: [ProductSearchSortInput!]
): ProductSearchResponse!
```

## Cabeçalhos obrigatórios

Você deve especificar os seguintes cabeçalhos HTTP para executar esta consulta.

| Cabeçalho | Descrição |
|--- | ---|
| `Magento-Customer-Group` | Para clientes da loja, esse valor estará disponível na loja na `dataservices_customer_group` cookie. |
| `Magento-Environment-Id` | Esse valor pode ser obtido executando o `bin/magento config:show services_connector/services_id/environment_id` comando. Consulte o campo &quot;Espaço de dados&quot; em [Commerce Services](https://docs.magento.com/user-guide/configuration/services/saas.html) |
| `Magento-Store-Code` | O código atribuído à loja associado à exibição de loja ativa. Por exemplo, `main_website_store`. |
| `Magento-Store-View-Code` | O código atribuído à exibição de loja ativa. Por exemplo, `default`. |
| `Magento-Website-Code` | O código atribuído ao site associado à exibição de loja ativa. Por exemplo, `base`. |
| `X-Api-Key` | Uma chave exclusiva gerada durante o processo de integração. |

## Exemplo de uso

No exemplo a seguir, o query retorna informações sobre os mesmos produtos que o exemplo anterior. No entanto, foi construído para retornar informações do item dentro do Serviço de Catálogo `productView` objeto em vez do núcleo `product` objeto. Observe que as informações sobre preços variam, dependendo do tipo de produto. Por motivos de brevidade, as informações da faceta não são exibidas.

**Solicitação:**

```graphql
{
  productSearch(
    phrase: "bag"
    sort: [
      {
        attribute: "price"
        direction: DESC }]
    page_size: 9
  ) {
    page_info {
      current_page
      page_size
      total_pages
    }
    items {
      productView {
        name
        sku
        ... on SimpleProductView {
          price {
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
          }
        }
        ... on ComplexProductView {
          options {
            id
            title
            required
            values {
              id
              title
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
            }
          }
        }
      }
    }
  }
}
```

**Resposta:**

```json
{
  "data": {
    "productSearch": {
      "page_info": {
        "current_page": 1,
        "page_size": 9,
        "total_pages": 3
      },
      "items": [
        {
          "productView": {
            "name": "Impulse Duffle",
            "sku": "24-UB02",
            "price": {
              "final": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 74,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Fusion Backpack 567890",
            "sku": "24-MB02",
            "price": {
              "final": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 59,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Rival Field Messenger",
            "sku": "24-MB06",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Push It Messenger Bag",
            "sku": "24-WB04",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Overnight Duffle",
            "sku": "24-WB07",
            "price": {
              "final": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 45,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Wayfarer Messenger Bag 987",
            "sku": "24-MB05",
            "price": {
              "final": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 44,
                  "currency": "USD"
                }
              }
            }
          }
        },
        {
          "productView": {
            "name": "Driven Backpack",
            "sku": "24-WB03",
            "price": {
              "final": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              },
              "regular": {
                "amount": {
                  "value": 36,
                  "currency": "USD"
                }
              }
            }
          }
        }
      ]
    }
  }
}
```
