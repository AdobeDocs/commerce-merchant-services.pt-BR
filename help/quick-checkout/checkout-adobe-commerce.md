---
title: "Fluxo de check-out para um usuário do Adobe Commerce"
description: "Visão geral do [!DNL Quick Checkout] para um usuário do Adobe Commerce."
exl-id: 085e393b-15f6-4d5a-a04d-927b1f95b74e
source-git-commit: f790732804e110aad298689c0ddf74547ff17618
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# Um usuário existente do Adobe Commerce: como funciona

Um usuário existente do Adobe Commerce pode selecionar os detalhes de remessa e pagamento salvos ao fazer um pedido com a [!DNL Quick Checkout] para obter uma experiência de check-out mais rápida.

Quando um comprador insere seu endereço de email no check-out, a variável [!DNL Quick Checkout] O valida e encontra um existente [!DNL Bolt] conta.

## Usuário registrado no Adobe Commerce e [!DNL Bolt]

Quando um comprador é um usuário registrado no Adobe Commerce e [!DNL Bolt] redes, ambas as redes recebem informações armazenadas de envio e pagamento.

Se um [!DNL Bolt] conta for encontrada durante o check-out, os compradores podem continuar com seus [!DNL Quick Checkout] experiência de check-out perfeita:

1. Insira a OTP (One-Time Password - Senha ocasional) enviada para ele [!DNL Bolt] endereço de email ou celular da conta, dependendo do [preferências do usuário no [!DNL Bolt] account](https://help.bolt.com/shoppers/account/account-settings/#how-to-set-preferred-login-method){target=_blank}.

![Pop-up OTP](assets/new-logo-otp-email.png)

1. Depois de fazer logon com a [!DNL Bolt] os detalhes são adicionados automaticamente:

   - Informações de remessa
   - Método de pagamento

1. Faça seu pedido.

>[!NOTE]
>
> O pop-up Parafuso OTP só é exibido quando o comprador está na página de check-out. O comprador pode recusar o logon no Bolt fechando essa janela pop-up.

Se o comprador estiver conectado ao Adobe Commerce antes do check-out, a variável [!DNL Bolt] O pop-up OTP não será exibido durante o check-out, mas uma mensagem será exibida sugerindo que o comprador faça logon para acessar a Bolt Wallet.

Se encontrar problemas ao fazer um pedido como um usuário existente do Adobe Commerce, consulte [Solução de problemas de Check-out rápido](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) no Centro de ajuda da Adobe Commerce.

## Logon automático

O componente de Logon automático detecta quando um comprador tem uma sessão de Bolt ativa e registra automaticamente o comprador. Isso ignora as etapas de detecção de conta e senha ocasional (OTP) porque o comprador as concluiu em uma sessão anterior.

É possível configurar um logon automático para [!DNL Quick Checkout] usuários. Você pode ativar uma configuração para fazer logon automaticamente em um usuário durante o check-out.

1. No _Admin_ barra lateral, navegue até **Lojas** > **Configuração** > **Check-out** para acessar a página de configuração geral do Administrador de check-out.
1. No _Configurações do serviço_ seção para [!DNL Quick Checkout], forneça todos os detalhes necessários para configurar o logon automático.

Consulte [[!DNL Quick Checkout] definir configurações de serviço](../quick-checkout/onboarding.md#configure-service-settings) para obter mais informações.

>[!NOTE]
>
> Primeiro logon quando **logon automático** está ativado requer o consentimento do usuário para autorizá-lo aceitando uma janela pop-up.

## Novo [!DNL Bolt] account

Se não [!DNL Bolt] for encontrada, os compradores continuarão com o checkout padrão do Adobe Commerce e selecionarão todos os detalhes necessários das informações salvas para fazer o pedido:

- Informações de remessa e faturamento
- Método de envio
- Revisar método de pagamento
- A opção de se registrar no [!DNL Bolt] para obter check-outs mais rápidos antes de fazer o pedido. O comprador pode concordar com os termos e condições para criar sua [!DNL Bolt] conta.

   ![Lembrar [!DNL Bolt]](assets/checkbox-remember-bolt.png)
