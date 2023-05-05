---
title: Visão geral do guia
description: Saiba como integrar dados do Adobe Commerce com o Adobe Experience Platform usando o conector Experience Platform.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: 0d5bbe7d4e2070173930df66c4f159d65c7383ea
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# Visão geral do conector Experience Platform

A extensão do conector Experience Platform permite que os comerciantes do Adobe Commerce enviem [vitrine](events.md#storefront-events) e [back office](events.md#back-office-events) dados na borda do Adobe Experience Platform para que outros produtos da Adobe Experience Cloud, como o Adobe Analytics e o Adobe Target, possam usar esses dados do Commerce. Ao conectar seus dados do Commerce a outros produtos na Adobe Experience Cloud, você pode realizar tarefas, como analisar o comportamento do usuário no seu site, realizar testes AB e criar campanhas personalizadas.

[Eventos de vitrine](events.md#storefront-events) capturar interações do comprador, como `View Page`, `View Product`, `Add to Cart`e [lista de requisições](events.md#b2b-events) informações (para comerciantes B2B). [Back Office](events.md#back-office-events) Os eventos capturam informações sobre o status de um pedido, como se ele fosse feito, cancelado, reembolsado, enviado ou concluído. Os dados capturados não incluem informações de identificação pessoal (PII). Todos os identificadores de usuário, como IDs de cookies e endereços IP, são estritamente anonimizados. [Saiba mais](https://www.adobe.com/privacy/experience-cloud.html).

O conector Experience Platform aparece no Administrador do Commerce em **Sistema** > Serviços > **Conector Experience Platform**.

![Extensão do conector do Experience Platform Exibição do administrador](assets/epc-adminui.png)

## Pré-requisitos {#prereqs}

Para usar o conector Experience Platform, você deve ter o seguinte:

- Adobe Commerce 2.4.3 ou mais recente
- Adobe ID e ID da organização
- [Camada de dados do cliente do Adobe (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). O ACDL é necessário para coletar dados de evento da loja.
- Direitos a outros produtos Adobe DX

## Etapas de integração

1. [Instalar](install.md) a extensão do conector Experience Platform.
1. [Fazer logon](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) para sua conta Adobe e [exibir para confirmar](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) sua ID da organização. A ID da organização é a ID associada à empresa provisionada pela Experience Cloud. Essa ID é uma sequência de 24 caracteres alfanuméricos seguidos por (e deve incluir) `@AdobeOrg`.
1. [Criar ou atualizar](update-xdm.md) seu esquema XDM com grupos de campos específicos de Comércio.
1. [Criar um conjunto de dados](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) com base no esquema criado ou atualizado. Esse conjunto de dados conterá os dados de Comércio enviados.
1. [Criar um conjunto de dados](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) e selecione o esquema XDM que contém os grupos de campos específicos de Comércio.
1. [Conectar-se aos Commerce Services](../landing/saas.md).
1. [Conectar-se ao Adobe Experience Platform](connect-data.md).

## Público

Este guia foi projetado para o comerciante da Adobe Commerce que deseja conectar seus dados do Adobe Commerce a outros produtos Adobe DX.

### Suporte a PWA Studio

Consulte a [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) documentação para obter informações sobre como usar o conector Experience Platform em uma loja de PWA Studio.

### Suporte AEM {#aem-support}

Consulte a [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html) documentação para saber como enviar dados de evento da loja de uma página de produto renderizada AEM para o Experience Platform usando o Conector CIF - Experience Platform.

Se você precisar de informações ou se tiver dúvidas que não são abordadas neste guia, use os seguintes recursos:

- [Central de ajuda](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
- [Tíquetes de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}—Envie um tíquete para receber ajuda adicional.
