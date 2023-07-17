---
title: Configuração da linha de comando
description: Após a instalação, é possível configurar [!DNL Payment Services] usando a Interface de linha de comando (CLI).
role: Admin, Developer
level: Intermediate
exl-id: 265ab1be-fe52-41f3-85cb-addbc2ddfb17
feature: Payments, Checkout, Configuration, Integration
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# Configuração da linha de comando

Depois de instalar [!DNL Payment Services], você pode configurá-lo facilmente no [dentro da página inicial](payments-home.md) ou pela CLI (Command-line Interface, interface de linha de comando).

## Configurar exportação de dados

[!DNL Payment Services] combina dados de pedidos exportados de [!DNL Magento Open Source] e [!DNL Adobe Commerce] com dados de pagamento agregados de provedores de pagamento para criar relatórios úteis. A variável [!DNL Payment Services] A extensão do usa indexadores para coletar com eficiência todos os dados necessários para os relatórios do.

Para saber mais sobre os dados usados no [!DNL Payment Services] relatórios, Consulte [Relatório de status do pagamento da ordem](order-payment-status.md#data-used-in-the-report).

### Configurar cron em [!DNL Magento Open Source]

Se quiser usar um `BY SCHEDULE` modo de índice ativado [!DNL Magento Open Source], você deve configurar o cron. Consulte [Configurar e executar o cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html).

### Definir indexadores

Os dados do pedido são exportados e mantidos no Serviço de pagamento, usando um dos dois modos de índice—`ON SAVE` (padrão) ou `BY SCHEDULE` (recomendado).

Os índices a seguir são para [!DNL Payment Services]:

| Código | Nome | Descrição |
|    ---    |  ---  |  ---  |
| `sales_order_data_exporter` | Feed de Ordem de Venda | Cria um índice de dados do pedido |
| `sales_order_status_data_exporter` | Feed de Status da Ordem de Venda | Cria índice de dados de status de ordens de venda |
| `store_data_exporter` | Feed de lojas | Cria um índice de dados de armazenamento |

Para alterar o modo de índice dos três indexadores, execute:

```bash
bin/magento indexer:set-mode schedule sales_order_data_exporter sales_order_status_data_exporter store_data_exporter
```

>[!TIP]
>
>Se você não especificar nenhum indexador em seu comando, todos os indexadores serão atualizados com o mesmo valor. Se quiser alterar um indexador específico, você deve listá-lo no comando.

Para saber mais sobre como alterar manualmente o modo de um indexador, consulte [Configurar indexadores](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#configure-indexers){target="_blank"} in the developer documentation. To learn how to change it in the Admin, see [Index management](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode){target="_blank"} no guia do usuário principal.

### Reindexar dados manualmente

Você pode reindexar os dados manualmente, em vez de esperar que eles aconteçam automaticamente. Consulte [Reindexar](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html#reindex){target="_blank"} in [Manage the Indexers](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html){target="_blank"} para obter mais informações.

Quando `BY SCHEDULE` estiver definido, o sistema rastreará as entidades alteradas e o trabalho cron atualizará o índice delas com base em um agendamento definido. Consulte [Executar cron a partir da linha de comando](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html#config-cli-cron-group-run) in [Configurar e executar o cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)) para saber como acionar manualmente a indexação usando trabalhos cron.

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

A variável `--feed` permite especificar qual feed deseja enviar:

| Feed | Descrição |
|  ---  |  ---  |
| `paymentServicesOrdersProduction` | Feed de pedidos no modo de Produção |
| `paymentServicesOrdersSandbox` | Feed de pedidos no modo Sandbox |
| `paymentServicesOrderStatusesProduction` | Status dos pedidos no modo Produção |
| `paymentServicesOrderStatusesSandbox` | Status dos pedidos no modo Sandbox |
| `paymentServicesStoresProduction` | Lojas no modo de produção |
| `paymentServicesStoresSandbox` | Lojas no modo Sandbox |

Todos os dados necessários para os relatórios são enviados para [!DNL Payment Services] automaticamente se o cron estiver configurado e instalado. Você também pode acionar manualmente o processo de envio de dados CRON para [!DNL Payment Services].

```bash
bin/magento cron:run --group payment_services_data_export
```

Para saber mais sobre reindexação e indexadores, consulte a [Gerenciar os indexadores](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) tópico na documentação do desenvolvedor.
