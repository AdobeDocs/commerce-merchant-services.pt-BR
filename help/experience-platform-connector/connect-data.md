---
title: Conectar dados do Commerce ao Adobe Experience Platform
description: Saiba como conectar seus dados de Comércio à Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 76bc0650f32e99f568c061e67290de6c380f46a4
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---

# Conectar dados do Commerce ao Adobe Experience Platform {#connectaep}

Para conectar sua instância do Adobe Commerce à Adobe Experience Platform, você deve fornecer uma ID da organização e uma ID do armazenamento de dados.

![Configuração do conector Experience Platform](assets/epc-config-sf.png)

## Geral

1. Faça logon na sua conta do Adobe na [Conector do Commerce Services](../landing/saas.md#organizationid) e selecione a ID da organização.

1. Em Admin, acesse **Sistema** > Serviços > **Conector Experience Platform**.

1. No **Escopo** , defina o contexto como **Site**.

1. No **ID da organização** , você verá a ID associada à sua conta do Adobe Experience Platform, conforme configurado na variável [Conector do Commerce Services](../landing/saas.md#organizationid). A ID da organização é global. Somente uma ID de organização pode ser associada por instância do Adobe Commerce.

1. (Opcional) Se você já tiver uma [AEP Web SDK (liga)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) implantado em seu site, ative a caixa de seleção e adicione o nome do SDK da Web da AEP. Caso contrário, deixe esses campos em branco e o conector de Experience Platform implante um para você.

   >[!NOTE]
   >
   >Se você especificar seu próprio SDK da Web da AEP, o conector do Experience Platform usará a ID do armazenamento de dados associada a esse SDK e não a ID do armazenamento de dados especificada nessa página (se houver).

## Coleta de dados

No **Coleta de dados** , especifique quais tipos de dados coletar e enviar para a borda do Experience Platform. Por padrão, os eventos de vitrine são enviados automaticamente, desde que o SDK da Web da AEP e a ID da organização sejam válidos. Consulte o tópico de eventos para saber mais sobre [vitrine](events.md#storefront-events) e [back office](events.md#back-office-events) eventos.

![Configuração do conector Experience Platform](assets/epc-config-dc.png)

>[!NOTE]
>
>Todos os campos na **Coleta de dados** aplicar à **Site** escopo ou superior.

1. Selecionar **Eventos do back-office** se desejar enviar informações sobre o status do pedido, como se um pedido foi feito, cancelado, reembolsado ou enviado.

   >[!NOTE]
   >
   >Por padrão, todos os dados do back office são enviados para a borda do Experience Platform. Se um comprador optar por rejeitar a coleta de dados, você deverá definir explicitamente a preferência de privacidade do comprador no Experience Platform. Isso é diferente dos eventos de loja, onde o coletor já lida com o consentimento com base nas preferências do comprador. [Saiba mais](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) sobre como definir a preferência de privacidade de um comprador no Experience Platform.

1. (Pule esta etapa se estiver usando seu próprio SDK da Web da AEP.) [Criar](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) um armazenamento de dados na Adobe Experience Platform ou selecione um armazenamento de dados existente que deseja usar para a coleta.

1. (Pule esta etapa se estiver usando seu próprio SDK da Web da AEP.) No **ID do fluxo de dados** , cole a ID desse armazenamento de dados novo ou existente.

## Descrições dos campos

| Campo | Descrição |
|--- |--- |
| Escopo | Site específico no qual você deseja que as configurações sejam aplicadas. |
| ID da organização (global) | ID que pertence à organização que comprou o produto Adobe DX. Essa ID vincula sua instância do Adobe Commerce ao Adobe Experience Platform. |
| O SDK da Web da AEP já foi implantado em seu site | Marque essa caixa de seleção se tiver implantado seu próprio SDK da Web da AEP no seu site |
| AEP Web SDK Name (Global) | Se você já tiver um SDK da Web do Experience Platform implantado em seu site, especifique o nome desse SDK neste campo. Isso permite que o Coletor de eventos de vitrine e o SDK de eventos de vitrine usem seu SDK da Web do Experience Platform em vez da versão implantada pelo conector do Experience Platform. Se você não tiver um SDK da Web do Experience Platform implantado em seu site, deixe este campo em branco e o conector do Experience Platform implante um para você. |
| Eventos de vitrine | É marcado por padrão, desde que a ID da organização e a ID do armazenamento de dados sejam válidas. Os eventos de vitrine coletam dados comportamentais anônimos dos compradores durante a navegação no site. |
| Eventos de back-office | Se marcado, a carga do evento contém informações de status de pedido anônimas, como se um pedido fosse feito, cancelado, reembolsado ou enviado. |
| ID do fluxo de dados (site) | ID que permite que os dados fluam do Adobe Experience Platform para outros produtos Adobe DX. Essa ID deve ser associada a um site específico na instância específica do Adobe Commerce. Se você especificar seu próprio SDK da Web do Experience Platform, não especifique uma ID de armazenamento de dados nesse campo. O conector Experience Platform usa a ID do armazenamento de dados associada a esse SDK e ignora qualquer ID do armazenamento de dados especificada nesse campo (se houver). |

Com a extensão do conector Experience Platform instalada, o link entre o Adobe Commerce e o Adobe Experience Platform criado e a ID de fluxo de dados especificada, os dados do Commerce começam a fluir para a borda do Adobe Experience Platform e para outros produtos Adobe DX.

>[!NOTE]
>
> O tempo necessário para os dados fluírem da borda para outros produtos Adobe DX pode variar.

## Verifique se os dados estão sendo enviados para o Experience Platform

Quando os dados do Commerce são enviados para a borda do Adobe Experience Platform, você pode criar relatórios como os seguintes:

![Dados de comércio no Adobe Experience Manager](assets/aem-data-1.png)
_Dados de comércio no Adobe Experience Manager_
