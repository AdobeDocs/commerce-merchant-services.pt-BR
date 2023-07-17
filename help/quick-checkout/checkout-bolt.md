---
title: "Fluxo de check-out de um usuário do Bolt no Adobe Commerce"
description: Visão geral do [!DNL Quick Checkout] para um usuário do Bolt no Adobe Commerce.
exl-id: 12f58b7e-1f86-4891-b225-9f4be82c2d5d
feature: Checkout, Services, Storefront
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Usuários convidados

A experiência de check-out do convidado é diferente da experiência do usuário Adobe. Quando um comprador insere um endereço de email no check-out, a variável [!DNL Quick Checkout] O valida e encontra um existente [!DNL Bolt] conta.

>[!WARNING]
>
> A variável [!DNL In-Store Pickup] (ISPU) não é compatível quando a variável [!DNL Quick Checkout] está ativado.

## Registrado [!DNL Bolt] account

Se um [!DNL Bolt] for encontrada, os compradores continuarão com seus [!DNL Quick Checkout] experiência de check-out perfeita:

1. Insira a OTP (One-Time Password - Senha ocasional) enviada para ele [!DNL Bolt] endereço de email ou celular da conta, dependendo do [preferências do usuário no [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![Pop-up OTP](assets/new-logo-otp-email.png)

1. Depois de fazer logon com a [!DNL Bolt] os detalhes são adicionados automaticamente:

   - Informações de remessa
   - Método de pagamento

1. Faça seu pedido.

>[!TIP]
>
> O usuário convidado faz o pedido e, opcionalmente, pode se registrar no Adobe Commerce.

## Novo [!DNL Bolt] account

Se não [!DNL Bolt] for encontrada, os compradores continuarão com o checkout padrão do Adobe Commerce e fornecerão todos os detalhes necessários para fazer o pedido:

- Informações de remessa e faturamento
- Método de envio
- Revisar método de pagamento
- Uma caixa de seleção aparece para se registrar no [!DNL Bolt] para obter check-outs mais rápidos antes de fazer o pedido. O comprador pode concordar com os termos e condições para criar sua [!DNL Bolt] conta.
- O usuário convidado faz o pedido e, opcionalmente, pode se registrar no Adobe Commerce.
