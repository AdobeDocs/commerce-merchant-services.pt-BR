---
title: consulta de produtos
description: '"Um guia de referência para a consulta GraphQL de "produtos" para o serviço de catálogo do Adobe Commerce."'
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# consulta de produtos

O serviço de catálogo do Adobe Commerce `products` query retorna detalhes sobre as SKUs especificadas como entrada. Embora esta consulta tenha o mesmo nome que a [`products` query](https://devdocs.magento.com//guides/v2.4/graphql/queries/products.html) que é fornecido com o Adobe Commerce principal e o Magento Open Source, há algumas diferenças.

A consulta do Serviço de catálogo requer um ou mais valores de SKU como entrada. O query foi desenvolvido principalmente para recuperar informações para renderizar os seguintes tipos de conteúdo:

* Páginas de detalhes do produto - Você pode fornecer detalhes completos sobre o produto identificado pelo SKU especificado.

* Páginas de comparação do produto - é possível recuperar informações selecionadas sobre vários produtos, como nome, preço e imagem.

O `ProductView` o objeto de saída é significativamente diferente do núcleo `products` query `Products` objeto de saída. As principais diferenças incluem:

* Os produtos são simples ou complexos. Os produtos simples, virtuais, baixáveis e de cartão-presente são mapeados para `SimpleProductView`. Todos os outros tipos de produtos são mapeados para `ComplexProductView`. Produtos simples têm preços definidos. Produtos complexos têm intervalos de preço. Uma vez que os produtos complexos são compostos por vários produtos simples, têm acesso a preços de produto simples.

* Os atributos definidos pelo comerciante são expostos em um contêiner de nível superior e indicam suas funções de vitrine. As funções incluem Mostrar na PDP, Mostrar na PLP e Mostrar nos Resultados da Pesquisa.

* As imagens também são acessíveis como um contêiner de nível superior e podem ser filtradas por sua função. Uma imagem pode ter uma função de base, pequena ou miniatura.

## Sintaxe

```graphql
products (skus [String]) [ProductView]
```

## Cabeçalhos obrigatórios

Você deve especificar os seguintes cabeçalhos HTTP para executar esta consulta.

| Cabeçalho | Descrição |
| --- | --- |
| `Magento-Customer-Group` | Para clientes da loja, esse valor estará disponível na loja na `dataservices_customer_group` cookie. |
| `Magento-Environment-Id` | Esse valor é exibido em **Sistema** > **Conector do Commerce Services** > **Identificador SaaS** > **ID do espaço de dados** ou pode ser obtida executando o `bin/magento config:show services_connector/services_id/environment_id` comando. |
| `Magento-Store-Code` | O código atribuído à loja associado à exibição de loja ativa. Por exemplo, `main_website_store`. |
| `Magento-Store-View-Code` | O código atribuído à exibição de loja ativa. Por exemplo, `default`. |
| `Magento-Website-Code` | O código atribuído ao site associado à exibição de loja ativa. Por exemplo, `base`. |
| `X-Api-Key` | Uma chave exclusiva gerada durante o processo de integração. |

## Exemplo de uso

### Retornar detalhes sobre um produto simples

A consulta a seguir retorna detalhes sobre um produto simples.

**Solicitação:**

```graphql
query {
  products(skus: ["24-MB02"]) {
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on SimpleProductView {
      price {
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
```

**Resposta:**

```json
{
  "data": {
    "products": [
      {
        "id": "TWpRdFRVSXdNZwBaR1ZtWVhWc2RBAE16UmxNamMwTUdFdE56UTNNeTAwWXpnNUxUZzNNekF0TlRjME1ETm1ZMlV5TjJGbABiV0ZwYmw5M1pXSnphWFJsWDNOMGIzSmwAWW1GelpRAFRVRkhVMVJITURBMU5UYzVNRE00",
        "sku": "24-MB02",
        "name": "Fusion Backpack 567890",
        "url": "http://example.com/fusion-backpack.html",
        "description": "<p>With the Fusion Backpack strapped on, every trek is an adventure - even a bus ride to work. That's partly because two large zippered compartments store everything you need, while a front zippered pocket and side mesh pouches are perfect for stashing those little extras, in case you change your mind and take the day off.</p>\r\n<ul>\r\n<li>Durable nylon construction.</li>\r\n<li>2 main zippered compartments.</li>\r\n<li>1 exterior zippered pocket.</li>\r\n<li>Mesh side pouches.</li>\r\n<li>Padded, adjustable straps.</li>\r\n<li>Top carry handle.</li>\r\n<li>Dimensions: 18\" x 10\" x 6\".</li>\r\n</ul>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "activity",
            "label": "Activity",
            "value": [
              "Hiking",
              "School",
              "Yoga"
            ],
            "roles": [
              "visible in PDP",
              "visible in compare list",
              "visible in Search"
            ]
          },
          {
            "name": "features_bags",
            "label": "Features",
            "value": [
              "Hydration Pocket",
              "Audio Pocket",
              "Waterproof",
              "Lightweight"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Burlap",
              "Nylon",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "strap_bags",
            "label": "Strap/Handle",
            "value": [
              "Adjustable",
              "Double",
              "Padded"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "style_bags",
            "label": "Style Bags",
            "value": [
              "Backpack",
              "Laptop"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          }
        ],
        "price": {
          "regular": {
            "amount": {
              "value": 59,
              "currency": "USD"
            }
          }
        }
      }
    ]
  }
}
```

### Retornar detalhes sobre um produto complexo {#complex-product-example}

A consulta a seguir retorna detalhes sobre um produto configurável.

**Solicitação:**

```graphql
query {
  products(skus: ["MH12"]) {
    __typename
    id
    sku
    name
    url
    description
    shortDescription
    attributes(roles: ["visible in Search"]) {
      name
      label
      value
      roles
    }
    ... on ComplexProductView {
      priceRange {
        maximum {
          regular {
            amount {
              value
              currency
            }
          }
        }
        minimum {
          regular {
            amount {
              value
              currency
            }
          }
        }
      }
      options {
        id
        required
        title
        values {
          id
          title
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
    "products": [
      {
        "__typename": "ComplexProductView",
        "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
        "sku": "MH12",
        "name": "Ajax Full-Zip Sweatshirt 2",
        "url": "http://example.com/ajax-full-zip-sweatshirt.html",
        "description": "<p>The Ajax Full-Zip Sweatshirt makes the optimal layering or outer piece for archers, golfers, hikers and virtually any other sportsmen. Not only does it have top-notch moisture-wicking abilities, but the tight-weave fabric also prevents pilling from repeated wash-and-wear cycles.</p>\r\n<p>&bull; Mint striped full zip hoodie.<br />&bull; 100% bonded polyester fleece.<br />&bull; Pouch pocket.<br />&bull; Rib cuffs and hem. <br />&bull; Machine washable.</p>",
        "shortDescription": "",
        "attributes": [
          {
            "name": "climate",
            "label": "Climate",
            "value": [
              "All-Weather",
              "Cool",
              "Indoor",
              "Spring",
              "Windy"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "customattribute",
            "label": "customAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          },
          {
            "name": "material",
            "label": "Material",
            "value": [
              "Fleece",
              "Polyester"
            ],
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "pattern",
            "label": "Pattern",
            "value": "Striped",
            "roles": [
              "visible in PDP",
              "visible in Search"
            ]
          },
          {
            "name": "testtttattribute",
            "label": "testtttAttribute",
            "value": "asd",
            "roles": [
              "visible in PDP",
              "visible in PLP",
              "visible in Search"
            ]
          }
        ],
        "priceRange": {
          "maximum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          },
          "minimum": {
            "regular": {
              "amount": {
                "value": 69,
                "currency": "USD"
              }
            }
          }
        },
        "options": [
          {
            "id": "color",
            "required": false,
            "title": "Color",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzU5",
                "title": "Blue"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzY3",
                "title": "Red"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzkzLzYy",
                "title": "Green"
              }
            ]
          },
          {
            "id": "size",
            "required": false,
            "title": "Size",
            "values": [
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzU=",
                "title": "XS"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzY=",
                "title": "S"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzc=",
                "title": "M"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzg=",
                "title": "L"
              },
              {
                "id": "Y29uZmlndXJhYmxlLzE4Ni8xNzk=",
                "title": "XL"
              }
            ]
          }
        ]
      }
    ]
  }
}
```

## Campos de saída

O `ProductView` o objeto return é uma interface que pode conter os seguintes campos. É implementado pela [`SimpleProductView`](#SimpleProductView-type) e [`ComplexProductView`](#ComplexProductView-type) tipos.

| Campo | Tipo de dados | Descrição |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | Uma lista de atributos definidos por comerciantes designados para a loja. |
| `description` | String | Descrição detalhada do produto. |
| `id` | ID! | A ID do produto, gerada como uma chave composta, exclusiva por localidade. |
| `images(roles: [String])` | [ProductViewImage] | Uma lista de imagens definidas para o produto. |
| `metaDescription` | String | Uma breve visão geral do produto para listagens dos resultados da pesquisa. |
| `metaKeyword` | String | Uma lista separada por vírgulas de palavras-chave que são visíveis apenas para mecanismos de pesquisa. |
| `metaTitle` | String | Uma string exibida na barra de título e na guia do navegador e nas listas de resultados da pesquisa. |
| `name` | String | Nome do produto. |
| `shortDescription` | String | Um resumo do produto. |
| `sku` | String | SKU do produto |
| `url` | String | URL canônico do produto. |

### Tipo ComplexProductView {#ComplexProductView-type}

O `ComplexProductView` representa produtos de pacote, configuráveis e de grupo. Preços complexos do produto são retornados como um intervalo de preço, pois os valores de preço podem variar com base nas opções selecionadas. O tipo implementa `ProductView`.

| Campo | Tipo de dados | Descrição |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | Uma lista de atributos definidos por comerciantes designados para a loja. |
| `description` | String | Descrição detalhada do produto. |
| `id` | ID! | A ID do produto, gerada como uma chave composta, exclusiva por localidade. |
| `images(roles: [String])` | [ProductViewImage] | Uma lista de imagens definidas para o produto. |
| `metaDescription` | String | Uma breve visão geral do produto para listagens dos resultados da pesquisa. |
| `metaKeyword` | String | Uma lista separada por vírgulas de palavras-chave que são visíveis apenas para mecanismos de pesquisa. |
| `metaTitle` | String | Uma string exibida na barra de título e na guia do navegador e nas listas de resultados da pesquisa. |
| `name` | String | Nome do produto. |
| `options` | [ProductViewOption] | Uma lista de opções selecionáveis. |
| `priceRange` | ProductViewPriceRange | Uma gama de preços possíveis para um produto complexo. |
| `shortDescription` | String | Um resumo do produto. |

### Tipo de preço

O `Price type` define o preço de um produto simples ou de uma parte de um intervalo de preços de um produto complexo. Pode incluir uma lista de ajustes de preço.

| Campo | Tipo de dados | Descrição |
|--- | --- | ---|
| `amount` | ProductViewMoney | Contém o valor monetário e o código monetário de um produto. |

### Tipo PriceAjuste

O `PriceAdjustment` especifica o montante e o tipo de um ajustamento de preços. Um exemplo de valor de código é `weee`.

| Campo | Tipo de dados | Descrição |
|--- | --- | ---|
| `amount` | Flutuar | O montante do ajustamento de preços. |
| `code` | String | Identifica o tipo de ajustamento de preços. |

### Tipo ProductViewAttribute

O `ProductViewAttribute` é um contêiner para atributos definidos pelo cliente que são exibidos na loja.

| Campo | Tipo de dados | Descrição |
|--- | --- | ---|
| `label` | String | Rótulo do atributo. |
| `name` | Corda! | Nome de um código de atributo. |
| `roles` | [String] | Funções designadas para um atributo na loja, como &quot;Mostrar na PLP&quot;, &quot;Mostrar na PDP&quot; ou &quot;Mostrar na pesquisa&quot;. |
| `value` | JSON | Valor do atributo, arbitrário do tipo . |

### Tipo ProductViewImage

O `ProductViewImage` contém detalhes sobre uma imagem de produto.

| Campo | Tipo de dados | Descrição |
|--- | --- | ---|
| `label` | String | O rótulo de exibição da imagem do produto. |
| `roles` | [String] | Uma lista que descreve como a imagem é usada. Pode ser `image`, `small_image`ou `thumbnail`. |
| `url` | Corda! | O URL para a imagem do produto. |

### Tipo ProductViewMoney

O `ProductViewMoney` define um valor monetário, incluindo um valor numérico e um código monetário.

| Campo | Tipo de dados | Descrição |
|--- | --- | ---|
| `currency` | ProductViewCurrency | Um código monetário de três letras, como USD ou EUR. |
| `value` | Flutuar | Um número que expressa um valor monetário. |

### Tipo ProductViewOption

As opções de produto fornecem uma maneira de configurar produtos fazendo seleções de valores de opção específicos. Selecionar uma ou várias opções apontará para um produto simples específico.

| Campo | Tipo de dados | Descrição |
|--- | --- | ---|
| `id` | ID | A ID da opção. |
| `multi` | Booleano | Indica se a opção permite várias opções. |
| `required` | Booleano | Indica se a opção deve ser selecionada. |
| `title` | String | O nome de exibição da opção. |
| `values` | [ProductViewOptionValue!] | Lista de valores de opção disponíveis. |

### Interface ProductViewOptionValue

O `ProductViewOptionValue` interface define os campos de produto disponíveis para a `ProductViewOptionValueProduct` e `ProductViewOptionValueConfiguration` tipos.

| Campo | Tipo de dados | Descrição |
|--- | --- | ---|
| `id` | ID | A ID de um valor de opção. |
| `title` | String | O nome de exibição do valor da opção. |

### Tipo ProductViewOptionValueConfiguration

O `ProductViewOptionValueConfiguration` é uma implementação de `ProductViewOptionValue` para valores de configuração.

| Campo | Tipo de dados | Descrição |
|--- | --- | ---|
| `id` | ID | A ID de um valor de opção. |
| `title` | String | O nome de exibição do valor da opção. |

### Tipo de produtoViewOptionValueProduct

O `ProductViewOptionValueProduct` é uma implementação de `ProductViewOptionValue` que adiciona detalhes sobre um produto simples.

| Campo | Tipo de dados | Descrição |
|--- | --- | ---|
| `id` | ID | A ID de um valor de opção. |
| `title` | String | O nome de exibição do valor da opção. |
| `product` | SimpleProductView | Detalhes sobre um produto simples. |

### Tipo ProductViewPrice

O `ProductViewPrice` O tipo fornece a visualização básica do preço do produto, inerente aos produtos simples.

| Campo | Tipo de dados | Descrição |
|--- | --- | ---|
| `final` | Preço | Valor de preço após descontos, excluindo promoções personalizadas. |
| `regular` | Preço | Preço base do produto especificado pelo comerciante. |
| `roles` | [String] | Determina se o preço deve estar visível ou oculto. |

### Tipo ProductViewPriceRange

O `ProductViewPriceRange` tipo lista o preço mínimo e máximo de um produto complexo.

| Campo | Tipo de dados | Descrição |
|--- | --- | ---|
| `maximum` | ProductViewPrice | Preço máximo. |
| `minimum` | ProductViewPrice | Preço mínimo. |

### Tipo SimpleProductView {#SimpleProductView-type}

O `SimpleProductView` representa todos os tipos de produto, exceto pacote, configurável e grupo. Os preços do produto simples não contêm intervalos de preços. `SimpleProductView` implementa `ProductView`.

| Campo | Tipo de dados | Descrição |
|--- | --- | ---|
| `attributes(roles: [String])` | [ProductViewAttribute] | Uma lista de atributos definidos por comerciantes designados para a loja. |
| `description` | String | Descrição detalhada do produto. |
| `id` | ID! | A ID do produto, gerada como uma chave composta, exclusiva por localidade. |
| `images(roles: [String])` | [ProductViewImage] | Uma lista de imagens definidas para o produto. |
| `metaDescription` | String | Uma breve visão geral do produto para listagens dos resultados da pesquisa. |
| `metaKeyword` | String | Uma lista separada por vírgulas de palavras-chave que são visíveis apenas para mecanismos de pesquisa. |
| `metaTitle` | String | Uma string exibida na barra de título e na guia do navegador e nas listas de resultados da pesquisa. |
| `name` | String | Nome do produto. |
| `price` | ProductViewPrice | Visualização básica de preço do produto. |
| `shortDescription` | String | Um resumo do produto. |
| `sku` | String | SKU do produto |
| `url` | String | URL canônico do produto. |
