---
title: "Regras de pesquisa"
description: "[!DNL Live Search] as regras combinam lógica e ações para moldar a experiência de compra."
exl-id: d06a3040-6987-4813-90ae-2f7b3ad0b232
source-git-commit: 40bcae7a792660f02390f4d55967767b15c84f38
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---

# Regras de pesquisa

[!DNL Live Search] as regras combinam a lógica com ações para moldar a experiência de pesquisa de um comprador em sua loja. Você pode usar regras para impulsionar, enterrar, fixar ou ocultar produtos a fim de calibrar os resultados da pesquisa em tempo real para apoiar suas metas comerciais.

Cada regra tem três componentes principais:

* Condições - as condições que acionam uma ação.
* Eventos - As ações que ocorrem quando as condições são atendidas.
* Detalhes - O nome da regra e o intervalo de tempo e a descrição opcionais.

É possível combinar várias condições e ações e agendar uma regra para ficar ativa por um período.

## Requisitos

Uma regra de pesquisa simples pode ter uma única condição e um único evento, enquanto uma regra complexa pode ter até dez condições que acionam até 25 eventos.
As regras podem ter:

* Até dez condições
* Até 25 eventos

O texto da consulta pode conter:

* Caracteres alfanuméricos (letras e números)
* Caracteres em maiúsculas ou minúsculas. Capitalização é ignorada.

## Operadores lógicos

Os operadores lógicos `AND` e `OR` associe duas condições e retorne resultados diferentes. Todos os operadores lógicos usados em uma regra com várias condições são os mesmos. Não é possível utilizar ambos `AND` e `OR` na mesma regra.

### Operadores de correspondência

Os operadores Match `All` e `Any` determine o operador lógico usado para unir várias condições na regra e que possa ser usado para alterar o operador existente.

* `All` - Usa o `AND` operador lógico para unir várias condições. Uma regra que usa a variável `All` O operador correspondente pode ter apenas um `Search query is` condição.
* `Any` - Usa o `OR` operador lógico para unir várias condições.

Ao compor uma regra complexa, pode ser útil anotá-la com recuo para descrever as condições, os eventos associados e os nomes de produtos ou SKUs necessários para retornar os resultados que você deseja alcançar. Em seguida, crie a regra e teste o resultado.

## Ordem de precedência com várias regras

Somente uma regra de pesquisa é aplicada a um termo de pesquisa de cada vez.
Se várias regras forem consideradas aplicáveis a uma frase de pesquisa, todas elas serão aplicadas. Se houver uma colisão entre duas regras...`rule 1` que aumenta o sku1, mas `rule 2` oculta o mesmo SKU — em seguida, a regra aplicada mais recentemente (`rule 2`) tem precedência.

* As regras são ordenadas pelo carimbo de data e hora &quot;Última modificação&quot;. A regra modificada mais recentemente é aplicada primeiro, e depois disso as regras mais antigas, na ordem do carimbo de data e hora.
* A variável `query is` A condição tem precedência sobre outras condições. Se uma regra mais recente contiver uma variável `query contains` condição, mas uma regra mais antiga tem uma `query is` condição, a variável `query is` a regra é aplicada.

### Solicitações de vitrine

Se uma regra ativa que contém uma variável `query is` condição corresponder à frase de pesquisa, ela será aplicada. Se houver várias regras correspondentes com uma variável `query is` condição, a regra ativa atualizada mais recentemente é aplicada.
Caso contrário, a regra ativa atualizada mais recentemente será aplicada.

### Visualizar solicitações

A solicitação feita no Administrador funciona de forma um pouco diferente. Ao visualizar no Admin, todas as regras são aplicadas, incluindo as expiradas e programadas.

* Se a regra que está sendo visualizada tiver uma `query is` condição, ela é aplicada.
* Se a regra que está sendo visualizada não tiver uma `query is` e uma regra de correspondência ativa subsequente com uma variável `query is` for encontrada, a variável `query is` a regra é aplicada.
* Se a regra que está sendo visualizada não tiver uma `query is` e nenhuma outra regra com uma condição `query is` for encontrada, a regra que está sendo visualizada será aplicada.

## Regras de categoria e atribuições de produto de categoria

[!DNL Live Search] O permite filtrar por Categorias.
No entanto, no Adobe Commerce é possível criar uma categoria virtual com [Atribuições de produto de categoria](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html). Esse tipo de categoria é criado no tempo de execução e não existe no banco de dados de categorias. Por conseguinte, [!DNL Live Search] O não pode ler ou usar este tipo de categoria.
