---
title: "Fluxo de check-out no Adobe Commerce"
description: "Visão geral do [!DNL Quick Checkout] no Adobe Commerce."
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: f790732804e110aad298689c0ddf74547ff17618
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# [!DNL Quick Checkout] Fluxo

Esta seção fornece uma visão geral da experiência típica de check-out usando o [!DNL Quick Checkout] para a extensão do Adobe Commerce.

Um sucesso [!DNL Quick Checkout] O fluxo consiste nas seguintes etapas:

1. Abra a vitrine e adicione itens ao carrinho.
1. Prossiga para o check-out.

![Check-out](assets/proceed-checkout.png)

>[!NOTE]
>
> Você pode ativar o logon automático para o comerciante. Consulte [Tópico Ativar o login automático da Bolt](https://help.bolt.com/products/embedded/direct-api/auto-login/) para obter mais informações.

1. Quando solicitado, insira um endereço de email associado a um [!DNL Bolt] conta.
1. Insira a OTP (One-Time Password - Senha ocasional) enviada para ele [!DNL Bolt] endereço de email ou número de telefone da conta.

![Pop-up OTP](assets/new-logo-otp-email.png)

1. Depois de fazer logon com a [!DNL Bolt] conta, os detalhes do check-out são preenchidos automaticamente:

   - Informações de remessa
   - Método de pagamento

   >[!NOTE]
   >
   > Você pode usar as informações existentes da carteira (endereço ou informações do cartão de crédito) mesmo se os detalhes do checkout forem preenchidos automaticamente.

1. Fazer pedido.

A variável [!DNL Quick Checkout] é compatível com as opções de check-out padrão adicionais do Adobe Commerce, como [cartões-presente](https://docs.magento.com/user-guide/catalog/product-gift-card.html) ou [códigos de desconto](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Quick Checkout] casos de uso

A variável [!DNL Quick Checkout] O permite vários casos de uso durante um fluxo de check-out:

- [Usuário convidado](../quick-checkout/checkout-bolt.md) com uma marca registrada ou nova [!DNL Bolt] conta.
- Um existente [usuário do Adobe Commerce](../quick-checkout/checkout-adobe-commerce.md) com ou sem registro [!DNL Bolt] conta.

## Obter ajuda

Entre em contato com o Suporte da Adobe Commerce por meio da [Centro de ajuda do Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html) para obter assistência.
