---
title: Configuração de serviços de pagamento herdados
description: Após a instalação, é possível configurar [!DNL Payment Services] em Admin na configuração da loja.
role: Admin, User
level: Intermediate
exl-id: e1a3269d-bdf9-4b0f-972f-e8a0ef469503
feature: Payments, Checkout, Configuration
source-git-commit: 31c1c9a99e75feae7a2a81faf17921a63a03a526
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 0%

---

# Herdados [!DNL Payment Services] Configuração

Você pode personalizar [!DNL Payment Services] às suas necessidades com opções de configuração úteis no painel Admin.

Ao configurar [!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source] no Admin, essas configurações se aplicam somente ao ambiente definido no _[!UICONTROL Method]_campo de_[!UICONTROL General Configuration]_. Quaisquer alterações feitas nos campos de configuração são independentes de alternar entre _[!UICONTROL Method]_seleção — se você alternar o método, suas seleções não serão redefinidas.

## Configuração geral

Você pode ativar [!DNL Payment Services] para sua loja e ative os testes de sandbox ou os pagamentos em tempo real no _[!UICONTROL General Configuration]_seção.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. No painel esquerdo, expanda **[!UICONTROL Sales]** e escolha **[!UICONTROL Payment Methods]**.

   ![Exibição de métodos](assets/methods-view.png){width="400" zoomable="yes"}

1. Expanda a _[!UICONTROL Recommended Solutions]_seção.
1. No _[!UICONTROL [!DNL Payment Services]]_, expanda a_[!UICONTROL General Configuration]_ seção.
1. Para **Ativar**, defina-o como `Yes` para habilitar [!DNL Payment Services] para sua loja.
1. Para **Método**, defina-o como `Sandbox` se você ainda estiver testando [!DNL Payment Services] para sua loja ou `Production` se estiver pronto para ativar os pagamentos em tempo real.

   >[!WARNING]
   >
   >Seu _[!UICONTROL Sandbox Merchant ID]_e_[!UICONTROL Production Merchant ID]_ são gerados automaticamente e estão presentes em seus respectivos campos quando você conclui a integração da sandbox e/ou produção. Não remova nem altere essas IDs.

1. Para **Descritor suave** (valores personalizados que são exibidos em demonstrativos bancários de transações do cliente para definir entre lojas/marcas/catálogos), adicione o texto personalizado (até 22 caracteres) ao campo de texto, substituindo `Custom descriptor` ou o valor existente.
1. Clique em **[!UICONTROL Save Config]** para salvar as alterações.
1. Navegue até **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

### Opções de configuração

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Enable] | site | Ativar ou desativar [!DNL Payment Services] para o seu site. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Method] | exibição de loja | Defina o método ou ambiente para sua loja. Opções: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | exibição de loja | Sua ID de comerciante de sandbox, que é gerada automaticamente durante a integração da sandbox. Não altere ou altere esta ID. |
| [!UICONTROL Production Merchant ID] | exibição de loja | Sua ID de comerciante de produção, que é gerada automaticamente durante a integração da sandbox. Não altere ou altere esta ID. |
| [!UICONTROL Soft Descriptor] | exibição de site ou loja | Adicione um descritor simples ao(s) site(s) e às visualizações da loja para adicionar informações às transações do cliente que definem marcas, lojas ou linhas de produtos. |

## [!UICONTROL Credit Card Fields]

A variável [!UICONTROL Credit Card Fields] as opções de pagamento fornecem um checkout simples e seguro para métodos de pagamento com cartão de crédito ou débito.

Consulte [Opções de pagamentos](payments-options.md#paypal-smart-buttons) para obter mais informações.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. No painel esquerdo, expanda **[!UICONTROL Sales]** e escolha **[!UICONTROL Payment Methods]**.
1. Expanda a _[!UICONTROL Recommended Solutions]_seção.
1. No _[!UICONTROL Payment Services]_, expanda a_[!UICONTROL Credit Card Fields]_ seção.
1. Para **[!UICONTROL Title]**, informe o texto (se necessário) para alterar o nome do método de pagamento conforme mostrado durante o checkout.
1. Para [definir a ação de pagamento](production.md#set-payment-services-as-payment-method), selecione **[!UICONTROL Authorize]** ou **Autorizar e capturar**.
1. Para priorizar um método de pagamento na página de finalização da compra, forneça uma `Numeric Only` valor no **[!UICONTROL Sort order]** campo.
1. Para **[!UICONTROL Show on checkout page]**, escolha `Yes` para ativar campos de cartão de crédito na página de check-out.
1. Para **[!UICONTROL Vault Enabled]**, escolha `Yes` para ativar a compartimentalização de cartão de crédito para finalização da compra.
1. Para **[!UICONTROL Vault Enabled in Admin]**, escolha `Yes` para permitir que o comerciante crie ordens para clientes usando seu cartão de crédito com cofre.
1. Para habilitar **[!UICONTROL 3DS Secure authentication]** (`Off` por padrão), escolha `Always` ou `When required`.
1. Para **[!UICONTROL Debug Mode]**, escolha `Yes` para ativar o modo de depuração ou `No` para desativá-lo.
1. Clique em **[!UICONTROL Save Config]** para salvar as alterações.
1. Navegue até **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

### Opções de configuração

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Title] | exibição de loja | Adicione o texto a ser exibido como o título para esta opção de pagamento na exibição de Método de Pagamento durante a finalização da compra. Opções: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | site | A variável [ação de pagamento](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) para o método de pagamento especificado. Opções: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Sort order] | exibição de loja | A ordem de classificação do método de pagamento especificado na página de check-out. `Numeric Only` value |
| [!UICONTROL Show on checkout page] | site | Ative ou desative os campos de cartão de crédito na página de check-out. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled] | exibição de loja | Ativar ou desativar [compartimentalização de cartão de crédito](vaulting.md). Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Vault enabled in Admin] | exibição de loja | Ativar ou desativar a capacidade para [comerciante para concluir pedidos de clientes no Administrador](vaulting.md) usando um método de pagamento com cofre. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL 3DS Secure authentication] | site | Ativar ou desativar [Autenticação segura 3DS](security.md#3ds). Opções: [!UICONTROL Always] / [!UICONTROL When Required] / [!UICONTROL Off] |
| [!UICONTROL Debug Mode] | site | Ative ou desative o Modo de depuração. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!UICONTROL Apple Pay]

A variável [!UICONTROL Apple Pay] A opção de pagamento permite que o comerciante ofereça o Apple Pay aos seus compradores, que podem usar o Touch ID em seus dispositivos para fazer compras no navegador Safari.

Consulte [Opções de pagamentos](payments-options.md#apple-pay-button) para obter mais informações.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. No painel esquerdo, expanda **[!UICONTROL Sales]** e escolha **[!UICONTROL Payment Methods]**.
1. Expanda a _[!UICONTROL Recommended Solutions]_seção.
1. No _[!UICONTROL Payment Services]_, expanda a_[!UICONTROL Apple Pay]_ seção.
1. Para **[!UICONTROL Title]**, informe o texto (se necessário) para alterar o nome do método de pagamento conforme mostrado durante o checkout.
1. Para [definir a ação de pagamento](production.md#set-payment-services-as-payment-method), selecione **[!UICONTROL Authorize]** ou **[!UICONTROL Authorize and Capture]**.
1. Para mostrar [!DNL Apple Pay] na página de check-out, selecione `Yes` para o **[!UICONTROL Show buttons on checkout page]**.
1. Para mostrar [!DNL Apple Pay] na página detalhes do produto, selecione `Yes` para o **[!UICONTROL Show buttons on product detail page]**.
1. Para mostrar [!DNL Apple Pay] na visualização do minicarrinho, selecione `Yes` para **[!UICONTROL Show buttons in mini cart preview]**.
1. Para mostrar [!DNL Apple Pay] na página do carrinho, selecione `Yes` para o **[!UICONTROL Show buttons on cart page]**.
1. Para ativar o modo de depuração, selecione `Yes` para o **[!UICONTROL Debug Mode]** (`No` O desativa).
1. Para salvar as alterações, clique em **[!UICONTROL Save Config]** .
1. Navegue até **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

### Opções de configuração

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Title] | exibição de loja | Adicione o texto a ser exibido como o título para esta opção de pagamento na exibição de Método de Pagamento durante a finalização da compra. Opções: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | site | A variável [ação de pagamento](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/payment-methods/payment-methods.html) para o método de pagamento especificado. Opções: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show on checkout page] | site | Ativar ou desativar [!DNL Apple Pay] na página de check-out. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on product detail page] | exibição de loja | Ativar ou desativar [!DNL Apple Pay] na página de detalhes do produto. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | exibição de loja | Ativar ou desativar [!DNL Apple Pay] na pré-visualização do minicarrinho. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | exibição de loja | Ativar ou desativar [!DNL Apple Pay] na página do carrinho. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | site | Ative ou desative o Modo de depuração. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## [!DNL PayPal Payment Buttons]

A variável [!DNL PayPal payment buttons] as opções de pagamento fornecem um processo de finalização simples, rápido e seguro para o cliente.

Consulte [Opções de pagamentos](payments-options.md#paypal-smart-buttons) para obter mais informações.

Configurar [!DNL PayPal payment buttons]

Você pode ativar e configurar as opções de pagamento dos botões de pagamento do PayPal em Admin:

1. No _Admin_ barra lateral, vá para **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. No painel esquerdo, expanda **[!UICONTROL Sales]** e escolha **[!UICONTROL Payment Methods]**.
1. Expanda a _[!UICONTROL Recommended Solutions]_seção.
1. No _[!UICONTROL Payment Services]_, expanda a_[!UICONTROL PayPal payment buttons]_ seção.
1. Para alterar o nome do método de pagamento conforme mostrado durante a finalização da compra, edite o _[!UICONTROL Title]_campo.
1. Para [definir a ação de pagamento](production.md#set-payment-services-as-payment-method), selecione **[!UICONTROL Authorize]** ou **[!UICONTROL Authorize and Capture]**.
1. Para priorizar um método de pagamento na página de finalização da compra, forneça uma `Numeric Only` valor no **[!UICONTROL Sort order]** campo.
1. Para ativar/desativar o [Mensagens de Pagamento Posterior](payments-options.md#pay-later-button), selecione `Yes`/`No` para **[!UICONTROL Display Pay Later Message]**.
1. Para mostrar os botões de pagamento do PayPal na página de check-out, selecione `Yes` para o **[!UICONTROL Show buttons on checkout page]**.
1. Para mostrar os botões de pagamento do PayPal na página de detalhes do produto, selecione `Yes` para o **[!UICONTROL Show buttons on product detail page]**.
1. Para mostrar os botões de pagamento do PayPal na visualização do minicarrinho, selecione `Yes` para **[!UICONTROL Show buttons in mini cart preview]**.
1. Para mostrar os botões de pagamento do PayPal na página do carrinho, selecione `Yes` para o **[!UICONTROL Show buttons on cart page]**.
1. Para habilitar Venmo como uma opção de pagamento, selecione `Yes` para **[!UICONTROL Venmo Enabled]**.
1. Para habilitar cartões de crédito e débito como opção de pagamento (botão PayPal Smart), selecione `Yes` para **[!UICONTROL Credit and Debit Card Enabled]**.
1. Para ativar/desativar o [PayPal Pay Later (Pagar mais tarde no PayPal)](payments-options.md#pay-later-button) opção de pagamento, selecione `Yes`/`No` para **[!UICONTROL PayPal Pay Later Enabled]**.
1. Para ativar o modo de depuração, selecione `Yes` para o **[!UICONTROL Debug Mode]** (`No` O desativa).
1. Para salvar as alterações, clique em **[!UICONTROL Save Config]** .
1. Navegue até **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

### Opções de configuração

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Title] | exibição de loja | Adicione o texto a ser exibido como o título para esta opção de pagamento na exibição de Método de Pagamento durante a finalização da compra. Opções: campo de texto |
| [!UICONTROL Payment Action] | site | A variável [ação de pagamento](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} para o método de pagamento especificado. Opções: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Display Pay Later Message] | site | Ative ou desative a mensagem Pagar mais tarde no carrinho de compras, página do produto, minicarrinho e durante o fluxo de finalização. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on checkout page] | exibição de loja | Ativar ou desativar [!DNL PayPal payment buttons] na página de check-out. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on product detail page] | exibição de loja | Ativar ou desativar [!DNL PayPal payment buttons] na página de detalhes do produto. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons in mini-cart preview] | exibição de loja | Ativar ou desativar [!DNL PayPal payment buttons] na pré-visualização do minicarrinho. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Show buttons on cart page] | exibição de loja | Ativar ou desativar [!DNL PayPal payment buttons] na página do carrinho. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Venmo Enabled] | exibição de loja | Habilite ou desabilite a opção de pagamento Venmo onde os botões de pagamento são exibidos. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Credit and Debit Card Enabled] | exibição de loja | Ative ou desative as opções de cartão de Crédito e Débito onde os botões de pagamento são exibidos. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL PayPal Pay Later Enabled] | exibição de loja | Ativar ou desativar a aparência da opção de pagamento PayPal Pay Posteriormente, onde os botões de pagamento são exibidos. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Debug Mode] | site | Ative ou desative o Modo de depuração. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## Estilo do botão

Você também pode configurar as opções _[!UICONTROL Button style]_opções dos botões de pagamento:

1. No _Admin_ barra lateral, vá para **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. No painel esquerdo, expanda **[!UICONTROL Sales]** e escolha **[!UICONTROL Payment Methods]**.
1. Expanda a _[!UICONTROL Recommended Solutions]_seção.
1. No _[!UICONTROL [!DNL Payment Services]]_, expanda a_[!UICONTROL PayPal Smart Button Styling]_ seção.
1. Para definir o layout, selecione `Vertical` ou `Horizontal` para **[!UICONTROL Layout]**
1. Para definir a cor, selecione uma das cores disponíveis no **[!UICONTROL Color]**.
1. Para definir a forma, selecione `Rectangular` ou `Pill` para **[!UICONTROL Shape]**.
1. Para usar a altura padrão, selecione `Yes` ou `No` para **[!UICONTROL Use Default Height]**.
1. Para definir a altura personalizada, adicione a altura de pixel desejada para **[!UICONTROL Height]**.
1. Para definir o slogan, selecione `Yes` ou `No` para **[!UICONTROL Tagline]**.
1. Para salvar as alterações, clique em **[!UICONTROL Save Config]** .
1. Navegue até **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

Você também pode configurar o estilo do botão de pagamento [em Configurações](settings.md#button-style) na Página Inicial de Serviços de Pagamento.

### Opções de configuração

| Campo | Escopo | Descrição |
|--- |--- |--- |
| [!UICONTROL Layout] | Exibição da loja | Definir estilo de layout para botões de pagamento Paypal. Opções: `[!UICONTROL Vertical]` / `[!UICONTROL Horizontal]` |
| [!UICONTROL Color] | Exibição da loja | Defina a cor dos botões de pagamento do Paypal. Opções: [!UICONTROL Blue] / `[!UICONTROL Gold]` / `[!UICONTROL Silver]` / `[!UICONTROL White]` / `[!UICONTROL Black]` |
| [!UICONTROL Shape] | Exibição da loja | Defina a forma dos botões de pagamento Paypal. Opções: `[!UICONTROL Rectangular]` / `[!UICONTROL Pill]` |
| [!UICONTROL Use Default Height] | Exibição da loja | Define se os botões de pagamento do PayPal usam uma altura padrão. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |
| [!UICONTROL Height] | Exibição da loja | Defina a altura dos botões de pagamento do PayPal. Valor padrão: nenhum |
| [!UICONTROL Label] | Exibição da loja | Defina o rótulo que aparece nos botões de pagamento do PayPal. Opções: `[!UICONTROL PayPal]` / `[!UICONTROL Checkout]` / `[!UICONTROL Buynow]` / `[!UICONTROL Pay]` / `[!UICONTROL Installment]` |
| [!UICONTROL Tagline] | Exibição da loja | Ativa o slogan. Opções: `[!UICONTROL Yes]` / `[!UICONTROL No]` |

## Liberar o cache

Se você alterar a configuração, [liberar manualmente o cache](/help/payment-services/settings.md#flush-the-cache) para que sua loja mostre as definições de configuração mais recentes.
