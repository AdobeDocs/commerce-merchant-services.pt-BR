---
title: Fluxo de finalização
description: Visão geral da [!DNL Quick Checkout] fluxo para um usuário Bolt no Adobe Commerce.
exl-id: 12f58b7e-1f86-4891-b225-9f4be82c2d5d
source-git-commit: a95d2ed92c69feba03d1b84d44abf08c1d1b4029
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Usuários convidados

A experiência de check-out de convidado é diferente da experiência de usuário do Adobe. Quando um comprador insere um endereço de email no check-out, a variável [!DNL Quick Checkout] O valida e encontra um [!DNL Bolt] conta.

## Registrado [!DNL Bolt] account

Se uma [!DNL Bolt] for encontrada, os compradores continuarão com suas [!DNL Quick Checkout] experiência de finalização contínua:

1. Insira a Senha única (OTP) enviada para isso [!DNL Bolt] endereço de email da conta ou dispositivo móvel, dependendo do [preferências do usuário na [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![Pop-up OTP](assets/pop-up.png)

1. Depois de fazer logon com o [!DNL Bolt] , os detalhes são adicionados automaticamente:

   - Informações sobre envio
   - Método de pagamento

1. Faça seu pedido.

>[!TIP]
>
> O usuário convidado coloca o pedido e pode se registrar no Adobe Commerce.

## Novo [!DNL Bolt] account

Se não [!DNL Bolt] for encontrada, os compradores continuarão com o check-out padrão do Adobe Commerce e o comprador fornecerá todos os detalhes necessários para fazer o pedido:

- Informações sobre remessa e faturamento
- Método de remessa
- Revisar método de pagamento
- Uma caixa de seleção aparece para se registrar no [!DNL Bolt] para finalizações mais rápidas antes de fazer o pedido. O comprador pode concordar com os termos e condições para criar seus [!DNL Bolt] conta.

   ![Lembrar [!DNL Bolt]](assets/checkbox-remember-bolt.png)

- O usuário convidado coloca o pedido e pode se registrar no Adobe Commerce.
