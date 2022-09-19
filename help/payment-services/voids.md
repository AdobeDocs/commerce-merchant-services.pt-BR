---
title: Vazios
description: As anulações permitem liberar os fundos de uma conta de cartão de crédito ou de débito bloqueados ou reservados por uma autorização para o montante de uma compra.
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
source-git-commit: 7b31fe7a71c3c238e6448627b2edfe06bbfbc80e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Vazios

Com [!DNL Payment Services], é possível usar a funcionalidade Comércio existente para evitar transações. As anulações permitem liberar os fundos de uma conta de cartão de crédito ou de débito bloqueados ou reservados por uma autorização para o montante de uma compra.

>[!NOTE]
>
>Você só poderá anular uma transação se o pagamento ainda não tiver sido capturado.

Se a sua loja for [configurado](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} para autorizar somente fundos (não capturar) no ponto de venda, uma compra da sua loja resulta em um pedido com um `Processing` no Administrador de comércio.

Você também pode [cancelar um pedido](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order){target=&quot;_blank&quot;} que não é faturado. Todas as autorizações não capturadas são igualmente anuladas no âmbito desse processo de cancelamento.

>[!NOTE]
>
>Cancelar um pedido também gera um vazio, mas anular um pedido não aciona um cancelamento.

Para saber mais sobre as etapas básicas de um pedido, consulte o [Fluxo de trabalho do pedido](https://docs.magento.com/user-guide/sales/order-workflow.html)Tópico {target=&quot;_blank&quot;} no guia do usuário principal.

Para saber mais sobre a funcionalidade void e como anular uma transação de pedido, consulte [Processamento de um pedido](https://docs.magento.com/user-guide/sales/order-processing.html){target=&quot;_blank&quot;} no guia do usuário principal.
