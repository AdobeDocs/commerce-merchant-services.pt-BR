---
title: Configuração do processo de segundo plano
description: "Configurar as programações para [!DNL Store Fulfillment] processos em segundo plano usados na sincronização de dados com os serviços de preenchimento."
role: User, Admin
level: Intermediate
exl-id: 742ae59e-77a0-4db6-b156-2992d4403be7
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 0%

---


# Configuração do processo de segundo plano

A integração Store Fulfillment usa processos em segundo plano e filas de mensagens para obter o desempenho e a escala ideais. Crie ambientes para suas lojas Adobe Commerce usando [variáveis de implantação](https://devdocs.magento.com/cloud/env/variables-deploy.html#cron_consumers_runner) que iniciam automaticamente [executores da fila de mensagens](https://devdocs.magento.com/guides/v2.4/config-guide/mq/rabbitmq-overview.html).

Os processos em segundo plano são gerenciados usando o Adobe Commerce padrão [Tarefas Agendadas](https://docs.magento.com/user-guide/system/cron.html) funcionalidade. Esses processos são responsáveis por sincronizar dados de configuração de ordem e armazenamento de comerciante com serviços da Web de preenchimento de loja.

## Gerenciar tarefas agendadas para Atendimento de Loja

No Administrador, acesse **[!UICONTROL Stores > Configuration > Advanced > System > Cron (Scheduled Tasks) > Cron configuration options for group:store_fulfillment]**.

Revise a configuração padrão para os serviços de Atendimento da Loja. Dependendo do volume de processamento do pedido e da disponibilidade de recursos, talvez seja necessário ajustar essas configurações.
