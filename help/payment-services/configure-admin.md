---
title: Configuração dos serviços de pagamento herdada
description: Após a instalação, você pode configurar [!DNL Payment Services] no Admin na configuração da loja.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
source-git-commit: bae0eeac349fe3c266d868f8d94c5e033390a661
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# Configuração dos serviços de pagamento herdada

Você pode personalizar [!DNL Payment Services] de acordo com suas necessidades com opções de configuração úteis no Administrador.

Ao configurar [!DNL Payment Services] para Adobe Commerce e Magento Open Source no Admin, essas configurações se aplicam somente ao ambiente definido no [!UICONTROL Method] campo de [!UICONTROL General Configuration]. Todas as alterações feitas nos campos de configuração são independentes de alternar a variável [!UICONTROL Method] seleção — se você alternar o método, suas seleções não serão redefinidas.

Consulte a [[!UICONTROL General Configuration] seção](#general-configuration) para obter mais informações.

## Configuração geral

Você pode ativar [!DNL Payment Services] para sua loja e ativar o teste de sandbox ou os pagamentos em tempo real na [!UICONTROL General Configuration] seção.

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. No painel esquerdo, expanda **[!UICONTROL Sales]** e escolha **[!UICONTROL Payment Methods]**.

   ![Visualização de métodos](assets/methods-view.png)

1. Expanda o _[!UICONTROL Recommended Solutions]_seção.
1. No _[!UICONTROL [!DNL Payment Services]]_expanda a seção_[!UICONTROL General Configuration]_ seção.
1. Para **Habilitar**, defina-o como `Yes` para ativar [!DNL Payment Services] para sua loja.
1. Para **Método**, defina-o como `Sandbox` se você ainda estiver testando [!DNL Payment Services] para sua loja ou `Production` se você estiver pronto para habilitar pagamentos em tempo real.

   >[!WARNING]
   >
   >Seu [!UICONTROL Sandbox Merchant ID] e [!UICONTROL Production Merchant ID] são geradas automaticamente e estão presentes em seus respectivos campos quando você terminar de integrar a sandbox e/ou produção. Não remova ou altere essas IDs.

1. Clique em **[!UICONTROL Save Config]** para salvar as alterações.

### Opções de configuração

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Enable] | site | Ativar ou desativar [!DNL Payment Services] para o seu site. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | exibição de loja | Defina o método ou o ambiente da sua loja. Opções: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | exibição de loja | Sua ID de comerciante da sandbox, que é gerada automaticamente durante a integração com a sandbox. Não altere ou altere essa ID. |
| [!UICONTROL Production Merchant ID] | exibição de loja | Sua ID de comerciante de produção, que é gerada automaticamente durante a integração com a sandbox. Não altere ou altere essa ID. |

## [!UICONTROL Credit Card Fields]

O [!UICONTROL Credit Card Fields] as opções de pagamento proporcionam um check-out simples e seguro para os métodos de pagamento com cartão de crédito ou cartão de débito.

Consulte [Opções de pagamentos](payments-options.md#paypal-smart-buttons) para obter mais informações.

### Configurar campos de cartão de crédito

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. No painel esquerdo, expanda **[!UICONTROL Sales]** e escolha **[!UICONTROL Payment Methods]**.
1. Expanda o _[!UICONTROL Recommended Solutions]_seção.
1. No _[!UICONTROL Payment Services]_expanda a seção_[!UICONTROL Credit Card Fields]_ seção.
1. Para **[!UICONTROL Title]**, insira o texto (se necessário) para alterar o nome do método de pagamento, conforme mostrado durante o check-out.
1. Para [definir a ação de pagamento](production.md#set-payment-services-as-payment-method), selecione **[!UICONTROL Authorize]** ou **Autorizar e capturar**.
1. Para **Modo de depuração**, escolha `Yes` para ativar o modo de depuração (ou `No` para desativá-lo).
1. Clique em **[!UICONTROL Save Config]** para salvar as alterações.

#### Opções de configuração

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Title] | exibição de loja | Adicione o texto para exibição como o título para esta opção de pagamento na exibição Método de Pagamento durante o check-out. Opções: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | site | O [ação de pagamento](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} para o método de pagamento especificado. Opções: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | site | Ative ou desative o Modo de depuração. Opções: [!UICONTROL Yes] / [!UICONTROL No] |

## [!DNL PayPal Smart Buttons]

O [!DNL PayPal Smart Buttons] as opções de pagamento oferecem um processo de check-out simples, rápido e seguro para o cliente.

Consulte [Opções de pagamentos](payments-options.md#paypal-smart-buttons) para obter mais informações.

### Configurar [!DNL PayPal Smart Buttons]

Você pode ativar e configurar as opções de pagamento dos Botões Inteligentes do PayPal no Administrador:

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. No painel esquerdo, expanda **[!UICONTROL Sales]** e escolha **[!UICONTROL Payment Methods]**.
1. Expanda o _[!UICONTROL Recommended Solutions]_seção.
1. No _[!UICONTROL Payment Services]_expanda a seção_[!UICONTROL PayPal Smart Buttons]_ seção.
1. Para alterar o nome do método de pagamento, como mostrado durante o check-out, edite a variável _[!UICONTROL Title]_campo.
1. Para [definir a ação de pagamento](production.md#set-payment-services-as-payment-method), selecione **[!UICONTROL Authorize]** ou **[!UICONTROL Authorize and Capture]**.
1. Para desativar o [Pagar Mensagens Mais Tarde](payments-options.md#pay-later-button) (se desejar), selecione `No` para **[!UICONTROL Display Pay Later Message]**.
1. Para ativar o modo de depuração, selecione `Yes` para **[!UICONTROL Debug Mode]** (`No` desativa-o).
1. Para salvar as alterações, clique em **[!UICONTROL Save Config]** .

### Opções de configuração

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Title] | exibição de loja | Adicione o texto a ser exibido como o título para esta opção de pagamento na exibição Método de Pagamento durante o check-out. Opções: campo de texto |
| [!UICONTROL Payment Action] | site | O [ação de pagamento](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} para o método de pagamento especificado. Opções: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | site | Ative ou desative as mensagens Pagar mais tarde no carrinho de compras, na página do produto, no minicarrinho e durante o fluxo de finalização. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Venmo Enabled] | exibição de loja | Ative ou desative a opção de pagamento de venmo, onde os botões de pagamento são exibidos. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL PayPal Pay Later Enabled] | exibição de loja | Ative ou desative a aparência da opção de pagamento posterior, onde os botões de pagamento são exibidos. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | site | Ative ou desative o Modo de depuração. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on product detail page] | exibição de loja | Ativar ou desativar [!DNL PayPal Smart Buttons] na página de detalhes do produto. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons in mini cart preview] | exibição de loja | Ativar ou desativar [!DNL PayPal Smart Buttons] na visualização do minicart. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on cart page] | exibição de loja | Ativar ou desativar [!DNL PayPal Smart Buttons] na página do carrinho. Opções: [!UICONTROL Yes] / [!UICONTROL No] |

### [!DNL PayPal Smart Buttons] Opções de estilo

| Campo | Escopo | Descrição |
|--- |--- |--- |
| [!UICONTROL Layout] | Exibição da loja | Defina o estilo do layout para Botões inteligentes de pagamento. Opções: [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Color] | Exibição da loja | Defina a cor dos botões inteligentes de pagamento. Opções: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | Exibição da loja | Defina a forma dos botões inteligentes de pagamento. Opções: [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Use Default Height] | Exibição da loja | Define se os botões inteligentes do PayPal usam uma altura padrão. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | Exibição da loja | Defina a altura dos botões inteligentes PayPal. Valor padrão: nenhum |
| [!UICONTROL Label] | Exibição da loja | Defina o rótulo que aparece nos Botões inteligentes do PayPal. Opções: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |
| [!UICONTROL Tagline] | Exibição da loja | Habilita o slogan. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
