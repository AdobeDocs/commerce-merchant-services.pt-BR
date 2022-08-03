---
title: '"Integrar a [!DNL Quick Checkout] para extensão do Adobe Commerce"'
description: '"Saiba como a função [!DNL Quick Checkout] pode beneficiar sua instância do Adobe Commerce e como integrar e configurar com êxito a extensão."'
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: 70f7772765dd66c8db779d29d4b661edb7d0c64a
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 0%

---

# [!DNL Quick Checkout] integração

Para começar a usar o [!DNL Quick Checkout] para a extensão Adobe Commerce, você deve concluir algumas etapas de integração para conectar sua instância com nossa funcionalidade de check-out.

1. [Obter extensão](#get-extension).
1. [Criar uma conta comercial de produção ou sandbox com [!DNL Bolt]](#create-account-with-bolt). Forneça todas as informações necessárias para verificar sua identidade.
1. [Forneça a [!DNL API Key] e [!DNL Publishable Key]](#obtain-api-credentials) gerado em [!DNL Bolt].
1. [Configure um provedor de pagamento no [!DNL Bolt] account](#configure-payment-providers).
1. [Defina a lista suspensa Ativar como Sim](#enable-extension) para ativar a extensão.
1. [Definir as configurações do serviço](#complete-admin-configuration) para configurar o [!DNL Quick Checkout] extensão.
1. [Clique no botão Salvar configuração](#enable-live-quick-checkout) para ativar a extensão.
1. Alterar escopo para **Site principal** e [clique em Configurar URL de retorno](#check-shopper-valid-account) botão.

>[!NOTE]
>
> Se você não configurar o [!DNL Bolt] contas que não é possível configurar os ambientes de sandbox ou de produção.

## Pré-requisitos

Para usar o [!DNL Quick Checkout], você deve ter o seguinte disponível para [!DNL Bolt]:

- Fornecedores de pagamento suportados
- Conta de produto e produção em [!DNL Bolt]
- API e [!DNL Publishable key] gerado em [!DNL Bolt]

Consulte a [pré-requisitos](../quick-checkout/prerequisites.md) para obter mais informações.

Consulte [Credenciais da API](#obtain-api-credentials) para saber como criar ou acessar seu [!DNL API keys] para sua instância.

## Obter extensão

Consulte a [instalar](../quick-checkout/install.md) para obter informações detalhadas sobre como obter a extensão do .

## Criar conta com [!DNL Bolt]

Antes de configurar o [!DNL Quick Checkout] no administrador do Adobe Commerce, é necessário criar um [sandbox](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} e [produção](https://merchant.bolt.com/register){target=&quot;_blank&quot;} contas comerciais em [!DNL Bolt]. Forneça todos os detalhes necessários para criar uma conta no [!DNL Bolt].

Consulte a [testar e validar](../quick-checkout/testing.md) para obter mais informações.

## Obter credenciais da API

Para usar o [!DNL Quick Checkout] é necessário [!DNL Bolt] chaves exclusivas e [!DNL signing secret]. Obtenha o seguinte [!DNL API keys] navegando até **Desenvolvedores** > **API** > **Teclas** no **Painel Bolt Merchant**.

- [!DNL API key]: Uma chave privada usada pelo back end para interagir com o [!DNL Bolt] APIs.
- [!DNL Publishable key]: Uma chave usada pelo front-end para interagir com [!DNL Bolt] APIs.
- [!DNL Signing secret]: Usado para verificação de assinatura em pedidos recebidos de [!DNL Bolt].

   ![Check-out rápido](assets/account-credentials.png)

Consulte a [[!DNL Bolt] detalhes do ambiente](https://help.bolt.com/developers/references/environment-details/#about-keys)página {target=&quot;_blank&quot;} para saber mais sobre chaves e assinar segredo de [!DNL Bolt] para [!DNL Quick Checkout] extensão.

>[!CAUTION]
>
> Você deve criar [!DNL API keys] para ambientes de sandbox e produção.

## Configurar provedores de pagamento

Para conectar seu provedor de serviços de pagamento, siga as etapas descritas na [configuração do processador](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/)desenvolvedor {target=&quot;_blank&quot;} [!DNL Bolt] página.

## Habilitar extensão

1. No _Administrador_ barra lateral, vá para **Lojas** > _Configurações_ > **Configuração**.
1. No painel esquerdo, expanda **Vendas** e selecione **Check-out**.
1. No [!DNL Quick Checkout] exibir, definir **Habilitar** para `Yes`.

![Check-out rápido](assets/quick-checkout-view-no-enable.png)

>[!CAUTION]
>
> Os campos de finalização rápida só ficam visíveis quando **Habilitar** está definida como `Yes`.

1. Selecione o método (sandbox ou produção) a ser usado.

   - Sandbox para fins de teste e desenvolvimento
   - Produção para processar transações com o processador de pagamento ao vivo

1. Valide as credenciais após fornecer sua API exclusiva e [!DNL Publishable keys].

![Check-out rápido](assets/quick-checkout-main-view.png)

>[!CAUTION]
>
> Você deve fornecer API exclusiva e [!DNL Publishable] antes de habilitar a extensão, caso contrário, os clientes verão um formulário de pagamento e não poderão fazer um pedido.

## Concluir configuração do administrador

1. No _Administrador_ barra lateral, navegue até **Lojas** > **Configuração** > **Check-out** para acessar a página de configuração geral do administrador de check-out .
1. No _Configurações de serviço_ , forneça todos os detalhes necessários para habilitar a extensão do .
1. Definir _Ação de pagamento_ para qualquer opção:

   - `Authorize`: Não capture a transação automaticamente após a autorização.
   - `Authorize and Capture`: Capture a transação automaticamente após a autorização.

Para obter mais informações sobre as opções de check-out padrão do Adobe Commerce, consulte [checkout](https://docs.magento.com/user-guide/configuration/sales/checkout.html) tópico.

## Ativar o Quick Checkout ativo

Para ativar o [!DNL Quick Checkout] para extensão Adobe Commerce:

1. Verifique se a variável [!UICONTROL Enable] a lista suspensa está definida como **Sim** para ativar a extensão.
1. Clique em **Salvar configuração**.

## Verificar conta válida do comprador

Para verificar se o comprador tem um [!DNL Bolt] conta:

1. Alterar o escopo para **Site principal**.
1. Clique no botão **Configurar URL de retorno** botão. Isso habilita [!DNL Bolt] para determinar se o comprador tem uma conta. Se o fizerem, a janela pop-up OTP será exibida.

>[!CAUTION]
>
> Alternar o escopo para a **Site principal** garante que o URL correto seja definido. Cada site pode ter vários domínios.

Consulte a [Site, Loja e Exibir Escopo](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings)Tópico {target=&quot;_blank&quot;} para obter mais informações sobre escopos no Adobe Commerce.

## Obter ajuda

O processo de integração foi projetado para orientá-lo pelas etapas necessárias para configurar e ativar o [!DNL Express Checkout] funcionalidade. Entre em contato com a equipe de engenharia da Adobe Commerce por meio do Slack atribuído [Canal de programas Adobe Beta](http://adobe-beta-programs.slack.com/) canal para obter assistência.

Consulte a [testar e validar](../quick-checkout/testing.md) para obter mais informações.
