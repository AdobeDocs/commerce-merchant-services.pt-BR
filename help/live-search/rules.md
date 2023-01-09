---
title: "Regras"
description: "[!DNL Live Search] as regras combinam lógica com ações para moldar a experiência de compra."
exl-id: d06a3040-6987-4813-90ae-2f7b3ad0b232
source-git-commit: 941fdc25f93679593cb3c5db0d29d7a561fcce58
workflow-type: tm+mt
source-wordcount: '296'
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
