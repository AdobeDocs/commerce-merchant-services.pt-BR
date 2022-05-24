---
title: Relatório de pagamentos
description: Use o relatório de Pagamentos para obter total transparência sobre a quantia de pagamento, o volume processado e o relatório detalhado sobre o nível da transação para reconciliação financeira.
role: User
level: Intermediate
exl-id: f3f99474-cd28-4c8f-b0ea-dca8e014b108
source-git-commit: 4554ea65ded73e9552f307ff51e0e7eff64cd2e9
workflow-type: tm+mt
source-wordcount: '975'
ht-degree: 0%

---

# Relatório de pagamentos

[!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source] O oferece relatórios abrangentes para que você possa obter uma visão clara dos pedidos e pagamentos da sua loja.

![Exibição de relatórios financeiros](assets/reports-view.png)

O relatório de Pagamentos mostra informações abrangentes sobre o pagamento imediatamente, permitindo que você tenha total transparência sobre a quantia de pagamento, o volume processado e o relatório detalhado sobre o nível da transação para reconciliação financeira.

>[!NOTE]
>
>Os relatórios de pagamentos mostram apenas as ordens capturadas — a ação de pagamento está definida como [`Authorize and Capture`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method))—ou [marcado como `Invoiced`](https://docs.magento.com/user-guide/sales/invoice-create.html).

Não é necessário abrir várias exibições para fazer referência cruzada a ordens e pagamentos ou reconciliar contas. [!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source] O permite que você execute todas essas ações em um único local, relatório de Pagamentos, para que possa visualizar e gerenciar seus pagamentos com eficiência.

Consulte IDs de transação e ordem de comércio vinculadas, valores de transação, método de pagamento por transação e muito mais, tudo dentro do relatório de Payouts no Administrador.

Você pode baixar transações de pagamento em um formato de arquivo .csv para uso em softwares existentes de contabilidade ou gerenciamento de pedidos.

>[!NOTE]
>
>Os dados mostrados nesta tabela são classificados em ordem decrescente (`DESC`) por padrão usando o `TRANS DATE`. O `TRANS DATE` é a data e hora em que a transação foi iniciada.

## Disponibilidade

No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.

![Transações de pagamento no Administrador](assets/payouts-report.png)

## Selecionar fonte de dados

Na exibição de relatório Saídas, é possível selecionar a fonte de dados—_[!UICONTROL Live]_ou [!UICONTROL Sandbox]_—para o qual você deseja ver os resultados do relatório.

![Seleção das fontes de dados](assets/datasource.png)

If _[!UICONTROL Live]_for a fonte de dados selecionada, você poderá ver as informações do relatório para suas lojas ativas. If [!UICONTROL Sandbox]_ for a fonte de dados selecionada, você poderá ver as informações do relatório para o seu ambiente de sandbox.

As seleções de fonte de dados funcionam da seguinte maneira:

* Se você não tiver lojas no modo Online, a seleção da fonte de dados assumirá como padrão _[!UICONTROL Sandbox]_.
* Se você tiver lojas (uma ou várias) no modo Online, a seleção da fonte de dados assumirá como padrão _[!UICONTROL Live]_.
* As exportações de relatório sempre seguem a seleção da fonte de dados.

Para selecionar a fonte de dados do seu relatório de Status do Pagamento da Ordem:

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Clique em **[!UICONTROL Data source]** e selecione _[!UICONTROL Live]_ou [!UICONTROL Sandbox]_.

   Os resultados do relatório são gerados com base na fonte de dados selecionada.

## Exibir transações

Por padrão, 30 dias de transações são mostrados na grade.

O número de linhas retornadas em uma pesquisa, ou mostradas nos 30 dias padrão de transações, são mostradas acima da grade de visualização de Pagamentos ao lado do filtro seletor de calendário de Datas da transação .

Role para a esquerda e para a direita para exibir [informações para cada transação de pagamento](#column-descriptions) no relatório diário, incluindo data da transação, ID de referência, número da fatura e detalhes do método de pagamento.

### Personalizar período de operações

Na visualização Payouts , é possível personalizar o período para as transações de pagamento que deseja visualizar inserindo datas específicas ou selecionando um intervalo de datas no seletor de datas:

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. Clique no filtro Seletor de calendário de datas de transação .
1. Escolha o intervalo de datas aplicável.
1. Exiba os status de pagamento na grade para as datas especificadas.

## Mostrar e ocultar colunas

Por padrão, o relatório Saídas mostra a maioria das colunas de informações disponíveis. Entretanto, é possível personalizar quais colunas você vê em seu relatório.

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]** > **[!UICONTROL Payouts]**.
1. Clique no botão _Configurações de coluna_ ícone (![ícone de configurações de coluna](assets/column-settings.png)).
1. Para personalizar quais colunas você vê no relatório, marque ou desmarque as colunas na lista.

   O relatório Saídas mostrará imediatamente quaisquer alterações feitas no menu Configurações de coluna . As preferências de coluna serão salvas e permanecerão em vigor se você sair da visualização do relatório.

## Baixar transações

Você pode baixar um arquivo .csv contendo todas as transações visíveis na grade Visualização de pagamentos .

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > **[!UICONTROL Payouts]**.
1. [Personalizar o intervalo de datas das transações](#customize-transactions-timeframe).
1. Clique no botão _Baixar_ (![](assets/icon-download.png)).

Suas transações de pagamento são baixadas em um formato .csv .

## Informações sobre transações

A exibição de Payouts mostra informações extensas para cada transação mostrada na grade.

### Descrições das colunas

Os relatórios de pagamento incluem as seguintes informações.

| Coluna | Descrição |
| ------------ | -------------------- |
| [!UICONTROL Provider] | Fornecedor de pagamento |
| [!UICONTROL Provider trans] | ID da transação |
| [!UICONTROL Trans date] | Data e hora em que a transação foi iniciada |
| [!UICONTROL Type] | Tipo de transação—*[!UICONTROL PAYMENT]*, *[!UICONTROL BONUS]*, *[!UICONTROL CHARGEBACK]*, *[!UICONTROL CORRECTION]*, *[!UICONTROL CURRENCY_CONVERSATION]*, *[!UICONTROL DEPOSIT]*, *[!UICONTROL DISBURSEMENT]*, *[!UICONTROL DISPUTE]*, *[!UICONTROL FEES]*, *[!UICONTROL HOLD]*, *[!UICONTROL HOLD_RELEASE]*, *[!UICONTROL INCENTIVES]*, *[!UICONTROL OTHERS]*, *[!UICONTROL RECOUP]*, *[!UICONTROL REFUND]*, *[!UICONTROL REVERSAL]*, *[!UICONTROL WITHDRAWAL]* <br> <br>Consulte [Tipos de transação](#transaction-types) para obter mais informações. |
| [!UICONTROL Status] | Situação atual da operação—*[!UICONTROL SUCCESS]*, *[!UICONTROL DENIED]*, *[!UICONTROL PENDING]* |
| [!UICONTROL Code] | Código de transação que indica Crédito (*CR*) ou Débito (*DR*) |
| [!UICONTROL Reference ID] | ID da transação original à qual esse evento está relacionado |
| [!UICONTROL Invoice] | ID da NFF (uma por ordem) da transação |
| [!UICONTROL Commerce order] | ID de pedido de comércio <br> <br>Para ver os [informações do pedido](https://docs.magento.com/user-guide/sales/orders.html){target=&quot;_blank&quot;}, clique na ID. |
| [!UICONTROL Commerce trans] | ID de transação de comércio <br> <br>Para ver os [informações da transação](https://docs.magento.com/user-guide/sales/transactions.html){target=&quot;_blank&quot;}, clique na ID. |
| [!UICONTROL Pay method] | Tipo de cartão de crédito—*[!UICONTROL BANK]*, *[!UICONTROL PAYPAL]*, *[!UICONTROL CREDIT_CARD]*—e fornecedor de cartões associado (como *Visto* ou *MasterCard*) |
| [!UICONTROL Trans amt] | Valor da transação |
| [!UICONTROL Cur] | Unidade de moeda para valor da transação |
| [!UICONTROL Pending] | Montante ainda por desembolsar |
| [!UICONTROL Cur] | Unidade de moeda para o valor pendente |
| [!UICONTROL Seller amt] | Montante dos fundos transferidos de ou para um cliente <br> <br>Os fundos que saem da conta de vendedor exibem um prefixo de travessão (-). |
| [!UICONTROL Cur] | Unidade monetária do montante do vendedor |
| [!UICONTROL Partner fee] | Taxas do parceiro associadas à transação <br> <br>Os fundos que saem da conta de taxa do parceiro exibem um prefixo de traço (-). |
| [!UICONTROL Cur] | Unidade de moeda para a taxa do parceiro |
| [!UICONTROL Prov fees] | Taxas associadas à transação <br> <br>Os fundos que saem da conta de taxa do provedor exibem um prefixo de traço (-). |
| [!UICONTROL Cur] | Unidade monetária para a taxa do fornecedor |
| [!UICONTROL Fee %] | Percentagem do valor da transação cobrado como taxa |
| [!UICONTROL Fixed fee] | Valor fixo da taxa do fornecedor |
| [!UICONTROL Chbk fee] | Taxa de reembolso associada à transação <br> <br>Um prefixo de traço (-) indica que a taxa de substituição foi revertida. |
| [!UICONTROL Cur] | Unidade monetária para a taxa de substituição de débito |
| [!UICONTROL Hold amt] | Montante colocado em retenção ou libertado da retenção <br> <br>Um prefixo (-) traço indica que os fundos em retenção estão sendo liberados. |
| [!UICONTROL Cur] | Unidade de moeda para o valor de retenção |
| [!UICONTROL Recoup amt] | Valor recuperado da conta de recuperação <br> <br>Os fundos que saem da conta de recuperação exibem um prefixo de traço (-). |
| [!UICONTROL Cur] | Unidade de moeda para o valor de recuperação |

### Tipos de transação

Esses tipos de transações podem ser anotados nas transações de pagamento.

| Relatório | Descrição |
| ------------ | -------------------- |
| [!UICONTROL PAYMENT] | Dinheiro transferido entre um comprador e um vendedor para uma encomenda |
| [!UICONTROL AUTH] | Autorização e autorização nula de transações |
| [!UICONTROL BONUS] | — |
| [!UICONTROL CHARGEBACK] | Transações de reversão de taxa e taxa de reversão de débito |
| [!UICONTROL CORRECTION] | — |
| [!UICONTROL CURRENCY_CONVERSION] | — |
| [!UICONTROL DEPOSIT] | — |
| [!UICONTROL DISBURSEMENT] | — |
| [!UICONTROL DISPUTE] | — |
| [!UICONTROL FEES] | Taxas do parceiro, taxas de pagamento e transações de estorno de taxa |
| [!UICONTROL HOLD] | — |
| [!UICONTROL HOLD_RELEASE] | — |
| [!UICONTROL INCENTIVES] | — |
| [!UICONTROL OTHERS] | — |
| [!UICONTROL RECOUP] | Retornos de contas bancárias ou de perdas |
| [!UICONTROL REFUND] | — |
| [!UICONTROL REVERSAL] | — |
| [!UICONTROL WITHDRAWAL] | — |
