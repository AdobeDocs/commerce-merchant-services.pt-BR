---
title: Indexação de preços SaaS
description: Usando a indexação de preços SaaS para melhorar o desempenho
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 747c0f3e-dfde-4365-812a-5ab7768342ab
source-git-commit: a93ada3230d3d29dd6b79f67a61ede38de7dc250
workflow-type: tm+mt
source-wordcount: '752'
ht-degree: 0%

---

# Indexação de preços SaaS

A indexação de preços SaaS acelera o tempo necessário para que as alterações de preço sejam refletidas no site de um cliente SaaS, após serem enviadas. Esse módulo opcional permite que comerciantes com catálogos grandes e complexos, ou com vários sites ou grupos de clientes, processem alterações de preço de forma mais rápida e contínua.

O maior gargalo do pipeline: processos computacionais pesados, como indexação e cálculo de preços, foram movidos do núcleo PHP para a infraestrutura Adobe Cloud. Isso permite que os comerciantes aumentem rapidamente os recursos para aumentar os tempos de indexação de preços e refletir essas alterações em sites com velocidades muito mais rápidas.

O fluxo de dados de indexação principal para serviços SaaS é semelhante a:

![Fluxo de dados padrão](assets/old_way.png)

Com a indexação de preços SaaS, o fluxo é:

![Fluxo de dados de indexação de preço SaaS](assets/new_way.png)

Todos os comerciantes que atendem aos requisitos podem se beneficiar dessas melhorias, mas os que verão os maiores ganhos são os clientes com:

* Alterações constantes de preço: comerciantes que exigem alterações repetidas em seus preços para atender a objetivos estratégicos, como promoções frequentes, descontos sazonais ou markdowns de inventário.
* Vários sites e/ou grupos de clientes: comerciantes com catálogos de produtos compartilhados em vários sites (domínios/marcas) e/ou grupos de clientes.
* Grande número de preços únicos em sites ou grupos de clientes: comerciantes com catálogos de produtos compartilhados extensos que contêm preços únicos em sites ou grupos de clientes, como comerciantes B2B com preços pré-negociados, marcas com estratégias de preços diferentes.

Se você tiver aplicativos de terceiros que dependem do indexador de preço principal do PHP, leia a documentação e consulte o provedor de extensão antes de fazer qualquer alteração.

A indexação de preços do SaaS está disponível gratuitamente para clientes que usam os serviços da Adobe Commerce.

Este miniguia descreve como a indexação de preços do SaaS funciona e como ativá-la.

## Requisitos do sistema

Para usar a indexação de preços SaaS, é necessário:

* Adobe Commerce 2.4.4+
* Pelo menos um dos seguintes serviços SaaS instalados:

   * [Serviço de catálogo](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Recommendations do produto](../product-recommendations/guide-overview.md)

## Módulos

A indexação de preço do SaaS usa um conjunto de módulos para fornecer funcionalidade. A lista de módulos necessários pode ser um pouco diferente, dependendo da configuração da loja.

Esses módulos adicionam os novos feeds ao Administrador. Esses feeds transferem dados necessários para cálculos de preço para o indexador SaaS e ignora o indexador de preço principal do PHP.

```
magento/module-saas-price
magento/module-saas-scopes
magento/module-product-override-price-remover
magento/module-bundle-product-override-data-exporter
```

Os clientes que usam o Luma e o Adobe Commerce Core GraphQL podem instalar um módulo que fornece compatibilidade com o Luma e o Core GraphQL e desativa o indexador de preço principal do PHP:

```
adobe-commerce/catalog-adapter
```

A variável `catalog-adapter` O só é compatível com a versão 2.4.5. O suporte para as versões 2.4.4 e 2.4.6 será lançado em breve.
O indexador de preço principal do PHP pode ser reativado se necessário por uma extensão de terceiros ou por qualquer outro motivo.

## Avisos

Dependendo de fatores como tipos de produto, complexidade de preço e tamanho do catálogo, a indexação de preço do SaaS pode ser a solução certa para sua loja. Leia as limitações a seguir e determine se esta é uma boa solução para o site.

Atualmente, a indexação de preços do SaaS é compatível com aplicativos simples, agrupados, virtuais, configuráveis e [Pacote dinâmico](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-bundle.html) tipos do produto.
Em breve, haverá suporte para tipos de produtos para download, cartões-presente e pacote fixo.

Os novos feeds devem ser sincronizados manualmente com o `resync` [comando CLI](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html#resynccmdline). Caso contrário, os dados serão atualizados no processo de sincronização padrão. Obter mais informações sobre o [Sincronização de catálogo](../landing/catalog-sync.md) processo.

## Cenários de uso

### Luma sem dependências de extensão

* Um comerciante do Luma ou do Abode Commerce Core GraphQL que tem um serviço necessário instalado (Live Search, Recommendations de produtos, Serviço de catálogo)
* Nenhuma extensão de terceiros depende do indexador de preço principal do PHP
* Venda de produtos dinâmicos simples, configuráveis, agrupados, virtuais e de pacotes

1. Ative novos feeds.
1. Instale o adaptador do catálogo.

### GraphQl principal do Commerce Luma e Abode com dependências do indexador de preço principal do PHP

* Um comerciante do Luma ou do Abode Commerce Core GraphQL que tem um serviço compatível instalado (Live Search, Recommendations de produtos, Serviço de catálogo)
* Com uma extensão de terceiros dependendo do indexador de preço principal do PHP
* Venda de produtos dinâmicos simples, configuráveis, agrupados, virtuais e de pacotes

1. Ativar os novos feeds
1. Instale o adaptador do catálogo.
1. Reative o indexador de preço principal do PHP.
1. Use novos feeds e o código de compatibilidade Luma no `catalog-adapter` módulo.

### Comerciante headless

* Um comerciante headless que tem um serviço compatível instalado (Live Search, Recommendations de produtos, Serviço de catálogo)
* Nenhuma dependência do indexador de preço principal do PHP
* Venda de produtos dinâmicos simples, configuráveis, agrupados, virtuais e de pacotes

1. Ativar novos feeds
1. Instale o adaptador do catálogo, que desativa o indexador de preço principal do PHP.

### Luma/Core GraphQL/Headless com tipos de produtos não compatíveis

* Comerciante da Luma/Headless
* Venda de cartões-presente, produtos fixos para download ou pacotes

Com os tipos de produtos não suportados no momento, aguarde o suporte completo para o tipo de produto.
