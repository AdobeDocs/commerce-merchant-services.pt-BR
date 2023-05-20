---
title: "[!DNL Quick Checkout] para informações do desenvolvedor do Adobe Commerce"
description: "[!DNL Quick Checkout] informações do desenvolvedor."
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
source-git-commit: b89427124cf76e7f36076454949191ee1d88f52c
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# [!DNL Quick Checkout] Informações do desenvolvedor

Este tópico contém informações para desenvolvedores que trabalham em conjunto com a Adobe Commerce e [!DNL Magento Open Source] e quiser saber mais sobre as informações detalhadas do [!DNL Quick Checkout] extensão.

## Pontos de extensão

Use pontos de extensão para personalizar o [!DNL Quick Checkout].

Ao usar pontos de extensão, você pode fazer personalizações sem realmente alterar os componentes principais no código do aplicativo.

## Etapa de detalhes de remessa

Um ponto de extensão pode ser usado para personalizar a navegação de etapa automatizada depois de fazer logon com [!DNL Bolt].

Uma vez que o comprador fizer logon com [!DNL Bolt], todas as informações válidas são preenchidas previamente e redirecionadas à etapa de detalhes do pagamento para fazer o pedido. Consulte a [fluxo de finalização](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-flow.html) para obter mais informações.

Esse ponto de extensão permite impedir a navegação para uma etapa de pagamento e pode ser útil caso haja extensões que exijam que um comprador execute ações adicionais na etapa de envio. Veja um exemplo abaixo sobre como usar o ponto de extensão com um mixin:

1. Registre um novo mixin na `require-config.js` arquivo localizado em `app/code/Vendor/ModuleName/view/frontend/`.

   ```js
   var config = {
       config: {
           mixins: {
               "Magento_ExpressCheckout/js/model/can-navigate-to-payment": {
                   "Vendor/ModuleName/js/model/can-navigate-to-payment-mixin": true
               }
           }
       }
   };
   ```

1. Estenda o modelo no `can-navigate-to-payment.js` arquivo localizado em `app/code/Vendor/ModuleName/view/frontend/web/js/model/`.

   ```js
   define([
       'Magento_Checkout/js/model/quote',
       'mage/utils/wrapper',
   ], function (quote, wrapper) {
       'use strict';
       return function (canNavigateToPayment) {
           return wrapper.wrap(canNavigateToPayment, function (originalAction) {
               /* Include custom checks or conditions to stay on the shipping step,i.e: your shopper is from Germany */
               return originalAction() && quote.shippingAddress().countryId !== 'DE');
           });
       };
   });
   ```

>[!WARNING]
>
> Este é um exemplo para um comprador na Alemanha (DE) que deseja permanecer na etapa Detalhes de envio.

Marcar [[!DNL Bolt] ajuda do desenvolvedor](https://help.bolt.com/developers/) para obter mais informações sobre [!DNL Bolt] para desenvolvedores.
