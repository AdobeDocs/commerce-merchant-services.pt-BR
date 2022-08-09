---
title: '"Aspectos"'
description: '"[!DNL Live Search] as facetas usam várias dimensões de valores de atributos como critérios de pesquisa."'
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: 40e7da1cb71bd3c977acb77714c2cab55b3b7bf8
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Aspectos

Faceting é um método de filtragem de alto desempenho que usa várias dimensões de valores de atributos como critérios de pesquisa. A pesquisa com facetas é semelhante, mas consideravelmente &quot;mais inteligente&quot; que o padrão [navegação em camadas](https://docs.magento.com/user-guide/catalog/navigation-layered.html). A lista de filtros disponíveis é determinada pela variável [atributos filtráveis](https://docs.magento.com/user-guide/catalog/navigation-layered-filterable-attributes.html) de produtos retornados nos resultados da pesquisa.

![Resultados da pesquisa filtrada](assets/storefront-search-results-run.png)

## Requisitos de aspecto

Os requisitos de atributo de categoria e produto para lapidação são semelhantes aos atributos filtráveis usados para navegação em camadas. As propriedades de loja de cada atributo devem ser definidas como `filterable (with results)`.

O Live Search suporta até:

* 100 atributos configurados como facetas
* 50 atributos classificáveis
* 200 atributos filtráveis
* 200 atributos pesquisáveis

| Configuração | Descrição |
|--- |--- |
| [Configurações de exibição de categoria](https://docs.magento.com/user-guide/catalog/categories-display-settings.html) | Âncora - `Yes` |
| [Propriedades do atributo](https://docs.magento.com/user-guide/stores/attribute-product-create.html) | [Tipo de entrada do catálogo](https://docs.magento.com/user-guide/stores/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price` |
| Propriedades da vitrine de atributos | Usar na navegação em camadas dos resultados da pesquisa - `Yes` |

## Valores de atributo padrão

Os atributos de produto a seguir têm [propriedades storefront](https://docs.magento.com/user-guide/stores/attributes-product.html) que são usados por [!DNL Live Search] e ativadas por padrão.

| Propriedade | Propriedade Storefront | Atributo |
|---|---|---|
| Classificável | Usado para Classificação na Lista de Produtos | `price` |
| Pesquisável | Usar na pesquisa | `price` <br />`sku`<br />`name` |
| FilterableInSearch | Usar na navegação em camadas - Filtrável (com resultados) | `price`<br />`visibility`<br />`category_name` |

## Propriedades de atributos não-sistema padrão

A tabela a seguir mostra as propriedades de filtragem e pesquisa padrão de atributos que não são do sistema, incluindo aqueles específicos aos dados de amostra do Luma. Definir a *Usar na pesquisa* propriedade de atributo para `Yes` torna o atributo pesquisável em ambos [!DNL Live Search] e Adobe Commerce nativo.

| Código do atributo | Pesquisável | Usar na navegação em camadas |
|--- |--- |--- |
| atividade | Sim | Filtrável (com resultados) |
| attributes_brand | Sim | Não |
| marca | Sim | Não |
| clima | Sim | Filtrável (com resultados) |
| coleira | Sim | Filtrável (com resultados) |
| color | Sim | Filtrável (com resultados) |
| custo | Sim | Não |
| eco_collection | Sim | Filtrável (com resultados) |
| gênero | Sim | Filtrável (com resultados) |
| fabricante | Sim | Filtrável (com resultados) |
| material | Sim | Filtrável (com resultados) |
| propósito | Sim | Filtrável (com resultados) |
| strap_bag | Sim | Filtrável (com resultados) |
| style_general | Sim | Filtrável (com resultados) |

## Propriedades padrão do atributo do sistema

A tabela a seguir mostra as propriedades de filtragem e pesquisa padrão dos atributos do sistema.

| Código do atributo | Pesquisável | Usar na navegação em camadas |
|--- |--- |--- |
| allow_open_amount | Sim | Filtrável (com resultados) |
| descrição | Sim | Não |
| name | Sim | Não |
| preço | Sim | Filtrável (com resultados) |
| short_description | Sim | Não |
| sku | Sim | Não |
| status | Sim | Não |
| tax_class_id | Sim | Não |
| url_key | Sim | Não |
| peso | Sim | Não |
