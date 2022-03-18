---
title: Notas técnicas de faceta
description: Notas técnicas sobre o uso de facetas do Live Search.
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '158'
ht-degree: 0%

---

# Notas técnicas de faceta

Faceting é um método de filtragem de alto desempenho que usa várias dimensões de valores de atributos estáticos e dinâmicos pesquisáveis como critérios de pesquisa.

[!DNL Live Search] usa a variável `productSearch` query que retorna lapidamento e outros dados específicos de [!DNL Live Search]. Consulte [`productSearch` query](https://devdocs.magento.com/live-search/product-search.html) para exemplos de código.

## Agregação de facetas

A agregação de facetas é realizada da seguinte maneira se a loja tiver três facetas (categorias, cor e preço) e o comprador filtrar os três (cor = azul, preço é de US$ 10,00 a 50,00, categorias = `promotions`).

* `categories` agregação - Agregados `categories`, aplica-se `color` e `price` , mas não a variável `categories` filtro.
* `color` agregação - Agregados `color`, aplica-se `price` e `categories` , mas não a variável `color` filtro.
* `price` agregação - Agregados `price`, aplica-se `color` e `categories` , mas não a variável `price` filtro.

## Valores de atributo padrão

Os atributos de produto a seguir têm alguns [propriedades storefront](https://docs.magento.com/user-guide/stores/attributes-product.html) que são ativadas por padrão.

| Propriedade | Propriedade Storefront | Atributo |
|---|---|---|
| Classificável | Usado para Classificação na Lista de Produtos | `price` |
| Pesquisável | Usar na pesquisa | `price` <br />`sku`<br />`name` |
| FilterableInSearch | Usar na navegação em camadas - Filtrável (com resultados) | `price`<br />`visibility`<br />`category_name` |
