---
title: '"Integrar a [!DNL Quick Checkout] para extensão do Adobe Commerce"'
description: '"Saiba como a função [!DNL Quick Checkout] pode beneficiar sua instância do Adobe Commerce e como integrar e configurar com êxito a extensão."'
exl-id: 8caf746c-e31b-4331-8b0d-ea0f1e545bdd
source-git-commit: ac55bf6354c8f5569ad83dc0ac2671b34c98d303
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# [!DNL Quick Checkout] integração

Para começar a usar o [!DNL Quick Checkout] para a extensão Adobe Commerce, você deve concluir algumas etapas de integração para conectar sua instância com nossa funcionalidade de check-out.

1. [Obter extensão](#get-extension).
1. [Criar uma conta comercial de produção ou sandbox com [!DNL Bolt]](#create-account-with-bolt). Forneça todas as informações necessárias para verificar sua identidade.
1. [Forneça a [!DNL API Key] e [!DNL Publishable Key] gerado em [!DNL Bolt]](#obtain-api-credentials).
1. [Configure um provedor de pagamento no [!DNL Bolt] account](#configure-payment-providers).
1. [Defina a lista suspensa Ativar como Sim](#enable-extension) para ativar a extensão.
1. [Definir as configurações do serviço](#complete-admin-configuration) para configurar o [!DNL Quick Checkout] extensão.
1. [Clique no botão Salvar configuração](#enable-live-quick-checkout) para ativar a extensão.

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

Para usar o [!DNL Quick Checkout] é necessário [!DNL Bolt] chaves exclusivas. Obtenha o seguinte [!DNL API keys] navegando até **Desenvolvedores** > **API** > **Teclas** no **Painel Bolt Merchant**.

- [!DNL API key]: Uma chave privada usada pelo back end para interagir com o [!DNL Bolt] APIs.
- [!DNL Publishable key]: Uma chave usada pelo front-end para interagir com [!DNL Bolt] APIs.

Consulte a [[!DNL Bolt] detalhes do ambiente](https://help.bolt.com/developers/references/environment-details/#about-keys)página {target=&quot;_blank&quot;} para saber mais sobre a API e [!DNL Publishable keys] para [!DNL Quick Checkout] extensão.

>[!CAUTION]
>
> Você deve criar [!DNL API keys] para ambientes de sandbox e produção.

## Configurar provedores de pagamento

Para conectar seu provedor de serviços de pagamento, siga as etapas descritas na [configuração do processador](https://help.bolt.com/integrations/adobe-quick-checkout/set-up/)desenvolvedor {target=&quot;_blank&quot;} [!DNL Bolt] página.

## Habilitar extensão

1. No _Administrador_ barra lateral, vá para **Lojas** > _Configurações_ > **Configuração**.
1. No painel esquerdo, expanda **Vendas** e selecione **Check-out**.

   ![Check-out rápido](assets/admin-view.png)

1. No [!DNL Quick Checkout] exibir, definir **Habilitar** para `Yes`.
1. Selecione o método (sandbox ou produção) a ser usado.

   - Sandbox para fins de teste e desenvolvimento
   - Produção para processar transações com o processador de pagamento ao vivo

1. Valide as credenciais após fornecer sua API exclusiva e [!DNL Publishable keys].

>[!CAUTION]
>
> Você deve fornecer API exclusiva e [!DNL Publishable keys] antes de habilitar a extensão, os clientes verão um formulário de pagamento e não poderão fazer uma ordem.

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

## Obter ajuda

O processo de integração foi projetado para orientá-lo pelas etapas necessárias para configurar e ativar o [!DNL Express Checkout] funcionalidade. Entre em contato com a equipe de engenharia da Adobe Commerce por meio do Slack atribuído [Canal de programas Adobe Beta](http://adobe-beta-programs.slack.com/) canal para obter assistência.

Consulte a [testar e validar](../quick-checkout/testing.md) para obter mais informações.
