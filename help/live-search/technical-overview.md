---
title: "Visão geral técnica"
description: "[!DNL Live Search] fluxo de integração, requisitos, limites e limitações do sistema"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
recommendations: noCatalog
source-git-commit: e235073031cae1304eaae4605d2f94332e52284f
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 0%

---

# Visão geral técnica

Este tópico analisa os requisitos técnicos e dicas para a instalação e otimização [!DNL Live Search] para Adobe Commerce.

## Requisitos {#requirements}

* [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
* PHP 8.1 / 8.2
* [!DNL Composer]

### Plataformas compatíveis

* Adobe Commerce no local (EE) : 2.4.4+
* Adobe Commerce na nuvem (ECE): 2.4.4+

## Endpoint

[!DNL Live Search] se comunica por meio do endpoint em `https://catalog-service.adobe.io/graphql`.

Como [!DNL Live Search] não tem acesso à base de dados completa do produto, [!DNL Live Search] O GraphQL e o Commerce Core GraphQL não terão paridade completa.

É recomendável chamar a API SaaS diretamente, especificamente o endpoint do Serviço de catálogo.

* Obter desempenho e reduzir a carga do processador, ignorando o processo de banco de dados/Graphql do Commerce
* Aproveite o [!DNL Catalog Service] federação a ser chamada [!DNL Live Search], [!DNL Catalog Service], e [!DNL Product Recommendations] de um único endpoint.

Para alguns casos de uso, talvez seja melhor chamar [!DNL Catalog Service] para obter detalhes sobre o produto e casos semelhantes. Consulte [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) para obter mais informações.

Se você tiver uma implementação personalizada do headless, verifique a [!DNL Live Search] implementações de referência:

* [Widget do PLP](https://github.com/adobe/storefront-product-listing-page)
* [Campo do Live Search](https://github.com/adobe/storefront-search-as-you-type)

Se você não usar os componentes padrão, como o Adaptador de pesquisa ou widgets do Luma, ou Widgets CIF AEM, saiba que o evento (dados de sequência de cliques que alimentam o Adobe Sensei para Merchandising inteligente e métricas de desempenho) não funcionará imediatamente e requer desenvolvimento personalizado para implementar eventos headless.
A versão mais recente de [!DNL Live Search] já usa [!DNL Catalog Service] e as instalações [!DNL Catalog Service] módulos.

## Limites e limites

Atualmente, a [!DNL Live Search] A API de pesquisa/categoria tem os seguintes limites e limites estáticos compatíveis:

### Indexação

* [Índices](indexing.md) até 300 atributos de produto por exibição de loja.
* Indexa somente produtos do banco de dados do Adobe Commerce.
* As páginas CMS não são indexadas.

### Query

* [!DNL Live Search] O não tem acesso à taxonomia completa da árvore de categoria, o que torna alguns cenários de pesquisa de navegação em camadas fora de seu alcance.
* [!DNL Live Search] O usa um endpoint exclusivo do GraphQL para consultas, a fim de oferecer suporte a recursos como facetas dinâmicas e pesquisa conforme o tipo. Embora semelhante à [API do GraphQL](https://developer.adobe.com/commerce/webapi/graphql/)Existem algumas diferenças e alguns campos podem não ser totalmente compatíveis.

Para restringir grupos de clientes usando permissões de Catálogo:

* Os produtos devem ser atribuídos à categoria Raiz.
* O grupo de clientes &quot;Não conectado&quot; deve receber permissões de navegação &quot;Permitir&quot;.
* Para restringir produtos ao grupo de clientes Não Conectado, vá para cada categoria e defina permissões para cada grupo de clientes.

### Regras

* Número máximo de merchandising de pesquisa [regras](rules.md) por exibição de loja é 50.
* O merchandising por categoria pode ter uma regra por categoria.
* O número máximo de condições por regra é 10.
* O número máximo de eventos por regra é 25.

### Sinônimos

* [!DNL Live Search] pode gerenciar até 200 [sinônimos](synonyms.md) por exibição da loja.

## Suporte de idioma

[!DNL Live Search] os widgets suportam os seguintes idiomas:

|  |  |  |  |
|--- |--- |--- |--- |
| Idioma | Região | Código do idioma | Localidade do Magento |
| Búlgaro | Bulgária | bg_BG | bg_BG |
| Catalão | Espanha | ca_ES | ca_ES |
| Tcheco | República Checa | cs_CZ | cs_CZ |
| Dinamarquês | Dinamarca | da_DK | da_DK |
| Alemão | Alemanha | de_DE | de_DE |
| Grego | Grécia | el_GR | el_GR |
| Inglês | Reino Unido | en_GB | en_GB |
| Inglês | Estados Unidos | pt_BR | pt_BR |
| Espanhol | Espanha | es_ES | es_ES |
| Estoniano | Estônia | et_EE | et_EE |
| Basco | Espanha | eu_ES | eu_ES |
| Persa | Irã | fa_IR | fa_IR |
| Finlandês | Finlândia | fi_FI | fi_FI |
| Francês | França | fr_FR | fr_FR |
| Galego | Espanha | gl_ES | gl_ES |
| Hindi | Índia | hi_IN | hi_IN |
| Húngaro | Hungria | hu_HU | hu_HU |
| Indonésio | Indonésia | id_ID | id_ID |
| Italiano | Itália | it_IT | it_IT |
| Coreano | Coreia do Sul | ko_KR | ko_KR |
| Lituano | Lituânia | lt_LT | lt_LT |
| Letão | Letônia | lv_LV | lv_LV |
| Norueguês | Noruega - Bokmal | nb_NO | nb_NO |
| Holandês | Holanda | nl_NL | nl_NL |
| Português | Brasil | pt_BR | pt_BR |
| Português | Portugal | pt_PT | pt_PT |
| Romeno | Romênia | ro_RO | ro_RO |
| Russo | Rússia | ru_RU | ru_RU |
| Sueco | Suécia | sv_SE | sv_SE |
| Tailandês | Tailândia | th_TH | th_TH |
| Turco | Turquia | tr_TR | tr_TR |
| Chinês | China | zh_CN | zh_Hans_CN |
| Chinês | Taiwan | zh_TW | zh_Hant_TW |

Se o widget detectar que a configuração de idioma do administrador do Commerce (_Lojas_ > Configurações > _Configuração_ > _Geral_ > Opções de país) corresponde a um idioma suportado, o padrão é esse idioma. Caso contrário, os widgets padrão serão em inglês.

Os administradores também podem definir o idioma do [índice de pesquisa](settings.md#language), para ajudar a garantir melhores resultados de pesquisa.

## Merchandising de categoria

[Merchandising de categoria](category-merch.md) permite configurar [!DNL Live Search] para trabalhar no nível da categoria do produto.

Este vídeo é uma introdução ao Merchandising por categoria.

>[!VIDEO](https://video.tv.adobe.com/v/3424617)

## Repositório de código do widget

O widget Página de listagem de produtos e o widget de campo do Live Search estão disponíveis para download no repositório do github.

Isso permite que os desenvolvedores personalizem totalmente a funcionalidade e o estilo. Esses usuários hospedam o código enquanto ainda aproveitam o [!DNL Live Search] serviço.

* [Widget do PLP](https://github.com/adobe/storefront-product-listing-page)
* [Barra de pesquisa](https://github.com/adobe/storefront-search-as-you-type)

## Inventory management

[!DNL Live Search] suporta [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html) no Commerce (conhecido anteriormente como Inventário de várias origens ou MSI). Para habilitar o suporte completo, você deve [atualizar](install.md#update) o módulo de dependência `commerce-data-export` para a versão 102.2.0+.

[!DNL Live Search] retorna um valor booleano observando se um produto está disponível no Inventory management, mas não contém informações sobre qual origem tem o estoque.

## Indexador de preços

Os clientes do Live Search podem usar o novo [Indexador de preços SaaS](../price-index/index.md), que oferece atualizações de alteração de preço e tempo de sincronização mais rápidos.

## Suporte de preço

Os widgets do Live Search são compatíveis com a maioria, mas não com todos os tipos de preço compatíveis com o Adobe Commerce.

Atualmente, os preços básicos são suportados. Os preços avançados que não são compatíveis são:

* Custo
* Preço Mínimo Anunciado

Examinar [API Mesh](../catalog-service/mesh.md) para cálculos de preços mais complexos.

O formato de preço oferece suporte à configuração de localidade na instância do Commerce: *Lojas* > Configurações > *Configuração* > Geral > *Geral* > Opções locais > Local.

## suporte para PWA

[!DNL Live Search] funciona com o PWA Studio, mas os usuários podem ver pequenas diferenças em comparação a outras implementações do Commerce. Funcionalidades básicas, como pesquisa e listagem de produtos, funcionam em Venia, mas algumas permutas de Graphql podem não funcionar corretamente. Também pode haver diferenças de desempenho.

* A atual implementação do PWA de [!DNL Live Search] requer mais tempo de processamento para retornar resultados de pesquisa do que [!DNL Live Search] com a loja nativa do Commerce.
* [!DNL Live Search] O no PWA não suporta [manipulação de eventos](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Como resultado, os relatórios de pesquisa e o merchandising inteligente funcionarão.
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

## Não suportado no momento

* A variável [Pesquisa avançada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) o módulo é desativado quando [!DNL Live Search] O está instalado e o link Pesquisa avançada no rodapé da loja é removido.
* [Preços da camada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-tier.html) e [Preços Especiais](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) não são compatíveis com o [!DNL Live Search] Widget de página de listagem de campo e produto.

## Cookies

[!DNL Live Search] O coleta dados de interação do usuário como parte de sua funcionalidade básica, e os cookies são usados para armazenar esses dados. Ao coletar qualquer informação do usuário, ele deve concordar em armazenar cookies. [!DNL Live Search] e [!DNL Product Recommendations] compartilhar o fluxo de dados e, portanto, o mesmo mecanismo de cookie. Leia mais sobre isso em [Lidar com restrições de cookies](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie.html).
