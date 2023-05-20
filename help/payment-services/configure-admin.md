---
title: Configuração de serviços de pagamento herdados
description: Após a instalação, é possível configurar [!DNL Payment Services] em Admin na configuração da loja.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 0%

---

# Herdados [!DNL Payment Services] Configuração

Você pode personalizar [!DNL Payment Services] às suas necessidades com opções de configuração úteis no painel Admin.

Ao configurar [!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source] no Admin, essas configurações se aplicam somente ao ambiente definido no _[!UICONTROL Method]_campo de_[!UICONTROL General Configuration]_. Quaisquer alterações feitas nos campos de configuração são independentes de alternar entre _[!UICONTROL Method]_seleção — se você alternar o método, suas seleções não serão redefinidas.

## Configuração geral

Você pode ativar [!DNL Payment Services] para sua loja e ative os testes de sandbox ou os pagamentos em tempo real no _[!UICONTROL General Configuration]_seção.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. No painel esquerdo, expanda **[!UICONTROL Sales]** e escolha **[!UICONTROL Payment Methods]**.

   ![Exibição de métodos](assets/methods-view.png)

1. Expanda a _[!UICONTROL Recommended Solutions]_seção.
1. No _[!UICONTROL [!DNL Payment Services]]_, expanda a_[!UICONTROL General Configuration]_ seção.
1. Para **Ativar**, defina-o como `Yes` para habilitar [!DNL Payment Services] para sua loja.
1. Para **Método**, defina-o como `Sandbox` se você ainda estiver testando [!DNL Payment Services] para sua loja ou `Production` se estiver pronto para ativar os pagamentos em tempo real.

   >[!WARNING]
   >
   >Seu _[!UICONTROL Sandbox Merchant ID]_e_[!UICONTROL Production Merchant ID]_ são gerados automaticamente e estão presentes em seus respectivos campos quando você conclui a integração da sandbox e/ou produção. Não remova nem altere essas IDs.

1. Clique em **[!UICONTROL Save Config]** para salvar as alterações.
1. Navegue até **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

### Opções de configuração

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Enable] | site | Ativar ou desativar [!DNL Payment Services] para o seu site. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | exibição de loja | Defina o método ou ambiente para sua loja. Opções: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | exibição de loja | Sua ID de comerciante de sandbox, que é gerada automaticamente durante a integração da sandbox. Não altere ou altere esta ID. |
| [!UICONTROL Production Merchant ID] | exibição de loja | Sua ID de comerciante de produção, que é gerada automaticamente durante a integração da sandbox. Não altere ou altere esta ID. |

## [!UICONTROL Credit Card Fields]

A variável [!UICONTROL Credit Card Fields] as opções de pagamento fornecem um checkout simples e seguro para métodos de pagamento com cartão de crédito ou débito.

Consulte [Opções de pagamentos](payments-options.md#paypal-smart-buttons) para obter mais informações.

### Configurar campos de cartão de crédito

1. No _Admin_ barra lateral, vá para **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. No painel esquerdo, expanda **[!UICONTROL Sales]** e escolha **[!UICONTROL Payment Methods]**.
1. Expanda a _[!UICONTROL Recommended Solutions]_seção.
1. No _[!UICONTROL Payment Services]_, expanda a_[!UICONTROL Credit Card Fields]_ seção.
1. Para **[!UICONTROL Title]**, informe o texto (se necessário) para alterar o nome do método de pagamento conforme mostrado durante o checkout.
1. Para [definir a ação de pagamento](production.md#set-payment-services-as-payment-method), selecione **[!UICONTROL Authorize]** ou **Autorizar e capturar**.
1. Para **[!UICONTROL Show on checkout page]**, escolha `Yes` para ativar campos de cartão de crédito na página de check-out.
1. Para **[!UICONTROL Vault Enabled]**, escolha `Yes` para ativar a compartimentalização de cartão de crédito para finalização da compra.
1. Para **[!UICONTROL Vault Enabled in Admin]**, escolha `Yes` para permitir que o comerciante crie ordens para clientes usando seu cartão de crédito com cofre.
1. Para **[!UICONTROL Debug Mode]**, escolha `Yes` para ativar o modo de depuração (ou `No` para desativá-lo).
1. Para habilitar **[!UICONTROL 3DS Secure authentication]** (`Off` por padrão), escolha `Always` ou `When required`.
1. Clique em **[!UICONTROL Save Config]** para salvar as alterações.
1. Navegue até **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

#### Opções de configuração

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Title] | exibição de loja | Adicione o texto para exibição como o título desta opção de pagamento na exibição de Método de Pagamento durante a finalização da compra. Opções: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | site | A variável [ação de pagamento](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) para o método de pagamento especificado. Opções: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | site | Ative ou desative os campos de cartão de crédito na página de check-out. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | exibição de loja | Ativar ou desativar [compartimentalização de cartão de crédito](vaulting.md). Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled in Admin] | exibição de loja | Ativar ou desativar a capacidade para [comerciante para concluir pedidos de clientes no Administrador](vaulting.md) usando um método de pagamento com cofre. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL 3DS Secure authentication] | site | Ativar ou desativar [Autenticação segura 3DS](security.md#3ds). Opções: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | site | Ative ou desative o Modo de depuração. Opções: [!UICONTROL Yes] / [!UICONTROL No] |

## [!DNL PayPal Smart Buttons]

A variável [!DNL PayPal Smart Buttons] as opções de pagamento fornecem um processo de finalização simples, rápido e seguro para o cliente.

Consulte [Opções de pagamentos](payments-options.md#paypal-smart-buttons) para obter mais informações.

### Configurar [!DNL PayPal Smart Buttons]

Você pode ativar e configurar as opções de pagamento dos Botões inteligentes do PayPal em Admin:

1. No _Admin_ barra lateral, vá para **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. No painel esquerdo, expanda **[!UICONTROL Sales]** e escolha **[!UICONTROL Payment Methods]**.
1. Expanda a _[!UICONTROL Recommended Solutions]_seção.
1. No _[!UICONTROL Payment Services]_, expanda a_[!UICONTROL PayPal Smart Buttons]_ seção.
1. Para alterar o nome do método de pagamento conforme mostrado durante a finalização da compra, edite o _[!UICONTROL Title]_campo.
1. Para [definir a ação de pagamento](production.md#set-payment-services-as-payment-method), selecione **[!UICONTROL Authorize]** ou **[!UICONTROL Authorize and Capture]**.
1. Para desativar o [Mensagens de Pagamento Posterior](payments-options.md#pay-later-button) (se desejar), selecione `No` para **[!UICONTROL Display Pay Later Message]**.
1. Para ativar o modo de depuração, selecione `Yes` para o **[!UICONTROL Debug Mode]** (`No` O desativa).
1. Para salvar as alterações, clique em **[!UICONTROL Save Config]** .
1. Navegue até **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

### Opções de configuração

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Title] | exibição de loja | Adicione o texto a ser exibido como o título para esta opção de pagamento na exibição de Método de Pagamento durante a finalização da compra. Opções: campo de texto |
| [!UICONTROL Payment Action] | site | A variável [ação de pagamento](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} para o método de pagamento especificado. Opções: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | site | Ative ou desative as mensagens Pagar mais tarde no carrinho de compras, página do produto, minicarrinho e durante o fluxo de finalização. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Venmo Enabled] | exibição de loja | Habilite ou desabilite a opção de pagamento Venmo onde os botões de pagamento são exibidos. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Apple Pay Enabled] | exibição de loja | Ative ou desative a opção Pagamento Apple onde os botões de pagamento são exibidos. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL PayPal Pay Later Enabled] | exibição de loja | Ativar ou desativar a aparência da opção de pagamento pagar mais tarde, onde os botões de pagamento são exibidos. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | site | Ative ou desative o Modo de depuração. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on product detail page] | exibição de loja | Ativar ou desativar [!DNL PayPal Smart Buttons] na página de detalhes do produto. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons in mini-cart preview] | exibição de loja | Ativar ou desativar [!DNL PayPal Smart Buttons] na pré-visualização do minicarrinho. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show buttons on cart page] | exibição de loja | Ativar ou desativar [!DNL PayPal Smart Buttons] na página do carrinho. Opções: [!UICONTROL Yes] / [!UICONTROL No] |

### [!DNL PayPal Smart Buttons] Opções de estilo

| Campo | Escopo | Descrição |
|--- |--- |--- |
| [!UICONTROL Layout] | Exibição da loja | Defina o estilo de layout para os botões inteligentes do Paypal. Opções: [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Color] | Exibição da loja | Defina a cor dos botões inteligentes do Paypal. Opções: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | Exibição da loja | Defina a forma dos botões inteligentes do Paypal. Opções: [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Use Default Height] | Exibição da loja | Define se os Botões Inteligentes do PayPal usam uma altura padrão. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | Exibição da loja | Defina a altura dos Botões Inteligentes do PayPal. Valor padrão: nenhum |
| [!UICONTROL Label] | Exibição da loja | Defina o rótulo que aparece nos Botões Inteligentes do PayPal. Opções: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |
| [!UICONTROL Tagline] | Exibição da loja | Ativa o slogan. Opções: [!UICONTROL Yes] / [!UICONTROL No] |

## Liberar o cache

Se você alterar a configuração, [liberar manualmente o cache](/help/payment-services/settings.md#flush-the-cache) para que sua loja mostre as definições de configuração mais recentes.

