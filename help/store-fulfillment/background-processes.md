---
title: Configuração do processo de segundo plano
description: "Configure os agendamentos para  [!DNL Store Fulfillment] processos em segundo plano usados na sincronização de dados com os serviços de preenchimento."
role: Admin, Developer
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---


# Configuração do processo de segundo plano

A integração Store Fulfillment usa processos em segundo plano e filas de mensagens para obter o desempenho e a escala ideais. Crie ambientes para seus armazenamentos Adobe Commerce usando [variáveis de implantação](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) que iniciam automaticamente [executores de fila de mensagens](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html).

Os processos em segundo plano são gerenciados com a funcionalidade padrão do Adobe Commerce [Tarefas Agendadas](https://docs.magento.com/user-guide/system/cron.html). Esses processos são responsáveis por sincronizar dados de configuração de ordem e armazenamento de comerciante com serviços da Web de preenchimento de loja.

## Gerenciar tarefas agendadas para Atendimento de Loja

No Administrador, vá para **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**.

Revise a configuração padrão para os serviços de Atendimento da Loja. Você pode personalizar essas configurações com base no volume de processamento do pedido e na disponibilidade de recursos.
