---
title: "[!DNL SaaS Data Export Guide]"
description: "Saiba mais sobre como usar o [!DNL data export] extensão para serviços SaaS do Adobe Commerce que sincroniza dados entre o Adobe Commerce e os serviços conectados da Commerce."
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Guia do [!DNL SaaS Data Export]

[!DNL SaaS data export] melhora o desempenho de front-end otimizando a sincronização de dados entre uma instância do Adobe Commerce e o Commerce Services conectado. Ao adicionar o Live Search, o Recommendations do produto ou o Serviço de catálogo a uma instalação do Adobe Commerce, a variável [!DNL Data export] A extensão do é instalada automaticamente.

A exportação de dados SaaS coleta e exporta vários tipos de dados, chamados de _Feeds_, que agregam tipos específicos de informações. Dependendo dos serviços Commerce instalados, os feeds de exportação de dados SaaS incluem:

- **Feeds de entidade de catálogo** agregar dados do produto. Os dados incluem produtos, atributos de produto, preços de produto, variações de produto, categorias, permissões de categoria e permissões de produto.
- A variável **Feed de escopos** agrega dados para grupos de clientes, sites, lojas e visualizações de loja.
- A variável **Feed da ordem de venda** agrega dados de ordens incluindo suas entidades relacionadas, como NFFs, entregas, avisos de crédito, etc.
- A variável **Feed de inventário de várias origens** agrega dados sobre itens de status do estoque de estoque.

A extensão de exportação de dados oferece suporte a vários métodos para iniciar e gerenciar o processo de sincronização de dados.

- **Sincronização manual do Administrador ou da linha de comando**

   - A variável [Painel de gerenciamento de dados](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) no Admin do Commerce, fornece uma exibição gráfica do status de sincronização. Você pode usar o painel para executar uma ressincronização completa (_sincronização completa_) de todos os feeds. No entanto, o Adobe recomenda apenas executar uma sincronização completa na primeira vez que você conecta o Adobe Commerce a um serviço do Commerce. Consulte [Processo de sincronização](data-synchronization.md).

   - A variável [Ferramenta de linha de comando do Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) A (CLI) fornece comandos para sincronizar feeds específicos e inclui opções adicionais para personalizar o processamento do feed.

- **Sincronização automatizada com trabalhos cron**

   - [Sincronização de dados parciais](data-synchronization.md#partial-synchronization-with-cron-jobs)—Os trabalhos do Cron acionam uma sincronização de dados parcial quando um usuário administrador do Commerce atualiza uma entidade. O processo de exportação de dados envia apenas essas atualizações para os serviços conectados da Commerce. O processo de sincronização parcial é baseado no mecanismo MView e não requer nenhuma ação do usuário administrador ou do integrador de sistema.

   - [Nova tentativa automática para erros de sincronização](data-synchronization.md#failed-items-sync-for-error-recovery)—Os trabalhos do Cron acionam uma nova tentativa automática do processo de sincronização quando ocorrem erros durante o processo de sincronização de dados.

- **Agendamento e desempenho de exportação**

   - Desenvolvedores e integradores de sistemas podem estimar o tempo necessário para a exportação de dados SaaS sincronizar dados entre o Adobe Commerce e os serviços conectados. Essa estimativa pode ajudar a agendar o processamento da exportação de dados para evitar a interrupção do site. Consulte [Estimar o volume de dados e o tempo de transmissão](estimate-data-volume-sync-time.md).

   - Nos casos em que a sincronização precisa ocorrer mais rapidamente, a exportação de dados do SaaS fornece opções de personalização para melhorar o desempenho do processamento da exportação. Consulte [Melhorar o desempenho da exportação de dados](customize-export-processing.md).

- **Rastrear e solucionar problemas de atividades de exportação de dados**—Use registros de exportação de dados e exportação de saas para revisar o status da sincronização e as cargas do feed durante o processo de sincronização e indexação. Consulte [Registro e solução de problemas](troubleshooting-logging.md).



