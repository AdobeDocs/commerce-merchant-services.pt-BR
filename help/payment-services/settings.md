---
title: Configurações dos serviços de pagamento
description: Após a instalação, você pode configurar [!DNL Payment Services] no Início.
role: Admin, User
level: Intermediate
exl-id: 108f2b24-39c1-4c87-8deb-d82ee1c24d55
source-git-commit: 65787d91c098e8f5d4ae46cba4d5e226b6301ecc
workflow-type: tm+mt
source-wordcount: '1555'
ht-degree: 0%

---

# Configurações

Você pode personalizar [!DNL Payment Services] de acordo com suas necessidades com as configurações úteis na [!DNL Payment Services] Casa.

Para configurar [!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source] click **[!UICONTROL Settings]**. Essas opções de configuração se aplicam somente ao ambiente definido na variável _[!UICONTROL Payment mode]_em_[!UICONTROL Settings]_ > _[!UICONTROL General]_.

>[!IMPORTANT]
>
> Para obter configurações de várias lojas ou legadas, consulte [Configurar no Administrador](configure-admin.md) tópico.

## Definir configurações gerais

O [!UICONTROL General] As configurações fornecem a capacidade de ativar ou desativar os Serviços de Pagamento como método de pagamento e adicionar informações às transações do cliente para marcar ou prefixar um site ou exibição de loja com informações personalizadas.

### Ativar serviços de pagamento

Você pode ativar [!DNL Payment Services] para o seu site e ative o teste de sandbox ou os pagamentos em tempo real.

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Exibição da página inicial](assets/payment-services-menu-small.png)

1. Clique em **[!UICONTROL Settings]**. Consulte [Introdução ao [!DNL Payment Services] Início](payments-home.md) para obter mais informações.

   O _[!UICONTROL General]_seção inclui configurações usadas para ativar [!DNL Payment Services] como método de pagamento.

1. Para ativar [!DNL Payment Services] como método de pagamento para a sua loja, no _[!UICONTROL General]_seção, alternar **[!UICONTROL Enable Payment Services as payment method]**para `Yes`.

1. Se você ainda estiver testando [!DNL Payment Services] para sua loja, defina **Modo de pagamento** para `Sandbox`. Se estiver pronto para ativar os pagamentos em tempo real, defina-o como `Production`.

   >[!NOTE]
   >
   >Seu _[!UICONTROL Sandbox Merchant ID]_e_[!UICONTROL Production Merchant ID]_ são geradas automaticamente e estão presentes em seus respectivos campos quando você conclui a integração com a sandbox e/ou produção.

1. Clique em **[!UICONTROL Save]**.

   Se você tentar sair dessa exibição sem salvar as alterações, será exibido um modal que solicitará que você descarte as alterações, continue a editar ou salve as alterações.

1. Navegar para **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

Agora você pode continuar alterando as configurações padrão de [opções de pagamento](#configure-payment-options) funções e vitrine são exibidas.

### Adicionar descritor suave

Você pode adicionar uma [!UICONTROL Soft Descriptor] para o(s) site(s) ou a configuração de exibição(s) de loja individual. Descritores suaves são exibidos em demonstrativos bancários de transação do cliente. Se você tiver várias lojas/marcas/catálogos, por exemplo, é possível delinear facilmente entre eles adicionando texto personalizado à variável [!UICONTROL Soft Descriptor] campo.

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.

   ![Exibição da página inicial](assets/payment-services-menu-small.png)

1. Clique em **[!UICONTROL Settings]**. Consulte [Introdução ao [!DNL Payment Services] Início](payments-home.md) para obter mais informações.
1. Selecione o site ou a exibição de loja na **[!UICONTROL Scope]** menu suspenso, para o qual deseja criar um descritor suave. Para a configuração inicial, deixe como **[!UICONTROL Default]** para definir o valor padrão.
1. Adicione o texto personalizado (até 22 caracteres) no campo de texto, substituindo `Custom descriptor`.
1. Clique em **[!UICONTROL Save]**.
1. Para criar um descritor suave diferente do padrão configurado para um site ou exibição de loja:
   1. Selecione o site ou a exibição de loja na **[!UICONTROL Scope]** menu suspenso, para o qual deseja criar um descritor suave.
   1. Alternar *off* **[!UICONTROL Use website]** ou **[!UICONTROL Use default]**, dependendo do escopo selecionado).
   1. Adicione o texto personalizado no campo de texto.
   1. Clique em **[!UICONTROL Save]**.
1. Para ativar um site ou armazenar, visualize o descritor flexível padrão *ou* o descritor suave usado para o site principal:
   1. Selecione o site ou a exibição de loja na **[!UICONTROL Scope]** menu suspenso, para o qual você deseja ativar um descritor suave existente.
   1. Alternar *on* **[!UICONTROL Use website]** ou **[!UICONTROL Use default]**, dependendo do escopo selecionado).
   1. Clique em **[!UICONTROL Save]**.

   Se você tentar sair dessa exibição sem salvar as alterações, será exibido um modal que solicitará que você descarte as alterações, continue a editar ou salve as alterações.

### Opções de configuração

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Enable] | site | Ativar ou desativar [!DNL Payment Services] para o seu site. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Payment mode] | exibição de loja | Defina o método ou o ambiente da sua loja. Opções: [!UICONTROL Sandbox] / [!UICONTROL Production] |
| [!UICONTROL Sandbox Merchant ID] | exibição de loja | Sua ID de comerciante da sandbox, que é gerada automaticamente durante a integração com a sandbox. |
| [!UICONTROL Production Merchant ID] | exibição de loja | Sua ID de comerciante de produção, que é gerada automaticamente durante a integração com a sandbox. |
| [!UICONTROL Soft Descriptor] | exibição de site ou loja | Adicione um descritor suave ao(s) site(s) e às visualizações de armazenamento para adicionar informações às transações do cliente que delineiam marcas, lojas ou linhas de produto. O [!UICONTROL Use website] O alternador aplica qualquer descritor suave adicionado no nível do site. O [!UICONTROL Use default] a alternância aplica qualquer descritor suave adicionado como padrão. |

## Configurar opções de pagamento

Agora que você ativou os Serviços de Pagamento do seu site, é possível alterar as configurações padrão para funções de pagamento e exibição da loja.

### Campos de cartão de crédito

O _[!UICONTROL Credit Card Fields]_As configurações oferecem uma opção de check-out simples e segura para os métodos de pagamento com cartão de crédito ou cartão de débito.

Consulte [Opções de pagamentos](payments-options.md#credit-card-fields) para obter mais informações.

1. Selecione a exibição de loja na **[!UICONTROL Scope]** menu suspenso, para o qual você deseja ativar um método de pagamento.
1. Para alterar o nome do método de pagamento exibido durante o check-out, edite o valor no **[!UICONTROL Checkout title]** campo.
1. Para [definir a ação de pagamento](production.md#set-payment-services-as-payment-method), alternar **[!UICONTROL Payment action]** para `Authorize` ou `Authorize and Capture`.
1. Para ativar o modo de depuração, alterne a função **[!UICONTROL Debug Mode]** seletor.
1. Clique em **[!UICONTROL Save]**.

   Se você tentar sair dessa exibição sem salvar as alterações, será exibido um modal que solicitará que você descarte as alterações, continue a editar ou salve as alterações.

1. Navegar para **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

#### Opções de configuração

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Title] | exibição de loja | Adicione o texto para exibição como o título para esta opção de pagamento na exibição Método de Pagamento durante o check-out. Opções: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | site | O [ação de pagamento](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} para o método de pagamento especificado. Opções: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | site | Ative ou desative o Modo de depuração. Opções: [!UICONTROL Yes] / [!UICONTROL No] |

### Botões de pagamento

O [!DNL PayPal Smart Buttons] as opções de pagamento oferecem um processo de check-out simples, rápido e seguro para o cliente. Consulte [Opções de pagamentos](payments-options.md#paypal-smart-buttons) para obter mais informações.

Você pode ativar e configurar as opções de pagamento dos botões inteligentes PayPal:

1. Selecione a exibição de loja na **[!UICONTROL Scope]** menu suspenso, para o qual você deseja ativar um método de pagamento.
1. Para alterar o nome do método de pagamento, como mostrado durante o check-out, edite o valor no **[!UICONTROL Checkout Title]** campo.
1. Para [definir a ação de pagamento](production.md#set-payment-services-as-payment-method), alternar **[!UICONTROL Payment action]** para `Authorize` ou `Authorize and Capture`.
1. Use os seletores de alternância para ativar ou desativar [!DNL PayPal smart button] recursos de exibição:
   - **[!UICONTROL Show PayPal buttons on product detail page]**
   - **[!UICONTROL Show PayPal buttons in mini-cart preview]**
   - **[!UICONTROL Show PayPal buttons on cart page]**
   - **[!UICONTROL Show PayPal Pay Later button]**
   - **[!UICONTROL Show PayPal Pay Later message]**
   - **[!UICONTROL Show Venmo button]**
   - **[!UICONTROL Show Apple Pay button]**

      >[!NOTE]
      >
      > Para usar o Apple Pay [deve ter uma conta de desenvolvedor do Apple](test-validate.md#test-in-sandbox-environment) (completo com informações falsas de cartão de crédito e faturamento) para testá-lo. Quando estiver pronto para usar o Apple Pay na sandbox *ou* modo de produção, após concluir qualquer [teste e validação](test-validate.md), entre em contato com seu representante de vendas para ativá-lo em sua(s) loja(s) ativa(s).

      À medida que você ativa/desativa a visibilidade dos botões de pagamento ou da mensagem Pagamento PayPal Mais Tarde, uma visualização dessa configuração é exibida na parte inferior da página Configurações.

1. Para ativar o modo de depuração, alterne a função **[!UICONTROL Debug Mode]** seletor.
1. Clique em **[!UICONTROL Save]**.

   Se você tentar sair dessa exibição sem salvar as alterações, será exibido um modal que solicitará que você descarte as alterações, continue a editar ou salve as alterações.

1. Navegar para **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

#### Opções de configuração

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Title] | exibição de loja | Adicione o texto a ser exibido como o título para esta opção de pagamento na exibição Método de Pagamento durante o check-out. Opções: campo de texto |
| [!UICONTROL Payment Action] | site | O [ação de pagamento](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target=&quot;_blank&quot;} para o método de pagamento especificado. Opções: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Show PayPal buttons on product detail page] | exibição de loja | Ativar ou desativar [!DNL PayPal Smart Buttons] na página de detalhes do produto. Opções: [!UICONTROL  Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons in mini-cart preview] | exibição de loja | Ativar ou desativar [!DNL PayPal Smart Buttons] na visualização do minicarrinho. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal buttons on cart page] | exibição de loja | Ativar ou desativar [!DNL PayPal Smart Buttons] na página do carrinho. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later button] | exibição de loja | Ative ou desative a aparência da opção de pagamento posterior, onde os botões de pagamento são exibidos. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show PayPal Pay Later Message] | site | Ative ou desative as mensagens Pagar mais tarde no carrinho de compras, na página do produto, no minicarrinho e durante o fluxo de finalização. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Venmo button] | exibição de loja | Ative ou desative a opção de pagamento Venmo, onde os botões de pagamento são exibidos. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Show Apple Pay button] | exibição de loja | Ative ou desative a opção Apple Pay payment , onde os botões de pagamento são exibidos. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Debug Mode] | site | Ative ou desative o Modo de depuração. Opções: [!UICONTROL Yes] / [!UICONTROL No] |

### Estilo do botão

Você também pode configurar o _[!UICONTROL Button style]_opções dos botões inteligentes PayPal:

1. Para alterar o **[!UICONTROL Layout]**, selecione `Vertical` ou `Horizontal`.

   >[!NOTE]
   >
   > Se o estilo do botão estiver configurado como `Horizontal` e a sua loja está configurada para mostrar vários botões inteligentes do PayPal, você só pode ver dois botões exibidos na página do produto, na página de check-out e no minicarrinho, e um botão exibido no carrinho.

1. Para ativar o slogan em um layout horizontal, alterne a **[!UICONTROL Show tagline]** seletor.
1. Para modificar o **[!UICONTROL Color]**, selecione a opção de cor desejada.
1. Para modificar o **[!UICONTROL Shape]**, selecione `Pill` ou `Rectangle`.
1. Para ativar o seletor de altura do botão, alterne a **[!UICONTROL Responsive button height]** seletor.
1. Para modificar o **[!UICONTROL Label]**, selecione a opção de rótulo desejada.

   À medida que você altera as opções de configuração para layout, cor, forma, altura e rótulo, uma visualização dessa configuração é exibida na parte inferior da página Configurações.

1. Clique em **[!UICONTROL Save]**.

   Se você tentar sair dessa exibição sem salvar as alterações, será exibido um modal que solicitará que você descarte as alterações, continue a editar ou salve as alterações.

1. Navegar para **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

Você pode configurar [!DNL PayPal Smart Buttons] estilo [na configuração herdada em Admin](configure-admin.md#configure-paypal-smart-buttons) ou aqui em [!DNL Payment Services Home]. Consulte [Guia de estilo de botões do PayPal](https://developer.paypal.com/docs/checkout/standard/customize/buttons-style-guide/) para obter mais informações sobre as opções.

#### Opções de configuração

| Campo | Escopo | Descrição |
|--- |--- |--- |
| [!UICONTROL Layout] | Exibição da loja | Defina o estilo do layout para botões de pagamento. Opções: [!UICONTROL Vertical] / [!UICONTROL Horizontal] |
| [!UICONTROL Tagline] | Exibição da loja | Ativar/desativar slogan. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Color] | Exibição da loja | Defina a cor dos botões de pagamento. Opções: [!UICONTROL Blue] / [!UICONTROL Gold] / [!UICONTROL Silver] / [!UICONTROL White] / [!UICONTROL Black] |
| [!UICONTROL Shape] | Exibição da loja | Defina a forma dos botões de pagamento. Opções: [!UICONTROL Rectangular] / [!UICONTROL Pill] |
| [!UICONTROL Responsive Button Height] | Exibição da loja | Define se os botões de pagamento usam uma altura padrão. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Height] | Exibição da loja | Defina a altura dos botões de pagamento. Valor padrão: nenhum |
| [!UICONTROL Label] | Exibição da loja | Defina o rótulo que aparece nos botões de pagamento. Opções: [!UICONTROL PayPal] / [!UICONTROL Checkout] / [!UICONTROL Buynow] / [!UICONTROL Pay] / [!UICONTROL Installment] |

## Usar várias contas do PayPal

Em Serviços de Pagamento, você pode usar várias contas do PayPal dentro de **one** conta comercial no nível do site. Por exemplo, se você estiver operando sua(s) loja(s) em vários países (que usam diferentes [moedas](https://docs.magento.com/user-guide/stores/currency.html)) ou deseja usar o Adobe Commerce para algumas partes de sua empresa, mas não *all*, você pode configurar sua conta comercial para usar várias contas PayPal.

Consulte [Site, Loja e Exibir Escopo](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) para obter mais informações sobre a hierarquia de sites, lojas e visualizações de loja.

Seu representante de vendas pode criar um novo [escopo](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) para sua conta comercial e o site adicional com o PayPal, de modo que qualquer um dos botões do PayPal configurados para serem exibidos apareça em seu site. Entre em contato com seu representante de vendas para obter ajuda com o uso de várias contas PayPal para seus sites.
