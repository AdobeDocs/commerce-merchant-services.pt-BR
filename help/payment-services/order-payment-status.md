---
title: Relatório de Status do Pagamento do Pedido
description: Use o relatório de status de pagamento de Pedido para obter visibilidade sobre o status de pagamento de seus pedidos e identificar possíveis problemas.
role: User
level: Intermediate
exl-id: 192e47b9-d52b-4dcf-a720-38459156fda4
feature: Payments, Checkout, Orders
source-git-commit: 0dc370409ace6ac6b0a56511cd0071cf525620f1
workflow-type: tm+mt
source-wordcount: '2045'
ht-degree: 0%

---

# Relatório de Status do Pagamento do Pedido

[!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source] O oferece relatórios abrangentes para que você possa ter uma visão clara das configurações da sua loja [transações](transactions.md), pedidos e pagamentos.

Há duas exibições disponíveis do relatório de status do pagamento da ordem para permitir que você exiba rapidamente o status do pagamento de suas ordens:

* **[Exibição de visualização do status do pagamento da ordem](#order-payment-status-data-visualization-view)**—Gráfico disponível na Página Inicial dos Serviços de Pagamento que é uma representação visual dos status de pagamento agregados por dia a partir da exibição do relatório Status do pagamento da ordem
* **[Exibição do relatório de status do pagamento da ordem](#order-payment-status-report-view)**—Relatório disponível no status do Order payment que mostra os status detalhado do pagamento, faturado, remetido, reembolso e contestação de todas as transações

As exibições de status do Pedido de pagamento ajudam você a entender facilmente onde uma ordem específica está dentro do fluxo do processo da ordem para caixa. Esses relatórios permitem visualizar rapidamente os pedidos, com base no status do pagamento e na data do pagamento, e identificar possíveis problemas.

Você pode [baixar Status de pagamento de pedido](#download-order-payment-statuses) em um formato de arquivo .csv para uso em software existente de contabilidade ou gerenciamento de pedidos.

>[!NOTE]
>
>Não é possível exibir relatórios financeiros se você não tiver [modo Online integrado e ativado](production.md#enable-live-payments) para [!DNL Payment Services].

## Exibição da visualização de dados do status do pagamento da ordem

A visualização de dados do status do pagamento do pedido está disponível na Página inicial dos Serviços de pagamento. É uma representação visual dos status de pagamento agregados por dia a partir da tabela detalhada [Exibição do relatório de status do pagamento da ordem](#order-payment-status-report-view).

No _Admin_ barra lateral, vá para **Vendas** > **Payment Services** > _Pedidos_ para ver a visualização de dados [gráfico de status de pagamento](#statuses-information).

![Visualização de dados de pagamento no Administrador](assets/orderpayment-dataviz.png){width="800" zoomable="yes"}

Clique em **[!UICONTROL View Report]** para navegar até a tabela detalhada [Exibição do relatório de status do pagamento da ordem](#order-payment-status-report-view).

### Personalizar período de status

Por padrão, são exibidos 30 dias de status de pagamento.

Na exibição de visualização do status do pagamento da Ordem, é possível personalizar o período dos status de pagamento que você deseja exibir, selecionando um intervalo de datas:

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. A visualização de dados do status do pagamento do pedido está visível no _Pedidos_ seção.
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

A visualização do relatório Status do pagamento do pedido está disponível na visualização Início dos Serviços de pagamento. Ele inclui status detalhados — pagamento, faturado, enviado, reembolso, contestação e muito mais — para todas as transações.

No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**para ver a exibição detalhada do relatório de status do pagamento da ordem.

![Transações de status de pagamento de pedido no Administrador](assets/orders-report-data.png){width="800" zoomable="yes"}

É possível configurar essa visualização, de acordo com as seções neste tópico, para apresentar melhor os dados que você deseja ver.

Você pode [baixar transações de pagamento](#download-order-payment-statuses) em um formato de arquivo .csv para uso em software existente de contabilidade ou gerenciamento de pedidos.

>[!NOTE]
>
>Os dados mostrados nesta tabela são classificados em ordem decrescente (`DESC`) por padrão usando o `TRANS DATE`. A variável `TRANS DATE` é a data e a hora em que a transação foi iniciada.

### Atualizações do status de pagamento

Determinados métodos de pagamento exigem um período para capturar o pagamento. [!DNL Payment Services] O agora detecta os status pendentes de uma transação de pagamento em uma ordem do:

* Detecção síncrona `pending capture` transações
* Monitoramento assíncrono `pending capture` transações

>[!NOTE]
>
>A detecção dos status pendentes das transações de pagamento em uma ordem impede a entrega acidental de ordens se o pagamento ainda não tiver sido recebido. Isso pode ocorrer para transações de Cheque eletrônico e PayPal.

#### Detecção síncrona de transações de captura pendentes

Detectar automaticamente transações de captura em uma `Pending` status e impedir que os pedidos insiram um `Processing` status quando essa transação é detectada.

Durante o checkout do cliente ou quando um administrador cria uma NFF para um pagamento autorizado anteriormente, [!DNL Payment Services] O detecta automaticamente as transações de captura em uma `Pending` O status e altera as ordens correspondentes para `Payment Review` status.

#### Monitoramento assíncrono de transações de captura pendentes

Detectar quando uma transação de captura pendente entra em uma `Completed` para que os comerciantes possam retomar o processamento do pedido afetado.

Para garantir que esse processo funcione conforme o esperado, os comerciantes devem configurar um novo trabalho cron. Quando o job estiver configurado para ser executado automaticamente, nenhuma outra intervenção será esperada do comerciante.

Consulte [Configurar trabalhos cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html). Uma vez configurado, o novo trabalho é executado a cada 30 minutos para buscar atualizações para pedidos que estão em uma `Payment Review` status.

Os comerciantes podem verificar o status de pagamento atualizado por meio da exibição do relatório Status de pagamento da ordem.

### Dados usados no relatório

[!DNL Payment Services] O usa dados de pedidos e os combina com dados de pagamentos agregados de outras fontes (incluindo PayPal), para fornecer relatórios significativos e altamente úteis.

Os dados do pedido são exportados e mantidos no serviço de pagamento. Quando você [alterar ou adicionar status de pedido](https://docs.magento.com/user-guide/sales/order-status-custom.html) ou [editar uma visualização de loja](https://docs.magento.com/user-guide/stores/stores-all-view-edit.html), [loja](https://docs.magento.com/user-guide/stores/store-information.html), ou nome do site, de que os dados são combinados com os dados de pagamento e o relatório de status de pagamento do pedido é preenchido com as informações combinadas.

Há duas etapas neste processo:

1. O índice é alterado nos dados `ON SAVE` (sempre que as informações da ordem ou da loja forem alteradas) ou `BY SCHEDULE` (em uma programação cron pré-configurada), dependendo de como ela é configurada no [Gerenciamento de índice](https://docs.magento.com/user-guide/system/index-management.html) em Admin.

   Por padrão, ocorre a indexação de dados `ON SAVE`, o que significa que sempre que algo for alterado no pedido, no status do pedido, na exibição da loja, na loja ou no site, o processo de reindexação ocorrerá imediatamente.

1. Os dados indexados são enviados para o serviço de pagamento, que é preenchido no relatório Order payment status.

Os únicos dados exportados e agrupados para fins de relatório são os dados usados pelo relatório de status do Pedido de pagamento.

>[!NOTE]
>
>Os dados mostrados nesta tabela são classificados em ordem decrescente (`DESC`) por padrão usando o `ORDER DATE`. A variável `ORDER DATE` é a data e a hora em que o pedido foi criado.

#### Configurar exportação de dados

Mesmo que, por padrão, a reindexação ocorra em `ON SAVE` , é recomendável indexar no `BY SCHEDULE` modo. A variável `BY SCHEDULE` O índice é executado em uma programação cron de um minuto, e quaisquer dados alterados são exibidos no relatório Status do pedido dentro de dois minutos após qualquer alteração de dados. Essa reindexação programada ajuda a reduzir qualquer esforço na loja, especialmente se você tiver um grande volume de pedidos recebidos, pois isso acontece em um cronograma (não conforme cada pedido é feito).

Você pode alterar o modo do índice—`ON SAVE` ou `BY SCHEDULE`—[no Admin](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).

Para saber como configurar a exportação de dados, consulte [Configuração da linha de comando](configure-cli.md#configure-data-export).

### Selecionar fonte de dados

Na exibição do relatório Status de pagamento da ordem, é possível selecionar a fonte de dados —**[!UICONTROL Live]** _ ou **[!UICONTROL Sandbox]**—para o qual você deseja ver os resultados do relatório.

![Seleção de fontes de dados](assets/datasource.png){width="300" zoomable="yes"}

Se _[!UICONTROL Live]_for a fonte de dados selecionada, você poderá ver as informações do relatório das lojas que usam [!DNL Payment Services] no modo de produção. Se_[!UICONTROL Sandbox]_ for a fonte de dados selecionada, você poderá ver informações de relatório para o modo sandbox.

As seleções de fonte de dados funcionam da seguinte maneira:

* Se você não tiver lojas que usam [!DNL Payment Services] no modo Online, a seleção da fonte de dados é padronizada como _[!UICONTROL Sandbox]_.
* Se você tiver lojas (uma ou várias) que usam [!DNL Payment Services] no modo Online, a seleção da fonte de dados é padronizada como _[!UICONTROL Live]_.
* As exportações de relatórios sempre seguem a seleção da fonte de dados.

Para selecionar a fonte de dados para sua [!UICONTROL Order Payment Status] relatório:

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Orders]** > **[!UICONTROL View Report]**.
1. Clique em _[!UICONTROL Data source]_filtro do seletor e selecione **[!UICONTROL Live]**ou **[!UICONTROL Sandbox]**.

   Os resultados do relatório são gerados novamente com base na fonte de dados selecionada.

### Personalizar período de datas do pedido

Na exibição do relatório Status de pagamento da ordem, você pode personalizar o período dos resultados do status que deseja exibir selecionando datas específicas. Por padrão, 30 dias de status de pedidos de pagamento são mostrados na grade.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Clique em _[!UICONTROL Order dates]_filtro seletor de calendário.
1. Escolha o intervalo de datas aplicável.
1. Exiba os status de pagamento da ordem para as datas especificadas na grade.

### Filtrar informações do relatório

Na exibição do relatório Status de pagamento da ordem, você pode filtrar os resultados dos status que deseja exibir selecionando critérios de filtro.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Clique em **[!UICONTROL Filter]** seletor.
1. Alterne a _Status do pagamento_ opções para ver os resultados do relatório apenas para os status do pagamento da ordem selecionado.
1. Exibir resultados do relatório dentro de uma faixa de valores da ordem informando uma _[!UICONTROL Min Order Amount]_ou _[!UICONTROL Max Order Amount_].
1. Clique em **[!UICONTROL Hide filters]** para ocultar o filtro.

### Mostrar e ocultar colunas

O relatório Status do Pagamento da Ordem mostra todas as colunas de informações disponíveis por padrão. No entanto, você pode personalizar quais colunas verá no relatório.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Clique em _Configurações de coluna_ ícone (![ícone configurações de coluna](assets/column-settings.png){width="20" zoomable="yes"}).
1. Para personalizar quais colunas você vê no relatório, marque ou desmarque as colunas na lista.

   O relatório de status do pagamento da Ordem mostra imediatamente quaisquer alterações feitas no menu de configurações Coluna. As preferências de coluna são salvas e permanecem em vigor se você sair da exibição de relatório.

### Exibir status

A exibição do relatório Status de pagamento da ordem mostra informações abrangentes de status de pagamento para cada ordem.

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

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Clique em _Atualizar_ ícone (![ícone de atualização](assets/refresh-button-med.png){width="20" zoomable="yes"}).

   Os dados do relatório de status do pagamento da ordem são atualizados, e *[!UICONTROL Update complete]* a confirmação é exibida e as informações mais recentes estão presentes na grade.

### Exibir contestações

Você pode visualizar todas as contestações nos pedidos da sua loja e navegar até o Centro de Resolução do PayPal para tomar medidas sobre elas, a partir do relatório Order payment status.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Navegue até a **[!UICONTROL Disputes column]**.
1. Veja todas as contestações de um pedido específico e veja [o status da contestação](#order-payment-status-information).
1. Revisar detalhes da contestação do [Centro de resolução do PayPal](https://www.paypal.com/us/cshelp/article/what-is-the-resolution-center-help246) clicando no link de ID de contestação que começa com _PP-D-_.
1. Tomar as medidas apropriadas para a disputa, conforme necessário.

   Para classificar contestações de ordem por status, clique no [!UICONTROL Disputes] cabeçalho da coluna.

### Baixar status de pagamento da ordem

É possível baixar um arquivo .csv com todos os status visíveis na grade de exibição do status do Order payment, seja visualizando os status padrão de 30 dias ou um período personalizado.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Orders]_>**[!UICONTROL View Report]**.
1. Se quiser ver os status de um período diferente dos últimos 30 dias, [personalizar o período do intervalo de datas para seus status](#customize-dates-timeframe).
1. Clique em _Baixar_ (![ícone de download](assets/icon-download.png){width="20" zoomable="yes"}) ícone.

Os status do seu pedido de pagamento são baixados em um formato .csv.

### Descrições da coluna

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
