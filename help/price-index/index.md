---
title: Indexação de Preço SaaS
description: Usar a indexação de preço de SaaS para melhorar o desempenho
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: 3820736a25942b147d6e2c7b8820c360d6a0a535
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---

# Indexação de Preço SaaS

A indexação de preços do SaaS acelera o tempo necessário para que as alterações de preço sejam refletidas no site de um cliente do SaaS depois de terem sido enviadas. Esse módulo opcional permite que os comerciantes com catálogos grandes e complexos ou com vários sites ou grupos de clientes processem alterações de preços de forma mais rápida e contínua.

O maior gargalo do gasoduto: processos complexos em computação, como indexação e cálculo de preço, foram transferidos do núcleo PHP para a infraestrutura Adobe Cloud. Isso permite que os comerciantes dimensionem recursos rapidamente para aumentar os tempos de indexação de preços e refletir essas alterações em sites a velocidades muito mais rápidas.

Todos os comerciantes que atendem aos requisitos podem se beneficiar desses aprimoramentos, mas aqueles que obterão os maiores benefícios são os clientes com:

* Alterações constantes de preço: Comerciantes que exigem alterações repetidas em seus preços para atingir objetivos estratégicos, como promoções frequentes, descontos sazonais ou análises de inventário.
* Vários sites e/ou grupos de clientes: Comerciantes com catálogos de produtos compartilhados em vários sites (domínios/marcas) e/ou grupos de clientes.
* Grande número de preços únicos em sites ou grupos de clientes: Comerciantes com catálogos de produtos compartilhados extensos que contêm preços únicos em sites ou grupos de clientes, como comerciantes B2B com preços pré-negociados, marcas com diferentes estratégias de preços.

Se você tem aplicativos de terceiros que dependem do indexador de preço principal do PHP, leia a documentação e consulte o provedor de extensão antes de fazer qualquer alteração.

A indexação de preço SaaS está disponível gratuitamente para clientes que usam serviços Adobe Commerce.

Este miniguia descreve como a indexação de preços SaaS funciona e como habilitá-la.

## Requisitos do sistema

Para usar a indexação de preço SaaS, você precisa:

* Adobe Commerce 2.4.4+
* Pelo menos um dos seguintes serviços SaaS instalados:

   * [Serviço de catálogo](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Recommendations do produto](../product-recommendations/guide-overview.md)

## Módulos

A indexação de preço SaaS usa um conjunto de módulos para fornecer funcionalidade. A lista de módulos necessários pode ser um pouco diferente, dependendo da configuração da loja.

Esses módulos adicionam os novos feeds ao Administrador. Esses feeds transferem dados necessários para cálculos de preço para o indexador SaaS e ignora o indexador de preço principal PHP.

```
magento/module-saas-price
magento/module-saas-scopes
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

Os clientes que usam o Luma e o Adobe Commerce Core GraphQL podem instalar um módulo que oferece compatibilidade com o Luma e o Core GraphQL e desativa o indexador de preço principal PHP:

```
adobe-commerce/catalog-adapter
```

O `catalog-adapter` O é compatível somente com o 2.4.5. O suporte para 2.4.4 e 2.4.6 será lançado em breve.
O indexador de preço principal PHP pode ser reativado se necessário por uma extensão de terceiros ou qualquer outro motivo.

## Avisos

Dependendo de fatores como tipos de produto, complexidade de preço e tamanho do catálogo, a indexação de preço de SaaS pode ser a solução correta para sua loja. Leia as limitações a seguir e determine se essa é uma boa solução para seu site.

Atualmente, a indexação de preços SaaS suporta tipos de produtos Simples, Agrupado, Virtual, Configurável e Dinâmico de Pacote.
O suporte para os tipos de produtos Baixáveis, Cartões de presente e Pacote fixo será lançado em breve.

Os novos feeds devem ser sincronizados manualmente com a variável `resync` [comando CLI](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). Caso contrário, os dados serão atualizados no processo de sincronização padrão. Obter mais informações sobre o [Sincronização do catálogo](../landing/catalog-sync.md) processo.

## Cenários de uso

### Luma sem dependências de extensão

* Um comerciante Luma ou Abode Commerce Core GraphQL que tem um serviço necessário instalado (Live Search, Product Recommendations, Catalog Service)
* Nenhuma extensão de terceiros que dependa do indexador de preço principal PHP
* Venda de produtos dinâmicos simples, configuráveis, agrupados, virtuais e de pacotes

1. Habilite novos feeds.
1. Instale o adaptador de catálogo.

### Luma e Abode Commerce Core GraphQl com dependências do indexador de preço principal PHP

* Um comerciante Luma ou Abode Commerce Core GraphQL que tem um serviço suportado instalado (Live Search, Product Recommendations, Catalog Service)
* Com uma extensão de terceiros confiando no indexador de preço principal PHP
* Venda de produtos dinâmicos simples, configuráveis, agrupados, virtuais e de pacotes

1. Ativar os novos feeds
1. Instale o adaptador de catálogo.
1. Reative o indexador de preço principal PHP.
1. Use novos feeds e o código de compatibilidade do Luma no `catalog-adapter` módulo.

### Comerciante autônomo

* Um comerciante sem periféricos que tem um serviço suportado instalado (Live Search, Product Recommendations, Catalog Service)
* Sem dependência do indexador de preço principal PHP
* Venda de produtos dinâmicos simples, configuráveis, agrupados, virtuais e de pacotes

1. Ativar novos feeds
1. Instale o adaptador de catálogo, que desativa o indexador de preço principal PHP.

### Luma/Core GraphQL/Headless com tipos de produtos não compatíveis

* Comerciante Luma/Sem Cabeça
* Venda de cartões-presente, produtos fixos para download ou pacote

Com tipos de produtos atualmente não compatíveis, aguarde o suporte completo ao tipo de produto.
