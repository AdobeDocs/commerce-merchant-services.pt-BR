---
title: "Tour rápido"
description: "Faça um rápido tour pelo [!DNL Live Search] da loja."
exl-id: bcb19506-6617-4c8a-83df-9d961f81e9e8
source-git-commit: 9f045a049ac775ed4673e807ab5e21b8811cde2d
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Tour rápido

Com foco na velocidade, relevância e facilidade de uso, [!DNL Live Search] O é um divisor de águas tanto para compradores quanto para comerciantes. Siga para um rápido tour pelo [!DNL Live Search] da loja.

## Pesquisar enquanto digita

[!DNL Live Search] O responde com produtos sugeridos e uma imagem em miniatura dos principais resultados da pesquisa em uma [popover](storefront-popover.md) à medida que os compradores digitam consultas na variável [Pesquisar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) caixa. A variável [detalhes do produto](https://experienceleague.adobe.com/docs/commerce-admin/start/storefront/storefront.html#product-page) é exibida quando os compradores clicam em um produto sugerido ou em destaque. A _Exibir todos_ no rodapé do popover exibe a página de resultados da pesquisa.

[!DNL Live Search] retorna resultados de &quot;pesquisa ao digitar&quot; para uma consulta de dois ou mais caracteres. Para uma correspondência parcial, o número máximo de caracteres por palavra é 20. O número de caracteres na consulta não é configurável. Os seguintes campos estão incluídos no popover: `name`, `sku`, e `category_ids`.

![Exemplo de vitrine - pesquisar à medida que você digita](assets/storefront-search-as-you-type.png)

## Exibir todos os resultados da pesquisa

Para listar todos os produtos retornados pela consulta &quot;pesquisar ao digitar&quot;, clique em _Exibir todos_ no rodapé do popover.

![Exemplo de vitrine - aspectos de preço](assets/storefront-view-all-search-results.png)

## Pesquisa filtrada com facetas

A pesquisa filtrada usa várias dimensões de valores de atributo ou [facetas](facets.md), como critério de pesquisa. A seleção de filtros é definida pelo comerciante e muda de acordo com os produtos retornados, com as facetas mais usadas fixadas no topo da lista.

Usar facetas como parâmetros de URL:`http://yourwebsite.com?color=red`, e o Live Search filtra os resultados com base nesses valores de atributo.

## Sinônimos

[Sinônimos](synonyms.md) expanda o alcance e ajuste a nitidez do foco das consultas ao incluir palavras que os compradores podem usar diferentes daquelas no catálogo. Você pode ajustar o dicionário de sinônimo para manter os compradores envolvidos e no caminho para comprar.

## Regras de merchandising

Merchandising [regras](rules.md) molde a experiência de compra com instruções if-then que adicionam lógica e eventos a serem pesquisados. Você pode facilmente impulsionar ou enterrar produtos para uma promoção, temporada ou outro período de tempo.

## Suporte a termos de pesquisa

[!DNL Live Search] oferece suporte ao Commerce [redirecionamentos de termo de pesquisa](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html). Por exemplo, os usuários podem procurar por um termo como &quot;Taxas de envio&quot; e ser direcionados diretamente para a página de taxas de envio.
