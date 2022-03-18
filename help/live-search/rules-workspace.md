---
title: Workspace de regras
description: Saiba mais sobre a área de trabalho de regras do Live Search.
exl-id: a52839fb-2264-4443-83c3-9eaa2ccb6996
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# Workspace de regras

O espaço de trabalho de regras lista a seleção atual de regras e seu status, e fornece acesso às ferramentas necessárias para criar e gerenciar regras. No espaço de trabalho, é possível:

* Procurar regras
* Exibir detalhes da regra
* Ativar/desativar regras
* Excluir regras
* Acessar o editor de regras

![Espaço de trabalho Regras](assets/rules-workspace.png)

## Definir o escopo

Se a instalação do Adobe Commerce incluir várias exibições de loja, defina **Escopo** para [exibição de loja](https://docs.magento.com/user-guide/configuration/scope.html) onde suas regras se aplicam.

## Mostrar/ocultar colunas

1. No canto superior direito, clique em **Mostrar/ocultar** ![Seletor de coluna](assets/btn-show-hide-columns.png) colunas.
As colunas visíveis têm uma marca de seleção azul no menu de opções. O nome da regra é a única coluna que não pode ser ocultada.

   ![Espaço de trabalho Regras](assets/rules-workspace-show-hide-columns.png)

1. No menu , siga um destes procedimentos:

   * Para mostrar uma coluna oculta, clique em qualquer nome de coluna sem uma marca de seleção.
   * Para ocultar uma coluna visível, clique em qualquer nome de coluna com uma marca de seleção.

   ![Espaço de trabalho Regras](assets/rules-workspace-all-columns.png)

## Filtrar regras por status

1. Se a loja tiver muitas regras, você poderá filtrar as regras por status para encurtar a lista. Por padrão, a lista de Regras exibe todas as regras.

   ![Regras - filtrar por status](assets/rules-workspace-filter-status.png)

1. Para listar apenas as regras com uma configuração de status específica, defina **Status** para um dos seguintes:

   * Todos
   * Ativo
   * Inativo
   * Programado

   ![Regras - filtrar por status](assets/rules-workspace-filter-status-active.png)

## Pesquisar regras por nome

Comece a digitar o nome da regra ou qualquer palavra no nome da regra.
A pesquisa encontra as regras correspondentes à medida que você digita. A sequência de caracteres correspondentes é realçada no nome de cada regra encontrada.

![Regras - pesquisar por nome](assets/rules-workspace-search-name.png)

## Exibir detalhes

O painel de detalhes mostra o nome da regra, o status, as condições e os eventos, a data inicial e final, a descrição e a data da última edição. As regras podem ser ativadas, editadas e excluídas do painel de detalhes.

1. No *Regras* , encontre a regra na grade que deseja visualizar e clique em **Mais** (...).
1. Clique em **Exibir detalhes**.
Você pode executar qualquer um dos seguintes procedimentos no painel Exibir detalhes:

   * Editar regra
   * Excluir regra
   * Ativar/Desativar Regra

1. Para fechar o *Exibir detalhes* painel, clique em **Fechar** (X) no canto superior direito.

   ![Regra - detalhes](assets/rules-workspace-details.png)

## Descrições das colunas

| Coluna | Descrição |
|--- |--- |
| Nome | O nome da regra. |
| Última atualização | A data em que a regra foi atualizada pela última vez. |
| Data de início | A data de início de uma regra agendada. |
| Data final | A data final de uma regra agendada. |
| Status | O status de código de cores indica o estado atual da regra. Use o Controle de status acima da grade para filtrar as regras por status. Valores:<br />Todo o status - Exibe todas as regras, independentemente do status.<br />Ativo (azul) - Exibe apenas as regras ativas.<br />Agendado (Laranja) - exibe somente as regras agendadas.<br />Inativo (cinza) - exibe somente as regras inativas. |

## Controles

| Controle | Descrição |
|--- |--- |
| Adicionar regra | Abre a variável [editor de regras]({% link live-search/rules-add.md %}). |
| Status | Filtra a lista de regras por status. Opções: Tudo, Ativo, Inativo, Programado |
| ![Seletor de coluna](assets/btn-show-hide-columns.png) | Especifica as colunas que são visíveis na grade. Opções: Última atualização, Data inicial, Data final, Status |
| Pesquisar | Pesquisa uma regra por nome completo ou correspondência parcial. |
| ![Mais seletor](assets/btn-more.png) | Exibe um menu com mais ações que podem ser aplicadas à regra selecionada. Opções: Editar, Exibir detalhes, Excluir |

## Detalhes da regra

| Campo | Descrição |
|--- |--- |
| Status | O status atual da regra. |
| Condições | A consulta de pesquisa que descreve as condições associadas à regra. |
| Data inicial | A data em que a regra entra em vigor, se programada. |
| Data final | A data em que a regra expira, se estiver programada. |
| Descrição | Uma breve descrição da regra. |
| Última atualização | A data e a hora em que a regra foi atualizada pela última vez. |
| Ativado | Um controle que altera o status da regra. Opções: Ativado / Desativado |
