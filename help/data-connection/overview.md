---
title: Visão geral do Guia
description: Saiba como integrar dados do Adobe Commerce ao Adobe Experience Platform usando o [!DNL Data Connection] extensão.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 1%

---

# [!DNL Data Connection] visão geral

>[!IMPORTANT]
>
>O conector Experience Platform foi renomeado para [!DNL Data Connection].

A variável [!DNL Data Connection] permite que os comerciantes do Adobe Commerce enviem [vitrine](events.md#storefront-events) e [back office](events.md#back-office-events) para a borda do Adobe Experience Platform, para que outros produtos da Adobe Experience Cloud, como o Adobe Analytics e o Adobe Journey Optimizer, possam usar esses dados do Commerce. Conectando os dados do Commerce a outros produtos na Adobe Experience Cloud, você pode executar tarefas como analisar o comportamento do usuário no site, executar testes AB e criar campanhas personalizadas.

[Eventos da loja](events.md#storefront-events) capturar interações do comprador, como `View Page`, `View Product`, `Add to Cart`, e [lista de requisições](events.md#b2b-events) informações (para os comerciantes B2B). [Back Office](events.md#back-office-events) os eventos capturam informações sobre o status de um pedido, como se um pedido foi feito, cancelado, reembolsado, enviado ou concluído. Os dados capturados não incluem informações de identificação pessoal (PII). Todos os identificadores de usuários, como IDs de cookies e endereços IP, são estritamente anônimos. [Saiba mais](https://www.adobe.com/privacy/experience-cloud.html).

A variável [!DNL Data Connection] A extensão do aparece no Administrador do Commerce em **Sistema** > Serviços > **[!DNL Data Connection]**.

![[!DNL Data Connection] exibição do administrador da extensão](assets/epc-adminui.png)

## Pré-requisitos {#prereqs}

Para usar o [!DNL Data Connection] extensão, você deve ter o seguinte:

- Adobe Commerce 2.4.3 ou mais recente
- Adobe ID e ID da organização
- [Camada de dados de clientes Adobe (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). A ACDL é necessária para coletar dados do evento da loja.
- Qualificações para outros produtos Adobe DX

## Etapas de integração

1. [Instalar](install.md) o [!DNL Data Connection] extensão.
1. [Fazer logon](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) para sua conta Adobe e [exibir para confirmar](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) sua ID da organização. A ID da organização é a ID associada à empresa de Experience Cloud provisionada. A ID é uma sequência de 24 caracteres alfanuméricos seguidos por (e deve incluir) `@AdobeOrg`.
1. [Criar ou atualizar](update-xdm.md) seu esquema XDM com grupos de campos específicos do Commerce.
1. [Criar um conjunto de dados](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) com base no esquema criado ou atualizado. Esse conjunto de dados contém os dados do Commerce enviados.
1. [Criar um fluxo de dados](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) e selecione o esquema XDM que contém os grupos de campos específicos do Commerce.
1. [Conectar-se a Commerce Services](../landing/saas.md).
1. [Conectar-se ao Adobe Experience Platform](connect-data.md).

## Público-alvo

Este guia foi projetado para o usuário da Adobe Commerce que deseja conectar seus dados Adobe Commerce a outros produtos Adobe DX.

### suporte para PWA Studio

Consulte a [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) para obter informações sobre como usar o [!DNL Data Connection] extensão em uma loja de PWA Studio.

### Suporte para AEM {#aem-support}

Consulte a [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) documentação para saber como enviar dados do evento da loja de uma página de produto renderizada por AEM para o Experience Platform usando o CIF - [!DNL Data Connection] extensão.

Se você precisar de informações ou tiver dúvidas que não são abordadas neste guia, use os seguintes recursos:

- [Central de ajuda](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [Tíquetes de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}—Envie um tíquete para receber ajuda adicional.
