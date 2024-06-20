---
title: Interface de linha de comando da exportação de dados SaaS
description: Saiba como usar os comandos da interface de linha de comando para gerenciar feeds e processos do [!DNL data export extension] para serviços SaaS da Adobe Commerce.
recommendations: noCatalog
exl-id: f360d920-7d02-4317-8c56-c7d4c4ed2ff2
source-git-commit: af9de40a717d2cb55a5f42483bd0e4cbcd913f64
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Referência da interface de linha de comando da exportação de dados SaaS

Desenvolvedores e administradores de sistema podem gerenciar operações de sincronização para exportação de dados SaaS usando o [Ferramenta de linha de comando do Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/config-cli) (CLI). A variável `saas:resync` está incluído na variável `magento/saas-export` pacote.

O Adobe não recomenda usar o `saas:resync` comando regularmente. Os cenários típicos para usar o comando são:

- A sincronização inicial
- A variável [ID do espaço de dados SaaS](https://experienceleague.adobe.com/en/docs/commerce-admin/config/services/saas) foi alterado e é necessário sincronizar os dados para o novo espaço de dados.
- Solução de problemas

## Sincronização inicial

>[!NOTE]
>Se você estiver usando o Live Search ou o Product Recommendations, não será necessário executar a sincronização inicial. O processo é iniciado automaticamente depois que você conecta o serviço à sua instância do Commerce.

Quando você aciona um `saas:resync` na linha de comando, dependendo do tamanho do catálogo, pode levar de alguns minutos a algumas horas para que os dados sejam atualizados.

Para a sincronização inicial, o Adobe recomenda executar os comandos na seguinte ordem:

```bash
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions
```

## Exemplos de comandos

Antes de usar `saas:resync` comandos, revise o [descrições de opção](#command-options).

- Executar uma ressincronização completa de um feed de entidade.

  ```
  bin/magento saas:resync --feed='<FEED_NAME>' 1
  ```

  Os feeds que já foram exportados com sucesso não são sincronizados novamente.

- Ressincronizar totalmente o feed especificado e os dados de limpeza

  ```
  bin/magento saas:resync --feed='FEED_NAME' --cleanup-feed
  ```

  Use somente depois de executar um [!DNL Data Space ID Cleanup] operação.

- Para feeds de exportação imediatos, reenvie todos os dados para os serviços conectados da Commerce sem truncar os dados de índice na tabela de feed

  ```
   bin/magento saas:resync --feed='FEED_NAME' --no-reindex
  ```

- Lista os comandos e opções disponíveis com descrições.

  ```
  bin/magento saas:resync --help
  ```

## Opções de comando

As seguintes opções estão disponíveis para gerenciamento `saas:resync` operações.

>[!NOTE]
>
>A variável `saas:resync` Este comando também oferece suporte a opções avançadas para melhorar os comandos de exportação de dados, aumentando o tamanho do lote e adicionando o processamento de vários threads. Consulte [Personalizar processamento de exportação](customize-export-processing.md).

### `feed`

Essa opção obrigatória especifica qual entidade de feed deve ser ressincronizada, como `products`.

A variável `feed` o valor da opção pode incluir qualquer um dos feeds de entidade disponíveis:

- `products`: feed de dados do produto
- `productAttributes`: feed de dados de atributos do produto
- `categories`: feed de dados de categorias
- `variants`: feed de dados de variações de produto configurável
- `prices`: feed de dados de preços do produto
- `categoryPermissions`: feed de dados de permissões de categoria
- `productOverrides`: feed de dados de permissões do produto
- `inventoryStockStatus`: feed de dados do status do estoque de estoque
- `scopesWebsite`: sites com lojas e visualizações de loja e feed de dados
- `scopesCustomerGroup`: feed de dados de grupos de clientes
- `orders`: feed de dados de ordens de venda

Dependendo de qual [Serviços da Commerce](../landing/saas.md) instalados, talvez você tenha um conjunto diferente de feeds disponíveis para o `saas:resync` comando.

### `no-reindex`

Essa opção reenvia os dados de catálogo existentes para [!DNL Commerce Services] sem reindexação. Se essa opção não for especificada, o comando executará uma reindexação completa antes de sincronizar os dados.

O comportamento dessa opção depende de o feed ser exportado ou não no [modo de exportação herdado ou imediato](data-synchronization.md#synchronization-modes)

- Para feeds de exportação herdados, o processo de sincronização não trunca os dados indexados na tabela de feeds. Em vez disso, ele reenvia todos os dados para o serviço Adobe Commerce.
- Para feeds de exportação imediatos, essa opção é ignorada se especificada. Para esses feeds, o processo de ressincronização não trunca o índice e só ressincroniza atualizações ou itens que falharam anteriormente.

### `cleanup`

Essa opção limpa a tabela indexadora de feed antes de uma sincronização. Quando especificado, a exportação de dados SaaS executa uma ressincronização completa para o feed especificado e limpa todos os dados existentes na tabela de feed.

O Adobe recomenda usar esse comando somente após executar a [!DNL Data Space ID Cleanup] operação.

>[!WARNING]
>
>**Não use esta opção regularmente**. Isso pode causar problemas de sincronização de dados nos Serviços da Adobe Commerce. Por exemplo, a variável `delete product event` pode não se propagar para o serviço Adobe Commerce se a variável `cleanup` é usada.

## Solução de problemas

Se você não vir os dados esperados nos Serviços Commerce conectados, solucione os problemas verificando os logs de erro da exportação de dados e usando o `saas:resync` comando com variáveis de ambiente para analisar cargas e dados do profiler. Consulte [Revisar logs e solucionar problemas](troubleshooting-logging.md).
