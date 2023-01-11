---
title: "Visão geral de integração"
description: "[!DNL Live Search] fluxo de integração, requisitos do sistema, limites e limitações"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Visão geral da integração

Para começar a usar [!DNL Live Search] para o Adobe Commerce, conclua o processo de integração para instalar a extensão, configurar as chaves da API e sincronizar o catálogo.

## Fluxo de integração

![[!DNL Live Search] diagrama de integração](assets/onboarding-flow.svg)

## Requisitos {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3 / 7.4 / 8.1
* [!DNL Composer]

### Plataformas compatíveis

* Adobe Commerce no local (EE) : 2.4.x
* Adobe Commerce on Cloud (ECE) : 2.4.x

## Limites e limites

Nesse momento, a variável [!DNL Live Search] a API search/category tem os seguintes limites compatíveis e limites estáticos:

### Indexação

* Indexa até 300 atributos de produto por visualização de loja.
* Indexa somente produtos do banco de dados do Adobe Commerce.
* As páginas CMS não são indexadas.

### Query

* [!DNL Live Search] não tem acesso à taxonomia completa da árvore de categorias, o que faz com que alguns cenários de pesquisa de navegação em camadas estejam além do seu alcance.
* [!DNL Live Search] O usa um endpoint exclusivo da GraphQL para consultas para oferecer suporte a recursos como lapidamento inteligente e pesquisa como tipo. Embora semelhantes ao [API do Magento GraphQL](https://developer.adobe.com/commerce/webapi/graphql/), há algumas diferenças e alguns campos podem não ser totalmente compatíveis no momento.

### Regras

* O número máximo de regras por exibição de loja é 50.
* O número máximo de condições por regra é 10.
* O número máximo de eventos por regra é 25.

### Sinônimos

* [!DNL Live Search] O pode gerenciar até 200 sinônimos por visualização de loja.

### Versão beta do PWA

* A implementação beta PWA do Live Search atual requer mais tempo de processamento para retornar os resultados da pesquisa do que o Live Search com a vitrine nativa do Commerce.
* A versão beta do PWA para [!DNL Live Search] não suporta [tratamento de evento](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* Os seguintes atributos de produto não são compatíveis com o GraphQL quando usados em relação à versão beta de [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### Não suportado no momento

* O [Pesquisa avançada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) está desativado quando [!DNL Live Search] O está instalado e o link Pesquisa avançada no rodapé da loja é removido.
* [Grupos de preços personalizados](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-group.html)
* Várias localizações de inventário, conforme usado por [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) ou outras extensões OMS
* Os preços do produto não incluem [imposto sobre o valor acrescentado](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (IVA).
