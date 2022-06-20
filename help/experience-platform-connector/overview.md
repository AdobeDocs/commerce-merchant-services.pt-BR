---
title: Visão geral do guia
description: O conector Adobe Experience Platform para Adobe Commerce conecta seu [!DNL Commerce] para outros produtos da Adobe Experience Cloud.
source-git-commit: 9b5f2da08167e22bbba504009bccc87d0ab02c48
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# Visão geral do conector Experience Platform

A extensão do conector Experience Platform permite que os comerciantes da Adobe Commerce enviem dados para a borda do Adobe Experience Platform, de modo que outros produtos da Adobe Experience Cloud, como o Adobe Analytics e o Adobe Target, possam usar essa [!DNL Commerce] dados. Ao conectar seu [!DNL Commerce] para outros produtos na Adobe Experience Cloud, você pode realizar tarefas, como analisar o comportamento do usuário em seu site, realizar testes AB e criar campanhas personalizadas.

Eventos de vitrine capturam interações do comprador, como `View Page`, `View Product`, `Add to Cart`e assim por diante. Os dados capturados não incluem informações de identificação pessoal (PII). Todos os identificadores de usuário, como IDs de cookies e endereços IP, são estritamente anonimizados. [Saiba mais](https://www.adobe.com/privacy/experience-cloud.html). Consulte a lista completa de eventos de vitrine no final desta página.

## Pré-requisitos para usar o conector de Experience Platform {#prereqs}

Para usar o conector Experience Platform, primeiro você deve:

- Preencha o seguinte [formulário](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4VH_dtG9hJVAk_TqGkZC2DxUM1FSWkdJOE41UVpUWUw0M1JWV0RKS1VXQi4u) O e o Adobe fornecerão acesso aos Datastreams e à Adobe Experience Platform (se necessário).

Quando o acesso é concedido:

1. [Fazer logon](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) para sua conta Adobe.
1. Veja o seu [organização](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html?lang=en#concept_EA8AEE5B02CF46ACBDAD6A8508646255). A ID da organização é a ID associada à empresa provisionada pela Experience Cloud. Essa ID é uma sequência de 24 caracteres alfanuméricos seguidos por (e deve incluir) @AdobeOrg.
1. Acesse o espaço de trabalho do armazenamento de dados e [criar um conjunto de dados](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en).

A ID da organização e o armazenamento de dados são usados ao conectar a instância do Adobe Commerce à Adobe Experience Platform.

## Próximas etapas

- Instale o [Extensão do conector Experience Platform](install.md).

   A extensão Experience Platform connector é instalada a partir da linha de comando do servidor e se conecta à instalação do Adobe Commerce como uma [service](../landing/saas.md). Quando o processo estiver concluído, o conector de Experience Platform aparecerá no **Sistema** menu em **Serviços** no [!DNL Commerce] _Administrador_.

## Público

Este guia foi projetado para o comerciante da Adobe Commerce que deve conectar seus dados de loja da Adobe Commerce a outros produtos Adobe DX.

## Problemas conhecidos

Atualmente, o conector do Experience Platform tem os seguintes problemas conhecidos:

- Os eventos de pesquisa não são suportados em uma Adobe Commerce Enterprise Edition com o módulo B2B instalado.
- Os dados de vitrine levam algumas horas para chegar do Commerce aos vários destinos após se conectar à borda do Adobe Experience Platform.

## Suporte

Se você precisar de informações ou se tiver dúvidas que não são abordadas neste guia, poste no seguinte canal do Slack:

- `#beacon-ama`
