---
title: "Componentes da regra"
description: "Saiba mais sobre [!DNL Live Search] componentes e operadores da regra."
exl-id: 4065aec3-a8d4-4d55-b939-16ad7b0f33ee
source-git-commit: 0a1d70465247422db44daee302c67fe1a5a29d32
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Componentes da regra

Uma regra descreve as condições necessárias para acionar eventos que alteram os resultados da pesquisa retornados em resposta a uma consulta do comprador.

## Requisitos

Uma regra simples pode ter uma única condição e um único evento, enquanto uma regra complexa pode ter até dez condições que acionam até 25 eventos.
As regras podem ter:

* Até dez condições
* Até 25 eventos

O texto da consulta pode conter:

* Caracteres alfanuméricos (letras e números)
* Caracteres maiúsculos ou minúsculos

## Operadores lógicos

Os operadores lógicos `AND` e `OR` associe duas condições e retorne resultados diferentes. Todos os operadores lógicos usados em uma regra com várias condições são iguais. Não é possível usar ambos `AND` e `OR` na mesma regra.

### Operadores de correspondência

Os operadores Match `All` e `Any` determine o operador lógico usado para unir várias condições na regra e possa ser usado para alterar o operador existente.

* `All` - Usa o `AND` operador lógico para unir várias condições. Uma regra que usa a variável `All` O operador de correspondência pode ter apenas um `Search query is` condição.
* `Any` - Usa o `OR` operador lógico para unir várias condições.

Ao compor uma regra complexa, pode ajudar a gravá-la com recuo para descrever as condições, os eventos associados e os nomes de produtos ou SKUs necessários para retornar os resultados que você deseja obter. Em seguida, crie a regra e teste o resultado.
