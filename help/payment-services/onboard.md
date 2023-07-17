---
title: Integrado [!DNL Payment Services]
description: Conecte sua instância com o [!DNL Payment Services] concluindo algumas etapas de integração.
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
feature: Payments, Checkout, Integration
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# Integrado [!DNL Payment Services]

Para começar a usar o [!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source], você deve concluir algumas etapas de integração para conectar sua instância à funcionalidade de pagamentos.

## Fluxo de integração

![Fluxo de integração](assets/onboarding-diagram.svg)

Este diagrama de fluxo de integração mostra o processo geral de integração [!DNL Payment Services].

Após concluir a integração para sandbox ou pagamentos em tempo real, os relatórios financeiros podem ser acessados em [!DNL Payment Services] em Admin.

Se os pagamentos sandbox e em tempo real forem integrados e ativados, é possível alternar facilmente entre esses modos do [!DNL Payment Services] Início.

## Pré-requisitos

Para utilizar [!DNL Payment Services], você deve ter o seguinte disponível para sua instância:

* Módulo do Conector de Serviços
* Módulo de ID de serviços
* Chaves de API

Os módulos do Conector de serviços e da ID de serviços são instalados automaticamente durante [instalação de [!DNL Payment Services]](install.md). Quando a instalação estiver concluída, você poderá ver uma nova seção nas definições de configuração (**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**) ao expandir **[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**.

Para saber como criar ou acessar suas chaves de API, consulte [Credenciais da API](#obtain-api-credentials).

## Etapas de integração

1. [Instale o [!DNL Payment Services] extensão](install.md#get-payment-services).
1. [Obter credenciais de API](connect.md#obtain-api-credentials).
1. [Conectar sua instância](connect.md#configure-commerce-services) para Commerce Services. Essa conexão deve ser concluída apenas uma vez por instância do Commerce.
1. [Configurar o serviço de sandbox](sandbox.md#enable-sandbox-testing) (ou, em alternativa, [ativando pagamentos em tempo real](sandbox.md#enable-live-payments) se você tiver testado a funcionalidade em outro ambiente) com uma conta de processamento de pagamento do PayPal de teste.
1. [Definir [!DNL Payment Services] como sua forma de pagamento](production.md#set-payment-services-as-payment-method), no modo sandbox, para iniciar o processamento de pagamentos de teste.
1. [Solicitar direitos a pagamentos](production.md#request-payments-entitlement-from-adobe) para ativar a integração em tempo real.
1. [Integração completa do comerciante](production.md#complete-merchant-onboarding) para ativar os pagamentos em tempo real para seus sites do Commerce.
1. [Obtenha o seu [!DNL Payment Services] ID do comerciante](production.md#configure-pricing-tier) e entregue-o ao Sales para configurar o tipo de preço correto.
1. [Ativar [!DNL Payment Services] no modo Online](production.md#enable-live-payments) para iniciar o processamento de pagamentos em tempo real.
1. Testar Pagamentos, em ambos [sandbox](sandbox.md#test-in-sandbox-environment) e [produção](production.md#test-in-production) ambientes.

>[!NOTE]
>
>Se você não configurar seus Commerce Services no Administrador (etapa 3), não poderá configurar sandbox ou pagamentos em tempo real.

## Solução de problemas

* [Solução de problemas [!DNL Payment Services] instalação](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html?lang=en)
* [Conta de sandbox do PayPal não verificada](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html)
* [Atrasado [!DNL Payment Services] dados do relatório](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html)
* [O cartão de crédito de teste falha no PayPal ao processar pagamentos em um ambiente de sandbox](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html?lang=en)
