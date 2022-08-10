---
title: Visão geral de integração para serviços de fornecimento de loja
description: '''[!DNL Live Search] fluxo de integração, requisitos do sistema, limites e limitações."'
role: User, Admin
level: Intermediate
exl-id: f8e403ac-9bbd-4ea2-b209-9b1a8d1e32a2
source-git-commit: 1fb22b4644d41ea5c60aead3fe2c455dfa3382f8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Visão geral de integração para o cumprimento da loja

Introdução a [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] configurando, configurando e habilitando os seguintes componentes:

- **Extensão de Arquivo de Cumprimento**-Instale e configure essa extensão de terceiros na instância do Adobe Commerce. Após a instalação, você pode configurar e gerenciar a solução Store Fulfillment do Administrador para oferecer suporte [!DNL buys online, pickup in store] (BOPIS) na loja de comércio.

   ![[!DNL Store Fulfillment Service] configuração na visualização Administração](assets/store-fulfillment-admin-home.png)

- **Conta de preenchimento da loja**-Durante o processo de ativação, um Gerente de conta cria sua conta de Atendimento à loja e fornece a você as informações e as credenciais da conta. Essas credenciais são necessárias para habilitar a conexão entre o Adobe Commerce e a solução de preenchimento da loja.

- **Aplicativo de assistência da loja**—Fornece associações de loja com um fluxo de trabalho completo de atendimento de loja para gerenciar pedidos BOPIS de dispositivos móveis. A Store Associates pode baixar e instalar o [!DNL Store Assist] para dispositivos iOS e Android™. O processo de integração de aplicativos é gerenciado pelo Centro de clientes de tecnologias Walmart como um processo separado. No entanto, [algumas configurações do aplicativo](user-setup.md) são concluídas pelo Administrador do Adobe Commerce.

   | Aplicativo de assistência de loja - exibição Introdução | Aplicativo de assistência da loja — exibição Módulos |
   |-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
   | ![[!DNL Store Assist App Getting Started] exibir em dispositivo móvel](assets/store-assist-get-started-small.png) | ![[!DNL Store Assist App Orders view] em dispositivo móvel](assets/store-assist-orders-small.png) |

## Etapas de provisionamento

- **Inscreva-se para[!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies]**-Preencha o formulário de inscrição em [business.adobe.com](https://business.adobe.com/resources/store-fulfillment.html)ou entre em contato com seu Gerente de conta da Adobe Commerce para obter assistência.

- **Iniciar a solicitação de provisionamento para o Cumprimento da Loja**-Preencha o formulário de entrada fornecido pelo Gerente de conta para fornecer as informações necessárias para iniciar o processo de provisionamento.

- **Obter as credenciais da conta de Cumprimento da Loja**-Depois que a conta de Atendimento da loja for criada para você, você receberá as credenciais necessárias para integrar a solução de Encerramento da loja com o Adobe Commerce.

- **[Baixe o código-fonte para instalar o [!DNL Store Fulfillment] extensão](install.md)**

## Etapas de integração

1. [Instalar a extensão de fornecimento de armazenamento para o Adobe Commerce](install.md).

1. Em Admin, [ativar a solução](enable-general.md).

1. [Configure a extensão de armazenamento de dados do administrador do Adobe Commerce](service-config-settings-overview.md).

1. [Conecte o [!DNL Store Fulfillment] usando as credenciais de Arquivo de Cumprimento fornecidas a você](connect-set-up-service.md).

1. [Criar usuários e funções para o aplicativo de assistência da loja](user-setup.md).

1. [Baixar o [!DNL Store Assist] aplicativo para o dispositivo desejado. O aplicativo está disponível no aplicativo Apple (iOS) e Google Play (Android™)](app-setup.md) lojas.

Após ter instalado, configurado, concluído a integração e ter acesso ao [!DNL Store Assist] app, você pode [comece a criar pedidos e a testar](test-and-deploy.md).
