---
title: Tipos de dados do Commerce
description: Saiba mais sobre os tipos de dados que você pode coletar e enviar para o Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: d5824e11b4961b518e35fcf56ff2c7ee00480617
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Tipos de dados do Commerce

A variável [Extensão de conexão de dados](overview.md) conecta os dados do Commerce à Experience Platform. Os dados destinados ao uso no Experience Platform são agrupados em dois tipos de comportamento: dados de série temporal, que pertencem à variável **Evento de experiência** e registrar dados, que pertencem à classe **Perfil individual** classe.

Saiba mais sobre [comportamento dos dados](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#data-behaviors) e [classes](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#class) em Experience Platform.

## Dados de série temporal

Os dados de série temporal fornecem um instantâneo do sistema no momento em que uma ação foi tomada direta ou indiretamente por um titular de registro. Por exemplo, quando um comprador navega por um produto em seu site, o adiciona um produto ao carrinho, faz um pedido e assim por diante. Os dados de série temporal são assimilados no Experience Platform usando um esquema que tem a classe definida como **Evento de experiência**.

### Dados de série temporal capturados

Consulte [eventos comportamentais](events.md) e [eventos de back office](events-backoffice.md) para saber quais dados são capturados quando um evento de série temporal é gerado.

### Esquema necessário para assimilar dados do evento de série temporal

Saiba como [criar um esquema](update-xdm.md) que podem assimilar dados de evento comportamentais e de séries de tempo de back office.

## Registrar dados

>[!NOTE]
>
>Esse recurso está na versão beta. Se você quiser participar do programa beta, envie uma solicitação para [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

Os dados do registro fornecem informações sobre os atributos de um assunto. Um assunto pode ser uma organização ou um indivíduo. Por exemplo, um comprador em seu site cria uma conta e gera dados de registro. Esses dados são assimilados no Experience Platform usando um esquema que tem a classe definida como **Perfil individual**. É possível enviar esses dados de registro para o serviço de gerenciamento e segmentação de perfil do Adobe: [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html).

### Dados de registro de perfil capturados

Consulte [dados de registro do perfil do cliente](events-profilerecord.md) para saber quais dados são capturados quando um registro de perfil é gerado.

### Esquema necessário para assimilar dados de registro de perfil

Saiba como [criar um esquema](profile-data.md) que podem assimilar dados de registro de perfil.
