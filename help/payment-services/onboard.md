---
title: Integrado [!DNL Payment Services]
description: Conecte sua instância com [!DNL Payment Services] concluindo algumas etapas de integração.
role: User
level: Intermediate
exl-id: 1ee8c660-0941-4378-a1d7-ae45de3de211
source-git-commit: bfb2b6632fe494d6e392c214f5e3f5a11930c0b2
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Integrado [!DNL Payment Services]

Para começar a usar [!DNL Payment Services] para o Adobe Commerce e o Magento Open Source, você deve concluir algumas etapas de integração para conectar sua instância ao recurso de pagamentos.

## Fluxo de integração

![Fluxo de integração](assets/onboarding-diagram.svg)

Este diagrama de fluxo de integração mostra o processo geral de integração [!DNL Payment Services].

Após concluir a integração para sandbox ou pagamentos em tempo real, o relatório financeiro é acessível a partir de [!DNL Payment Services] em Admin.

Se a sandbox e os pagamentos ao vivo estiverem integrados e ativados, você poderá alternar facilmente entre esses modos do [!DNL Payment Services] em casa.

## Pré-requisitos

Para usar [!DNL Payment Services], você deve ter o seguinte disponível para sua instância:

* Módulo Conector de serviços
* Módulo de ID de serviços
* Chaves da API

Os módulos do Conector de serviços e ID de serviços são instalados automaticamente durante a [instalação de [!DNL Payment Services]](install.md). Quando a instalação estiver concluída, você poderá ver uma nova seção nas configurações (**[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**) ao expandir **[!UICONTROL Services]**—**[!UICONTROL Commerce Services Connector]**.

Para saber como criar ou acessar as chaves da API, consulte [Credenciais da API](#obtain-api-credentials).

## Etapas de integração

1. [Instale o [!DNL Payment Services] extensão](install.md#get-payment-services).
1. [Obter credenciais da API](connect.md#obtain-api-credentials).
1. [Conecte sua instância](connect.md#configure-commerce-services) para Commerce Services. Essa conexão deve ser concluída somente uma vez por instância do Commerce.
1. [Configurar o serviço de sandbox](sandbox.md#enable-sandbox-testing) (ou, em alternativa, proceder a [permitir pagamentos em tempo real](sandbox.md#enable-live-payments) se tiver testado a funcionalidade em outro ambiente) com uma conta de processamento de pagamento PayPal de teste.
1. [Definir [!DNL Payment Services] como seu método de pagamento](production.md#set-payment-services-as-payment-method), no modo sandbox, para iniciar o processamento de pagamentos de teste.
1. [Solicitar direitos de pagamento](production.md#request-payments-entitlement-from-adobe) para permitir a integração ao vivo.
1. [Integração completa de merchant](production.md#complete-merchant-onboarding) para ativar pagamentos ao vivo para seus sites do Commerce.
1. [Obtenha seus [!DNL Payment Services] ID de Merchant](production.md#configure-pricing-tier) e enviá-lo para Vendas para configurar o nível de preços correto.
1. [Habilitar [!DNL Payment Services] no modo Online](production.md#enable-live-payments) para começar a processar pagamentos em tempo real.
1. Pagamentos de Teste, em ambos [sandbox](sandbox.md#test-in-sandbox-environment) e [produção](production.md#test-in-production) ambientes .

>[!NOTE]
>
>Se você não configurar os Commerce Services no Admin (etapa 3), não poderá configurar sandbox ou pagamentos em tempo real.

## Solução de problemas

* [Solução de problemas [!DNL Payment Services] instalação](https://support.magento.com/hc/en-us/articles/4406603542541)
* [Conta de sandbox PayPal não verificada](https://support.magento.com/hc/en-us/articles/4406954952461)
* [Atrasado [!DNL Payment Services] dados do relatório](https://support.magento.com/hc/en-us/articles/4406114741517)
* [O cartão de crédito de teste falha com o PayPal ao processar pagamentos em um ambiente de sandbox](https://support.magento.com/hc/en-us/articles/5201041963917)
