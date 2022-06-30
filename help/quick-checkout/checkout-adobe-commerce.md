---
title: '"Fluxo de check-out"'
description: '"Visão geral da [!DNL Quick Checkout] fluxo para um usuário do Adobe Commerce."'
source-git-commit: 01bb92d1de1f6a6da1d6326c0190eb7711274045
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---


# Um usuário existente do Adobe Commerce: Como funciona

Um usuário existente do Adobe Commerce pode selecionar detalhes de envio e pagamento salvos ao fazer um pedido com a [!DNL Quick Checkout] para obter uma experiência de finalização mais rápida.

Quando um comprador insere seu endereço de email no check-out, a variável [!DNL Quick Checkout] O valida e encontra um [!DNL Bolt] conta.

## Registrado [!DNL Bolt] conta com um usuário do Adobe Commerce

Se uma [!DNL Bolt] for encontrada, os compradores continuarão com suas [!DNL Quick Checkout] experiência de finalização contínua:

1. Insira a Senha única (OTP) enviada para isso [!DNL Bolt] endereço de email da conta ou dispositivo móvel, dependendo do [preferências do usuário na [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.
1. Depois de fazer logon com o [!DNL Bolt] , os detalhes são adicionados automaticamente:

   - Informações sobre envio
   - Método de pagamento

1. Faça seu pedido.

Se encontrar problemas ao colocar um pedido como um usuário existente do Adobe Commerce, consulte a [Solução de problemas de check-out rápido](https://support.magento.com/hc/en-us/articles/6909450342541) artigo na Central de ajuda do Adobe Commerce.

## Novo [!DNL Bolt] account

Se não [!DNL Bolt] for encontrada, os compradores continuarão com o check-out padrão do Adobe Commerce e o comprador selecionará todos os detalhes necessários das informações salvas para colocar o pedido:

- Informações sobre remessa e faturamento
- Método de remessa
- Revisar método de pagamento
- A opção de se registrar em [!DNL Bolt] para finalizações mais rápidas antes de fazer o pedido, é exibido. O comprador pode concordar com os termos e condições para criar seus [!DNL Bolt] conta.

   ![Lembrar [!DNL Bolt]](assets/checked-bolt.png)
