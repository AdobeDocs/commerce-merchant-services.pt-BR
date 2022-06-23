---
title: Configurações dos serviços de pagamento
description: Após a instalação, você pode configurar [!DNL Payment Services] no Início.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: aed9469d6acf638d86389cbf1c178fccd8d42759
workflow-type: tm+mt
source-wordcount: '695'
ht-degree: 0%

---

# Configurações

Você pode personalizar [!DNL Payment Services] de acordo com suas necessidades com as configurações úteis na [!DNL Payment Services] Casa.

Para configurar [!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source] click **[!UICONTROL Settings]**. Essas opções de configuração se aplicam somente ao ambiente definido na variável _[!UICONTROL Payment mode]_nas Configurações gerais.

Consulte a [[!UICONTROL General] seção configurações](#general-settings) para obter mais informações.

>[!IMPORTANT]
>
> Para obter configurações de várias lojas ou legadas, consulte [Configurar no Administrador](configure-admin.md) tópico.

## Ativar serviços de pagamento

Você pode ativar [!DNL Payment Services] para o seu site e ativar o teste de sandbox ou os pagamentos em tempo real, na [!UICONTROL General] seção.

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Exibição da página inicial](assets/payment-services-menu-small.png)

1. Clique em **[!UICONTROL Settings]**. Consulte [Introdução ao [!DNL Payment Services] Início](payments-home.md) para obter mais informações.

   O _[!UICONTROL General]_seção inclui configurações usadas para ativar [!DNL Payment Services] como método de pagamento.

1. Para ativar [!DNL Payment Services] como método de pagamento para sua loja, alterne (**[!UICONTROL Enable Payment Services as payment method]**) a `Yes`.

1. Se você ainda estiver testando [!DNL Payment Services] para sua loja, defina **Modo de pagamento** para `Sandbox`. Se estiver pronto para ativar os pagamentos em tempo real, defina-o como `Production`.

   >[!WARNING]
   >
   >Seu _[!UICONTROL Sandbox Merchant ID]_e_[!UICONTROL Production Merchant ID]_ são geradas automaticamente e estão presentes em seus respectivos campos quando você conclui a integração com a sandbox e/ou produção. Não remova ou altere essas IDs.

1. Selecione a exibição de loja na **[!UICONTROL Scope]** menu suspenso, para o qual você deseja ativar um método de pagamento.
1. Para alterar as configurações padrão das funções de pagamento e da tela de loja, defina as opções adicionais conforme necessário:

   - [Campos de cartão de crédito](#credit-card-fields)
   - [Botões inteligentes PayPal](#paypal-smart-buttons)
   - [Estilo do botão](#button-style)

1. Clique em **[!UICONTROL Save]**.

   Se você tentar sair dessa exibição sem salvar as alterações, será exibido um modal que solicitará que você descarte as alterações, continue a editar ou salve as alterações.

1. Navegar para **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

### Campos de cartão de crédito

O _[!UICONTROL Credit Card Fields]_As configurações oferecem uma opção de check-out simples e segura para os métodos de pagamento com cartão de crédito ou cartão de débito.

Consulte [Opções de pagamentos](payments-options.md#paypal-smart-buttons) para obter mais informações.

1. Para alterar o nome do método de pagamento exibido durante o check-out, edite o valor no **[!UICONTROL Checkout title]** campo.
1. Para [definir a ação de pagamento](production.md#set-payment-services-as-payment-method), alternar **[!UICONTROL Payment action]** para `Authorize` ou `Authorize and Capture`.
1. Para ativar o modo de depuração, alterne a função **[!UICONTROL Debug Mode]** seletor.

   Quando você ativa o modo de depuração, informações de depuração adicionais sobre o pagamento do cartão de crédito são gravadas no `var/log/payment.log` arquivo. Essas informações podem fornecer mais informações sobre um pagamento específico para ajudar na solução de problemas.

1. Clique em **[!UICONTROL Save]**.

   Se você tentar sair dessa exibição sem salvar as alterações, será exibido um modal que solicitará que você descarte as alterações, continue a editar ou salve as alterações.

1. Navegar para **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

### Botões inteligentes PayPal

O [!DNL PayPal Smart Buttons] as opções de pagamento oferecem um processo de check-out simples, rápido e seguro para o cliente. Consulte [Opções de pagamentos](payments-options.md#paypal-smart-buttons) para obter mais informações.

Você pode ativar e configurar as opções de pagamento dos botões inteligentes PayPal:

1. Para alterar o nome do método de pagamento, como mostrado durante o check-out, edite o valor no **[!UICONTROL Checkout Title]** campo.
1. Para [definir a ação de pagamento](production.md#set-payment-services-as-payment-method), alternar **[!UICONTROL Payment action]** para `Authorize` ou `Authorize and Capture`.
1. Use os seletores de alternância para ativar ou desativar [!DNL PayPal smart button] recursos de exibição:
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL PayPal Pay Later enabled]**
   - **[!UICONTROL Show Venmo button]**

1. Para alterar o [Pagar Mensagens Mais Tarde](payments-options.md#pay-later-button), alterne a **[!UICONTROL Display Pay Later message]** opção.
1. Para ativar o modo de depuração, alterne a função **[!UICONTROL Debug Mode]** seletor.

   Quando você ativa o modo de depuração, informações de depuração adicionais sobre o pagamento PayPal são gravadas no `var/log/payment.log` arquivo. Essas informações podem fornecer mais informações sobre um pagamento específico para ajudar na solução de problemas.

1. Clique em **[!UICONTROL Save]**.

   Se você tentar sair dessa exibição sem salvar as alterações, será exibido um modal que solicitará que você descarte as alterações, continue a editar ou salve as alterações.

1. Navegar para **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

#### Estilo do botão

Você também pode configurar o _[!UICONTROL Button style]_opções dos botões inteligentes PayPal:

1. Para alterar o **[!UICONTROL Layout]**, selecione `Vertical` ou `Horizontal`.

   >[!NOTE]
   >
   > Se o estilo do botão estiver configurado como `Horizontal` e a sua loja está configurada para mostrar vários botões inteligentes do PayPal, você só pode ver dois botões exibidos na página do produto, na página de checkout e no minicarrinho, e um botão exibido no carrinho.

1. Para ativar o slogan em um layout horizontal, alterne a **[!UICONTROL Show tagline]** seletor.
1. Para modificar o **[!UICONTROL Color]**, selecione a opção de cor desejada.
1. Para modificar o **[!UICONTROL Shape]**, selecione `Pill` ou `Rect`.
1. Para ativar o seletor de altura do botão, alterne a **[!UICONTROL Responsive button height]** seletor.
1. Para modificar o **[!UICONTROL Label]**, selecione a opção de rótulo desejada.
1. Clique em **[!UICONTROL Save]**.

   Se você tentar sair dessa exibição sem salvar as alterações, será exibido um modal que solicitará que você descarte as alterações, continue a editar ou salve as alterações.

1. Navegar para **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

Você pode configurar [!DNL PayPal Smart Buttons] no Admin ou [!DNL Payment Services Home]. Consulte [Guia de estilo de botões do PayPal](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) para obter mais informações.
