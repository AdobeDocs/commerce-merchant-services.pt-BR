---
title: "Espaço de trabalho facetado"
description: "Saiba mais sobre o [!DNL Live Search] espaço de trabalho facetado."
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: 4978bdb5549f5df911863a23fdfbfc9ab9ad05df
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# Espaço de trabalho Faceting

A variável *Facetagem* o espaço de trabalho lista todas as facetas disponíveis no momento e fornece acesso às ferramentas necessárias para configurar e gerenciar facetas. As facetas fixadas aparecem primeiro na lista de facetas existentes, seguidas pelas facetas dinâmicas. A lista pode ser filtrada para mostrar todas as facetas, ou apenas aquelas que estão fixadas ou dinâmicas.

![Espaço de trabalho facetado](assets/faceting-workspace.png)

## Definir o escopo

Se a sua instalação do Adobe Commerce incluir várias visualizações de loja, defina **Escopo** para o [exibição de loja](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) onde suas configurações de facetas se aplicam.

## Filtrar a lista

1. Clique em **Filtrar por** controle.
1. Escolha uma das seguintes opções:

   * Todos os filtros
   * Fixado
   * Dinâmico

## Adicionar uma faceta

1. Clique em **Adicionar facetas**.
1. Consulte [Adicionar facetas](facets-add.md) para obter instruções detalhadas.

## Descrições da coluna

| Coluna | Descrição |
|--- |--- |
| (primeira coluna) | Lista os aspectos fixados e dinâmicos pelo [rótulo](facets-type.md) visível para o comprador. |
| Tipo de classificação | A variável [classificação ordem](facets-type.md) de valores de facetas. Os aspectos são classificados em ordem alfabética para todos [!DNL Commerce] vitrines. Para [headless] implementações, os aspectos podem ser classificados em ordem alfabética ou por contagem. Opções: alfabética, contagem (somente headless) |
| Valor máximo | O número de valores de facetas que estão disponíveis na loja como filtros, com um máximo de 10. |

## Controles

| Controle | Descrição |
|--- |--- |
| Adicionar facetas | Abre a [editor de facetas](facets-add.md). |
| Filtrar por | Determina o [tipo de facetas](facets-type.md) que aparecem na lista. Opções: Tudo, Fixo, Dinâmico |
