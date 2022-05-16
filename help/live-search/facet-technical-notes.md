---
title: '"Notas técnicas de faceta"'
description: '"Notas técnicas sobre o uso de [!DNL Live Search] facetas."'
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '112'
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
