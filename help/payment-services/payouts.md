---
title: Relatório de pagamentos
description: Use o relatório de Pagamentos para obter total transparência no valor do pagamento, no volume processado e em relatórios detalhados no nível da transação para reconciliação financeira.
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '1335'
ht-degree: 0%

---

# Relatório de pagamentos

[!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source] O oferece relatórios abrangentes para que você possa ter uma visão clara dos pedidos e pagamentos da loja.

![Exibição de relatórios financeiros](assets/reports-justpayouts.png)

Há duas visualizações de relatórios de Pagamentos disponíveis para permitir que você veja informações detalhadas sobre todos os seus pagamentos:

* **[Visualização de visualização de dados de pagamentos](#payouts-data-visualization-view)**—Gráfico disponível na Página inicial dos serviços de pagamento que é uma representação visual dos valores agregados por dia a partir da visualização do relatório de Pagamentos
* **[Exibição do relatório de pagamentos](#payouts-report-view)**—Relatório disponível em Pagamentos que mostra informações detalhadas de pagamento para todas as transações

As visualizações de Pagamentos mostram rapidamente informações abrangentes sobre o pagamento, permitindo total transparência sobre o valor do pagamento, o volume processado e relatórios detalhados sobre o nível da transação para reconciliação financeira.

>[!NOTE]
>
>Os relatórios de pagamentos mostram apenas ordens capturadas (a ação de pagamento está definida como [`Authorize and Capture`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method))—ou [marcado como `Invoiced`](https://docs.magento.com/user-guide/sales/invoice-create.html).

## Visualização de visualização de dados de pagamentos

A visualização de dados de Pagamentos está disponível na Página inicial dos Serviços de pagamento. É uma representação visual das quantidades agregadas por dia da tabela detalhada [Exibição do relatório de pagamentos](#payouts-report-view).

No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** para ver o gráfico de visualização de dados de créditos vs. débitos e as médias móveis ao longo do tempo.

![Visualização de dados de pagamento no Administrador](assets/payouts-report.png)

Clique em **[!UICONTROL View Report]** para navegar até a tabela detalhada [Exibição do relatório de pagamentos](#payouts-report-view).

### Personalizar período de transações

Por padrão, 30 dias de transações são exibidos.

Na visualização de dados de Pagamentos, é possível personalizar o período das transações de pagamento que deseja exibir, selecionando um intervalo de datas:

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**. A visualização de dados dos Pagamentos está visível na seção Pagamentos.
1. Clique em **[!UICONTROL Range]** filtro seletor.
1. Escolha o intervalo de datas aplicável: 30 dias, 15 dias ou 7 dias.
1. Exibir as informações de transações para as datas especificadas.

### Informações de transações

Os valores de transação para um intervalo de datas selecionado são mostrados à esquerda da visualização de dados de Pagamentos. As datas do intervalo de datas selecionado são mostradas na parte inferior da exibição. Se não houver pagamentos em uma data específica, essa data não será exibida.

A visualização de visualização de dados dos Pagamentos inclui as seguintes informações.

| Dados | Descrição |
| ------------ | -------------------- |
| [!UICONTROL Transaction amount] | Intervalo de valores para transações no intervalo de tempo especificado; dados no eixo Y (à esquerda) |
| Intervalo de datas | Intervalo de datas para o intervalo de tempo especificado; dados no eixo X (inferior) |
| Crédito | Pagamentos no prazo especificado |
| Débito | Débitos (reembolsos) para o período de tempo especificado |
| Média móvel | Representação do pagamento médio para cada data no período especificado |
| Líquido para intervalo | Valor líquido de pagamento para o período de tempo especificado (intervalo) |

## Exibição do relatório de pagamentos

A visualização de relatório Pagamentos está disponível na visualização Pagamentos dos Serviços de pagamento. Ele inclui todas as informações disponíveis sobre pagamentos para sua(s) loja(s). A variável [Visualização de visualização de dados de pagamentos](#payouts-data-visualization-view) A na Página inicial dos Serviços de pagamento é uma representação visual dos valores agregados por dia nesta visualização de relatório mais detalhada.

No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]** para ver a visualização detalhada do relatório de Pagamentos em formato tabular.

![Transações de pagamento no Administrador](assets/payouts-report-new.png)

É possível configurar essa visualização, de acordo com as seções neste tópico, para apresentar melhor os dados que você deseja ver.

Consulte IDs de ordem e transação vinculadas do Commerce, valores da transação, método de pagamento por transação e muito mais, tudo no relatório de Pagamentos no Administrador.

Você pode fazer download de transações de pagamento em um formato de arquivo .csv para uso em software de contabilidade ou gerenciamento de pedidos existente.

>[!NOTE]
>
>Os dados mostrados nesta tabela são classificados em ordem decrescente (`DESC`) por padrão usando o `TRANS DATE`. A variável `TRANS DATE` é a data e a hora em que a transação foi iniciada.

### Selecionar fonte de dados

Na visualização de relatório de Pagamentos, é possível selecionar a fonte de dados —_[!UICONTROL Live]_ou_[!UICONTROL Sandbox]_—para o qual você deseja ver os resultados do relatório.

![Seleção de fontes de dados](assets/datasource.png)

Se _[!UICONTROL Live]_for a fonte de dados selecionada, você poderá ver informações do relatório das suas lojas em tempo real. Se [!UICONTROL Sandbox]_ for a fonte de dados selecionada, você poderá ver informações de relatório para seu ambiente de Sandbox.

As seleções de fonte de dados funcionam da seguinte maneira:

* Se você não tiver armazenamentos no modo Online, a seleção da fonte de dados assumirá como padrão _[!UICONTROL Sandbox]_.
* Se você tiver algum armazenamento (um ou vários) no modo Online, a seleção da fonte de dados assumirá como padrão _[!UICONTROL Live]_.
* As exportações de relatórios sempre seguem a seleção da fonte de dados.

Para selecionar a origem de dados para o relatório de Status de Pagamento da Ordem:

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Clique em **[!UICONTROL Data source]** e selecione _[!UICONTROL Live]_ou_[!UICONTROL Sandbox]_.

   Os resultados do relatório são gerados novamente com base na fonte de dados selecionada.

### Exibir transações

Por padrão, 30 dias de transações são exibidos.

O número de linhas retornado em uma pesquisa, ou mostrado no padrão de 30 dias de transações, é mostrado acima da grade de exibição Pagamentos ao lado do filtro seletor de calendário de datas da transação.

Role para a esquerda e para a direita para visualizar [informações para cada transação de pagamento](#column-descriptions) no relatório diário, incluindo a data da transação, o ID de referência, o número da NFF e os detalhes do método de pagamento.

#### Personalizar período de transações

Na exibição do relatório de Pagamentos, é possível personalizar o período das transações de pagamento que deseja exibir, informando datas específicas ou selecionando um intervalo de datas no seletor de datas:

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Clique no filtro Seletor de calendário de datas de transação.
1. Escolha o intervalo de datas aplicável.
1. Exiba os status de pagamentos na grade para as datas especificadas.

### Mostrar e ocultar colunas

A visualização de relatório de Pagamentos mostra a maioria das colunas de informações disponíveis por padrão. No entanto, você pode personalizar quais colunas verá no relatório.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Payouts]**.
1. Clique em _Configurações de coluna_ ícone (![ícone configurações de coluna](assets/column-settings.png)).
1. Para personalizar quais colunas você vê no relatório, marque ou desmarque as colunas na lista.

   A visualização de relatório de Pagamentos mostrará imediatamente quaisquer alterações feitas no menu Configurações de coluna. As preferências de coluna serão salvas e permanecerão em vigor se você sair da exibição de relatório.

### Baixar transações

É possível baixar um arquivo .csv contendo todas as transações visíveis na grade de exibição de Pagamentos.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. [Personalizar o período de intervalo de datas para suas transações](#customize-transactions-timeframe).
1. Clique em _Baixar_ (![](assets/icon-download.png)) ícone.

Suas transações de pagamento são baixadas em um formato .csv.

### Descrições da coluna

Os relatórios de pagamento incluem as seguintes informações.

| Coluna | Descrição |
| ------------ | -------------------- |
| [!UICONTROL Provider] | Provedor de pagamento |
| [!UICONTROL Provider trans] | ID da transação |
| [!UICONTROL Trans date] | Data e hora em que a transação foi iniciada |
| [!UICONTROL Type] | Tipo de transação—*[!UICONTROL PAYMENT]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REFUND]*, *[!UICONTROL REVERSAL]*, *[!UICONTROL WITHDRAWAL]* <br> <br>Consulte [Tipos de transação](#transaction-types) para obter mais informações. |
| [!UICONTROL Status] | Status atual da transação—*[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | Código da transação que indica Crédito (*CR*) ou Débito (*DR*) |
| [!UICONTROL Reference ID] | ID da transação original para a qual este evento está relacionado |
| [!UICONTROL Invoice] | ID da fatura (uma por pedido) da transação |
| [!UICONTROL Commerce order] | ID da ordem de comércio <br> <br>Para ver as [informações do pedido](https://docs.magento.com/user-guide/sales/orders.html){target="_blank"}, clique no ID. |
| [!UICONTROL Commerce trans] | ID de transação comercial <br> <br>Para ver as [informações da transação](https://docs.magento.com/user-guide/sales/transactions.html){target="_blank"}, clique no ID. |
| [!UICONTROL Pay method] | Tipo de cartão de crédito—*[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL APPLE_PAY]*, *[!UICONTROL CREDIT_CARD]*—e o provedor de cartões associado (como *Visa* ou *MasterCard*) |
| [!UICONTROL Trans amt] | Valor da transação |
| [!UICONTROL Cur] | Unidade monetária para valor da transação |
| [!UICONTROL Pending] | Valor a ser desembolsado |
| [!UICONTROL Cur] | Unidade monetária para o valor pendente |
| [!UICONTROL Seller amt] | Quantidade de fundos transferidos de ou para um cliente <br> <br>Os fundos que saem da conta do vendedor mostram um prefixo de traço (-). |
| [!UICONTROL Cur] | Unidade monetária para o valor do vendedor |
| [!UICONTROL Partner fee] | Taxas de parceiro associadas à transação <br> <br>Os fundos que saem da conta de taxa do parceiro mostram um prefixo de traço (-). |
| [!UICONTROL Cur] | Unidade monetária da taxa do parceiro |
| [!UICONTROL Prov fees] | Taxas associadas à transação <br> <br>Os fundos que saem da conta de taxas do provedor mostram um prefixo de traço (-). |
| [!UICONTROL Cur] | Unidade monetária para a taxa do provedor |
| [!UICONTROL Fee %] | Porcentagem do valor da transação cobrado como uma taxa |
| [!UICONTROL Fixed fee] | Valor da taxa fixa do provedor |
| [!UICONTROL Chbk fee] | Taxa de chargeback associada à transação <br> <br>Um prefixo de traço (-) indica que a taxa de chargeback foi revertida. |
| [!UICONTROL Cur] | Unidade monetária para a taxa de substituição de débito |
| [!UICONTROL Hold amt] | Quantia colocada em espera ou liberada da retenção <br> <br>Um prefixo de traço (-) indica que os fundos em espera estão sendo liberados. |
| [!UICONTROL Cur] | Unidade monetária para o valor de retenção |
| [!UICONTROL Recoup amt] | Valor recuperado da conta de recuperação <br> <br>Os fundos que saem da conta de recuperação mostram um prefixo de traço (-). |
| [!UICONTROL Cur] | Unidade monetária para o valor de recuperação |

### Tipos de transação

Esses tipos de transação podem ser observados nas transações de pagamento.

| Relatório | Descrição |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | Dinheiro movido entre um comprador e um vendedor para um pedido |
| [!UICONTROL AUTH] | Transações de anulação de autorização e autorização |
| [!UICONTROL BONUS] | -- |
| [!UICONTROL CHARGEBACK] | Transações de estorno de taxa de substituição de débito e de taxa de substituição de débito |
| [!UICONTROL CORRECTION] | -- |
| [!UICONTROL CURRENCY_CONVERSION] | -- |
| [!UICONTROL DEPOSIT] | -- |
| [!UICONTROL DISBURSEMENT] | -- |
| [!UICONTROL DISPUTE] | -- |
| [!UICONTROL FEES] | Transações de reversão de taxas, taxas de pagamento e tarifas do parceiro |
| [!UICONTROL HOLD] | -- |
| [!UICONTROL HOLD_RELEASE] | -- |
| [!UICONTROL INCENTIVES] | -- |
| [!UICONTROL OTHERS] | -- |
| [!UICONTROL RECOUP] | Recuperações de contas bancárias ou de perdas |
| [!UICONTROL REFUND] | -- |
| [!UICONTROL REVERSAL] | -- |
| [!UICONTROL WITHDRAWAL] | -- |
