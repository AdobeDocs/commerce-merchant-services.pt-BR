---
title: Relatório de status do pagamento da ordem
description: Use o relatório Status do pagamento da Ordem para obter visibilidade sobre o status do pagamento de suas ordens e identificar possíveis problemas.
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
source-git-commit: ac1d0a4e64f358da44796edb0138b3656a907440
workflow-type: tm+mt
source-wordcount: '1436'
ht-degree: 0%

---

# Relatório de status do pagamento da ordem

[!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source] O oferece relatórios abrangentes para que você possa obter uma visão clara dos pedidos e pagamentos da sua loja.

![Exibição de relatórios financeiros](assets/reports-view-new.png)

O relatório de status do pagamento da ordem ajuda você a entender facilmente onde uma ordem específica está dentro do fluxo do processo de pagamento da ordem. Este relatório permite que você visualize rapidamente o status do pagamento de suas ordens e identifique possíveis problemas.

Não é necessário abrir várias exibições para fazer referência manual a pedidos e pagamentos. [!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source] permite que você obtenha uma visão geral dos seus pedidos e pagamentos — tudo isso dentro do relatório de status do pagamento de pedido.

Veja status de pagamento, status faturado e enviado, status de reembolso, status de contestação e muito mais, tudo dentro deste relatório no Administrador.

Você pode baixar as transações de status de pagamento de ordem em um formato de arquivo .csv para uso em softwares contábeis ou de gerenciamento de pedidos existentes.

>[!NOTE]
>
>Não é possível exibir relatórios financeiros caso não tenha [Modo online integrado e ativado](production.md#enable-live-payments) para [!DNL Payment Services].

## Dados usados no relatório

O [!DNL Payment Services] O módulo usa dados de ordem e os combina com dados de pagamento agregados de outras fontes (incluindo PayPal), para fornecer relatórios significativos e altamente úteis.

Os dados do pedido são exportados e mantidos no serviço de pagamento. Quando você [alterar ou adicionar status de pedido](https://docs.magento.com/user-guide/sales/order-status-custom.html){target=&quot;_blank&quot;} ou [editar uma exibição de loja](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html){target=&quot;_blank&quot;}, [loja](https://docs.magento.com/user-guide/stores/store-information.html){target=&quot;_blank&quot;}, ou nome do site, esses dados são combinados com dados de pagamento e o relatório de status do pagamento de pedido é preenchido com as informações combinadas.

Há duas etapas neste processo:

1. O índice é alterado nos dados `ON SAVE` (sempre que as informações do pedido ou as informações da loja são alteradas) ou `BY SCHEDULE` (em um agendamento cron pré-configurado), dependendo de como ele é configurado em [Gerenciamento de índice](https://docs.magento.com/user-guide/system/index-management.html){target=&quot;_blank&quot;} na Admin.

   Por padrão, a indexação de dados ocorre `ON SAVE`, o que significa que sempre que algo é alterado no pedido, no status do pedido, na exibição da loja, na loja ou no site, o processo de reindexação acontece imediatamente.

1. Os dados indexados são enviados ao serviço de pagamento, que é preenchido no relatório de status do pagamento da ordem .

Os únicos dados exportados e coletados para fins de relatório são os dados usados pelo relatório de status do pagamento da ordem .

>[!NOTE]
>
>Os dados mostrados nesta tabela são classificados em ordem decrescente (`DESC`) por padrão usando o `ORDER DATE`. O `ORDER DATE` é o carimbo de data e hora em que o pedido foi criado.

### Configurar exportação de dados

Mesmo que, por padrão, a reindexação ocorra em `ON SAVE` é recomendável indexar no modo `BY SCHEDULE` modo. O `BY SCHEDULE` O índice é executado em um cronograma de tempo real de um minuto e os dados alterados são exibidos no relatório de status do pedido em dois minutos de qualquer alteração de dados. Essa reindexação agendada ajuda a reduzir qualquer esforço em sua loja, especialmente se você tiver um grande volume de pedidos recebidos, pois isso acontece de acordo com uma programação (não conforme cada pedido é feito).

Você pode alterar o modo de índice—`ON SAVE` ou `BY SCHEDULE`—[no Administrador](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target=&quot;_blank&quot;}.

Para saber como configurar a exportação de dados, consulte [Configuração da linha de comando](configure-cli.md#configure-data-export).

## Disponibilidade

No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Order payment status]** para ver os status de pagamento de suas ordens.

![Status de pagamento da ordem na Administração](assets/order-payment-status-report.png)

## Selecionar fonte de dados

Na exibição de relatório Status do pagamento da ordem, é possível selecionar a fonte de dados—_[!UICONTROL Live]_ou_[!UICONTROL Sandbox]_—para o qual você deseja ver os resultados do relatório.

![Seleção das fontes de dados](assets/datasource.png)

If _[!UICONTROL Live]_for a fonte de dados selecionada, você poderá ver as informações do relatório para suas lojas que usam [!DNL Payment Services] em_[!UICONTROL Live]_ modo. If [!UICONTROL Sandbox]_ for a fonte de dados selecionada, você poderá ver as informações do relatório para o seu ambiente de sandbox.

As seleções de fonte de dados funcionam da seguinte maneira:

* Se você não tiver lojas que usem [!DNL Payment Services] no modo Online, a seleção da fonte de dados assume como padrão _[!UICONTROL Sandbox]_.
* Se você tiver lojas (uma ou várias) que usam [!DNL Payment Services] no modo Online, a seleção da fonte de dados assume como padrão _[!UICONTROL Live]_.
* As exportações de relatório sempre seguem a seleção da fonte de dados.

Para selecionar a fonte de dados para seu [!UICONTROL Order Payment Status] relatório:

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Clique em **[!UICONTROL Data source]** e selecione _[!UICONTROL Live]_ou_[!UICONTROL Sandbox]_.

   Os resultados do relatório são gerados com base na fonte de dados selecionada.

## Personalizar período de datas

Na exibição do relatório Status do pagamento da ordem, é possível personalizar o período dos status que deseja visualizar selecionando datas específicas. Por padrão, 30 dias de status de pagamento de ordem são mostrados na grade.

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Clique no botão **[!UICONTROL Order dates]** filtro do seletor de calendário.
1. Escolha o intervalo de datas aplicável.
1. Exibir os status de pagamento da ordem para as datas especificadas na grade.

## Mostrar e ocultar colunas

O relatório Status do Pagamento da Ordem mostra todas as colunas disponíveis de informações por padrão. Entretanto, é possível personalizar quais colunas você vê em seu relatório.

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Clique no botão _Configurações de coluna_ ícone (![ícone de configurações de coluna](assets/column-settings.png)).
1. Para personalizar quais colunas você vê no relatório, marque ou desmarque as colunas na lista.

   O relatório Status do pagamento da ordem mostrará imediatamente as alterações feitas no menu Configurações de coluna . As preferências de coluna serão salvas e permanecerão em vigor se você sair da visualização do relatório.

## Exibir status

A exibição do relatório Status do pagamento da Ordem mostra informações abrangentes sobre o status da transação e do pagamento para cada ordem dos Serviços de Pagamento.

### Status da transação

Por padrão, 30 dias de status de pagamento de ordem são mostrados na grade.

Role para a esquerda e para a direita para exibir [informações sobre o status do pagamento da ordem](#column-descriptions), incluindo data de pedido, data autorizada, faturada, enviada, status de pagamento e muito mais.

O número de linhas retornadas em uma pesquisa, ou mostradas nos status padrão de 30 dias de pagamento da ordem, são mostradas acima da grade de exibição Status do pagamento da ordem ao lado do filtro seletor de calendário Datas da ordem .

### Status do pagamento

A coluna Status do pagamento mostra o status atual de qualquer pagamento. A `Capture failed` pagamento mostra um status de alerta vermelho e um `Voided` pagamento mostra um status de alerta cinza.

### Status do reembolso

A coluna Status de reembolso mostra o status atual de qualquer reembolso. A `Capture failed` pagamento mostra um status de alerta vermelho e um `Voided` pagamento mostra um status de alerta cinza.

## Atualizar dados do relatório

A exibição do relatório de status do pagamento da ordem mostra um _[!UICONTROL Last updated]_carimbo de data e hora que mostra a última vez que as informações do relatório foram atualizadas. Por padrão, os dados do relatório de status do pagamento de pedido são atualizados automaticamente a cada três horas.

Você também pode forçar manualmente uma atualização dos dados do relatório de status do pagamento da ordem para ver as informações do relatório mais atualizadas.

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Clique no botão _Atualizar_ ícone (![ícone atualizar](assets/refresh-button-med.png)).

   Os dados do relatório de status do pagamento da ordem são atualizados e um *[!UICONTROL Update complete]* é exibida e as informações mais recentes estão presentes na grade.

## Visualizar litígios

Você pode visualizar qualquer contestação nos pedidos da sua loja e navegar até o Centro de Resolução do PayPal para tomar medidas, a partir do relatório de status do Pagamento da Ordem.

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Navegue até o **[!UICONTROL Disputes column]**.
1. Veja quaisquer contestações para uma ordem específica e consulte [estatuto de litígio](#order-payment-status-information).
1. Clique no link da ID de litígio (começando com _PP-D-_) para acessar o [Centro de Resolução PayPal](https://www.paypal.com/us/smarthelp/article/what-is-the-resolution-center-faq3327).
1. Tomar as medidas adequadas para o litígio, se necessário.

   Para classificar contestações de ordem por status, clique no cabeçalho da coluna Disputes .

## Baixar status de pagamento da ordem

Você pode fazer o download de um arquivo .csv com todos os status visíveis na grade de exibição do status do pagamento do pedido, esteja você exibindo os status padrão de 30 dias ou um período personalizado.

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Se quiser ver os status para um período diferente dos últimos 30 dias, [personalizar o período do intervalo de datas para seus status](#customize-dates-timeframe).
1. Clique no botão _Baixar_ (![ícone de download](assets/icon-download.png)).

Os status de pagamento de pedido são baixados em um formato .csv .

<!-- ## Default order payment status timeframes

These order payment status timeframes are currently available in [!DNL Payment Services].

| Report       | Description          |
| ------------ | -------------------- |
| Yesterday | Available from the Order payment status dates selector, this shows information for the prior date. |
| | Today | Available from the Order payment status dates selector, this shows information for the current day. |
| Last 7 days | Available from the Order payment status dates selector, this shows information for the last seven days. |
| Last 30 days | Available from the Order payment status dates selector and by default in the Order payment statuses view, this shows information for the last 30 days. |
| Last 90 days | Available from the Order payment status dates selector, this shows information for the last 90 days. |
| Year to date | Available from the Order payment status dates selector, this shows information for the the entire year to date. |
| Custom range | Available from the Order payment status dates selector, this can be filtered to show a custom date range. |
-->

## Informações sobre o status do pagamento da ordem

A exibição Status do pagamento da ordem mostra informações extensas para cada status mostrado na grade.

### Descrições das colunas

Os relatórios de status do pagamento da ordem incluem as seguintes informações.

| Coluna | Descrição |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | ID de pedido de comércio<br> <br>Para ver os [informações do pedido](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}, clique na ID. |
| [!UICONTROL Order Date] | Carimbo de data e hora do pedido |
| [!UICONTROL Authorized Date] | Data e hora da autorização de pagamento |
| [!UICONTROL Order Status] | Comércio atual [status do pedido](https://docs.magento.com/user-guide/sales/order-status.html){target=&quot;_blank&quot;} |
| [!UICONTROL Invoiced] | Status da nota fiscal—*[!UICONTROL No]*, *[!UICONTROL Partial]* ou *[!UICONTROL Yes]* |
| [!UICONTROL Shipped] | Estado da encomenda —*[!UICONTROL No]*, *[!UICONTROL Partial]* ou *[!UICONTROL Yes]* |
| [!UICONTROL Order Amt] | Montante total geral do despacho |
| [!UICONTROL Cur] | Tipo de moeda da ordem |
| [!UICONTROL Pay Status] | Status de pagamento de uma ordem específica |
| [!UICONTROL Paid Amt] | Valor pago em um pedido |
| [!UICONTROL Cur] | Tipo de moeda do valor pago em um pedido |
| [!UICONTROL Refund Status] | Status de reembolso em um pedido (como informações de devoluções, RMAs e avisos de crédito)—   *[!UICONTROL Requires refund]*, *[!UICONTROL Refund requested]*, *[!UICONTROL Refunded]*, *[!UICONTROL Refund failed]* ou *[!UICONTROL Voided]* |
| [!UICONTROL Refund Amount] | Total do montante reembolsado de um pedido |
| [!UICONTROL Cur] | Tipo de moeda do valor reembolsado de uma ordem |
| [!UICONTROL Disputes] | Estatuto de qualquer litígio relativo a uma injunção (informações sobre litígios e retornos de encargos) —*[!UICONTROL Open]*, *[!UICONTROL Waiting for buyer response]*, *[!UICONTROL Waiting for seller response]*, *[!UICONTROL Under review]*, *[!UICONTROL Resolved]* ou *[!UICONTROL Other]* |
| [!UICONTROL Payment Method] | Método de pagamento usado na transação Comércio de uma ordem |
| [!UICONTROL Website] | Site do qual o pedido foi feito |
| [!UICONTROL Store] | Armazenar a partir do qual o pedido foi feito |
| [!UICONTROL Store View] | Exibição de armazenamento da qual o pedido foi feito |
