---
title: "[!DNL SaaS Data Export Extension] Notas de versão"
description: As informações mais recentes da versão do [!DNL Data Export Extension] para Adobe Commerce.
feature: Services, Release Notes
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# [!DNL SaaS Data Export] Notas de versão da extensão

Essas notas de versão descrevem as versões mais recentes da [!DNL SaaS data export] extensão. O suporte é fornecido para a versão principal atual lançada. As notas de versão para versões mais antigas são fornecidas para referência.

As atualizações incluem:

![Novo](../assets/new.svg) Novos recursos
![Correção](../assets/fix.svg) Correções e aprimoramentos
![Bug](../assets/bug.svg) Problemas conhecidos


>[!NOTE]
>
>A extensão de exportação de dados SaaS é uma coleção de módulos instalados automaticamente com o Live Search, o Recommendations de produtos e o Serviço de catálogo. Você pode verificar a versão instalada em seu sistema usando o composer. Em alguns casos, você pode querer atualizar a extensão de exportação de dados no seu sistema para coletar correções ou novos recursos sem atualizar a versão do Serviço do Commerce.

## Versão principal atual

## Versão 103.3.5

![Correção](../assets/fix.svg) Defina a dependência para a versão de exportação de dados compatível mais recente para o módulo comum SaaS.

![Correção](../assets/fix.svg) Substituído `ScopeConfig` instância com `ServiceConfigInterface` para oferecer suporte a diferentes configurações de serviço.

## Versão 103.3.4

![Correção](../assets/fix.svg) Melhore o registro de exportação de dados SaaS do Commerce adicionando mais detalhes sobre o processo de reindexação.

## Versão 103.3.3

![Novo](../assets/new.svg) A exportação de dados SaaS agora armazena em cache os atributos Entity-Attribute-Value (EAV) para a consulta de metadados do atributo.

![Correção](../assets/fix.svg) Correção de um problema em que a variável `InventoryStockStatus` o feed não era salvo na tentativa se o produto fosse excluído.

## Versão 103.3.2

![Correção](../assets/fix.svg) Correção de um problema em que a variável `modifiedAt` o campo estava ausente dos feeds de entidades removidos.

## Versão 103.3.1

![Correção](../assets/fix.svg) Correção de um problema que causava uma `Invalid Template File` mensagem a ser exibida durante a reindexação do feed de produtos quando o Page Builder estiver instalado.

## Versão 103.3.0

![Novo](../assets/new.svg) Tabelas de feed de exportação imediata migradas para a estrutura unificada:
`id`, `source_entity_id`, `feed_id`, `modified_at`, `is_deleted`, `status`, `feed_data`, `feed_hash`, `errors`

![Novo](../assets/new.svg) Feeds de catálogo e inventário migrados para a solução de exportação imediata.

![Novo](../assets/new.svg) Exportação imediata de cron-jobs de feed renomeados para `*_feed_resend_failed_items`.

![Novo](../assets/new.svg) Feed de exportação imediato renomeado e tabelas de log de alterações.

![Correção](../assets/fix.svg) Definir `modified_at` nos dados de feed somente para feeds que o exijam.

![Correção](../assets/fix.svg) Modifique o `productAttributes` query para recuperar somente os atributos do produto.

## Versão 103.2.6

![Correção](../assets/fix.svg) Correção de um problema que impedia a reindexação de feeds quando tabelas tinham um prefixo.

## Versão 103.2.5

![Correção](../assets/fix.svg) Otimização da consulta de preços.

## Versão 103.2.4

![Correção](../assets/fix.svg) Corrigido o status incorreto do Stock que era exibido para um produto quando o Commerce Inventory management estava ativado.

## Versão 103.2.3

![Correção](../assets/fix.svg) Preço especial no nível do site fixo.
![Correção](../assets/fix.svg) Adição do mutex para todos os feeds processados.


## Versão 103.2.2

![Correção](../assets/fix.svg) Estratégia de agrupamento de feeds aprimorada para catálogos grandes. A tabela de lotes agora é preenchida com um número limitado de IDs para reduzir o uso da memória.

![Correção](../assets/fix.svg) Eliminação da dependência forte do CommerceInventoryDataExporter para módulos MSI.

![Correção](../assets/fix.svg) Aprimorado `commerce-data-exporter` logs para coletar mais informações e organizar por diferentes estágios de exportação.

## Versão 103.2.1

- Versão atualizada lançada.

## Versão 103.2.0

- Adição da sincronização de dados de vários threads para produtos e preços.

