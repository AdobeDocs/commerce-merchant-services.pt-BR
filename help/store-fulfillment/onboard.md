---
title: Visão geral de integração para serviços de fornecimento da loja
description: '[!DNL Live Search] fluxo de integração, requisitos do sistema, limites e limitações.'
role: User, Admin
level: Intermediate
exl-id: f8e403ac-9bbd-4ea2-b209-9b1a8d1e32a2
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# Visão geral de integração do fornecimento da loja

Introdução a [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] ao instalar, configurar e ativar os seguintes componentes:

- **Extensão de Atendimento da Loja**-Instale e configure essa extensão de terceiros na sua instância do Adobe Commerce. Após a instalação, você pode configurar e gerenciar a solução Store Fulfillment do Administrador para oferecer suporte [!DNL buys online, pickup in store] (BOPIS) na vitrine do Commerce.

   ![[!DNL Store Fulfillment Service] configuração na exibição Admin](assets/store-fulfillment-admin-home.png)

- **Conta de Atendimento da Loja**-Durante o processo de habilitação, um Gerente de Conta cria sua conta de Atendimento de Loja e fornece as informações e credenciais da conta. Essas credenciais são necessárias para habilitar a conexão entre o Adobe Commerce e a solução Store Fulfillment.

- **Aplicativo de assistência da loja**—Fornece às lojas associadas um fluxo de trabalho completo de atendimento de loja para gerenciar pedidos de BOPIS de dispositivos móveis. A Store Associates pode baixar e instalar o Walmart [!DNL Store Assist] para dispositivos iOS e Android™. O processo de integração de aplicativos é gerenciado pelo Centro de clientes de tecnologias do Walmart Commerce como um processo separado. No entanto, [algumas configurações de aplicativo](user-setup.md) são concluídas no Administrador do Adobe Commerce.

   | Aplicativo de Assistência da Loja - Exibição de introdução | Aplicativo Store Assist — visualização Módulos |
   |-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
   | ![[!DNL Store Assist App Getting Started] exibir no dispositivo móvel](assets/store-assist-get-started-small.png) | ![[!DNL Store Assist App Orders view] no dispositivo móvel](assets/store-assist-orders-small.png) |

## Etapas de provisionamento

- **Inscrever-se para[!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies]**-Preencha o formulário de inscrição em [business.adobe.com](https://business.adobe.com/resources/store-fulfillment.html)ou entre em contato com o Gerente de conta da Adobe Commerce para obter assistência.

- **Iniciar a solicitação de provisionamento para Atendimento da Loja**-Preencha o formulário de entrada fornecido pelo Gerente de conta para fornecer as informações necessárias para iniciar o processo de provisionamento.

- **Obter credenciais da conta de Atendimento da Loja**-Depois que sua conta de Atendimento da Loja for criada para você, você receberá as credenciais necessárias para integrar a solução de Atendimento da Loja à Adobe Commerce.

- **[Baixe o código-fonte para instalar o [!DNL Store Fulfillment] extensão](install.md)**

## Etapas de integração

1. [Instalar a extensão Store Fulfillment para Adobe Commerce](install.md).

1. Do Administrador, [habilitar a solução](enable-general.md).

1. [Configurar a extensão Store Fulfillment com o Administrador do Adobe Commerce](service-config-settings-overview.md).

1. [Conecte o [!DNL Store Fulfillment] serviço usando as credenciais de Atendimento da Loja fornecidas a você](connect-set-up-service.md).

1. [Criar usuários e funções para o aplicativo Store Assist](user-setup.md).

1. [Baixar do Walmart [!DNL Store Assist] para o dispositivo desejado. O aplicativo está disponível no aplicativo Apple (iOS) e Google Play (Android™)](app-setup.md) lojas.

Após ter instalado, configurado, concluído a integração com êxito e ter acesso à [!DNL Store Assist] aplicativo, você pode [começar a criar pedidos e testar](test-and-deploy.md).
