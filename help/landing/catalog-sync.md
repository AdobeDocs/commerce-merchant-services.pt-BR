---
title: Sincronização de catálogo
description: Saiba como exportar dados do produto do [!DNL Commerce] servidor para [!DNL Commerce Services].
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: af9de40a717d2cb55a5f42483bd0e4cbcd913f64
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 0%

---


# Sincronização de catálogo

>[!NOTE]
>
> O Painel de sincronização do catálogo agora é o Painel de gerenciamento de dados. Esse painel renovado agora é compatível com [[!DNL Product Recommendations]](../product-recommendations/guide-overview.md), [[!DNL Live Search]](../live-search/overview.md), e [[!DNL Catalog Service]](../catalog-service/overview.md). Os clientes podem obter o Painel de gerenciamento de dados atualizando para a versão mais recente de um desses serviços. Leia mais sobre isso no [Painel de gerenciamento de dados](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) documentação. Este tópico atual permanece para os usuários que ainda não atualizaram e ainda têm o painel Sincronização de catálogo.

O Adobe Commerce usa indexadores para compilar dados de catálogo em tabelas. O processo é automaticamente acionado por [events](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) como uma alteração no preço de um produto ou no nível do inventário.

O serviço de Sincronização do catálogo move os dados do produto de um [!DNL Adobe Commerce] para a instância [!DNL Commerce Services] plataforma para manter os dados atualizados. Por exemplo, [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) exige informações atuais do catálogo para retornar com precisão as recomendações com nomes, preços e disponibilidade corretos. Use o _Sincronização de catálogo_ painel para observar e gerenciar o processo de sincronização ou a interface de linha de comando para acionar uma sincronização de catálogo e reindexar os dados do produto para consumo por [!DNL Commerce Services]. Consulte [Referência de interface de linha de comando](../data-export/data-export-cli-commands.md) no _Exportação de dados SaaS_ Guia.

## Acesso ao painel Sincronização do catálogo

Para acessar o painel Sincronização de catálogo, selecione **Sistema** > _Transferência de dados_ > **Sincronização de catálogo**.

Com o **Sincronização de catálogo** painel é possível:

- Exibir o status da sincronização (**Em andamento**, **Sucesso**, **Failed**)
- Exibir o número total de produtos sincronizados
- Pesquisar produtos sincronizados para exibir seu estado atual
- Pesquise o catálogo da loja por nome, SKU etc.
- Exibir detalhes do produto sincronizado no JSON para ajudar a diagnosticar uma discrepância de sincronização
- Reiniciar o processo de sincronização

### Última sincronização

Relata um status de sincronização de:

- **Sucesso** - Exibe a data e a hora em que a sincronização foi bem-sucedida e o número de produtos atualizados
- **Failed** - Exibe a data e a hora em que a sincronização foi tentada
- **Em andamento** - Exibe a data e a hora da última sincronização bem-sucedida

O processo de sincronização de catálogo é executado automaticamente a cada hora. Se não encontrar os produtos esperados na loja ou se os produtos não refletirem as alterações recentes feitas, você poderá resolver [problemas de sincronização do catálogo](#resolvesync).

### Produtos sincronizados

Exibe o número total de produtos sincronizados do [!DNL Commerce] catálogo. Após a sincronização inicial, somente os produtos alterados devem ser sincronizados.

## Ressincronizar {#resync}

Se você precisar iniciar uma ressincronização do catálogo antes que a sincronização agendada por hora ocorra, é possível forçar uma ressincronização.

>[!NOTE]
>
> Forçar uma ressincronização aciona uma ressincronização de todo o catálogo de produtos, o que pode aumentar a carga dos recursos de hardware.

1. No _Sincronização de catálogo_ painel, selecione **Configurações**.

   A variável _Configurações de sincronização do catálogo_ é exibida.

1. No _Ressincronizar Dados_ clique em [!UICONTROL Resync].

   [!DNL Commerce] sincroniza seu catálogo durante a próxima janela de sincronização agendada. Dependendo do tamanho do catálogo, essa operação pode levar muito tempo.

## Produtos de catálogo sincronizados

A variável **Produtos de catálogo sincronizados** A tabela exibe as seguintes informações.

| Campo | Descrição |
|---|---|
| ID | Identificador exclusivo do produto |
| Nome | Nome da vitrine do produto |
| Tipo | Identifica o tipo do produto, como simples, configurável ou baixável |
| Última exportação | Data em que o produto foi exportado com êxito do catálogo pela última vez |
| Última modificação | Data da última modificação do produto no catálogo |
| SKU | Exibe a unidade de manutenção de estoque do produto |
| Preço | Preço do produto |
| Visibilidade | Uma configuração de visibilidade do produto, conforme definido na [!DNL Commerce] catálogo |

## Resolver problemas de sincronização do catálogo {#resolvesync}

Consulte [Logs e solução de problemas](../data-export/troubleshooting-logging.md#troubleshooting) no _Guia de exportação de dados SaaS_.
