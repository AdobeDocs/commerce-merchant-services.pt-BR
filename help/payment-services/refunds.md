---
title: Reembolsos
description: Criar reembolsos para  [!DNL Payment Services] pedidos no Administrador como parte do processo de memorando de crédito.
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 0%

---

# Reembolsos

Os reembolsos de [!DNL Payment Services] pedidos são criados no Administrador como parte do processo de aviso de crédito. Um aviso de crédito é um documento que mostra a quantia devida ao cliente, para uma restituição total ou parcial, que pode ser aplicada a uma compra ou reembolsada diretamente ao cliente. Os avisos de crédito só podem ser emitidos para ordens [faturadas](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"}.

Consulte [Avisos de Crédito](https://docs.magento.com/user-guide/sales/credit-memos.html){target="_blank"} em nosso guia do usuário principal para obter mais informações e saber como emitir e imprimir avisos de crédito.

Para pedidos processados com PayPal ou um cartão de crédito, você pode:

* Reembolsar o valor total da ordem
* Reembolsar uma quantia parcial de uma ordem (ou várias quantias parciais)
* Reembolsar um valor inferior ao valor de um item de pedido específico

Consulte [Emitindo um Aviso de Crédito](https://docs.magento.com/user-guide/sales/credit-memo-create.html){target="_blank"} em nosso guia do usuário principal para obter mais informações.

>[!NOTE]
>
>Ocorre um erro para pedidos processados por cartão de crédito ou PayPal se você tentar reembolsar parcialmente um pedido por mais do que o valor restante do pedido (valor original menos o total de reembolsos existentes) ou se você emitir um reembolso por um valor maior do que o valor total do pedido.

A configuração [!UICONTROL Payment Action] na sua configuração [!UICONTROL Payment Settings]—`Authorize` ou `Authorize and Capture`—determina o [fluxo de trabalho básico de reembolso](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow){target="_blank"} para pedidos.

Consulte a [seção de configuração da ação de pagamento](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target="_blank"} de _Emitindo um Aviso de Crédito_ para obter mais informações.
