---
title: consulta refineProduct
description: '"Um guia de referência para a consulta GraphQL "refineProduct" para o serviço de catálogo do Adobe Commerce."'
source-git-commit: 7edfdd71c0900a6bdc7c064a29a6cce405a361ab
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# consulta refineProduct

O `refineProduct` consulta reduz os resultados de um `products` que foi executada em relação a um produto complexo. Antes de executar o `refineProduct` você deve executar o `products` e construa a resposta para que ela retorne uma lista de `options` em `ComplexProductView` fragmento em linha. Quando um comprador selecionar uma opção de produto (como tamanho ou cor) na loja, execute o `refineProduct` , especificando o SKU e as IDs de valor de opção selecionadas como entrada. Dependendo do número de opções do produto complexo, talvez seja necessário executar o `refineProduct` consulte várias vezes, até que o comprador tenha selecionado uma variante específica.

Você deve construir a resposta de sua query de modo que ela contenha ambos os parâmetros `ComplexProductView` e `SimpleProductView` fragmentos em linha. Se o comprador não tiver selecionado todas as opções necessárias, o query retornará as IDs das opções não selecionadas e o preço mínimo e máximo do produto, com base nas opções selecionadas e nas possíveis opções restantes. Se o comprador selecionou todas as opções necessárias, a query retorna detalhes sobre um produto simples, que inclui um preço definido.

## Sintaxe

```graphql
refineProduct(sku: String!, optionIds: [String!]!): ProductView
```

## Cabeçalhos obrigatórios

Você deve especificar os seguintes cabeçalhos HTTP para executar esta consulta.

| Cabeçalho | Descrição |
|--- | ---|
| `Magento-Customer-Group` | Para clientes da loja, esse valor estará disponível na loja na `dataservices_customer_group` cookie. |
| `Magento-Environment-Id` | Esse valor é exibido em **Sistema** > **Conector do Commerce Services** > **Identificador SaaS** > **ID do espaço de dados** ou pode ser obtida executando o `bin/magento config:show services_connector/services_id/environment_id` comando. |
| `Magento-Store-Code` | O código atribuído à loja associado à exibição de loja ativa. Por exemplo, `main_website_store`. |
| `Magento-Store-View-Code` | O código atribuído à exibição de loja ativa. Por exemplo, `default`. |
| `Magento-Website-Code` | O código atribuído ao site associado à exibição de loja ativa. Por exemplo, `base`. |
| `X-Api-Key` | Uma chave exclusiva gerada durante o processo de integração. |

## Exemplo de uso

### Retornar detalhes sobre um produto complexo parcialmente selecionado

A consulta a seguir retorna detalhes sobre as opções de cor disponíveis para uma variante de produto de médio porte `MH12`. O valor da variável `optionIDs` o parâmetro de entrada é retirado do `products` query&#39;s [Retornar detalhes sobre um produto complexo](products.md#complex-product-example) exemplo.

**Solicitação:**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc="], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
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
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
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
    "refineProduct": {
      "__typename": "ComplexProductView",
      "id": "VFVneE1nAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12",
      "name": "Ajax Full-Zip Sweatshirt 2",
      "url": "http://example.com/ajax-full-zip-sweatshirt.html",
      "options": [
        {
          "id": "color",
          "title": "Color",
          "required": false,
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
        }
      ],
      "priceRange": {
        "maximum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        },
        "minimum": {
          "final": {
            "amount": {
              "value": 69
            }
          },
          "regular": {
            "amount": {
              "value": 69
            }
          }
        }
      }
    }
  }
}
```

### Retornar detalhes sobre um produto complexo totalmente selecionado

Na consulta a seguir, o comprador selecionou opções para tamanho e cor. A resposta contém detalhes sobre o produto simples correspondente.

**Solicitação:**

```graphql
query {
    refineProduct(optionIds: ["Y29uZmlndXJhYmxlLzE4Ni8xNzc=", "Y29uZmlndXJhYmxlLzkzLzU5"], sku: "MH12") {
        __typename
        id
        sku
        name
        url
        ... on SimpleProductView {
            price {
                final {
                    amount {
                        value
                    }
                }
                regular {
                    amount {
                        value
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
                        }
                    }
                    regular {
                        amount {
                            value
                        }
                    }
                }
                minimum {
                    final {
                        amount {
                            value
                        }
                    }
                    regular {
                        amount {
                            value
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
    "refineProduct": {
      "__typename": "SimpleProductView",
      "id": "VFVneE1pMU5MVUpzZFdVAFpHVm1ZWFZzZEEATXpSbE1qYzBNR0V0TnpRM015MDBZemc1TFRnM016QXROVGMwTURObVkyVXlOMkZsAGJXRnBibDkzWldKemFYUmxYM04wYjNKbABZbUZ6WlEAVFVGSFUxUkhNREExTlRjNU1ETTQ",
      "sku": "MH12-M-Blue",
      "name": "Ajax Full-Zip Sweatshirt -M-Blue",
      "url": "http://example.com/catalog/product/view/id/235/s/ajax-full-zip-sweatshirt-m-blue/",
      "price": {
        "final": {
          "amount": {
            "value": 69
          }
        },
        "regular": {
          "amount": {
            "value": 69
          }
        }
      }
    }
  }
}
```

## Campos de entrada

Você deve especificar um valor de SKU e pelo menos uma ID de opção como entrada.

| Campo | Tipo de dados | Descrição |
|--- | --- | ---|
| `optionIds` | [Corda!]! | Uma lista de IDs atribuídas às opções de produto selecionadas pelo comprador, como cores e tamanhos específicos. |
| `sku` | Corda! | O SKU de um produto complexo. |

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
