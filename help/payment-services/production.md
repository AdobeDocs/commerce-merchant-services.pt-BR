---
title: Habilitar [!DNL Payment Services] para produção
description: Conclua o processo de integração habilitando [!DNL Payment Services] para produção.
exl-id: 3b1269e8-127b-47f8-9738-9722a5737c63
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '702'
ht-degree: 0%

---

# Habilitar [!DNL Payment Services] para produção

Você pode colocar o serviço em produção e concluir a [processo de integração](onboard.md), de acordo com as etapas neste tópico, depois de:

* [Instalar](install.md) a extensão dos serviços de pagamento
* [Configurar e conectar](connect.md) sua instância
* [Configurar](sandbox.md) e [teste](test-validate.md) seu sandbox

## Definir [!DNL Payment Services] como método de pagamento

Depois de [configurar seus Commerce Services](connect.md#configure-commerce-services) e ativar [teste de sandbox](sandbox.md#enable-sandbox-testing) ou [pagamentos em direto](#enable-live-payments), você deve definir [!DNL Payment Services] como seu método de pagamento.

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Clique em **[!UICONTROL Enable Payment Services]**.

   Essa opção estará visível se você ainda não tiver configurado [!DNL Payment Services] como método de pagamento para um ou mais de seus sites.

   Você é direcionado para a área de configurações na exibição Início, com as opções relevantes expandidas (**[!UICONTROL Sales]** > **[!UICONTROL Payment Services]** > _[!UICONTROL Settings]_), onde você pode ativar a variável [!DNL Payment Services] opções como [método de pagamento](https://docs.magento.com/user-guide/configuration/sales/payment-methods.html){target="_blank"}.

1. Em _[!UICONTROL General Configuration]_, definir **[!UICONTROL Enable]**para `Yes`.
1. Definir **[!UICONTROL Payment Action]** para ambos _[!UICONTROL Credit Card Fields]_e_[!UICONTROL PayPal Smart Buttons]_, para uma das seguintes opções:

   | Configuração | Descrição |
   |---|---|
   | `Authorize` | Aprova a compra e coloca os fundos em espera. O montante não é retirado até ser &quot;capturado&quot; pelo comerciante. |
   | `Authorize and Capture` | Aprova a compra e o comerciante &quot;captura&quot; os fundos. |

1. Clique em **[!UICONTROL Save]**.
1. Clique em **[!UICONTROL Go to Payment Services]** para ser direcionado de volta ao [!DNL Payment Services] Casa.
1. [Limpar o cache](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   A limpeza deve ser feita após cada alteração de configuração.

Consulte [Configurar serviços de pagamento](settings.md) para obter mais informações sobre como configurar os Campos do cartão de crédito e os Botões inteligentes do PayPal.

## Integração completa de merchant

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Clique em **[!UICONTROL Live onboarding]**.

   Essa opção ficará visível se você ainda não tiver concluído a integração ao vivo para o [!DNL Payment Services].

   Você é apresentado com uma janela PayPal.

1. Continue com o fluxo do PayPal, usando suas credenciais de conta do PayPal (não suas credenciais de conta da sandbox) ou inscreva-se para obter uma nova conta do PayPal.
1. Na barra lateral Admin, acesse **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**

   O _[!UICONTROL Live onboarding]_O botão não está mais visível e você vê um &quot;[!UICONTROL Live payments pending]&quot; caixa de texto.

   Nessa caixa de texto, você também pode ser solicitado a confirmar seu endereço de email com o PayPal para concluir a integração.

1. Se for solicitado a confirmar o endereço de email, verifique o email para a mensagem de confirmação enviada do PayPal e clique em para confirmar o endereço de email.
1. Na barra lateral Admin, acesse **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Atualize a janela do navegador.

   Quando a integração do comerciante PayPal for aprovada, você deverá ver uma notificação informando que seu sistema de pagamento está no modo sandbox e não está processando pagamentos em tempo real.

   >[!IMPORTANT]
   >
   >Se você revogar o consentimento para [!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source] para processar seus pagamentos (nas configurações da conta PayPal), os pedidos em sua loja não podem ser processados por [!DNL Payment Services]. Na Página inicial dos Serviços de Pagamento, é exibido um alerta sobre o consentimento revogado.

## Solicitar direitos de pagamento do Adobe

Para habilitar a integração ao vivo, você deve solicitar o direito de pagamento do Adobe:

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Clique em **[!UICONTROL Get Live Payments]** em seu [!DNL Payment Services] Casa.

   ![Solicitar direitos](assets/request-entitlements.png)

1. Preencha o formulário.
1. Um membro da equipe de vendas entrará em contato com você.

Como alternativa, você pode solicitar direitos de pagamento de Adobe em [business.adobe.com](https://business.adobe.com/resources/payment-services.html).

>[!IMPORTANT]
>
>**Integração ao vivo** não é acessível até que o direito ao pagamento tenha sido aprovado.

## Configurar camada de preços

Para obter as [!DNL Payment Services] _ID de Merchant_:


1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Na exibição Início, clique em **[!UICONTROL Settings]**. Consulte [Início](payments-home.md) para obter mais informações.
1. Selecione o _ID de Merchant_ e envie-o ao seu representante de vendas, que configurará o nível de preços correto.

## Ativar pagamentos em tempo real

A _ID de comerciante de produção_ é gerado automaticamente e preenchido no [configuração](configure-admin.md). Não altere ou altere essa ID.

Para permitir pagamentos em tempo real:

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL Payment Services]**.
1. Na página inicial, clique em **[!UICONTROL Settings]** na parte superior direita da página. Consulte [Início](payments-home.md) para obter mais informações.
1. No _[!UICONTROL General Configuration]_conjunto de seções **[!UICONTROL Payment mode]**para `Production`.
1. Clique em **[!UICONTROL Save]**.
1. [Limpar o cache](https://docs.magento.com/user-guide/system/cache-management.html){target="_blank"}.

   >[!IMPORTANT]
   >
   >Se você não limpar o cache, os clientes não poderão ver as opções de pagamento PayPal durante o check-out.

Se você voltar para [!DNL Payment Services] Home, a mensagem Modo de pagamento Sandbox não será mais exibida porque você está processando pagamentos em tempo real.

Consulte [Configurar no Administrador](configure-admin.md) para opções de configuração herdada.

>[!IMPORTANT]
>
>Se você revogar o consentimento para [!DNL Payment Services] para processar seus pagamentos (nas configurações da conta PayPal), os pedidos em sua loja não podem ser processados por [!DNL Payment Services]. Se quiser reativar o processamento do pagamento, conclua a integração novamente. Na Página inicial dos Serviços de Pagamento, é exibido um alerta sobre o consentimento revogado.

## Teste na produção

É altamente recomendável testar Pagamentos em produção, com cartões de crédito reais e bancos, antes de expor essa funcionalidade aos compradores.

Consulte [Testar e validar](test-validate.md) para obter mais informações.
