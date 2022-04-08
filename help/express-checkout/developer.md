---
title: '''[!DNL Express Checkout] para informações do desenvolvedor do Adobe Commerce'''
description: '''[!DNL Express Checkout] informações do desenvolvedor."'
exl-id: 8926eda4-b4de-4938-a86c-b095616f61f6
source-git-commit: 46d5cae4e55a2983a2dc8c442cf5530803be65af
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Express Checkout] informações do desenvolvedor

>[!IMPORTANT]
>
> Esse recurso destina-se somente aos usuários do EAP (Early Adobe Program) e ainda não está acessível para todos os clientes. Atualmente limitado a clientes dos EUA. Entre em contato com o Suporte da Adobe Commerce para obter assistência e perguntas.

Este tópico contém informações para desenvolvedores que trabalham em conjunto com o código Adobe Commerce e Magento Open Source e desejam saber mais sobre as [!DNL Express Checkout] extensão.

## Pontos de extensão

Use pontos de extensão para personalizar o [!DNL Express Checkout].

Ao usar pontos de extensão, você pode fazer personalizações sem alterar os componentes principais no código do aplicativo.

## Etapa de detalhes da remessa

Um ponto de extensão pode ser usado para personalizar a navegação em etapas automatizadas após fazer logon com o [!DNL Bolt].

Uma vez que um comprador faz logon com [!DNL Bolt], todas as informações válidas são pré-preenchidas e redirecionadas para a etapa de detalhes do pagamento para colocar a ordem. Consulte a [fluxo de finalização](https://experienceleague.adobe.com/docs/commerce-merchant-services/express-checkout/manage-checkout/checkout-flow.html) para obter mais informações.

Esse ponto de extensão permite impedir a navegação para uma etapa de pagamento e pode ser útil caso existam extensões que exigem que um comprador execute ações adicionais na etapa de envio. Veja um exemplo abaixo sobre como usar o ponto de extensão com uma combinação:

1. Registre uma nova combinação no `require-config.js` arquivo localizado em `app/code/Vendor/ModuleName/view/frontend/`.

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

1. Estender o modelo no `can-navigate-to-payment.js` arquivo localizado em `app/code/Vendor/ModuleName/view/frontend/web/js/model/`.

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
> Este é um exemplo para um comprador na Alemanha (DE) que deseja permanecer na etapa Detalhes do frete.

Verificar [[!DNL Bolt] ajuda do desenvolvedor](https://help.bolt.com/developers/) para obter mais informações sobre [!DNL Bolt] para desenvolvedores.
