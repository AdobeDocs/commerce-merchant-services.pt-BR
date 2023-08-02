---
title: "Facetas"
description: "[!DNL Live Search] As facetas usam várias dimensões de valores de atributo como critérios de pesquisa."
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: 9cf48f6f900385a5cb772adee8834ec9cfe5ee13
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# Facetas

Faceting é um método de filtragem de alto desempenho que usa várias dimensões de valores de atributo como critérios de pesquisa. A pesquisa facetada é semelhante, mas consideravelmente &quot;mais inteligente&quot; do que o padrão [navegação em camadas](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html). A lista de filtros disponíveis é determinada pelo parâmetro [atributos filtráveis](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html#filterable-attributes) de produtos retornados nos resultados da pesquisa.

![Resultados da pesquisa filtrada](assets/storefront-search-results-run.png)

Qualquer faceta definida pode ser usada como um parâmetro de URL e os resultados serão filtrados com base nos valores de parâmetro: `http://yourstore.com?brand=acme&color=red`.

## Requisitos de facetagem

Os requisitos do atributo de categoria e produto para facetas são semelhantes aos atributos filtráveis usados para navegação em camadas. As propriedades de vitrine de cada atributo devem ser definidas como `filterable (with results)`.

[!DNL Live Search] suporta até:

* 100 atributos configurados como facetas
* 50 atributos classificáveis
* 200 atributos filtráveis
* 200 atributos pesquisáveis

| Configuração | Descrição |
|--- |--- |
| [Configurações de exibição de categoria](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/create/categories-display-settings.html) | Âncora - `Yes` |
| [Propriedades do atributo](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) | [Tipo de entrada de catálogo](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price`, `Visual swatch` (somente widget), `Text swatch` (somente widget) |
| Propriedades da vitrine do atributo | Usar na navegação em camadas dos resultados da pesquisa - `Yes` |

## Valores de atributo padrão

Os seguintes atributos de produto têm [propriedades da loja](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) que são usados por [!DNL Live Search] e ativado por padrão.

| Propriedade | Propriedade da vitrine | Atributo |
|---|---|---|
| Classificável | Usado para Classificação na Lista de Produtos | `price` |
| Pesquisável | Usar na pesquisa | `price` <br />`sku`<br />`name` |
| FiltrávelNaPesquisa | Uso na navegação em camadas - Filtrável (com resultados) | `price`<br />`visibility`<br />`category_name` |

## Propriedades de atributo não-sistema padrão

A tabela a seguir mostra a pesquisa padrão e as propriedades filtráveis de atributos não pertencentes ao sistema, incluindo aqueles específicos aos dados de amostra do Luma. Definição de *Usar na pesquisa* atribuir propriedade a `Yes` torna o atributo pesquisável em ambos [!DNL Live Search] e Adobe Commerce nativo.

| Código do atributo | Pesquisável | Usar na navegação em camadas |
|--- |--- |--- |
| atividade | Sim | Filtrável (com resultados) |
| attributes_brand | Sim | Não |
| marca | Sim | Não |
| clima | Sim | Filtrável (com resultados) |
| colar | Sim | Filtrável (com resultados) |
| cor | Sim | Filtrável (com resultados) |
| custo | Sim | Não |
| eco_collection | Sim | Filtrável (com resultados) |
| gênero | Sim | Filtrável (com resultados) |
| fabricante | Sim | Filtrável (com resultados) |
| material | Sim | Filtrável (com resultados) |
| finalidade | Sim | Filtrável (com resultados) |
| strap_bags | Sim | Filtrável (com resultados) |
| style_general | Sim | Filtrável (com resultados) |

## Propriedades padrão do atributo do sistema

A tabela a seguir mostra a pesquisa padrão e as propriedades filtráveis dos atributos do sistema.

| Código do atributo | Pesquisável | Usar na navegação em camadas |
|--- |--- |--- |
| allow_open_amount | Sim | Filtrável (com resultados) |
| descrição | Sim | Não |
| name | Sim | Não |
| preço | Sim | Filtrável (com resultados) |
| descrição_curta | Sim | Não |
| sku | Sim | Não |
| status | Sim | Não |
| tax_class_id | Sim | Não |
| url_key | Sim | Não |
| peso | Sim | Não |
