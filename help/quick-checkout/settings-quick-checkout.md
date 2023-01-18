---
title: Configure o [!DNL Quick Checkout] para extensão do Adobe Commerce
description: Saiba mais sobre as opções de configuração do [!DNL Quick Checkout] e como integrar e configurar com êxito a extensão.
exl-id: 892e04dc-17d6-45e9-b2ab-c7a0735a75bc
source-git-commit: 1b2847b71e2a6aa843de2e73dfe5f3ad295c7b5f
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Quick Checkout] configurações

[!DNL Quick Checkout] para Adobe Commerce e Magento Open Source fornece uma visualização de configuração com todas as informações necessárias para configurar a extensão.

Para acessar essas configurações:

1. No _Administrador_ barra lateral, vá para **Lojas** > _Configurações_ > **Configuração**.
1. No painel esquerdo, expanda **Vendas** e selecione **Check-out**.

   ![Check-out rápido](assets/configuration-view.png)

Consulte a [Integração](../quick-checkout/onboarding.md) para obter mais informações sobre como configurar o [!DNL Quick Checkout] para Adobe Commerce.

## Habilitar extensão

![Check-out rápido](assets/enable-method.png)

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Enable] | site | Ativar ou desativar [!DNL Quick Checkout] para o seu site. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | site | Defina o método ou o ambiente para [!DNL Quick Checkout]. Opções: [!UICONTROL Sandbox] / [!UICONTROL Production] |

{style=&quot;table-layout:auto&quot;}

## Credenciais da conta

![Check-out rápido](assets/account-creds.png)

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL API key] | site | Uma chave privada usada pelo back end para interagir com o [!DNL Bolt] APIs. |
| [!UICONTROL Publishable key] | site | Uma chave usada pelo front-end para interagir com [!DNL Bolt] APIs. |
| [!UICONTROL Signing secret] | site | Usado para verificação de assinatura em pedidos recebidos de [!DNL Bolt]. |

{style=&quot;table-layout:auto&quot;}

## Configurações de serviço

![Check-out rápido](assets/service-settings.png)

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Title] | exibição de loja | Adicione o texto para exibição como o título para esta opção de pagamento na exibição Método de Pagamento durante o check-out. Opções: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | site | O [ação de pagamento](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} para o método de pagamento especificado. Opções: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | site | Ative ou desative o Modo de depuração. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Enable checkout tracking] | site | Defina se o Adobe Commerce permite que as informações de rastreamento de check-out sejam compartilhadas com Bolt. Ativado por padrão. Se estiver desativado, os relatórios serão afetados. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Next Stage After Login Mode] | site | Altere o fluxo de navegação depois que o cliente estiver conectado. Opções: [!UICONTROL Payment] / [!UICONTROL Shipping] |
| [!UICONTROL Automatic Login Enabled] | site | Definir se [!DNL Quick Checkout] O permite o logon automático durante o check-out. Ativado por padrão. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Automatic Login Network] | site | Selecione a rede em que o cliente faz logon automaticamente. Ativar Bolt por padrão. Opções: [!UICONTROL Bolt + Merchant] / [!UICONTROL Bolt] |

{style=&quot;table-layout:auto&quot;}
