---
title: Visão geral do guia
description: O conector Adobe Experience Platform para Adobe Commerce conecta sua instância do Commerce a outros produtos da Adobe Experience Cloud.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
source-git-commit: 2b735c292920bb0e9052d86bf152748e7ce96079
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Visão geral do conector Experience Platform

A extensão do conector Experience Platform permite que os comerciantes da Adobe Commerce enviem dados para a borda do Adobe Experience Platform para que outros produtos da Adobe Experience Cloud, como o Adobe Analytics e o Adobe Target, possam usar esses dados do Commerce. Ao conectar seus dados do Commerce a outros produtos na Adobe Experience Cloud, você pode realizar tarefas, como analisar o comportamento do usuário no seu site, realizar testes AB e criar campanhas personalizadas.

Eventos de vitrine capturam interações do comprador, como `View Page`, `View Product`, `Add to Cart`e assim por diante. Os dados capturados não incluem informações de identificação pessoal (PII). Todos os identificadores de usuário, como IDs de cookies e endereços IP, são estritamente anonimizados. [Saiba mais](https://www.adobe.com/privacy/experience-cloud.html). Veja a lista completa de [eventos storefront](events.md).

## Pré-requisitos para usar o conector de Experience Platform {#prereqs}

Para usar o conector Experience Platform, primeiro você deve:

- Preencha o seguinte [formulário](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4VH_dtG9hJVAk_TqGkZC2DxUM1FSWkdJOE41UVpUWUw0M1JWV0RKS1VXQi4u) O e o Adobe fornecerão acesso aos Datastreams e à Adobe Experience Platform (se necessário).

Quando o acesso é concedido:

1. [Fazer logon](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) para sua conta Adobe.
1. Veja o seu [organização](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255). A ID da organização é a ID associada à empresa provisionada pela Experience Cloud. Essa ID é uma sequência de 24 caracteres alfanuméricos seguidos por (e deve incluir) `@AdobeOrg`.
1. Crie ou atualize seu [Esquema XDM](update-xdm.md) com grupos de campos específicos de Comércio.
1. [Criar um conjunto de dados](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) e selecione o esquema XDM que contém o específico de Comércio **Grupos de campos**.

>[!NOTE]
>
> A ID da organização e o armazenamento de dados são usados para conectar a instância do Adobe Commerce à Adobe Experience Platform.

## Próximas etapas

- Instale o [Extensão do conector Experience Platform](install.md).

   A extensão Experience Platform connector é instalada a partir da linha de comando do servidor e se conecta à instalação do Adobe Commerce como uma [service](../landing/saas.md). Quando o processo estiver concluído, o conector de Experience Platform aparecerá no **Sistema** menu em **Serviços** no Commerce _Administrador_.
- [Fazer upload de perfis de consumidor](profile.md) para que os dados da loja possam ser atribuídos a compradores específicos para melhorar a experiência de compra.

## Público

Este guia foi projetado para o comerciante da Adobe Commerce que deve conectar seus dados de loja da Adobe Commerce a outros produtos Adobe DX.

### Suporte a PWA Studio

Consulte a [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/) documentação para obter informações sobre como usar o conector Experience Platform em uma loja de PWA Studio.

## Problemas conhecidos

Atualmente, o conector do Experience Platform tem os seguintes problemas conhecidos:

- Os eventos de pesquisa não são suportados em uma Adobe Commerce Enterprise Edition com o módulo B2B instalado.
- Os dados de vitrine levam cerca de uma hora para chegar do Adobe Commerce aos vários destinos após se conectar à borda do Adobe Experience Platform.

Se você precisar de informações ou se tiver dúvidas que não são abordadas neste guia, use os seguintes recursos:

- [Central de ajuda](https://support.magento.com/hc/en-us){target=&quot;_blank&quot;}
- [Tíquetes de suporte](https://support.magento.com/hc/en-us/articles/360000913794#submit-ticket){target=&quot;_blank&quot;} — Envie um tíquete para receber ajuda adicional.
- No Slack: `#beacon-ama`
