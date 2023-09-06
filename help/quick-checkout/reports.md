---
title: '[!DNL Quick Checkout] relatório'
description: '''[!DNL Quick Checkout] informações completas sobre a elaboração de relatórios."'
exl-id: 91c687f4-9953-4c2f-b240-73430603e6a1
feature: Checkout, Services
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 1%

---

# Relatórios

[!DNL Quick Checkout] O para Adobe Commerce e Magento Open Source oferece relatórios abrangentes para que você possa obter informações detalhadas das estatísticas de experiência de check-out da sua loja.

![Exibição de relatórios](assets/reports-view-big-checkout.png){width="600" zoomable="yes"}

>[!WARNING]
>
> Para permitir que o Adobe Commerce compartilhe informações de check-out com o Bolt, a variável [**Rastreamento de check-out**](../quick-checkout/settings-quick-checkout.md)  A configuração deve estar ativada no Administrador. Por padrão, essa opção de configuração está definida como **Sim**. Se essa opção estiver definida como **Não**, os relatórios serão afetados. O Bolt atualiza as informações de relatório uma vez por dia às 03:00 da manhã, horário padrão do leste (EST).

## Relatórios de visão geral

Os gráficos na seção Visão geral mostram informações detalhadas sobre o desempenho de finalização da loja, incluindo o tempo médio de finalização, as novas contas criadas durante a finalização ou o abandono de finalização.

![Visão geral dos relatórios](assets/overview-report-checkout.png){width="600" zoomable="yes"}

| Gráfico | Descrição |
|---|---|
| [!UICONTROL Checkout abandonment] | A porcentagem de visitantes que saem do processo de finalização sem concluir uma compra. |
| [!UICONTROL Checkout abandonment breakdown] | O abandono do checkout dividido pelo tipo de visitante. A dica de ferramenta mostra uma diferença percentual entre Parafuso e Convidado. Opções: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Average checkout time] | O tempo médio que um visitante leva para concluir o processo de finalização. |
| [!UICONTROL Average checkout time breakdown] | Tempo médio de checkout dividido pelo tipo de visitante. A dica de ferramenta mostra uma diferença percentual entre Parafuso e Convidado. Opções: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | Pedidos feitos divididos por tipo de visitante. Opções: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |

## Relatórios de tendências

Os gráficos na seção Tendências mostram as tendências da experiência de check-out filtradas por tipo de conta ou por novas contas criadas durante o check-out.

![Relatórios de tendências](assets/trends-report-checkout.png){width="600" zoomable="yes"}

| Gráfico | Descrição |
|---|---|
| [!UICONTROL Checkout abandonment by account type] | A tendência de abandono do check-out dividida por tipo de visitante. Opções: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL Orders by account type] | A tendência dos pedidos foi dividida pelo tipo de visitante. Opções: [!UICONTROL Bolt] / [!UICONTROL Merchant] / [!UICONTROL Guest] |
| [!UICONTROL New accounts on your store] | Novas contas na tendência da loja. |

## Filtrar dados

É possível filtrar os resultados mostrados por data ou predefinições existentes, como **Últimos 30 dias**.

![Filtrar exibição](assets/filter-view.png){width="300" zoomable="yes"}

| Campo | Descrição |
|---|---|
| [!UICONTROL Preset] | Uma lista suspensa que exibe predefinições padrão que podem ser usadas para mostrar intervalos de dados específicos. Por padrão: Últimos 30 dias |
| [!UICONTROL Date range] | Uma lista suspensa que permite selecionar um intervalo específico de dados, dependendo das datas selecionadas. |
