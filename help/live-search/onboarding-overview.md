---
title: "Visão geral de integração"
description: "[!DNL Live Search] fluxo de integração, requisitos do sistema, limites e limitações"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 86e6fdb653278f3e70640155d697897a2ea1b674
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# Visão geral da integração

Para começar a usar [!DNL Live Search] para o Adobe Commerce, conclua o processo de integração para instalar a extensão, configurar as chaves da API e sincronizar o catálogo.

## Fluxo de integração

![[!DNL Live Search] diagrama de integração](assets/onboarding-flow.svg)

## Requisitos {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### Plataformas compatíveis

* Adobe Commerce no local (EE) : 2.4.4+
* Adobe Commerce on Cloud (ECE) : 2.4.4+

## Limites e limites

Atualmente, o [!DNL Live Search] a API search/category tem os seguintes limites compatíveis e limites estáticos:

### Indexação

* Indexa até 300 atributos de produto por visualização de loja.
* Indexa somente produtos do banco de dados do Adobe Commerce.
* Os produtos devem estar no Catálogo compartilhado padrão.
* As páginas CMS não são indexadas.

### Query

* [!DNL Live Search] não tem acesso à taxonomia completa da árvore de categorias, o que faz com que alguns cenários de pesquisa de navegação em camadas estejam além do seu alcance.
* [!DNL Live Search] O usa um endpoint exclusivo da GraphQL para consultas para oferecer suporte a recursos como lapidamento dinâmico e pesquisa como tipo. Embora semelhantes ao [API do GraphQL](https://developer.adobe.com/commerce/webapi/graphql/), há algumas diferenças e alguns campos podem não ser totalmente compatíveis.

Para restringir grupos de clientes usando permissões de Catálogo:

* Os produtos devem ser atribuídos à categoria Raiz.
* O grupo de clientes &quot;Não conectado&quot; deve receber permissões de navegação &quot;Permitir&quot;.
* Para restringir os produtos ao grupo de clientes Não conectados, vá para cada categoria e defina a permissão para cada grupo de clientes.

### Regras

* O número máximo de regras por exibição de loja é 50.
* O número máximo de condições por regra é 10.
* O número máximo de eventos por regra é 25.

### Sinônimos

* [!DNL Live Search] O pode gerenciar até 200 sinônimos por visualização de loja.

## Indexador de preços

Os clientes do Live Search podem usar o novo [Indexador de preço SaaS](../price-index/index.md), que fornece atualizações de alteração de preço e tempo de sincronização mais rápidos.

### Suporte a PWA

O suporte do Live Search é considerado beta porque nem todo o PWA foi testado com [!DNL Live Search]. Funcionalidades básicas, como pesquisa e página de listagem de produtos, funcionam em Venia, mas algumas permutas de Graphql podem não funcionar corretamente.

* A implementação atual do PWA beta [!DNL Live Search] requer mais tempo de processamento para retornar os resultados da pesquisa do que [!DNL Live Search] com a loja nativa do Commerce.
* [!DNL Live Search] no PWA não suporta [tratamento de evento](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* Filtragem diretamente em `description`, `name`, `short_description` não é compatível com o GraphQL quando usado com [PWA](https://developer.adobe.com/commerce/pwa-studio/), mas são retornados com um filtro mais geral.

### Não suportado no momento

* O [Pesquisa avançada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) está desativado quando [!DNL Live Search] O está instalado e o link Pesquisa avançada no rodapé da loja é removido.
* Várias localizações de inventário, conforme usado por [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) ou outras extensões OMS
* Os preços do produto não incluem [imposto sobre o valor acrescentado](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (IVA).
* [Preço da camada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) não é compatível com o Live Search Popover e o Widget de página de listagem de produtos.

## Cookies

[!DNL Live Search] O coleta dados de interação do usuário como parte de sua funcionalidade básica e os cookies são usados para armazenar esses dados. Ao coletar qualquer informação do usuário, ele deve concordar em armazenar cookies. [!DNL Live Search] e [!DNL Product Recommendations] compartilhar o fluxo de dados e, portanto, o mesmo mecanismo de cookie. Leia mais sobre isso em [Lidar com restrições de cookies](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
