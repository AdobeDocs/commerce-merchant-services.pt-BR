---
title: "Fluxo de check-out para um usuário do Adobe Commerce"
description: "Visão geral da [!DNL Quick Checkout] fluxo para um usuário do Adobe Commerce."
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
source-git-commit: f790732804e110aad298689c0ddf74547ff17618
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Um usuário existente do Adobe Commerce: Como funciona

Um usuário existente do Adobe Commerce pode selecionar detalhes de envio e pagamento salvos ao fazer um pedido com a [!DNL Quick Checkout] para obter uma experiência de finalização mais rápida.

Quando um comprador insere seu endereço de email no check-out, a variável [!DNL Quick Checkout] O valida e encontra um [!DNL Bolt] conta.

## Usuário registrado no Adobe Commerce e [!DNL Bolt]

Quando um comprador é um usuário registrado no Adobe Commerce e [!DNL Bolt] redes, ambas as redes são fornecidas com dados armazenados sobre o envio e o pagamento.

Se uma [!DNL Bolt] for encontrada durante o check-out, os compradores poderão continuar com suas [!DNL Quick Checkout] experiência de finalização contínua:

1. Insira a Senha única (OTP) enviada para isso [!DNL Bolt] endereço de email da conta ou dispositivo móvel, dependendo do [preferências do usuário na [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![Pop-up OTP](assets/new-logo-otp-email.png)

1. Depois de fazer logon com o [!DNL Bolt] , os detalhes são adicionados automaticamente:

   - Informações sobre envio
   - Método de pagamento

1. Faça seu pedido.

>[!NOTE]
>
> O pop-up OTP de Bolt só é exibido quando o comprador está na página de checkout. O comprador pode recusar o logon no Bolt ao fechar essa janela pop-up.

Se o comprador estiver conectado à Adobe Commerce antes do check-out, a variável [!DNL Bolt] A pop-up OTP não aparecerá durante o check-out, mas será exibida uma mensagem sugerindo que o comprador faça logon para acessar sua Bolsa de Bolt.

Se encontrar problemas ao colocar um pedido como um usuário existente do Adobe Commerce, consulte a [Solução de problemas de check-out rápido](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) artigo na Central de ajuda do Adobe Commerce.

## Logon automático

O componente Logon automático detecta quando um comprador tem uma sessão Bolt ativa e faz o logon automático do comprador. Isso ignora as etapas de detecção de conta e código de acesso único (OTP), pois o comprador as concluiu em uma sessão anterior.

É possível configurar um logon automático para [!DNL Quick Checkout] usuários. Você pode ativar uma configuração para fazer logon automático em um usuário durante o check-out.

1. No _Administrador_ barra lateral, navegue até **Lojas** > **Configuração** > **Check-out** para acessar a página de configuração geral do administrador de check-out .
1. No _Configurações de serviço_ seção para [!DNL Quick Checkout], forneça todos os detalhes necessários para configurar o logon automático.

Consulte [[!DNL Quick Checkout] definir configurações de serviço](../quick-checkout/onboarding.md#configure-service-settings) para obter mais informações.

>[!NOTE]
>
> Primeiro login quando **logon automático** estiver ativado requer o consentimento do usuário para autorizá-lo aceitando uma janela pop-up.

## Novo [!DNL Bolt] account

Se não [!DNL Bolt] for encontrada, os compradores continuarão com o check-out padrão do Adobe Commerce e o comprador selecionará todos os detalhes necessários das informações salvas para colocar o pedido:

- Informações sobre remessa e faturamento
- Método de remessa
- Revisar método de pagamento
- A opção de se registrar em [!DNL Bolt] para finalizações mais rápidas antes de fazer o pedido, é exibido. O comprador pode concordar com os termos e condições para criar seus [!DNL Bolt] conta.

   ![Lembrar [!DNL Bolt]](assets/checkbox-remember-bolt.png)
