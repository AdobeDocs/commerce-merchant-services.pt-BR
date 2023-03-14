---
title: "Notas técnicas da Facet"
description: "Notas técnicas sobre o uso de [!DNL Live Search] aspectos."
exl-id: 37982610-0ff7-48b7-b088-be7d2eff8a57
source-git-commit: 995f528abc0011c6ae7c4c524982c301072ec2eb
workflow-type: tm+mt
source-wordcount: '123'
ht-degree: 0%

---

# Notas técnicas da Facet

Faceting é um método de filtragem de alto desempenho que usa várias dimensões de valores de atributo estáticos e dinâmicos pesquisáveis como critérios de pesquisa.

[!DNL Live Search] usa o `productSearch` consulta que retorna facetas e outros dados específicos para [!DNL Live Search]. Consulte [`productSearch` query](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) para obter exemplos de código.

## Agregação de facetas

A agregação de facetas é executada da seguinte maneira: se a loja tiver três facetas (categorias, cor e preço) e os filtros do comprador em todas as três (cor = azul, preço vai de US$ 10,00 a US$ 50,00, categorias = `promotions`).

* `categories` agregação - Agregados `categories`, aplica a variável `color` e `price` filtros, mas não os `categories` filtro.
* `color` agregação - Agregados `color`, aplica a variável`price` e `categories` filtros, mas não os `color` filtro.
* `price` agregação - Agregados `price`, aplica a variável `color` e `categories` filtros, mas não os `price` filtro.
