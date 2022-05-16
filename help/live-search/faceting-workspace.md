---
title: '"Faceting Workspace"'
description: '"Saiba mais sobre a [!DNL Live Search] faceting workspace."'
exl-id: b47b5c19-59bb-41e4-9599-3b90cbc44b70
source-git-commit: bffbede99865e9085f60392e474065a454446370
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# Facting Workspace

O [!DNL Live Search] A área de trabalho lista todas as facetas disponíveis no momento e fornece acesso às ferramentas necessárias para configurar e gerenciar aspectos. As facetas fixadas aparecem primeiro na lista de facetas existentes, seguidas de facetas dinâmicas. A lista pode ser filtrada para mostrar todas as facetas, ou apenas aquelas que são fixadas ou dinâmicas.

![Espaço de trabalho Facting](assets/faceting-workspace.png)

## Definir o escopo

Se a instalação do Adobe Commerce incluir várias exibições de loja, defina **Escopo** para [exibição de loja](https://docs.magento.com/user-guide/configuration/scope.html) onde suas configurações de faceta se aplicam.

## Filtrar a lista

1. Clique no botão **Filtrar por** controlo.
1. Escolha uma das seguintes opções:

   * Todos os filtros
   * Fixo
   * Dinâmico

   ![Espaço de trabalho Facting](assets/facets-filter-by.png)

## Adicionar uma faceta

1. Clique em **Adicionar aspectos**.
1. Consulte [Adicionar aspectos](facets-add.md) para obter instruções detalhadas.

## Descrições das colunas

| Coluna | Descrição |
|--- |--- |
| (primeira coluna) | Lista os aspectos dinâmicos e fixados pela [label](facets-type.md) que é visível para o comprador. |
| Selecionar tipo | O [método de seleção](facets-type.md) que é atribuído ao atributo do produto correspondente. O `single select` O tipo é usado para todos [!DNL Commerce] vitrines. Para implementações sem periféricos, `multi-select` pode ser atribuído com um operador lógico (`or` ou `and`) para determinar o conjunto de produtos retornados. |
| Tipo de classificação | O [ordem de classificação](facets-type.md) de valores de facetas. As facetas são classificadas alfabeticamente para todos [!DNL Commerce] vitrines. Para [impiedoso] implementações, facetas podem ser classificadas alfabeticamente ou por contagem. Opções: Alfabético, Contagem (somente sem cabeçalho) |
| Valor máximo | O número de valores de faceta que estão disponíveis na loja como filtros, com no máximo 10. |

## Controles

| Controle | Descrição |
|--- |--- |
| Adicionar aspectos | Abre a variável [editor de facetas](facets-add.md). |
| Filtrar por | Determina o [tipo de facetas](facets-type.md) que aparecem na lista. Opções: Tudo, Fixo, Dinâmico |
