---
title: Configure o [!DNL Quick Checkout] para extensão do Adobe Commerce
description: Saiba mais sobre as opções de configuração do [!DNL Quick Checkout] e como integrar e configurar a extensão com êxito.
exl-id: 892e04dc-17d6-45e9-b2ab-c7a0735a75bc
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# [!DNL Quick Checkout] Configurações

[!DNL Quick Checkout] O para Adobe Commerce e Magento Open Source fornece uma visualização de configuração com todas as informações necessárias para configurar a extensão.

Para acessar essas definições de configuração:

1. No _Admin_ barra lateral, vá para **Lojas** > _Configurações_ > **Configuração**.
1. No painel esquerdo, expanda **Vendas** e selecione **Check-out**.

   ![Check-out rápido](assets/config-new-logo-view.png)

Consulte a [Integração](../quick-checkout/onboarding.md) tópico para obter mais informações sobre como configurar a variável [!DNL Quick Checkout] para Adobe Commerce.

## Habilitar extensão

![Check-out rápido](assets/enable-method.png)

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Enable] | site | Ativar ou desativar [!DNL Quick Checkout] para o seu site. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Method] | site | Defina o método ou ambiente para o seu [!DNL Quick Checkout]. Opções: [!UICONTROL Sandbox] / [!UICONTROL Production] |

{style="table-layout:auto"}

## Credenciais da conta

![Check-out rápido](assets/account-creds.png)

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL API key] | site | Uma chave privada usada pelo back-end para interagir com o [!DNL Bolt] APIs. |
| [!UICONTROL Publishable key] | site | Uma chave usada pelo front-end para interagir com o [!DNL Bolt] APIs. |
| [!UICONTROL Signing secret] | site | Usado para verificação de assinatura em solicitações recebidas do [!DNL Bolt]. |

{style="table-layout:auto"}

## Configurações de serviço

![Check-out rápido](assets/service-settings.png)

| Campo | Escopo | Descrição |
|---|---|---|
| [!UICONTROL Title] | exibição de loja | Adicione o texto para exibição como o título desta opção de pagamento na exibição de Método de Pagamento durante a finalização da compra. Opções: [!UICONTROL text field] |
| [!UICONTROL Payment Action] | site | A variável [ação de pagamento](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html#payment-actions){target="_blank"} para o método de pagamento especificado. Opções: [!UICONTROL Authorize] / [!UICONTROL Authorize and Capture] |
| [!UICONTROL Debug Mode] | site | Ative ou desative o Modo de depuração. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Enable checkout tracking] | site | Defina se o Adobe Commerce permite que as informações de rastreamento de check-out sejam compartilhadas com o Bolt. Ativado por padrão. Se desativado, os relatórios serão afetados. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Next Stage After Login Mode] | site | Altere o fluxo de navegação depois que o cliente estiver conectado. Opções: [!UICONTROL Payment] / [!UICONTROL Shipping] |
| [!UICONTROL Automatic Login Enabled] | site | Definir se [!DNL Quick Checkout] permite o logon automático durante o check-out. Ativado por padrão. Opções: [!UICONTROL Yes] / [!UICONTROL No] |
| [!UICONTROL Automatic Login Network] | site | Selecione a rede na qual o cliente faz logon automaticamente. Parafuso ativado por padrão. Opções: [!UICONTROL Bolt + Merchant] / [!UICONTROL Bolt] |

{style="table-layout:auto"}
