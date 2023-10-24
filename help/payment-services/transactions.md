---
title: Relatório de Transações
description: Use o relatório de Transações para obter visibilidade sobre taxas de autorização de transações e tendências de transações.
role: User
level: Intermediate
exl-id: dd1d80f9-5983-4181-91aa-971522eb56fa
source-git-commit: 91acc6e1dfd142caca77c0dc9ba55da34f75dd60
workflow-type: tm+mt
source-wordcount: '1274'
ht-degree: 0%

---

# Relatório de Transações

[!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source] O oferece relatórios abrangentes para que você possa ter uma visão clara das transações, pedidos e pagamentos da loja.

![Relatório de transações](assets/transactions-report.png){width="700" zoomable="yes"}

O relatório de Transações oferece visibilidade sobre taxas de autorização de transações e tendências de transações negativas, para que você possa monitorar efetivamente a integridade do armazenamento e identificar e resolver quaisquer problemas de transação.

Consulte transações individuais para pedidos colocados na loja e seus métodos de pagamento, resultado, códigos de resposta de pagamento e muito mais.

As informações fornecidas no relatório de Transações se destinam apenas ao uso comercial. Não compartilhe essas informações com clientes ou outros possíveis fraudadores. As informações sobre transações podem ser usadas para ignorar as verificações de segurança ou fazer pedidos que resultem em substituições de débitos.

Você pode fazer download do relatório de Transações em um formato de arquivo .csv para uso em software de contabilidade ou gerenciamento de pedidos existente.

>[!NOTE]
>
>Não é possível exibir relatórios financeiros se você não tiver [modo Online integrado e ativado](production.md#enable-live-payments) para [!DNL Payment Services].

## Exibição do relatório de transações

A visualização do relatório Transações está disponível na visualização Transações dos Serviços de pagamento. Inclui todas as informações disponíveis sobre transações para sua(s) loja(s).

No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**para ver a exibição detalhada do relatório de Transações tabulares.

![Exibição do relatório de transações](assets/transactions-report-detail.png){width="600" zoomable="yes"}

É possível configurar essa visualização, de acordo com as seções neste tópico, para apresentar melhor os dados que você deseja ver.

Consulte IDs de transação de fornecedor e ordem de comércio vinculados, valores da transação, método de pagamento por transação e muito mais, tudo nesse relatório.

Nem todos os métodos de pagamento fornecem a mesma granularidade de informações. Por exemplo, as transações com cartão de crédito fornecem resposta, AVS, e códigos CCV, e os últimos quatro dígitos do cartão no relatório de Transações; os botões PayPal Smart não.

Você pode [transações de download](#download-transactions) em um formato de arquivo .csv para uso em software existente de contabilidade ou gerenciamento de pedidos.

### Selecionar fonte de dados

Na visualização do relatório Transactions, é possível selecionar a fonte de dados —**[!UICONTROL Live]** ou **[!UICONTROL Sandbox]**—para o qual você deseja ver os resultados do relatório.

![Seleção de fontes de dados](assets/datasource.png){width="300" zoomable="yes"}

Se _[!UICONTROL Live]_for a fonte de dados selecionada, você poderá ver as informações do relatório das lojas que usam [!DNL Payment Services] no modo de produção. Se_[!UICONTROL Sandbox]_ for a fonte de dados selecionada, você poderá ver informações de relatório para o modo sandbox.

As seleções de fonte de dados funcionam da seguinte maneira:

* Se você não tiver lojas que usam [!DNL Payment Services] no modo de produção, a seleção da fonte de dados assume como padrão _[!UICONTROL Sandbox]_.
* Se você tiver lojas (uma ou várias) que usam [!DNL Payment Services] no modo de produção, a seleção da fonte de dados assume como padrão _[!UICONTROL Live]_.
* As exportações de relatórios sempre seguem a seleção da fonte de dados.

Para selecionar a fonte de dados para sua [!UICONTROL Transactions] relatório:

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Clique em **[!UICONTROL Data source]** e selecione **[!UICONTROL Live]** ou **[!UICONTROL Sandbox]**.

   Os resultados do relatório são gerados novamente com base na fonte de dados selecionada.

### Personalizar período de datas

Na exibição do relatório Transações, você pode personalizar o período das transações que deseja exibir selecionando datas específicas. Por padrão, 30 dias de transações são mostrados na grade.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Clique em **[!UICONTROL Transaction dates]** filtro seletor de calendário.
1. Escolha o intervalo de datas aplicável.
1. Exiba as transações para as datas especificadas na grade.

### Filtrar informações do relatório

Na exibição do relatório Transações, você pode filtrar os resultados de status que deseja exibir selecionando critérios de filtro.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Clique em **[!UICONTROL Filter]** seletor.
1. Alterne a _[!UICONTROL Transaction Result]_opções para ver os resultados do relatório somente para as transações de ordem selecionadas.
1. Selecione o _[!UICONTROL Card Type]_para ver os resultados do relatório para o tipo de cartão selecionado. Uma dica de ferramenta com mais informações é exibida quando o processador de pagamento não consegue identificar o tipo de cartão.
1. Selecione o _[!UICONTROL Card Brand]_para ver os resultados do relatório da marca de cartão selecionada. Uma dica de ferramenta com mais informações é exibida quando o processador de pagamento não consegue identificar a marca do cartão.
1. Alterne a _[!UICONTROL Payment Method]_opções para ver os resultados do relatório somente para os métodos de pagamento selecionados.
1. Insira um _Valor mínimo do pedido_ ou _Valor máximo do pedido_ para ver os resultados do relatório dentro dessa faixa de quantias da ordem.
1. Insira um _[!UICONTROL Order ID]_para procurar uma transação específica.
1. Insira o _[!UICONTROL Card Last Four Digits]_para procurar um cartão de crédito ou débito específico.
1. Clique em **[!UICONTROL Hide filters]** para ocultar o filtro.

### Mostrar e ocultar colunas

O relatório de Transações mostra todas as colunas de informações disponíveis por padrão. No entanto, você pode personalizar quais colunas verá no relatório.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Clique em **[!UICONTROL Column settings]** ícone ![ícone configurações de coluna](assets/column-settings.png){width="20" zoomable="yes"}.
1. Para personalizar quais colunas você vê no relatório, marque ou desmarque colunas na lista.

   O relatório de Transações mostra imediatamente quaisquer alterações feitas no menu de configurações Coluna. As preferências de coluna são salvas e permanecem em vigor se você sair da exibição de relatório.

### Atualizar dados do relatório

A visualização do relatório Transactions mostra uma _[!UICONTROL Last updated]_carimbo de data e hora que mostra a última vez que as informações do relatório foram atualizadas. Por padrão, os dados do relatório de Transações são atualizados automaticamente a cada três horas.

Você também pode forçar manualmente uma atualização dos dados do relatório para ver as informações mais atualizadas do relatório.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > _[!UICONTROL Transactions]_>**[!UICONTROL View Report]**.
1. Clique em _Atualizar_ ícone (![ícone de atualização](assets/refresh-button-med.png){width="20" zoomable="yes"}).

   Os dados do relatório de Transações são atualizados, e *[!UICONTROL Update complete]* a confirmação é exibida e as informações mais recentes estão presentes na grade.

### Baixar transações

É possível baixar um arquivo .csv com todas as transações visíveis na grade de exibição de transações, seja visualizando os 30 dias padrão de transações ou um período personalizado.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Transactions]**.
1. Se quiser ver transações para um período diferente dos últimos 30 dias, [personalizar o período do intervalo de datas para seus status](#customize-dates-timeframe).
1. Clique em _Baixar_ ![ícone de download](assets/icon-download.png){width="20" zoomable="yes"} ícone.

Suas transações são baixadas em um formato .csv.

### Descrições da coluna

Os relatórios de transações incluem as seguintes informações.

| Coluna | Descrição |
| ------------ | -------------------- |
| [!UICONTROL Order ID] | ID da ordem de comércio (contém apenas valores para transações bem-sucedidas e está vazia para transações rejeitadas)<br> <br>Para ver as [informações do pedido](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}, clique no ID. |
| [!UICONTROL Provider Transaction ID] | A ID da transação fornecida pelo provedor de serviço de pagamento; contém apenas valores para transações bem-sucedidas e contém um traço para transações rejeitadas. |
| [!UICONTROL Transaction Date] | Carimbo de data e hora da transação |
| [!UICONTROL Payment Method] | Método de pagamento da transação com informações detalhadas sobre marca e tipo de cartão. Consulte [tipos de cartão](https://developer.paypal.com/docs/api/orders/v2/#definition-card_type) para obter mais informações; disponível para Payment Services versões 1.6.0 e mais recentes |
| [!UICONTROL Card Last Four Digits] | Últimos quatro dígitos dos cartões de crédito ou débito usados na transação |
| [!UICONTROL Result] | O resultado da transação —*[!UICONTROL OK]* (transação bem-sucedida), *[!UICONTROL Rejected by Payment Provider]* (rejeitado pelo PayPal), *[!UICONTROL Rejected by Bank]* (rejeitado pelo banco que emitiu o cartão) |
| [!UICONTROL Response Code] | Código de erro que fornece o motivo da rejeição do provedor de serviço de pagamento ou do banco; consulte a lista de possíveis códigos de resposta e descrições para [`Rejected by Bank` status](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) e [`Rejected by Payment Provider` status](https://developer.paypal.com/api/rest/reference/orders/v2/errors/). |
| [!UICONTROL AVS Code] | Código do Serviço de Verificação de Endereço; as informações de resposta do processador para solicitações de pagamento. Consulte [lista de códigos e descrições possíveis](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) para obter mais informações. |
| [!UICONTROL CVV Code] | Código de valor de verificação de cartão para cartões de crédito e débito; consulte [lista de códigos e descrições possíveis](https://developer.paypal.com/docs/api/orders/v2/#definition-processor_response) para obter mais informações. |
| [!UICONTROL Amount] | Valor da ordem da transação |
| [!UICONTROL Currency] | Moeda usada para a ordem na transação |
| [!UICONTROL Type] | [Ação de pagamento](../payment-services/production.md#set-payment-services-as-payment-method) para transação—`Authorize` ou `Authorize and Capture` |

### Códigos de resposta de erro

A variável _Código de resposta_ mostra um erro específico ou código de sucesso relacionado à transação. Alguns códigos de erro comuns que podem ser exibidos incluem:

* `PAYMENT_DENIED`—A transação foi recusada pelo PayPal porque havia suspeita de fraude.
* `INTERNAL_SERVER_ERROR`—A transação foi recusada pelo PayPal e incorreu em um erro de servidor do PayPal. A transação pode ser repetida.
* `INSTRUMENT_DECLINED`—O cliente foi recusado pelo PayPal de acordo com o método de pagamento selecionado. A transação pode ser repetida com um método de pagamento diferente.
* `9500`—A transação foi recusada pelo banco associado porque havia suspeita de fraude.
* `5120`—A transação foi recusada pelo banco associado porque o cliente não tinha fundos suficientes para o pagamento.
* `5650`—A transação foi recusada pelo banco associado porque o banco requer autenticação forte do cliente ([3DS](security.md#3ds)).

Códigos de resposta de erro detalhados para transações com falha estão disponíveis para transações anteriores a 1° de junho de 2023. Os dados parciais do relatório serão exibidos para transações que ocorreram antes de 1° de junho de 2023.