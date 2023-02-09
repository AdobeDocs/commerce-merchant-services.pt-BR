---
title: "Fluxo de check-out no Adobe Commerce"
description: "Visão geral da [!DNL Quick Checkout] no Adobe Commerce."
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: 66082614ffe6456e2c24a1e8d9baaa1113fb7ffb
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# [!DNL Quick Checkout] fluxo

Esta seção fornece uma visão geral da experiência típica de check-out usando o [!DNL Quick Checkout] para extensão do Adobe Commerce.

Um sucesso [!DNL Quick Checkout] O fluxo consiste nas seguintes etapas:

1. Abra a loja e adicione itens ao carrinho.
1. Prossiga para o check-out.

![Check-out](assets/proceed-checkout.png)

>[!NOTE]
>
> Você pode ativar o logon automático para seu comerciante. Consulte [Tópico Ativar logon automático do Bolt](https://help.bolt.com/products/embedded/direct-api/auto-login/) para obter mais informações.

1. Quando solicitado, insira um endereço de email associado a um [!DNL Bolt] conta.
1. Insira a Senha única (OTP) enviada para isso [!DNL Bolt] endereço de email ou número de telefone da conta.

![Pop-up OTP](assets/pop-up.png)

1. Depois de fazer logon com o [!DNL Bolt] Os detalhes de check-out são automaticamente preenchidos:

   - Informações sobre envio
   - Método de pagamento

   >[!NOTE]
   >
   > Você pode usar suas informações de carteira existentes (endereço ou informações do cartão de crédito) mesmo se os detalhes de check-out forem preenchidos automaticamente.

1. Colocar pedido.

O [!DNL Quick Checkout] é compatível com as opções padrão adicionais de check-out do Adobe Commerce, como [cartões-presente](https://docs.magento.com/user-guide/catalog/product-gift-card.html) ou [códigos de desconto](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Quick Checkout] casos de uso

O [!DNL Quick Checkout] O permite vários casos de uso durante um fluxo de finalização:

- [Usuário convidado](../quick-checkout/checkout-bolt.md) com um registro ou [!DNL Bolt] conta.
- Um [Usuário do Adobe Commerce](../quick-checkout/checkout-adobe-commerce.md) com ou sem registro [!DNL Bolt] conta.

## Obter ajuda

Entre em contato com o Suporte da Adobe Commerce por meio do [Central de ajuda da Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html) para qualquer assistência.
