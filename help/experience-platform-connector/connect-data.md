---
title: Conectar dados do Commerce ao Adobe Experience Platform
description: Saiba como conectar seus dados de Comércio à Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 2b735c292920bb0e9052d86bf152748e7ce96079
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Conectar dados do Commerce ao Adobe Experience Platform {#connectaep}

Antes de conectar seus dados do Adobe Commerce à Adobe Experience Platform, você deve fazer logon em sua conta do Adobe na [Conector do Commerce Services](../landing/saas.md#organizationid). Depois de fazer logon e selecionar a ID da organização, é possível especificar o escopo e a ID do armazenamento de dados na **Conector Experience Platform** na página Admin.

1. Em Admin, acesse **Sistema** > Serviços > **Conector Experience Platform**.

1. No **Escopo** selecione o contexto ou &quot;escopo&quot; da visualização da loja.

   A ID da organização é global. Somente uma ID de organização pode ser associada por instância da Adobe Commerce.

1. No **IMS Organization** , você verá a ID associada à sua conta do Adobe Experience Platform, conforme configurado na variável [Conector do Commerce Services](../landing/saas.md#organizationid).

1. No **ID do fluxo de dados** , cole a ID do fluxo de dados que você [criado](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html) no Adobe Experience Platform.

## Relação da ID do fluxo de dados e da visualização da instância do comércio

A ID do conjunto de dados permite o encaminhamento de eventos do Adobe Experience Platform para outros produtos Adobe DX e pode ser associada a uma visualização de armazenamento específica em sua instância específica do Adobe Commerce. Também é possível associar várias visualizações de armazenamento à mesma ID de conjunto de dados. Depende do que faz mais sentido para a sua empresa.

## Descrições dos campos

| Campo | Descrição |
|--- |--- |
| Escopo | Exibição de armazenamento específica onde você deseja que as configurações sejam aplicadas. |
| Organização IMS (Global) | ID que pertence à organização que comprou o produto Adobe DX. Essa ID vincula sua instância do Adobe Commerce ao Adobe Experience Platform. |
| ID do fluxo de dados (Storeview) | ID que permite que os dados fluam do Adobe Experience Platform para outros produtos Adobe DX. Essa ID pode ser associada a um storeView específico na instância específica do Adobe Commerce. |

Com a extensão do conector Experience Platform instalada, o link entre o Adobe Commerce e o Adobe Experience Platform criado e a ID de fluxo de dados especificada, os dados do Commerce começam a fluir para a borda do Adobe Experience Platform e para outros produtos Adobe DX.

## Dados de comércio na borda

Quando os dados do Commerce são enviados para a borda do Adobe Experience Platform, você pode criar relatórios como os seguintes:

![Dados de comércio no Adobe Experience Manager](assets/aem-data-1.png)
_Dados de comércio no Adobe Experience Manager_
