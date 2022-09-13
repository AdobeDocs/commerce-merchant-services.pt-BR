---
title: Visão geral do guia
description: Saiba como integrar dados do Adobe Commerce com o Adobe Experience Platform usando o conector Experience Platform.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: c7344efead97b0562a146f096123dd84f998fd5e
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Visão geral do conector Experience Platform

A extensão do conector Experience Platform permite que os comerciantes da Adobe Commerce enviem dados para a borda do Adobe Experience Platform para que outros produtos da Adobe Experience Cloud, como o Adobe Analytics e o Adobe Target, possam usar esses dados do Commerce. Ao conectar seus dados do Commerce a outros produtos na Adobe Experience Cloud, você pode realizar tarefas, como analisar o comportamento do usuário no seu site, realizar testes AB e criar campanhas personalizadas.

[Eventos de vitrine](events.md) capturar interações do comprador, como `View Page`, `View Product`, `Add to Cart`e assim por diante. Os dados capturados não incluem informações de identificação pessoal (PII). Todos os identificadores de usuário, como IDs de cookies e endereços IP, são estritamente anonimizados. [Saiba mais](https://www.adobe.com/privacy/experience-cloud.html).

O conector Experience Platform aparece no Administrador do Commerce em **Sistema** > Serviços > **Conector Experience Platform**.

![Extensão do conector do Experience Platform Exibição do administrador](assets/epc-adminui.png)

## Pré-requisitos {#prereqs}

Para usar o conector de Experience Platform, você deve ter o seguinte:

- Adobe Commerce 2.4.3 ou mais recente
- Adobe ID e ID da organização
- Direitos a outros produtos Adobe DX

## Etapas de integração

1. [Instalar](install.md) a extensão do conector Experience Platform.
1. [Fazer logon](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) para sua conta Adobe e [exibir](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255) sua ID da organização. A ID da organização é a ID associada à empresa provisionada pela Experience Cloud. Essa ID é uma sequência de 24 caracteres alfanuméricos seguidos por (e deve incluir) `@AdobeOrg`.
1. [Connect](connect-data.md) sua instância do Adobe Commerce para a Adobe Experience Platform.
1. [Criar ou atualizar](update-xdm.md) seu esquema XDM com grupos de campos específicos de Comércio.
1. [Criar um conjunto de dados](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) e selecione o esquema XDM que contém os grupos de campos específicos de Comércio.
1. (Opcional) [Fazer upload de perfis de consumidor](profile.md) para que os dados da loja possam ser atribuídos a compradores específicos para melhorar a experiência de compra.

## Público

Este guia foi projetado para o comerciante da Adobe Commerce que deseja conectar seus dados de loja da Adobe Commerce a outros produtos Adobe DX.

### Suporte a PWA Studio

Consulte a [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) documentação para obter informações sobre como usar o conector Experience Platform em uma loja de PWA Studio.

Se você precisar de informações ou se tiver dúvidas que não são abordadas neste guia, use os seguintes recursos:

- [Central de ajuda](https://support.magento.com/hc/en-us){target=&quot;_blank&quot;}
- [Tíquetes de suporte](https://support.magento.com/hc/en-us/articles/360000913794#submit-ticket){target=&quot;_blank&quot;} — Envie um tíquete para receber ajuda adicional.
