---
title: Popover de frente de loja
description: A vitrine do Live Search retorna dinamicamente produtos sugeridos e miniaturas.
exl-id: 88fdc3ed-b606-40de-94b7-435be09c4072
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Popover de frente de loja

When [!DNL Live Search] é [instalado](install.md), uma tomada aparece na loja quando os compradores digitam na variável [Pesquisar](https://docs.magento.com/user-guide/catalog/search-quick.html) caixa. Com cada caractere digitado, o portátil é atualizado com produtos sugeridos e imagens em miniatura dos principais resultados da pesquisa.

[!DNL Live Search] retorna resultados para uma consulta de dois caracteres ou mais. Para uma correspondência parcial, o número máximo de caracteres por palavra é 20. O número de caracteres em uma consulta &quot;pesquisar à medida que você digita&quot; não é configurável.

>[!NOTE]
>
>O [!DNL Live Search] o fornecedor de vitrine está disponível somente para lojas que usam o *Luma* tema ou um tema personalizado baseado em *Luma*. O *Luma* o tema está incluído na variável [!DNL Commerce] dados de amostra. O provedor não suporta a variável *Em branco* tema. Consulte [Trabalhar com um tema modificado](#working-with-modified-theme) para obter mais informações.

## Atributos pesquisáveis

Para produzir resultados altamente direcionados, analise o conjunto de [pesquisável](https://docs.magento.com/user-guide/stores/attributes-product.html#storefront-properties) (`searchable=true`) atributos do produto. Para garantir a relevância, os atributos podem ser pesquisados somente se apresentarem conteúdo com um significado claro e conciso. Evite usar atributos que contenham texto menos preciso e longo, como `description`, que embora a pesquisa tenha sido habilitada por padrão, pode reduzir a precisão dos resultados da pesquisa. Por exemplo, se uma pessoa procurar por &quot;shorts&quot; e houver camisas com uma descrição que inclua o termo &quot;mangas curtas&quot;, as camisas serão incluídas nos resultados da pesquisa.

Os atributos a seguir sempre podem ser pesquisados:

* `sku`
* `name`
* `categories`

![Potência do Live Search](assets/storefront-search-as-you-type.png)
