---
title: "Estilo [!DNL Popover] Elementos"
description: "Notas técnicas sobre a personalização do [!DNL Live Search storefront popover]"
exl-id: 033049f2-976e-4299-b026-333ac4b481a3
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '203'
ht-degree: 0%

---

# Estilo [!DNL Popover] Elementos

A variável [[!DNL storefront popover]](storefront-popover.md) sempre exibe o produto `name` e `price`, e a seleção de campos não é configurável. No entanto, [!DNL popover] Os elementos podem ser estilizados usando classes CSS. Por exemplo, as declarações a seguir alteram a cor do plano de fundo do [!DNL popover] contêiner e rodapé

```css
.livesearch.popover-container {
    background-color: lavender;
}

.livesearch.view-all-footer {
    background-color: magenta;
}
```

## Visibilidade do contêiner

O componente principal do `.livesearch.popover-container` é `.search-autocomplete`.  A variável `.active` indica a visibilidade do container. A variável `.active` A classe é adicionada condicionalmente quando a variável [!DNL popover] está aberto.

```css
.search-autocomplete.active   /* visible */
.search-autocomplete          /* not visible */
```

Para obter mais informações sobre o estilo de elementos de vitrine, consulte [Folhas de estilos em cascata (CSS)](https://developer.adobe.com/commerce/frontend-core/guide/css/) no [Guia do desenvolvedor de front-end](https://developer.adobe.com/commerce/frontend-core/guide/).

## Seletores de classe

Os seletores de classe a seguir podem ser usados para estilizar os elementos de contêiner e produto no [!DNL popover].

* `.livesearch.popover-container`
* `.livesearch.view-all-footer`
* `.livesearch.products-container`
* `.livesearch.product-result`
* `.livesearch.product-name`
* `.livesearch.product-price`

### Seletores de classe de contêiner

#### .livesearch.popover-container

![[!DNL Popover] container](assets/livesearch-popover-container.png)

#### .livesearch.view-all-footer

![Exibir todos os rodapés](assets/livesearch-view-all-footer.png)

### Seletores de classe de produto

#### .livesearch.products-container

![Contêiner do produto](assets/livesearch-product-container.png)

#### .livesearch.product-result

![Resultado do produto](assets/livesearch-product-result.png)

#### .livesearch.product-name

![Nome do produto](assets/livesearch-product-name.png)

#### .livesearch.product-price

![Preço do produto](assets/livesearch-product-price.png)

## Trabalhar com um tema modificado {#working-with-modified-theme}

A variável [!DNL storefront popover] pode ser usado com um personalizado [tema](https://developer.adobe.com/commerce/frontend-core/guide/themes/) que herda os arquivos necessários de *Luma*. A variável `top.search` bloco no `header-wrapper` do `Magento_Search` o módulo não deve ser modificado.

```html
<referenceContainer name="header-wrapper">
   <block class="Magento\Framework\View\Element\Template" name="top.search" as="topSearch" template="Magento_Search::form.mini.phtml">
      <arguments>
         <argument name="configProvider" xsi:type="object">Magento\Search\ViewModel\ConfigProvider</argument>
      </arguments>
   </block>
</referenceContainer>
```

## Desativar o [!DNL popover]

Para desativar o [!DNL popover] e restaurar o padrão [Pesquisa rápida](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) insira o seguinte comando:

```bash
bin/magento module:disable Magento_LiveSearchStorefrontPopover
```
