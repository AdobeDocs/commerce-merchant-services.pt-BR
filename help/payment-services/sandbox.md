---
title: Configurar a sandbox de teste
description: Usar uma conta de sandbox PayPal para usar [!DNL Payment Services] no modo de teste.
exl-id: 99c14b4e-e6cf-48f9-9546-5c0d5c71464d
source-git-commit: ab4a2f4d432f74cb48dc4b92468305c93088593a
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# Configurar a sandbox de teste

Antes de iniciar a integração com sandbox, você deve se inscrever para obter uma conta gratuita do Desenvolvedor do PayPal e criar contas do comerciante (para usar a integração) e do comprador (para usar no teste de check-out). Você pode criar várias contas de desenvolvedor, se desejar.

Uma conta de sandbox PayPal permite usar [!DNL Payment Services] no modo de teste. O PayPal requer que você use uma conta de teste de caixa de proteção de negócios gerada pelo Portal do desenvolvedor PayPal, email e senha para integração com a caixa de proteção. *Não crie outra conta durante o processo de integração da sandbox.*

## Integração de sandbox

Para concluir a integração de sandbox:

1. Navegue até o [Página Conta de Desenvolvedor do PayPal](https://developer.paypal.com/developer/accounts/).
1. Clique em **[!UICONTROL Log in to Home]** e faça logon com sua conta de teste de caixa de proteção de negócios gerada pelo Portal de desenvolvedores do PayPal ou clique em **Inscrever-se** para criar uma conta.
1. Criar uma conta de sandbox PayPal:
   1. Ir para _[!UICONTROL SANDBOX]_>**[!UICONTROL Accounts]**.
   1. Clique em **[!UICONTROL Create account]**.

      Se você criou uma conta de sandbox PayPal durante o processo de integração do sandbox PayPal, é necessário [redefinir sua sandbox de integração](#reset-your-sandbox-account) ou você não pode verificar seu email.

   1. Selecionar **[!UICONTROL Business]** como Tipo de conta e clique em **[!UICONTROL Create]**.
   1. No _[!UICONTROL Sandbox Accounts]_clique nos três pontos na seção_[!UICONTROL Manage accounts]_ para a conta da sandbox que você criou.
   1. Clique em **[!UICONTROL View/edit account]**.

      ![PayPal - Exibir/editar conta de sandbox](assets/onboarding-viewedit-sandbox.png)

   1. Copie e salve a ID de email e a Senha gerada pelo sistema para uso futuro.

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Clique em **[!UICONTROL Sandbox onboarding]**.

   Essa opção ficará visível se você ainda não tiver concluído a integração da sandbox para o [!DNL Payment Services].

   Uma ID de comerciante de sandbox é gerada automaticamente e preenchida na [configurações](settings.md). Não altere ou altere essa ID.

   Você recebe uma janela PayPal para conectar uma conta PayPal para começar a aceitar pagamentos.

1. Insira o email da sua conta comercial do PayPal (não conta de sandbox do PayPal) e seu país ou região e clique em **[!UICONTROL Next]**.

   ![PayPal - Conta PayPal de Conexão para pagamentos](assets/paypal-connectacct.png)

1. Continue a seguir o fluxo do PayPal, usando suas credenciais de conta da sandbox salvas anteriormente.
1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   O **[!UICONTROL Sandbox onboarding]** O botão não está mais visível e você vê um texto &quot;Pagamentos de sandbox pendentes&quot;.

Quando a integração da sandbox do PayPal for aprovada, você deverá ver uma notificação informando que seu sistema de pagamento está atualmente no modo sandbox e não está processando pagamentos em tempo real.

>[!IMPORTANT]
>
>Se você revogar o consentimento para [!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source] para processar seus pagamentos (nas configurações da conta PayPal), os pedidos em sua loja não podem ser processados por [!DNL Payment Services]. Na página inicial dos Serviços de Pagamento, é exibido um alerta sobre o consentimento revogado. Para ignorar o alerta, clique em **[!UICONTROL Do not show again]**.

### Redefinir a conta da sandbox

Se você criou uma conta de sandbox PayPal durante o processo de integração do sandbox PayPal, é necessário redefinir a sandbox de integração porque ou não é possível verificar o email.

Para redefinir a conta da sandbox:

1. Clique em **[!UICONTROL Reset sandbox]**. [Criar uma conta de sandbox comercial do PayPal](https://developer.paypal.com/docs/api-basics/sandbox/accounts/#create-a-business-sandbox-account).
1. Clique em **[!UICONTROL Sandbox onboarding]** e conclua o próximo conjunto de etapas.

## Ativar número de telefone do contato

O número de telefone de contato permite obter os números de telefone de contato que o PayPal coleta de seus clientes. O PayPal sempre coleta números de telefone de contato dos titulares de contas do PayPal para ajudar a confirmar suas identidades e para contatá-las para resolver problemas em suas contas ou para concluir seus processos de atendimento. No entanto, o PayPal desencoraja o uso de números de telefone de contato diretamente do comerciante, pois pode afetar negativamente as vendas. Consulte a [PayPal obter números de telefone de contato](https://developer.paypal.com/docs/admin/checkout-settings/#get-contact-telephone-numbers) documentação para obter mais informações.

Este recurso é `off` por padrão. Ao habilitá-lo, os administradores de armazenamento podem ver números de telefone quando um cliente conclui um fluxo de Check-out da marca fora da página de check-out.

>[!IMPORTANT]
>
>Essa configuração não se aplica a outros fluxos de check-out.

## Testar no ambiente sandbox

Consulte [Testar e validar](test-validate.md) para obter mais informações.
