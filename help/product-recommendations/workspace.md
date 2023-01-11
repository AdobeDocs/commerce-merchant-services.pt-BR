---
title: Workspace
description: Saiba como configurar, gerenciar e monitorar o desempenho das recomendações de produtos.
exl-id: 85a06cc3-91b9-484a-96a9-fc85718e6d70
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 0%

---

# Workspace

O [!DNL Product Recommendations] O workspace exibe uma lista de recomendações configuradas anteriormente com métricas que ajudam a rastrear o sucesso de cada recomendação. A lista pode ser configurada para calcular métricas do último dia, semana ou mês. Você pode usar as métricas para criar insights acionáveis com base na frequência com que uma unidade de recomendação é exibida ou clicada, ou para analisar o desempenho de suas recomendações.

![Área de trabalho do Recommendations](assets/workspace.png)
_Recommendations Workspace_

## Definir o escopo

Inicialmente, o [escopo](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) de todas as configurações de recomendação definidas como `Default Store View`. Se a sua instalação do Commerce incluir várias exibições de loja, defina **Escopo** para [exibição de loja](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) onde suas recomendações se aplicam.

## Definir o intervalo de datas das métricas

1. Clique no botão **Calendário** ![Seletor de calendário](assets/icon-calendar.png) controlo.

1. Escolha uma das opções a seguir:

   - Últimas 24 horas
   - Últimos 7 dias
   - Últimos 30 dias

   Os valores calculados nas colunas de métricas são alterados para refletir o intervalo de datas atual.

## Mostrar/ocultar colunas

1. No canto superior esquerdo, clique em **Mostrar/ocultar** ![Seletor de coluna](assets/icon-show-hide-columns.png) colunas.

   As colunas visíveis têm uma marca de verificação azul.

1. No menu , siga um destes procedimentos:

   - Para mostrar uma coluna oculta, clique em qualquer nome de coluna sem uma marca de seleção.
   - Para ocultar uma coluna visível, clique em qualquer nome de coluna com uma marca de seleção.

   A tabela é atualizada para incluir somente as colunas selecionadas.

   ![Área de trabalho do Recommendations](assets/workspace-select-columns.png)
   _Mostrar/ocultar colunas_

## Configurações

As configurações determinam o espaço de dados SaaS que fornece os dados comportamentais da recomendação.

- Para alterar a origem dos dados de comportamento da recomendação, escolha um espaço de dados SaaS diferente.

- Para configurar um novo espaço de dados SaaS, clique em **Editar configuração**. Para saber mais, consulte [Configurações](settings.md).

![Configurações do Recommendations](assets/settings.png)
_Configurações do Recommendations_

## Exibir detalhes

1. Na tabela , clique na recomendação que deseja examinar.

   ![Área de trabalho do Recommendations](assets/recommendation-detail.png)
   _Detalhe da taxa de conversão da página inicial_

1. Para alterar o status da recomendação, clique em **Ativar** ou **Desativar**.

## Editar recomendação

Na página de detalhes da recomendação, clique em **Editar**. Para saber mais, acesse [Editar Recommendations](edit.md).

## Criar recomendação

Na página de detalhes da recomendação, clique em **Criar**. Para saber mais, acesse [Criar Recommendations](create.md).

## Controles do Workspace

| Controle | Descrição |
|---|---|
| ![Seletor de calendário](assets/icon-calendar.png) | Determina o intervalo de tempo usado para cálculos de métricas. Opções: 24 horas / 7 dias / 30 dias |
| ![Seletor de coluna](assets/icon-show-hide-columns.png) | Determina as colunas que aparecem no [!DNL Product Recommendations] tabela. |
| Configurações | Determina o espaço de dados SaaS onde os dados comportamentais da recomendação são buscados e também permite o tipo de recomendação de similaridade visual. |
| Criar recomendação | Abre a variável [Criar Nova Recomendação](create.md) página. |

## Descrições de colunas

| Coluna | Descrição |
|---|---|
| Nome | O nome da recomendação. |
| Página | A página onde a recomendação é exibida. |
| Tipo | O tipo de recomendação. |
| Status | O status da recomendação. Opções: Inativo/Ativo/Rascunho |
| Criado | A data em que a recomendação foi criada. |
| Última edição | A data em que a recomendação foi editada pela última vez. |
| Impressões | O número de vezes que uma unidade de recomendação é carregada e renderizada em uma página. Uma unidade de recomendação que está abaixo da dobra da janela de visualização do navegador é renderizada na página, mas não é visualizada pelo comprador. Nesse caso, a unidade renderizada é contada como uma impressão, mas uma visualização é contada somente se o usuário rola a unidade para a exibição. |
| vImpressões | (Impressões visualizáveis) O número de unidades de recomendação que registram pelo menos uma visualização. |
| Exibições | O número de unidades de recomendação que aparecem no visor do navegador do comprador. Esse evento pode ser acionado várias vezes em uma página. |
| Cliques | A soma do número de vezes que um comprador clica em um item na unidade de recomendação e o número de vezes que o comprador clica no **Adicionar ao carrinho** na unidade de recomendação |
| Receita | A receita gerada pela recomendação para o intervalo de tempo atual. |
| Receita Lt | (Receita vitalícia) A receita vitalícia guiada por uma recomendação. |
| Viabilidade | A porcentagem de unidades de recomendação que se registram para a exibição. |
| Ctr | (Taxa de click-through) A porcentagem de impressões da unidade para a recomendação que registra um clique. |
| vCtr | (Taxa de click-through visualizável) A porcentagem de impressões visualizáveis para a unidade de recomendação que registra um clique. |
