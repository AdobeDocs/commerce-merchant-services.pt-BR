---
title: Sincronizar dados com a exportação de dados SaaS
description: "Saiba como a [!DNL SaaS Data Export] coleta e sincroniza dados entre instâncias do Adobe Commerce e serviços SaaS conectados."
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 0%

---

# Sincronizar dados com a exportação de dados SaaS

Quando você instala um serviço do Commerce que requer exportação de dados, como Serviço de catálogo, Live Search ou Recommendations de produtos, uma coleção de módulos de exportação de dados do Saas é instalada para gerenciar o processo de coleta e sincronização de dados. O diagrama a seguir mostra o fluxo de exportação de dados SaaS.

![Coleta de exportação de dados SaaS e fluxo de sincronização para o Adobe Commerce](assets/data-export-flow.png){width="900" zoomable="yes"}

Os principais componentes do fluxo de exportação de dados SaaS incluem:

- Módulos de exportação de dados SaaS que coletam os dados para feeds do Adobe Commerce, montam itens de feed, aguardam atualizações e persistem o status do feed.
- Módulos de exportação SaaS que exportam dados, configuram o roteamento e publicam os feeds para serviços conectados.
- O Serviço do Adobe Commerce gerencia o processo de assimilação de dados para validar feeds recebidos e atualizações persistentes nos serviços conectados.

## Modos de sincronização

A exportação de dados SaaS tem dois modos para processar feeds de entidade:

- **Modo de exportação imediata**—Nesse modo, os dados são coletados e enviados imediatamente para o Commerce Service em uma única iteração. Esse modo acelera a entrega de atualizações de entidades ao serviço do Commerce e reduz o tamanho do armazenamento das tabelas de feed.

- **Modo de exportação herdado**— Nesse modo, os dados são coletados em um único processo. Em seguida, um trabalho cron envia os dados coletados para os serviços de comércio conectados. Nas entradas do log de exportação de dados, os feeds que usam o modo herdado são rotulados `(legacy)`.

## Tipos de sincronização

A exportação de dados SaaS suporta três tipos de sincronização - sincronização completa, sincronização parcial e nova tentativa de sincronização de itens com falha.

### Sincronização completa

Depois de conectar uma instância do Adobe Commerce ao Commerce Service, execute uma sincronização completa para enviar dados de feed de entidade do Adobe Commerce para o serviço conectado.

>[!NOTE]
>
>A sincronização completa é principalmente para a fase de integração. Evite o uso regular para evitar a sobrecarga do banco de dados. Após a sincronização inicial, as alterações em andamento são sincronizadas automaticamente usando a sincronização parcial.

### Sincronização parcial

Com a sincronização parcial, a exportação de dados SaaS envia automaticamente as atualizações do aplicativo Commerce, como alterações de nome de produto ou atualizações de preço, para os serviços de comércio conectados.

O processo de exportação de dados usa os seguintes trabalhos cron para automatizar a operação de sincronização parcial.

- trabalhos do grupo cron &quot;index&quot;:
   - A variável `indexer_reindex_all_invalid` o trabalho reindexa todos os feeds inválidos. É um trabalho cron padrão do Adobe Commerce.
   - A variável `saas_data_exporter` o trabalho é para feeds de exportação herdados.
   - A variável `sales_data_exporter` o trabalho é específico para o feed de exportação de dados de vendas.

Esses trabalhos são executados a cada minuto.

Para que a sincronização parcial funcione, o aplicativo Commerce requer a seguinte configuração:

- [O agendamento de tarefas é habilitado através de trabalhos cron](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html)

- Todos os indexadores de exportação de dados SaaS estão configurados no `Update by Schedule` modo.

  Na versão de exportação de dados SaaS 103.1.0 e posterior, `Update by Schedule` está ativado por padrão. Você pode verificar a configuração de índice no servidor usando o comando da CLI do Commerce, `bin/magento indexer:show-mode | grep -i feed`

### Repetir sincronização de Itens com Falha

A sincronização Repetir itens com falha usa um processo separado para reenviar itens que não foram sincronizados devido a erros durante o processo de sincronização, por exemplo, um erro de aplicativo, uma interrupção de rede ou um erro de serviço SaaS. A implementação desta sincronização também se baseia em trabalhos cron.

- `resync_failed_feeds_data_exporter` trabalhos do grupo cron:
   - A variável `<feed name>_feed_resend_failed_feeds_items` o trabalho reenvia itens com falha de sincronização, por exemplo `products_feed_resend_failed_items`.

### Exibir e gerenciar o processo de sincronização

A maioria das atividades de sincronização é processada automaticamente com base na configuração do aplicativo. No entanto, a exportação de dados SaaS também fornece ferramentas para gerenciar o processo.

- Os usuários administradores podem visualizar e rastrear o progresso da sincronização e obter informações sobre os dados do [Painel de gerenciamento de dados](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).

- Desenvolvedores, integradores de sistemas ou administradores com acesso ao servidor de aplicativos do Commerce podem gerenciar o processo de sincronização e os feeds de dados usando a CLI (Command-Line Tool, ferramenta de linha de comando) do Adobe Commerce. Consulte [Referência do comando de exportação de dados](data-export-cli-commands.md).

### Verificar a configuração do aplicativo do Commerce

A sincronização parcial e a sincronização de itens com falha de Repetir funcionam somente se a instância do Commerce tiver sido configurada corretamente. Normalmente, a configuração é concluída ao configurar o serviço do Commerce. Se a exportação de dados não estiver funcionando corretamente, verifique a seguinte configuração.

- [Confirme se os trabalhos cron estão em execução](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).

- Verifique se os indexadores estão sendo executados no [Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) ou usando o comando da CLI do Commerce `bin/magento indexer:info`.

- Verifique se os indexadores dos seguintes feeds estão definidos como `Update by Schedule`: Atributos do catálogo, Produto, Substituições de produto e Variante de produto. É possível verificar os indexadores em [Gerenciamento de índice](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) no Admin ou usando a CLI (`bin/magento indexer:show-mode | grep -i feed`).
