---
title: Tipos de dados do Commerce
description: Saiba mais sobre os tipos de dados que você pode coletar e enviar para o Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 1cdf3fcb-fb16-47ef-be5c-0ebbf1feaff4
source-git-commit: d5d5741442973d86a2d403edc940d18333defd67
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Tipos de dados do Commerce

A [extensão de Conexão de Dados](overview.md) conecta os dados do Commerce ao Experience Platform. Os dados a serem usados no Experience Platform estão agrupados em dois tipos de comportamento: dados de série temporal, que pertencem à classe **Evento de experiência**, e dados de registro, que pertencem à classe **Perfil individual**.

Saiba mais sobre [comportamento dos dados](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#data-behaviors) e [classes](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html#class) no Experience Platform.

## Dados de série temporal

Os dados de série temporal fornecem um instantâneo do sistema no momento em que uma ação foi tomada direta ou indiretamente por um titular de registro. Por exemplo, quando um comprador navega por um produto em seu site, o adiciona um produto ao carrinho, faz um pedido e assim por diante. Os dados de série temporal são assimilados no Experience Platform usando um esquema que tem a classe definida como **Evento de experiência**.

### Dados de série temporal capturados

Consulte [eventos comportamentais](events.md) e [eventos de back office](events-backoffice.md) para saber quais dados são capturados quando um evento de série temporal é gerado.

### Esquema necessário para assimilar dados do evento de série temporal

Saiba como [criar um esquema](update-xdm.md) que possa assimilar dados de evento de série temporal comportamental e de back office.

## Registrar dados

Os dados do registro fornecem informações sobre os atributos de um assunto. Um assunto pode ser uma organização ou um indivíduo. Por exemplo, um comprador em seu site cria uma conta e gera dados de registro. Estes dados são assimilados no Experience Platform usando um esquema que tem a classe definida como **Perfil Individual**. Você pode enviar esses dados de registro para o serviço de gerenciamento e segmentação de perfil do Adobe: [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=pt-BR).

### Dados de registro de perfil capturados

Consulte [dados de registro de perfil do cliente](events-profilerecord.md) para saber quais dados são capturados quando um registro de perfil é gerado.

### Esquema necessário para assimilar dados de registro de perfil

Saiba como [criar um esquema](profile-data.md) que possa assimilar dados de registro de perfil.
