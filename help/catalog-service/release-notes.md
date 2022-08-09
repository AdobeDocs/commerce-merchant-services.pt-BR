---
title: '"[!DNL Catalog Service] Notas de versão"'
description: '"As informações mais recentes da versão para [!DNL Catalog Service] para Adobe Commerce."'
source-git-commit: 3959cc5d07f9a0da0ba772a4f3bc56adeb3c6bf3
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 2%

---


# [!DNL Catalog Service] Notas de versão

{{catalog-service-beta}}

Essas notas de versão descrevem as versões mais recentes da [!DNL Catalog Service] e incluem:

* ![Novo](../assets/new.svg) - Novos recursos
* ![Correção](../assets/fix.svg) - Correções e melhorias
* ![Bug](../assets/bug.svg) - Problemas conhecidos

## Versão beta

* ![Novo](../assets/new.svg) - O `products` e `refineProduct` as consultas retornam os seguintes dados:
   * Atributos de produto predefinidos (do sistema).
   * Atributos dinâmicos do produto e os filtre por função (página de exibição do produto/página de lista de produtos).
   * Opções de produto.
   * Imagens do produto e filtrá-las por função (PDP/PLP).
   * Um preço específico para produtos simples e intervalos de preço para produtos configuráveis.
   * Preços e intervalos de preços do grupo de clientes. Eles retornam um preço padrão de fallback para compradores sem um grupo de clientes.
   * Tipos de produto que usam preços específicos de clientes B2B.

## Limitações conhecidas

* Os preços de camada não são suportados.
* Em uma matriz de imagens, somente a primeira imagem contém funções.
* As imagens para variantes não são recuperadas.
* As atualizações não são recebidas quando os produtos ou variantes são excluídos do catálogo.
