---
title: Configurar no painel
description: Após a instalação, você pode configurar [!DNL Payment Services] no painel.
role: Admin, User
level: Intermediate
exl-id: 015c5c8c-8184-45c1-932a-f4365ddf5a30
source-git-commit: 44e97a0299e980656aef557eb5c2bac9b6443452
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---

# Configurar no painel

Você pode personalizar [!DNL Payment Services] de acordo com suas necessidades com opções de configuração úteis no painel.

Ao clicar em [!UICONTROL Settings] no painel, você pode configurar rapidamente [!DNL Payment Services] para Adobe Commerce e Magento Open Source. Essas opções de configuração se aplicam somente ao ambiente definido na variável [!UICONTROL Payment mode] nas Configurações gerais.

Consulte a [[!UICONTROL General] seção configurações](#general-settings) para obter mais informações.

>[!IMPORTANT]
>
> Para obter configurações de várias lojas ou legadas, consulte [Configurar no Administrador](configure-admin.md) tópico.

## Configurar serviços de pagamento

Você pode ativar [!DNL Payment Services] para o seu site e ative o teste de sandbox ou os pagamentos em tempo real na [!UICONTROL General] seção de configurações.

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Exibição do painel](assets/payment-services-menu-small.png)

1. No painel, clique em **[!UICONTROL Settings]** na parte superior direita da página.

   O _[!UICONTROL General]_inclui as opções de configuração usadas para definir [!DNL Payment Services] como método de pagamento.

1. Para a opção de alternância na parte superior (**[!UICONTROL Enable Payment Services as payment method]**), defina-o como `Yes` para ativar [!DNL Payment Services] para o seu site.

1. Para **Modo de pagamento**, defina-o como `Sandbox` se você ainda estiver testando [!DNL Payment Services] para sua loja ou `Production` se você estiver pronto para habilitar pagamentos em tempo real.

   >[!WARNING]
   >
   >Seu [!UICONTROL Sandbox Merchant ID] e [!UICONTROL Production Merchant ID] são geradas automaticamente e estão presentes em seus respectivos campos quando você terminar de integrar a sandbox e/ou produção. Não remova ou altere essas IDs.

1. Para alterar as configurações padrão das funções de pagamento e da tela de loja, defina as opções adicionais conforme necessário:

   - [Campos de cartão de crédito](#credit-card-fields)
   - [Botões inteligentes PayPal](#paypal-smart-buttons)
   - [Estilo do botão](#button-style)

1. Para salvar as alterações, clique em **[!UICONTROL Save]** na parte superior direita da página.

   Se você tentar sair dessa exibição sem salvar as alterações, será exibido um modal que solicitará que você descarte as alterações, continue a editar ou salve as alterações.

1. Navegar para **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

### Campos de cartão de crédito

O [!UICONTROL Credit Card Fields] as opções de pagamento proporcionam um check-out simples e seguro para os métodos de pagamento com cartão de crédito ou cartão de débito.

Consulte [Opções de pagamentos](payments-options.md#paypal-smart-buttons) para obter mais informações.

1. Para **[!UICONTROL Checkout title]**, insira o texto (se necessário) para alterar o nome do método de pagamento exibido durante o check-out.
1. Para [definir a ação de pagamento](production.md#set-payment-services-as-payment-method), definir **[!UICONTROL Payment action]** para `Authorize` ou `Authorize and Capture`.
1. Para **[!UICONTROL Debug Mode]**, alterne o seletor para ativar o modo de depuração.
1. Para salvar as alterações, clique em **[!UICONTROL Save]** na parte superior direita da página.

   Se você tentar sair dessa exibição sem salvar as alterações, será exibido um modal que solicitará que você descarte as alterações, continue a editar ou salve as alterações.

1. Navegar para **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

### Botões inteligentes PayPal

O [!DNL PayPal Smart Buttons] as opções de pagamento oferecem um processo de check-out simples, rápido e seguro para o cliente. Consulte [Opções de pagamentos](payments-options.md#paypal-smart-buttons) para obter mais informações.

Você pode ativar as opções de pagamento dos botões inteligentes PayPal no painel:

1. Para alterar o nome do método de pagamento, como mostrado durante o check-out, edite o valor no **[!UICONTROL Checkout Title]** campo.
1. Para [definir a ação de pagamento](production.md#set-payment-services-as-payment-method), definir **[!UICONTROL Payment action]** para `Authorize` ou `Authorize and Capture`.
1. Use os seletores de alternância para ativar ou desativar [!DNL PayPal smart button] recursos de exibição:
   - **[!UICONTROL Show buttons on product detail page]**
   - **[!UICONTROL Show buttons in mini cart preview]**
   - **[!UICONTROL Show buttons on cart page]**
   - **[!UICONTROL Show Venmo button]**.
   - **[!UICONTROL PayPal Pay Later enabled]** para ativar a opção de mostrar botão durante o check-out.

1. Para alterar o [Pagar Mensagens Mais Tarde](payments-options.md#pay-later-button) (se desejar), alterne a opção **[!UICONTROL Display Pay Later message]** opção.
1. Para ativar o modo de depuração, clique em **[!UICONTROL Debug Mode]**,
1. Para salvar as alterações, clique em **[!UICONTROL Save]** na parte superior direita da página.

   Se você tentar sair dessa exibição sem salvar as alterações, será exibido um modal que solicitará que você descarte as alterações, continue a editar ou salve as alterações.

1. Navegar para **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

### Estilo do botão

Você também pode configurar o _[!UICONTROL Button style]_opções dos botões inteligentes PayPal no painel:

1. Para alterar o **[!UICONTROL Layout]**, selecione `Vertical` ou `Horizontal`.
1. Para ativar o slogan em um layout horizontal, clique em **[!UICONTROL Show tagline]**.
1. Para modificar o **[!UICONTROL Color]**, selecione a opção de cor desejada.
1. Para alterar o **[!UICONTROL Shape]**, selecione `Pill` ou `Rect`.
1. Para ativar o seletor de altura do botão, clique em **[!UICONTROL Responsive button height]**.
1. Para modificar o **[!UICONTROL Label]**, selecione a opção de rótulo desejada.
1. Para salvar as alterações, clique em **[!UICONTROL Save]** na parte superior direita da página.

   Se você tentar sair dessa exibição sem salvar as alterações, será exibido um modal que solicitará que você descarte as alterações, continue a editar ou salve as alterações.

1. Navegar para **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

Você pode configurar [!DNL PayPal Smart Buttons] no Admin ou no Painel. Consulte [Guia de estilo de botões do PayPal](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) para obter mais informações.
