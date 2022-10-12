---
title: Conectar dados do Commerce ao Adobe Experience Platform
description: Saiba como conectar seus dados de Comércio à Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 1af2dee51391c94e19b68481d390cc2629fe1d6e
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# Conectar dados do Commerce ao Adobe Experience Platform {#connectaep}

Para conectar sua instância do Adobe Commerce à Adobe Experience Platform, você deve fornecer uma ID da organização e uma ID do armazenamento de dados.

![Configuração do conector Experience Platform](assets/epc-config.png)

1. Faça logon na sua conta do Adobe na [Conector do Commerce Services](../landing/saas.md#organizationid) e selecione a ID da organização.

1. Em Admin, acesse **Sistema** > Serviços > **Conector Experience Platform**.

1. No **Escopo** , defina o contexto como **Site**.

1. No **ID da organização** , você verá a ID associada à sua conta do Adobe Experience Platform, conforme configurado na variável [Conector do Commerce Services](../landing/saas.md#organizationid). A ID da organização é global. Somente uma ID de organização pode ser associada por instância do Adobe Commerce.

1. No **ID do fluxo de dados** , cole a ID do armazenamento de dados que você [criado](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html#create) na Adobe Experience Platform.

   >[!NOTE]
   >
   >O escopo da ID do armazenamento de dados deve ser definido no nível do site ou superior. Nesse nível, a mesma ID do armazenamento de dados é usada para cada site na hierarquia. Não é possível definir o escopo da ID do armazenamento de dados no nível da visualização de armazenamento.

1. (Opcional) Se você não tiver um SDK da Web da AEP implantado em seu site, deixe este campo em branco e o conector do Experience Platform implanta um para você. Caso contrário, adicione o nome do SDK da Web da AEP.

## Descrições dos campos

| Campo | Descrição |
|--- |--- |
| Escopo | Site específico no qual você deseja que as configurações sejam aplicadas. |
| ID da organização (global) | ID que pertence à organização que comprou o produto Adobe DX. Essa ID vincula sua instância do Adobe Commerce ao Adobe Experience Platform. |
| ID do fluxo de dados (site) | ID que permite que os dados fluam do Adobe Experience Platform para outros produtos Adobe DX. Essa ID deve ser associada a um site específico na instância específica do Adobe Commerce. |
| AEP Web SDK Name (Global) | Se você não tiver um SDK da Web da AEP implantado em seu site, deixe este campo em branco e o conector do Experience Platform implanta um para você. Se você já tiver um SDK da Web da AEP implantado em seu site, especifique o nome desse SDK neste campo. Isso permite que o Coletor de eventos de frente de loja e o SDK de eventos de frente de loja usem seu SDK da Web da AEP em vez da versão implantada pelo conector do Experience Platform. |

Com a extensão do conector Experience Platform instalada, o link entre o Adobe Commerce e o Adobe Experience Platform criado e a ID de fluxo de dados especificada, os dados do Commerce começam a fluir para a borda do Adobe Experience Platform e para outros produtos Adobe DX.

>[!NOTE]
>
> O tempo necessário para os dados fluírem da borda para outros produtos Adobe DX pode variar.

## Dados de comércio na borda

Quando os dados do Commerce são enviados para a borda do Adobe Experience Platform, você pode criar relatórios como os seguintes:

![Dados de comércio no Adobe Experience Manager](assets/aem-data-1.png)
_Dados de comércio no Adobe Experience Manager_
