---
title: "[!DNL Storefront Popover]"
description: "O [!DNL Live Search storefront popover] retorna dinamicamente produtos sugeridos e miniaturas."
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# [!DNL Storefront Popover]

When [!DNL Live Search] é [instalado](install.md), a [!DNL popover] aparece na loja quando os compradores digitam o [Pesquisar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) caixa. Com cada caractere digitado, a variável [!DNL popover] O é atualizado com produtos sugeridos e imagens em miniatura dos principais resultados de pesquisa.

[!DNL Live Search] retorna resultados para uma consulta de dois caracteres ou mais. Para uma correspondência parcial, o número máximo de caracteres por palavra é 20. O número de caracteres em uma consulta &quot;pesquisar à medida que você digita&quot; não é configurável.

>[!NOTE]
>
>O [!DNL Live Search] [!DNL storefront popover] está disponível somente para lojas que usam o *Luma* tema ou um tema personalizado baseado em *Luma*. O *Luma* o tema está incluído na variável [!DNL Commerce] dados de amostra. O [!DNL popover] não suporta o *Em branco* tema. Consulte [Estilo [!DNL Popover] Elementos](storefront-popover-styling.md) para saber mais.

## Atributos pesquisáveis

Para produzir resultados altamente direcionados, analise o conjunto de [pesquisável](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`) atributos do produto. Para garantir a relevância, os atributos podem ser pesquisados somente se apresentarem conteúdo com um significado claro e conciso. Evite usar atributos que contenham texto menos preciso e longo, como `description`, que embora a pesquisa tenha sido habilitada por padrão, pode reduzir a precisão dos resultados da pesquisa. Por exemplo, se uma pessoa procurar por &quot;shorts&quot; e houver camisas com uma descrição que inclua o termo &quot;mangas curtas&quot;, as camisas serão incluídas nos resultados da pesquisa.

Os atributos a seguir sempre podem ser pesquisados:

* `sku`
* `name`
* `categories`

[[!DNL Live Search popover]](assets/storefront-search-as-you-type.png)

## [!DNL Popover] tamanho da página

O tamanho da página do [!DNL popover] determina quantas linhas de produtos autopreenchidos podem ser retornadas. Anteriormente, o tamanho da página era codificado como seis linhas. No entanto, a variável `page_size` agora é uma configuração que pode ser configurada no *Administrador*. Durante a instalação do Live Search, a variável `page_size` O valor é alterado para o valor atual da variável [Pesquisa no catálogo](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/catalog.html) - `Autocomplete Limit` configuração.

Por padrão, o valor de Limite de Conclusão Automática - Pesquisa no Catálogo é definido como oito linhas (ou linhas). Para alterar o tamanho da página do [!DNL popover], faça o seguinte:

1. No *Administrador* barra lateral, vá para **Lojas** > Configurações > **Configuração**.
1. No painel esquerdo, expanda **Catálogo** e escolha **Catálogo** na lista de configurações.
1. Expanda o *Pesquisa no catálogo* seção.
1. Defina as **Limite de preenchimento automático** para o número de linhas que você deseja permitir no [!DNL popover].
1. Ao concluir, clique em **Salvar configuração**.
