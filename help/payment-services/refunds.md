---
title: Reembolsos
description: Criar reembolsos para [!DNL Payment Services] no Administrador como parte do processo de aviso de crédito.
exl-id: 2b3721a1-9c9d-4e3f-ab7d-5bd61573dcb4
source-git-commit: fd818dadbaa2a58efd7313ce888c7dda27d25f14
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Reembolsos

Restituições para [!DNL Payment Services] Os pedidos são criados no Admin como parte do processo de aviso de crédito. Um aviso de crédito é um documento que mostra o valor que é devido ao cliente, para um reembolso total ou parcial, que pode ser aplicado para uma compra ou reembolsado diretamente ao cliente. Avisos de crédito só podem ser emitidos para ordens que sejam [faturado](https://docs.magento.com/user-guide/sales/invoice-create.html){target=&quot;_blank&quot;}.

Consulte [Avisos de Crédito](https://docs.magento.com/user-guide/sales/credit-memos.html){target=&quot;_blank&quot;} em nosso guia do usuário principal para obter mais informações e saber como emitir e imprimir avisos de crédito.

Para pedidos processados com PayPal ou cartão de crédito, você pode:

* Reembolsar todo o valor do pedido
* Reembolsar uma quantidade parcial de um pedido (ou várias quantidades parciais)
* Reembolsar uma quantia menor que o valor de um item de ordem específico

Consulte [Emitir Nota de Crédito](https://docs.magento.com/user-guide/sales/credit-memo-create.html){target=&quot;_blank&quot;} em nosso guia do usuário principal para obter mais informações.

>[!NOTE]
>
>Ocorre um erro para ordens PayPal ou processadas por cartão de crédito se você tentar reembolsar parcialmente um pedido por mais do que o valor restante do pedido (valor original menos o total de reembolsos existentes), ou se você emitir um reembolso por um valor maior do que o valor total do pedido.

O [!UICONTROL Payment Action] na sua [!UICONTROL Payment Settings] configuração — Ou `Authorize` ou `Authorize and Capture`—determina a [fluxo de trabalho básico de reembolso](https://docs.magento.com/user-guide/sales/credit-memos.html#refund-workflow){target=&quot;_blank&quot;} para pedidos.

Consulte a [Seção Configuração da ação de pagamento](https://docs.magento.com/user-guide/sales/credit-memo-create.html#payment-action-setting){target=&quot;_blank&quot;} de _Emitir Nota de Crédito_ para obter mais informações.
