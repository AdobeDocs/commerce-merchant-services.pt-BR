---
title: Nulos
description: Anulações permitem que você libere os fundos em uma conta de cartão de crédito ou débito que estão bloqueados ou retidos por uma autorização para a quantia de uma compra.
exl-id: 029a7038-2812-46ce-b188-929a7a758d89
feature: Payments, Checkout
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Nulos

Com [!DNL Payment Services], você pode usar a funcionalidade existente do Commerce para anular transações. Anulações permitem que você libere os fundos em uma conta de cartão de crédito ou débito que estão bloqueados ou retidos por uma autorização para a quantia de uma compra.

>[!NOTE]
>
>Você só poderá anular uma transação se o pagamento ainda não tiver sido capturado.

Se sua loja está [configurada](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} para autorizar (não capturar) fundos apenas no ponto de venda, uma compra em sua loja resulta em um pedido com status `Processing` no Administrador do Commerce.

Você também pode [cancelar um pedido](https://docs.magento.com/user-guide/sales/order-update.html#cancel-a-pending-order){target="_blank"} que não esteja faturado. Quaisquer autorizações não capturadas também são anuladas como parte desse processo de cancelamento.

>[!NOTE]
>
>Cancelar uma ordem também produz um cancelamento, mas a anulação de uma ordem não aciona um cancelamento.

Para saber mais sobre as etapas básicas pelas quais uma ordem é encaminhada, consulte o tópico do [Fluxo de trabalho de ordem](https://docs.magento.com/user-guide/sales/order-workflow.html){target="_blank"} no guia do usuário principal.

Para saber mais sobre a funcionalidade void e como anular uma transação de pedido, consulte [Processando um Pedido](https://docs.magento.com/user-guide/sales/order-processing.html){target="_blank"} no guia do usuário principal.
