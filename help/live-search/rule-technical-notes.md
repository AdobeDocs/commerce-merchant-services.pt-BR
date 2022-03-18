---
title: Notas técnicas da regra
description: Notas técnicas sobre o uso das regras do Live Search.
exl-id: 24ff6a19-f7cd-42f7-b466-fc18f9091504
source-git-commit: 7402e97f53b71e488d860215487f4809572b7e6f
workflow-type: tm+mt
source-wordcount: '92'
ht-degree: 0%

---

# Notas técnicas da regra

[!DNL Live Search] As regras acionam ações com base em uma variedade de condições de consulta e oferecem aos comerciantes a capacidade de moldar a experiência de pesquisa para vários cenários.

A versão atual do [!DNL Live Search] As regras são baseadas na sequência de consulta inserida pelo comprador, em vez do conjunto de resultados retornados. Uma sequência de consulta pode incluir caracteres alfanuméricos e a capitalização é ignorada. Assim como com facetas e sinônimos, as regras são armazenadas em `protobuf dynamo`. No momento da consulta, o serviço de pesquisa recupera as regras por meio de `grpc` chamadas para `search-admin-service`.
