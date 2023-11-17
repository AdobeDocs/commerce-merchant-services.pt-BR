---
title: "[!DNL Storefront Popover]"
description: "O [!DNL Live Search storefront popover] retorna dinamicamente os produtos e miniaturas sugeridos."
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: c77b2f9cb55d3eb339dcc900ce606b94c592f559
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# [!DNL Storefront Popover]

Quando [!DNL Live Search] é [instalado](install.md), um [!DNL popover] aparece na loja quando os compradores digitam na [Pesquisar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) caixa. Com cada caractere digitado, a variável [!DNL popover] O é atualizado com produtos sugeridos e imagens em miniatura dos principais resultados da pesquisa.

[!DNL Live Search] retorna resultados para uma consulta de dois caracteres ou mais. Para uma correspondência parcial, o número máximo de caracteres por palavra é 20. O número de caracteres em uma consulta &quot;pesquisar ao digitar&quot; não é configurável.

Por padrão, [!DNL Live Search] suporta [redirecionamentos de termo de pesquisa](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html).

![[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## Atributos pesquisáveis

Para produzir resultados altamente direcionados, revise o conjunto de [pesquisável](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`) atributos do produto. Para garantir relevância, torne os atributos pesquisáveis somente se eles tiverem conteúdo com significado claro e conciso. Evite usar atributos que contenham texto menos preciso e longo, como `description`, que embora ativadas por padrão para pesquisa, podem reduzir a precisão dos resultados da pesquisa.
Por exemplo, se uma pessoa procurar por &quot;shorts&quot; e houver camisas com uma descrição que inclua o termo &quot;mangas curtas&quot;, as camisas serão incluídas nos resultados da pesquisa.

[!DNL Live Search] respeita igualmente a [peso](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html#weighted-search) de um atributo de produto, conforme definido no Adobe Commerce. Atributos com um peso maior aparecerão mais altos nos resultados da pesquisa.

Os seguintes atributos são sempre pesquisáveis:

* `sku`
* `name`
* `categories`

## [!DNL Popover] tamanho da página

O tamanho da página de [!DNL popover] determina quantas linhas de produtos preenchidos automaticamente podem ser devolvidas. Anteriormente, o tamanho da página era codificado como seis linhas. No entanto, a `page_size` agora, o valor é uma configuração que pode ser definida no *Admin*. Durante a instalação do Live Search, a variável `page_size` O valor de é alterado para o valor atual do [Pesquisa no catálogo](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` configuração.

Por padrão, o valor Pesquisa no catálogo - Limite de preenchimento automático é definido como oito linhas (ou linhas). Para alterar o tamanho da página de [!DNL popover], faça o seguinte:

1. No *Admin* barra lateral, vá para **Lojas** > Configurações > **Configuração**.
1. No painel esquerdo, expanda **Catálogo** e escolha **Catálogo** na lista de configurações.
1. Expanda a *Pesquisa no catálogo* seção.
1. Defina o **Limite de preenchimento automático** ao número de linhas que você deseja permitir na variável [!DNL popover].
1. Quando terminar, clique em **Salvar configuração**.

## Serviço de catálogo

A variável [Serviço de catálogo do Adobe Commerce](../catalog-service/overview.md) A extensão do fornece dados avançados de catálogo do modelo de visualização para renderizar de maneira rápida e completa as experiências da loja relacionadas ao produto. O Serviço de catálogo pode ser usado em conjunto com o Live Search para fornecer funcionalidades que atualmente não são compatíveis com a extensão nativa:

* Atributos estendidos
* Outras informações sobre o produto podem ser trazidas

Os comerciantes podem personalizar e estender widgets ou elementos de vitrine usando o Serviço de catálogo, mas isso está fora do escopo da equipe de suporte do Adobe.

## Implementações headless

Para aqueles com implementações headless, é possível instalar o popover do Live Search com um [pacote npm](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).

## Limitação

* A variável [!DNL Live Search] [!DNL storefront popover] está disponível somente para lojas que usam o *Luma* tema ou um tema personalizado baseado em *Luma*. As navegações estruturais na página de resultados da pesquisa não terão *Luma* estilo.
* A variável [!DNL popover] não suporta o *Em branco* tema. Consulte [Estilo [!DNL Popover] Elementos](storefront-popover-styling.md) para saber mais.
* A variável [!DNL popover] não é suportado no formulário Pedido rápido.
* As listas de desejos e as comparações de produtos não são compatíveis.
