---
title: "Facetas"
description: "[!DNL Live Search] As facetas usam várias dimensões de valores de atributo como critérios de pesquisa."
exl-id: 63c0b255-6be9-41ad-b4bf-13bb7ff098fd
source-git-commit: a8643ca9567feb7dde67358eeae321825b0253f2
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%

---

# Facetas

Faceting é um método de filtragem de alto desempenho que usa várias dimensões de valores de atributo como critérios de pesquisa. A pesquisa facetada é semelhante, mas consideravelmente &quot;mais inteligente&quot; do que o padrão [navegação em camadas](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html). A lista de filtros disponíveis é determinada pelo parâmetro [atributos filtráveis](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation-layered.html#filterable-attributes) de produtos retornados nos resultados da pesquisa.

[!DNL Live Search] usa o `productSearch` consulta, que retorna facetas e outros dados específicos de [!DNL Live Search]. Consulte [`productSearch` query](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) na documentação do desenvolvedor para obter exemplos de código.

![Resultados da pesquisa filtrada](assets/storefront-search-results-run.png)

Qualquer faceta definida pode ser usada como um parâmetro de URL e os resultados serão filtrados com base nos valores de parâmetro: `http://yourstore.com?brand=acme&color=red`.

## Requisitos de facetagem

Os requisitos do atributo de categoria e produto para facetas são semelhantes aos atributos filtráveis usados para navegação em camadas. As propriedades de vitrine de cada atributo devem ser definidas como `filterable (with results)`.

[!DNL Live Search] suporta até:

* 100 atributos configurados como facetas
* 50 atributos classificáveis
* 200 atributos filtráveis
* 200 atributos pesquisáveis

>[!NOTE]
>
> Se houver mais de 200 atributos filtráveis definidos, não é determinístico quais 200 serão realmente indexados.

Se você tiver um grande número de atributos com os quais lidar, considere combinar atributos em um único &quot;metatributo&quot;. Por exemplo, sapatos geralmente têm tamanhos numéricos, enquanto camisas são comumente dimensionadas &quot;S/M/L/XL&quot;. Esses dois tipos de tamanhos podem ser combinados em um único atributo pesquisável.

| Configuração | Descrição |
|--- |--- |
| [Configurações de exibição de categoria](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/create/categories-display-settings.html) | Âncora - `Yes` |
| [Propriedades do atributo](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) | [Tipo de entrada de catálogo](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) - `Yes/No`, `Dropdown`, `Multiple Select`, `Price`, `Visual swatch` (somente widget), `Text swatch` (somente widget) |
| Propriedades da vitrine do atributo | Usar na navegação em camadas dos resultados da pesquisa - `Yes` |

## Agregação de facetas

A agregação de facetas é executada da seguinte maneira: se a loja tiver três facetas (categorias, cor e preço) e os filtros do comprador nos três (cor = azul, preço vai de US$ 10,00 a US$ 50,00, categorias = `promotions`).

* `categories` agregação - Agregados `categories`, aplica a variável `color` e `price` filtros, mas não os `categories` filtro.
* `color` agregação - Agregados `color`, aplica a variável`price` e `categories` filtros, mas não os `color` filtro.
* `price` agregação - Agregados `price`, aplica a variável `color` e `categories` filtros, mas não os `price` filtro.

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
