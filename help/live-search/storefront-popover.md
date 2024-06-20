---
title: "[!DNL Storefront Popover]"
description: "O [!DNL Live Search storefront popover] retorna dinamicamente os produtos e miniaturas sugeridos."
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: e375404a50dd4972ab584f69d7953aba2c8f4566
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# [!DNL Storefront Popover]

Quando [!DNL Live Search] é [instalado](install.md), um [!DNL popover] aparece na loja quando os compradores digitam na [Pesquisar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) caixa. Com cada caractere digitado, a variável [!DNL popover] O é atualizado com produtos sugeridos e imagens em miniatura dos principais resultados da pesquisa.

[!DNL Live Search] retorna resultados para uma consulta de dois caracteres ou mais. Para uma correspondência parcial, o número máximo de caracteres por palavra é 20. O número de caracteres em uma consulta &quot;pesquisar ao digitar&quot; não é configurável.

Por padrão, [!DNL Live Search] suporta [redirecionamentos de termo de pesquisa](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

>[!TIP]
>
>Saiba como definir atributos de produto como pesquisáveis no [Configuração do Live Search](workspace.md) artigo.

## [!DNL Popover] tamanho da página

O tamanho da página de [!DNL popover] determina quantas linhas de produtos preenchidos automaticamente podem ser devolvidas. Durante a instalação do Live Search, a variável `page_size` O valor de é alterado para o valor atual do [Pesquisa no catálogo](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` configuração.

Por padrão, o valor Pesquisa no catálogo - Limite de preenchimento automático é definido como oito linhas (ou linhas). Para alterar o tamanho da página de [!DNL popover], faça o seguinte:

1. No *Admin* barra lateral, vá para **Lojas** > Configurações > **Configuração**.
1. No painel esquerdo, expanda **Catálogo** e escolha **Catálogo** na lista de configurações.
1. Expanda a *Pesquisa no catálogo* seção.
1. Defina o **Limite de preenchimento automático** ao número de linhas que você deseja permitir na variável [!DNL popover].
1. Quando terminar, clique em **Salvar configuração**.

## Estilo [!DNL Popover] exemplo

Você pode personalizar a aparência da [!DNL Popover] para corresponder ao estilo e às diretrizes de marca da sua empresa.

A variável [!DNL storefront popover] sempre exibe o produto `name` e `price`, e a seleção de campos não é configurável. No entanto, [!DNL popover] os elementos podem ser estilizados usando [CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/) classes. Por exemplo, as declarações a seguir alteram a cor do plano de fundo do [!DNL popover] contêiner e rodapé

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

Você pode usar os seguintes seletores de classe para estilizar o contêiner e os elementos de produto no [!DNL popover].

- `.livesearch.popover-container`
- `.livesearch.view-all-footer`
- `.livesearch.products-container`
- `.livesearch.product-result`
- `.livesearch.product-name`
- `.livesearch.product-price`

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

#### link do produto .livesearch

![Resultado do produto](assets/livesearch-product-link.png)

## Trabalhar com um tema modificado {#working-with-modified-theme}

Você pode usar o [!DNL storefront popover] com um personalizado [tema](https://developer.adobe.com/commerce/frontend-core/guide/themes/) que herda os arquivos necessários de *Luma*. A variável `top.search` bloco no `header-wrapper` do `Magento_Search` o módulo não deve ser modificado.

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

## Implementações headless

Para aqueles com implementações headless, você pode instalar o [!DNL Live Search popover] usando um [pacote npm](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
