---
title: Widget da página de listagem de produtos
description: Ativação e estilo do [!DNL Live Search Product Listing Page Widget]
exl-id: f7346a06-a8c7-4a33-8437-ea4f61d9281f
source-git-commit: c77b2f9cb55d3eb339dcc900ce606b94c592f559
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# Widget da página de listagem de produtos

A variável [!DNL Live Search Product Listing Page Widget] (PLP) usa a plataforma Commerce Services para fornecer uma página de listagem de produtos com desempenho, pesquisável e facetável. Este tópico descreve como ativar e estilizar o widget PLP.

## Ativar o dispositivo PLP

Quando a variável [!DNL Live Search] estiver instalado, a funcionalidade de pesquisa padrão será convertida em [!DNL Live Search] automaticamente.

A variável [!DNL Live Search] O widget PLP é habilitado por padrão para novas instalações. Se você estiver atualizando [!DNL Live Search] e o widget PLP já foi desligado, ele permanecerá assim.

Para desativar o dispositivo PLP:

1. Ir para **Lojas** > Configurações > **Configuração** > **[!DNL Live Search]** > **Recursos da loja** e defina **Ativar widgets de listagem de produtos** para &quot;Não&quot;.
1. Selecionar **Salvar configuração** para salvar a configuração.

## Exemplo de estilo

Você pode personalizar a aparência do widget PLP para corresponder ao seu site usando [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/).

>[!NOTE]
>
>Elementos com classes personalizadas em um tema do Adobe Commerce não são herdados. Esses elementos devem ser direcionados por sua classe específica para corresponder às classes personalizadas; as classes de ação principais não funcionarão em um botão de widget.
>Os elementos direcionados genéricos dentro do CSS são herdados; `button` aplica-se a botões de widget.

Os divs destacados contêm a classe de destino `ds-sdk-product-item__product-name`.

![Paginação](assets/plp-css-example.png)

Personalize o nome do produto adicionando uma regra para torná-lo em letras maiúsculas.

```css
.ds-sdk-product-item__product-name {
 text-transform: uppercase;
}
```

![Paginação](assets/plp-css-example-after.png)

## Classes CSS

### Lista de produtos

* `.ds-sdk-product-list`: div externa
* `.ds-sdk-product-list__grid`: div interna

![Paginação](assets/plp-css-product-list.png)

#### Paginação de lista de produtos

* `.ds-plp-pagination`

![Paginação](assets/plp-css-pagination.png)

* `.ds-plp-pagination_item`

![Item de paginação](assets/plp-css-pagination-item.png)

* `.ds-plp-pagination_item--current`

![Paginação do item atual](assets/plp-css-pagination-item-current.png)

### Widgets

* `.ds-widgets`: div externa
* `.ds-widgets__actions`: div interna do lado esquerdo
* `.ds-widgets__results`: div interna do lado direito

![Resultados do widget](assets/plp-css-widgets.png)

### Lista suspensa Classificar

* `.ds-sdk-sort-dropdown`

![Lista suspensa Classificar](assets/plp-css-dropdown.png)

* `.ds-sdk-sort-dropdown__button`

![Botão suspenso](assets/plp-css-dropdown-button.png)

* `.ds-sdk-sort-dropdown__items`

![Itens suspensos](assets/plp-css-dropdown-items.png)

* `.ds-sdk-sort-dropdown__items--item`

![Item suspenso](assets/plp-css-dropdown-item.png)

* `.ds-sdk-sort-dropdown__items--item-selected`

![Lista suspensa de itens selecionados](assets/plp-css-dropdown-selected.png)

* `.ds-sdk-sort-dropdown__items--item-active`

![Seleção ativa suspensa](assets/plp-css-dropdown-active.png)

### Facetas

* `.ds-plp-facets`
* `.ds-plp-facets__header`
* `.ds-plp-facets__header_title`
* `.ds-plp-facets__header__clear-all`

![Título do cabeçalho do Facets](assets/plp-css-facets-title-clear.png){width="350"}

* `.ds-plp-facets__pills`
* `.ds-sdk-pill`

![Pílulas faciais](assets/plp-css-facets-pill.png){width="350"}

* `.ds-sdk-pill__label`
* `.ds-sdk-pill__cta`

![Rótulo de facetas](assets/plp-css-pill-label-cta.png){width="350"}

* `.ds-plp-facets__list`

![Lista de aspectos](assets/plp-css-facets-list.png){width="350"}

* `.ds-sdk-input`
* `.ds-sdk-input__label`
* `.ds-sdk-product-item__product-swatch-group`
* `ds-sdk-product-item__product-swatch-item`
* `.ds-sdk-input_fieldset_show-more`

![Entrada](assets/plp-css-sdk-input.png)

* `.ds-sdk-labelled-input`

![Entrada rotulada](assets/plp-css-labelled-input.png)

* `.ds-sdk-labelled-input__input`
* `.ds-sdk-labelled-input__label`

![Rótulo de entrada](assets/plp-css-labelled-input-label.png)

### Item do produto

* `.ds-sdk-product-item`
* `.ds-sdk-product-item__image`
* `.ds-sdk-product-item__product-name`
* `.ds-sdk-product-item__product-options`
* `.ds-sdk-product-price`
   * `.ds-sdk-product-price--no-discount`
   * `.ds-sdk-product-price--grouped`
   * `.ds-sdk-product-price--bundle`
   * `.ds-sdk-product-price--discount`

![Produto](assets/plp-css-product.png)

### Carregando

* `.ds-sdk-loading`
* `.ds-sdk-loading__spinner`
* `.ds-sdk-loading__spinner-label`

![Carregando indicador](assets/plp-css-loading.png)
