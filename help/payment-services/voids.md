---
title: Nulos
description: Anulações permitem que você libere os fundos em uma conta de cartão de crédito ou débito que estão bloqueados ou retidos por uma autorização para a quantia de uma compra.
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
source-git-commit: 7b31fe7a71c3c238e6448627b2edfe06bbfbc80e
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Nulos

Com [!DNL Payment Services], você pode usar a funcionalidade existente do Commerce para anular transações. Anulações permitem que você libere os fundos em uma conta de cartão de crédito ou débito que estão bloqueados ou retidos por uma autorização para a quantia de uma compra.

>[!NOTE]
>
>Você só poderá anular uma transação se o pagamento ainda não tiver sido capturado.

Se a loja estiver [configurado](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} para autorizar (não capturar) fundos somente no ponto de venda, uma compra em sua loja resulta em um pedido com uma `Processing` status no Administrador do Commerce.

Também é possível [cancelar um pedido](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order){target="_blank"} que não foi faturado. Quaisquer autorizações não capturadas também são anuladas como parte desse processo de cancelamento.

>[!NOTE]
>
>Cancelar uma ordem também produz um cancelamento, mas a anulação de uma ordem não aciona um cancelamento.

Para saber mais sobre as etapas básicas pelas quais um pedido é realizado, consulte a [Fluxo de trabalho do pedido](https://docs.magento.com/user-guide/sales/order-workflow.html){target="_blank"} tópico no guia do usuário principal.

Para saber mais sobre a funcionalidade de anulação e como anular uma transação de ordem, consulte [Processar um pedido](https://docs.magento.com/user-guide/sales/order-processing.html){target="_blank"} no guia do usuário principal.
