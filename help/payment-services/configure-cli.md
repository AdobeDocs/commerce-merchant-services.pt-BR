---
title: Configuração da linha de comando
description: Após a instalação, você pode configurar [!DNL Payment Services] usando a Interface de linha de comando (CLI).
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# Configuração da linha de comando

Depois de instalar [!DNL Payment Services], você pode configurá-lo facilmente a partir de [na casa](payments-home.md) ou através da Interface de linha de comando (CLI).

## Configurar exportação de dados

[!DNL Payment Services] combina dados de pedido exportados de [!DNL Magento Open Source] e [!DNL Adobe Commerce] com dados de pagamento agregados dos prestadores de pagamentos para criar relatórios úteis. O [!DNL Payment Services] A extensão usa indexadores para coletar com eficiência todos os dados necessários para os relatórios.

Para saber mais sobre os dados usados no [!DNL Payment Services] para relatórios, consulte [Relatório de status do pagamento da ordem](order-payment-status.md#data-used-in-the-report).

### Configurar o cron em [!DNL Magento Open Source]

Se quiser usar um `BY SCHEDULE` modo de índice ativado [!DNL Magento Open Source], você deve configurar o cron. Consulte [Configurar e executar o cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html).

### Definir indexadores

Os dados da ordem são exportados e mantidos no Serviço de Pagamento, utilizando um dos dois modos de índice.`ON SAVE` (padrão) ou `BY SCHEDULE` (recomendado).

Os seguintes índices são para [!DNL Payment Services]:

| Código | Nome | Descrição |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | Feed da ordem de venda | Cria o índice de dados de pedido |
| `sales_order_status_data_exporter` | Feed de status da ordem de venda | Cria o índice de dados de status de ordens de venda |
| `store_data_exporter` | Feed de lojas | Cria o índice de dados de armazenamento |

Para alterar o modo de índice para todos os três indexadores, execute:

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>Se você não especificar nenhum indexador em seu comando, todos os indexadores serão atualizados para o mesmo valor. Se quiser alterar um indexador específico, você deve listá-lo em seu comando.

Para saber mais sobre como alterar manualmente o modo de um indexador, consulte [Configurar indexadores](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers){target=&quot;_blank&quot;} na documentação do desenvolvedor. Para saber como alterá-lo no Administrador, consulte [Gerenciamento de índices](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target=&quot;_blank&quot;} no guia do usuário principal.

### Reindexar dados manualmente

Você pode reindexar dados manualmente, em vez de esperar que aconteça automaticamente. Consulte [Reindexar](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target=&quot;_blank&quot;} em [Gerenciar os indexadores](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target=&quot;_blank&quot;} para obter mais informações.

When `BY SCHEDULE` for definido, o sistema rastreará entidades alteradas e o trabalho cron atualizará o índice para elas com base em um agendamento definido. Consulte [Execute cron a partir da linha de comando](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) em [Configurar e executar o cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)) para saber como acionar manualmente a indexação usando trabalhos cron.

### Enviar dados reindexados para o serviço de pagamento

Depois que os dados forem indexados, eles serão enviados automaticamente para [!DNL Payment Services]. Você também pode acionar manualmente o processo de envio de dados indexados com este comando:

```bash
bin/magento saas:resync --feed [feedName]
```

Use as seguintes opções de comando:

| Comando | Descrição |
|  ---  |  ---  |
| `bin/magento saas:resync --feed [feedName]` | Executa uma reindexação do feed especificado e o envia para o serviço correspondente |
| `bin/magento saas:resync --no-reindex` | Ignora a indexação e envia dados não sincronizados dos índices |

O `--feed` permite especificar qual feed deseja enviar:

| Feed | Descrição |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | Feed de pedidos no modo Produção |
| `paymentServicesOrdersSandbox` | Feed de pedidos no modo Sandbox |
| `paymentServicesOrderStatusesProduction` | Status do pedido no modo Produção |
| `paymentServicesOrderStatusesSandbox` | Status do pedido no modo Sandbox |
| `paymentServicesStoresProduction` | Armazenamentos no modo Produção |
| `paymentServicesStoresSandbox` | Lojas no modo Sandbox |

Todos os dados necessários para os relatórios são enviados para [!DNL Payment Services] automaticamente se o cron estiver configurado e instalado. Você também pode acionar manualmente o processo de envio de dados cron para o [!DNL Payment Services].

```bash
bin/magento cron:run --group payment_services_data_export
```

Para saber mais sobre reindexação e indexadores, consulte o [Gerenciar os indexadores](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) na documentação do desenvolvedor.
