---
title: "Regras"
description: "[!DNL Live Search] as regras combinam lógica com ações para moldar a experiência de compra."
exl-id: d06a3040-6987-4813-90ae-2f7b3ad0b232
source-git-commit: 7307702a62a6b2c3e6c6083a59f2ac3587b0985e
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# Regras

[!DNL Live Search] as regras combinam lógica com ações para moldar a experiência de pesquisa de um comprador na sua loja. Você pode usar as regras para impulsionar, enterrar, prender ou ocultar produtos para calibrar os resultados da pesquisa em tempo real, a fim de apoiar suas metas de negócios.

Cada regra tem três componentes principais:

* Condições - As condições que acionam uma ação.
* Eventos - As ações que ocorrem quando as condições são cumpridas.
* Detalhes - O nome da regra, o período de tempo e a descrição opcionais.

É possível combinar várias condições e ações e agendar uma regra para permanecer ativa por um período.

## Requisitos

Uma regra simples pode ter uma única condição e um único evento, enquanto uma regra complexa pode ter até dez condições que acionam até 25 eventos.
As regras podem ter:

* Até dez condições
* Até 25 eventos

O texto da consulta pode conter:

* Caracteres alfanuméricos (letras e números)
* Caracteres maiúsculos ou minúsculos. A capitalização é ignorada.

## Operadores lógicos

Os operadores lógicos `AND` e `OR` associe duas condições e retorne resultados diferentes. Todos os operadores lógicos usados em uma regra com várias condições são iguais. Não é possível usar ambos `AND` e `OR` na mesma regra.

### Operadores de correspondência

Os operadores Match `All` e `Any` determine o operador lógico usado para unir várias condições na regra e possa ser usado para alterar o operador existente.

* `All` - Usa o `AND` operador lógico para unir várias condições. Uma regra que usa a variável `All` O operador de correspondência pode ter apenas um `Search query is` condição.
* `Any` - Usa o `OR` operador lógico para unir várias condições.

Ao compor uma regra complexa, pode ajudar a gravá-la com recuo para descrever as condições, os eventos associados e os nomes de produtos ou SKUs necessários para retornar os resultados que você deseja obter. Em seguida, crie a regra e teste o resultado.

## Ordem de precedência com várias regras

Somente uma regra é aplicada a um termo de pesquisa de cada vez.
Se várias regras forem consideradas aplicáveis a uma frase de pesquisa, todas essas regras serão aplicadas. Se houver conflito entre duas regras—`rule 1` que impulsiona o sku1 mas `rule 2` oculta o mesmo SKU; em seguida, a regra aplicada mais recentemente (`rule 2`) tem precedência.

* As regras são ordenadas pelo carimbo de data e hora de &quot;Última modificação&quot;. A regra modificada mais recentemente é aplicada primeiro e regras mais antigas depois disso, em ordem de carimbo de data e hora.
* O `query is` tem precedência sobre outras condições. Se uma regra mais recente contiver uma `query contains` , mas uma regra mais antiga tem uma `query is` , a `query is` é aplicada.

### Solicitações de vitrine

Se uma regra ativa contiver uma `query is` corresponda à frase de pesquisa, ela será aplicada. Se houver várias regras correspondentes com uma `query is` a regra ativa atualizada mais recentemente é aplicada.
Caso contrário, a regra ativa atualizada mais recentemente será aplicada.

### Visualizar solicitações

A solicitação feita no Administrador funciona de uma forma um pouco diferente. Ao visualizar no Administrador, todas as regras são aplicadas, incluindo as expiradas e programadas.

* Se a regra que está sendo visualizada tiver uma `query is` , ela é aplicada.
* Se a regra que está sendo visualizada não tiver um `query is` e uma regra ativa subsequente, correspondente com uma `query is` for encontrada, a variável `query is` é aplicada.
* Se a regra que está sendo visualizada não tiver um `query is` e nenhuma outra regra com uma `query is` for encontrada, a regra que está sendo visualizada será aplicada.

## Regras de categoria e atribuições de produto de categoria

[!DNL Live Search] permite filtrar por Categorias.
No entanto, no Adobe Commerce, é possível criar uma categoria virtual com [Atribuições de produto da categoria](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html). Esse tipo de categoria é criado no tempo de execução e não existe no banco de dados de categoria. Por conseguinte, [!DNL Live Search] não é possível ler ou usar este tipo de categoria.
