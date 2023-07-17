---
title: Relatório de Status do Pagamento do Pedido
description: Use o relatório de status de pagamento de Pedido para obter visibilidade sobre o status de pagamento de seus pedidos e identificar possíveis problemas.
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
feature: Payments, Checkout, Orders
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '1828'
ht-degree: 0%

---

# Relatório de Status do Pagamento do Pedido

[!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source] O oferece relatórios abrangentes para que você possa ter uma visão clara dos pedidos e pagamentos da loja.

Há duas exibições disponíveis do relatório de status do pagamento da ordem para permitir que você exiba rapidamente o status do pagamento de suas ordens:

* **[Exibição de visualização do status do pagamento da ordem](#order-payment-status-data-visualization-view)**—Gráfico disponível na Página Inicial dos Serviços de Pagamento que é uma representação visual dos status de pagamento agregados por dia a partir da exibição do relatório Status do pagamento da ordem
* **[Exibição do relatório de status do pagamento da ordem](#order-payment-status-report-view)**—Relatório disponível no status do Order payment que mostra os status detalhado do pagamento, faturado, remetido, reembolso e contestação de todas as transações

As exibições de status do Pedido de pagamento ajudam você a entender facilmente onde uma ordem específica está dentro do fluxo do processo da ordem para caixa. Esses relatórios permitem visualizar rapidamente os pedidos, com base no status do pagamento e na data do pagamento, e identificar possíveis problemas.

Você pode fazer download de transações de status de pagamento de pedidos em um formato de arquivo .csv para uso em software de contabilidade ou gerenciamento de pedidos existente.

>[!NOTE]
>
>Não é possível exibir relatórios financeiros se você não tiver [modo Online integrado e ativado](production.md#enable-live-payments) para [!DNL Payment Services].

## Exibição da visualização de dados do status do pagamento da ordem

A visualização de dados do status do pagamento do pedido está disponível na Página inicial dos Serviços de pagamento. É uma representação visual dos status de pagamento agregados por dia a partir da tabela detalhada [Exibição do relatório de status do pagamento da ordem](#order-payment-status-report-view).

No _Admin_ barra lateral, vá para **Vendas** > **Payment Services** para ver a visualização de dados [gráfico de status de pagamento](#statuses-information).

![Visualização de dados de pagamento no Administrador](assets/orderpayment-dataviz.png){zoomable=yes}

Clique em **Exibir Relatório** para navegar até a tabela detalhada [Exibição do relatório de status do pagamento da ordem](#order-payment-status-report-view).

### Personalizar período de status

Por padrão, são exibidos 30 dias de status de pagamento.

Na exibição de visualização do status do pagamento da Ordem, é possível personalizar o período dos status de pagamento que você deseja exibir, selecionando um intervalo de datas:

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. A visualização de dados do status do pagamento do pedido está visível na seção Status do pagamento do pedido.
1. Clique em **[!UICONTROL Range]** filtro seletor.
1. Escolha o intervalo de datas aplicável: 30 dias, 15 dias ou 7 dias.
1. Exiba as informações de status das datas especificadas.

### Informações de status

Os status de pagamento de um intervalo de datas selecionado são mostrados à esquerda da visualização de dados Status do pagamento do pedido. As datas do intervalo de datas selecionado são mostradas na parte inferior da exibição. Se não houver pedidos em uma data específica, essa data não aparecerá.

A visualização de dados do status do pagamento do pedido inclui as seguintes informações.

| Dados | Descrição |
| ------------ | -------------------- |
| [!UICONTROL Orders] | Intervalo de valores para ordens no intervalo de tempo especificado; dados no eixo Y (à esquerda) |
| Intervalo de datas | Intervalo de datas para o intervalo de tempo especificado; dados no eixo X (inferior) |
| Autorizado | Pedido autorizado |
| Captura solicitada | Captura solicitada para o pedido |
| Captura confirmada | Captura de pedido concluída |
| Captura parcial | Pedido parcialmente capturado |
| Falha na captura | Falha na captura do pedido |
| Anulado | Pedido anulado |

## Exibição do relatório de status do pagamento da ordem

A visualização do relatório Status do pagamento da ordem está disponível na visualização Status do pagamento da ordem dos Serviços de pagamento. Ele inclui status detalhados — pagamento, faturado, enviado, reembolso, contestação e muito mais — para todas as transações. A variável [Exibição da visualização de dados do status do pagamento da ordem](#order-payment-status-data-visualization-view) Na Página Inicial dos Serviços de Pagamento, há uma representação visual dos status de pagamento agregados por dia na exibição do relatório Status do pagamento de pedidos.

No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Order payment status]** para ver a exibição detalhada do relatório de status do pagamento da ordem.

![Transações de status de pagamento de pedido no Administrador](assets/orders-report-data.png)

É possível configurar essa visualização, de acordo com as seções neste tópico, para apresentar melhor os dados que você deseja ver.

Você pode [baixar transações de pagamento](#download-order-payment-statuses) em um formato de arquivo .csv para uso em software existente de contabilidade ou gerenciamento de pedidos.

>[!NOTE]
>
>Os dados mostrados nesta tabela são classificados em ordem decrescente (`DESC`) por padrão usando o `TRANS DATE`. A variável `TRANS DATE` é a data e a hora em que a transação foi iniciada.

### Dados usados no relatório

A variável [!DNL Payment Services] O módulo usa dados de pedido e os combina com dados de pagamento agregados de outras fontes (incluindo PayPal), para fornecer relatórios significativos e altamente úteis.

Os dados do pedido são exportados e mantidos no serviço de pagamento. Quando você [alterar ou adicionar status de pedido](https://docs.magento.com/user-guide/sales/order-status-custom.html){target="_blank"} or [edit a store view](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html){target="_blank"}, [store](https://docs.magento.com/user-guide/stores/store-information.html){target="_blank"}, ou nome do site, de que os dados são combinados com os dados de pagamento e o relatório de status de pagamento do pedido é preenchido com as informações combinadas.

Há duas etapas neste processo:

1. O índice é alterado nos dados `ON SAVE` (sempre que as informações da ordem ou da loja forem alteradas) ou `BY SCHEDULE` (em uma programação cron pré-configurada), dependendo de como ela é configurada no [Gerenciamento de índice](https://docs.magento.com/user-guide/system/index-management.html){target="_blank"} em Admin.

   Por padrão, ocorre a indexação de dados `ON SAVE`, o que significa que sempre que algo for alterado no pedido, no status do pedido, na exibição da loja, na loja ou no site, o processo de reindexação ocorrerá imediatamente.

1. Os dados indexados são enviados para o serviço de pagamento, que é preenchido no relatório Order payment status.

Os únicos dados exportados e agrupados para fins de relatório são os dados usados pelo relatório de status do Pedido de pagamento.

>[!NOTE]
>
>Os dados mostrados nesta tabela são classificados em ordem decrescente (`DESC`) por padrão usando o `ORDER DATE`. A variável `ORDER DATE` é a data e a hora em que o pedido foi criado.

#### Configurar exportação de dados

Mesmo que, por padrão, a reindexação ocorra em `ON SAVE` , é recomendável indexar no `BY SCHEDULE` modo. A variável `BY SCHEDULE` O índice é executado em uma programação cron de um minuto, e quaisquer dados alterados são exibidos no relatório Status do pedido dentro de dois minutos após qualquer alteração de dados. Essa reindexação programada ajuda a reduzir qualquer esforço na loja, especialmente se você tiver um grande volume de pedidos recebidos, pois isso acontece em um cronograma (não conforme cada pedido é feito).

Você pode alterar o modo do índice—`ON SAVE` ou `BY SCHEDULE`—[no Admin](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target="_blank"}.

Para saber como configurar a exportação de dados, consulte [Configuração da linha de comando](configure-cli.md#configure-data-export).

### Selecionar fonte de dados

Na exibição do relatório Status de pagamento da ordem, é possível selecionar a fonte de dados —_[!UICONTROL Live]_ou_[!UICONTROL Sandbox]_—para o qual você deseja ver os resultados do relatório.

![Seleção de fontes de dados](assets/datasource.png){width=400px}

Se _[!UICONTROL Live]_for a fonte de dados selecionada, você poderá ver as informações do relatório das lojas que usam [!DNL Payment Services] no modo de produção. Se_[!UICONTROL Sandbox]_ for a fonte de dados selecionada, você poderá ver informações de relatório para o modo sandbox.

As seleções de fonte de dados funcionam da seguinte maneira:

* Se você não tiver lojas que usam [!DNL Payment Services] no modo Online, a seleção da fonte de dados é padronizada como _[!UICONTROL Sandbox]_.
* Se você tiver lojas (uma ou várias) que usam [!DNL Payment Services] no modo Online, a seleção da fonte de dados é padronizada como _[!UICONTROL Live]_.
* As exportações de relatórios sempre seguem a seleção da fonte de dados.

Para selecionar a fonte de dados para sua [!UICONTROL Order Payment Status] relatório:

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Clique em **[!UICONTROL Data source]** e selecione _[!UICONTROL Live]_ou_[!UICONTROL Sandbox]_.

   Os resultados do relatório são gerados novamente com base na fonte de dados selecionada.

### Personalizar período de datas

Na exibição do relatório Status de pagamento da ordem, você pode personalizar o período dos status que deseja exibir selecionando datas específicas. Por padrão, 30 dias de status de pedidos de pagamento são mostrados na grade.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Clique em **[!UICONTROL Order dates]** filtro seletor de calendário.
1. Escolha o intervalo de datas aplicável.
1. Exiba os status de pagamento da ordem para as datas especificadas na grade.

### Mostrar e ocultar colunas

O relatório Status do Pagamento da Ordem mostra todas as colunas de informações disponíveis por padrão. No entanto, você pode personalizar quais colunas verá no relatório.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Clique em _Configurações de coluna_ ícone (![ícone configurações de coluna](assets/column-settings.png)).
1. Para personalizar quais colunas você vê no relatório, marque ou desmarque as colunas na lista.

   O relatório de status do Pedido de pagamento mostrará imediatamente quaisquer alterações feitas no menu de configurações Coluna. As preferências de coluna serão salvas e permanecerão em vigor se você sair da exibição de relatório.

### Exibir status

A exibição do relatório Status de pagamento da ordem mostra informações abrangentes sobre o status da transação e o status do pagamento de cada ordem de Serviços de Pagamento.

#### Status da transação

Por padrão, 30 dias de status de pedidos de pagamento são mostrados na grade.

Role para a esquerda e para a direita para visualizar [informações de status do pagamento da ordem](#column-descriptions), incluindo data do pedido, data de autorização, faturado, remetido, status de pagamento e muito mais.

O número de linhas retornadas em uma pesquisa, ou mostradas nos 30 dias padrão de status de pagamento da ordem, é mostrado acima da grade de exibição Status de pagamento da ordem, ao lado do filtro Seletor de calendário de datas da ordem.

#### Status de pagamento

A coluna Status do pagamento mostra o status atual de qualquer pagamento. A `Capture failed` pagamento mostra um status de alerta vermelho e um `Voided` pagamento mostra um status de alerta cinza.

#### Status do reembolso

A coluna Status da restituição mostra o status atual de qualquer restituição. A `Capture failed` pagamento mostra um status de alerta vermelho e um `Voided` pagamento mostra um status de alerta cinza.

### Atualizar dados do relatório

A exibição do relatório Status do pagamento da ordem mostra uma _[!UICONTROL Last updated]_carimbo de data e hora que mostra a última vez que as informações do relatório foram atualizadas. Por padrão, os dados do relatório de status de pagamento da ordem são atualizados automaticamente a cada três horas.

Você também pode forçar manualmente uma atualização dos dados do relatório Status de pagamento da ordem para ver as informações mais atualizadas do relatório.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Clique em _Atualizar_ ícone (![ícone de atualização](assets/refresh-button-med.png)).

   Os dados do relatório de status do pagamento da ordem são atualizados, e *[!UICONTROL Update complete]* a confirmação é exibida e as informações mais recentes estão presentes na grade.

### Exibir contestações

Você pode visualizar todas as contestações nos pedidos da sua loja e navegar até o Centro de Resolução do PayPal para tomar medidas sobre elas, a partir do relatório Order payment status.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Navegue até a **[!UICONTROL Disputes column]**.
1. Veja todas as contestações de um pedido específico e veja [o status da contestação](#order-payment-status-information).
1. Clique no link de ID de contestação (começando com _PP-D-_) para acessar o [Centro de resolução do PayPal](https://www.paypal.com/us/smarthelp/article/what-is-the-resolution-center-faq3327).
1. Tomar as medidas apropriadas para a disputa, conforme necessário.

   Para classificar contestações de ordem por status, clique no cabeçalho da coluna Contestações.

### Baixar status de pagamento da ordem

É possível baixar um arquivo .csv com todos os status visíveis na grade de exibição do status do Order payment, seja visualizando os status padrão de 30 dias ou um período personalizado.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Order payment status]**.
1. Se quiser ver os status de um período diferente dos últimos 30 dias, [personalizar o período do intervalo de datas para seus status](#customize-dates-timeframe).
1. Clique em _Baixar_ (![ícone de download](assets/icon-download.png)) ícone.

Os status do seu pedido de pagamento são baixados em um formato .csv.

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

#### Informações de status

Os relatórios de status do pagamento da ordem incluem as informações a seguir.

| Coluna | Descrição |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | ID da ordem de comércio<br> <br>Para ver as [informações do pedido](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}, clique no ID. |
| [!UICONTROL Order Date] | Carimbo de data e hora do pedido |
| [!UICONTROL Authorized Date] | Data/carimbo de data/hora da autorização de pagamento |
| [!UICONTROL Order Status] | Comércio atual [status do pedido](https://docs.magento.com/user-guide/sales/order-status.html){target="_blank"} |
| [!UICONTROL Invoiced] | Status da fatura do pedido—*[!UICONTROL No]*, *[!UICONTROL Partial]* ou *[!UICONTROL Yes]* |
| [!UICONTROL Shipped] | Status da remessa do pedido—*[!UICONTROL No]*, *[!UICONTROL Partial]* ou *[!UICONTROL Yes]* |
| [!UICONTROL Order Amt] | Valor total geral do pedido |
| [!UICONTROL Cur] | Tipo de moeda do pedido |
| [!UICONTROL Pay Status] | Status do pagamento de um pedido específico |
| [!UICONTROL Paid Amt] | Valor pago em um pedido |
| [!UICONTROL Cur] | Tipo de moeda do valor pago em um pedido |
| [!UICONTROL Refund Status] | Status de uma restituição em uma ordem (como informações de devoluções, RMAs e avisos de crédito)—   *[!UICONTROL Requires refund]*, *[!UICONTROL Refund requested]*, *[!UICONTROL Refunded]*, *[!UICONTROL Refund failed]* ou *[!UICONTROL Voided]* |
| [!UICONTROL Refund Amount] | Total do valor reembolsado de um pedido |
| [!UICONTROL Cur] | Tipo de moeda do valor reembolsado de um pedido |
| [!UICONTROL Disputes] | Status de qualquer contestação em uma ordem (informações de contestações e chargebacks) —*[!UICONTROL Open]*, *[!UICONTROL Waiting for buyer response]*, *[!UICONTROL Waiting for seller response]*, *[!UICONTROL Under review]*, *[!UICONTROL Resolved]* ou *[!UICONTROL Other]* |
| [!UICONTROL Payment Method] | Método de pagamento usado na transação Comércio de uma ordem |
| [!UICONTROL Website] | Site do qual o pedido foi feito |
| [!UICONTROL Store] | Armazenamento no qual o pedido foi feito |
| [!UICONTROL Store View] | Exibição de armazenamento da qual o pedido foi feito |
