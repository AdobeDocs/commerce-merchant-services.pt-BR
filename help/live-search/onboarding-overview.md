---
title: "Visão geral da integração"
description: "[!DNL Live Search] fluxo de integração, requisitos, limites e limitações do sistema"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---

# Visão geral da integração

Para começar a usar o [!DNL Live Search] para o Adobe Commerce, conclua o processo de integração para instalar a extensão, configurar as chaves de API e sincronizar o catálogo.

## Fluxo de integração

![[!DNL Live Search] diagrama de integração](assets/onboarding-flow.svg)

## Requisitos {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### Plataformas compatíveis

* Adobe Commerce no local (EE) : 2.4.4+
* Adobe Commerce na nuvem (ECE): 2.4.4+

## Limites e limites

Atualmente, a [!DNL Live Search] A API de pesquisa/categoria tem os seguintes limites e limites estáticos compatíveis:

### Indexação

* Indexa até 300 atributos de produto por exibição de loja.
* Indexa somente produtos do banco de dados do Adobe Commerce.
* Os produtos devem estar no Catálogo compartilhado padrão.
* As páginas CMS não são indexadas.

### Query

* [!DNL Live Search] O não tem acesso à taxonomia completa da árvore de categoria, o que torna alguns cenários de pesquisa de navegação em camadas fora de seu alcance.
* [!DNL Live Search] O usa um endpoint exclusivo do GraphQL para consultas, a fim de oferecer suporte a recursos como facetas dinâmicas e pesquisa conforme o tipo. Embora semelhante à [API do GraphQL](https://developer.adobe.com/commerce/webapi/graphql/)Existem algumas diferenças e alguns campos podem não ser totalmente compatíveis.

Para restringir grupos de clientes usando permissões de Catálogo:

* Os produtos devem ser atribuídos à categoria Raiz.
* O grupo de clientes &quot;Não conectado&quot; deve receber permissões de navegação &quot;Permitir&quot;.
* Para restringir produtos ao grupo de clientes Não Conectado, vá para cada categoria e defina permissões para cada grupo de clientes.

### Regras

* O número máximo de regras por exibição de loja é 50.
* O número máximo de condições por regra é 10.
* O número máximo de eventos por regra é 25.

### Sinônimos

* [!DNL Live Search] O pode gerenciar até 200 sinônimos por exibição de loja.

## Indexador de preços

Os clientes do Live Search podem usar o novo [Indexador de preços SaaS](../price-index/index.md), que oferece atualizações de alteração de preço e tempo de sincronização mais rápidos.

### suporte para PWA

[!DNL Live Search] funciona com o PWA Studio, mas os usuários podem ver pequenas diferenças em comparação a outras implementações do Commerce. Funcionalidades básicas, como pesquisa e listagem de produtos, funcionam em Venia, mas algumas permutas de Graphql podem não funcionar corretamente. Também pode haver diferenças de desempenho.

* A atual implementação do PWA de [!DNL Live Search] requer mais tempo de processamento para retornar resultados de pesquisa do que [!DNL Live Search] com a loja nativa do Commerce.
* [!DNL Live Search] O no PWA não suporta [manipulação de eventos](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Por isso, o merchandising inteligente não funcionará.
* Filtrar diretamente em `description`, `name`, `short_description` não é compatível com o GraphQL quando usado com [PWA](https://developer.adobe.com/commerce/pwa-studio/), mas são retornados com um filtro mais geral.

Para usar [!DNL Live Search] com o PWA Studio, os integradores também devem:

1. Instalar [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. Defina o `environmentId` no `storeDetails` objeto.

   ```javascript
   const storeDetails: StoreDetailsProps = {
       environmentId: <Storefront_ID>,
       websiteCode: "base",
       storeCode: "main_website_store",
       storeViewCode: "default",
       searchUnitId: searchUnitId,
       config: {
           minQueryLength: 5,
           pageSize: 8,
           currencySymbol: "$",
           },
       };
   ```

### Não suportado no momento

* A variável [Pesquisa avançada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) o módulo é desativado quando [!DNL Live Search] O está instalado e o link Pesquisa avançada no rodapé da loja é removido.
* Várias localizações de estoque conforme usadas por [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) ou outras extensões OMS
* Os preços do produto não incluem [imposto sobre o valor acrescentado](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (IVA)
* [Preço da camada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) não é compatível com o Popover do Live Search e com o Widget de página de listagem de produtos.

## Cookies

[!DNL Live Search] O coleta dados de interação do usuário como parte de sua funcionalidade básica, e os cookies são usados para armazenar esses dados. Ao coletar qualquer informação do usuário, ele deve concordar em armazenar cookies. [!DNL Live Search] e [!DNL Product Recommendations] compartilhar o fluxo de dados e, portanto, o mesmo mecanismo de cookie. Leia mais sobre isso em [Lidar com restrições de cookies](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
