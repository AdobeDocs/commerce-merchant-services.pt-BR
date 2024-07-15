---
title: '[!DNL SaaS Data Export Extension] Notas de Versão'
description: As informações da versão mais recente do  [!DNL Data Export Extension] para Adobe Commerce.
feature: Services, Release Notes
recommendations: noCatalog
exl-id: 0c7aeeda-e8a6-4740-b466-0661a6d2df07
source-git-commit: 42a9ea0f62f35db451cd3e780adf530d0699a638
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# Notas de versão da extensão [!DNL SaaS Data Export]

Essas notas de versão descrevem as versões mais recentes da extensão [!DNL SaaS data export]. O suporte é fornecido para a versão principal atual lançada. As notas de versão para versões mais antigas são fornecidas para referência.

As atualizações incluem:

![Novos](../assets/new.svg) Novos recursos
![Correção](../assets/fix.svg) correções e melhorias
![Bug](../assets/bug.svg) Problemas conhecidos


>[!NOTE]
>
>A extensão de exportação de dados SaaS é uma coleção de módulos instalados automaticamente com o Live Search, o Recommendations de produtos e o Serviço de catálogo. Você pode verificar a versão instalada em seu sistema usando o composer. Em alguns casos, você pode querer atualizar a extensão de exportação de dados no seu sistema para coletar correções ou novos recursos sem atualizar a versão do Serviço do Commerce.

## Versão principal atual

## Versão 103.3.5

![Correção](../assets/fix.svg) Definir dependência para a versão de exportação de dados compatível mais recente para o módulo comum SaaS.

![Correção](../assets/fix.svg) Substituiu a instância `ScopeConfig` por `ServiceConfigInterface` para dar suporte a diferentes configurações de serviço.

## Versão 103.3.4

![Correção](../assets/fix.svg) Melhore o log de exportação de dados SaaS do Commerce adicionando mais detalhes sobre o processo de reindexação.

## Versão 103.3.3

A ![nova](../assets/new.svg) exportação de dados SaaS agora armazena em cache os atributos Entity-Attribute-Value (EAV) para a consulta de metadados do atributo.

![Correção](../assets/fix.svg) Corrigido um problema no qual o feed do `InventoryStockStatus` não era salvo na tentativa caso o produto fosse excluído.

## Versão 103.3.2

![Correção](../assets/fix.svg) Corrigido um problema no qual o campo `modifiedAt` não estava presente nos feeds de entidades removidos.

## Versão 103.3.1

![Correção](../assets/fix.svg) Corrigido um problema que fazia com que uma mensagem `Invalid Template File` fosse exibida durante a reindexação do feed de produtos quando o Page Builder estava instalado.

## Versão 103.3.0

![Novo](../assets/new.svg) tabelas de feeds de exportação imediata migradas para a estrutura unificada:
`id`, `source_entity_id`, `feed_id`, `modified_at`, `is_deleted`, `status`, `feed_data`, `feed_hash`, `errors`

![Novo](../assets/new.svg) migrou os feeds de catálogo e inventário para a solução de exportação imediata.

![Novo](../assets/new.svg) cron-jobs de feed de exportação imediata renomeados para `*_feed_resend_failed_items`.

![Novo](../assets/new.svg) feed de exportação imediata renomeado e tabelas de log de alterações.

![Correção](../assets/fix.svg) Defina o campo `modified_at` nos dados de feed somente para feeds que o exijam.

![Correção](../assets/fix.svg) Modifique a consulta `productAttributes` para recuperar apenas atributos do produto.

## Versão 103.2.6

![Correção](../assets/fix.svg) Corrigido um problema que impedia que os feeds fossem reindexados quando as tabelas tinham um prefixo.

## Versão 103.2.5

![Correção](../assets/fix.svg) Otimizou a consulta de preço.

## Versão 103.2.4

![Correção](../assets/fix.svg) Corrigido o status incorreto do Stock que era exibido para um produto quando o Commerce Inventory management estava habilitado.

## Versão 103.2.3

![Corrigir](../assets/fix.svg) preços especiais no nível do site fixo.
![Correção](../assets/fix.svg) Adicionou mutex para todos os feeds processados.


## Versão 103.2.2

![Correção](../assets/fix.svg) Feeds aprimorados na estratégia de agrupamento para catálogos grandes. A tabela de lotes agora é preenchida com um número limitado de IDs para reduzir o uso da memória.

![Correção](../assets/fix.svg) Eliminou a dependência forte do CommerceInventoryDataExporter para módulos MSI.

![Corrigir](../assets/fix.svg) Logs `commerce-data-exporter` aprimorados para coletar mais informações e organizar por diferentes estágios de exportação.

## Versão 103.2.1

- Versão atualizada lançada.

## Versão 103.2.0

- Adição da sincronização de dados de vários threads para produtos e preços.
