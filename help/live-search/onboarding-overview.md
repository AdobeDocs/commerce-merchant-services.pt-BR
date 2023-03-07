---
title: "Visão geral da integração"
description: "[!DNL Live Search] fluxo de integração, requisitos, limites e limitações do sistema"
exl-id: 45f6c1ae-544b-47ef-9feb-c1a05f93108a
source-git-commit: 484319fc1df6c29c972b57c13bd0ed711e374e99
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 0%

---

# Visão geral da integração

Para começar a usar o [!DNL Live Search] para o Adobe Commerce, conclua o processo de integração para instalar a extensão, configurar as chaves de API e sincronizar o catálogo.

## Fluxo de integração

![[!DNL Live Search] diagrama de integração](assets/onboarding-flow.svg)

## Requisitos {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.4+
* PHP 8.1, 8.2
* [!DNL Composer]

### Plataformas compatíveis

* Adobe Commerce no local (EE) : 2.4.4+
* Adobe Commerce na nuvem (ECE): 2.4.4+

## Limites e limites

Neste momento, a [!DNL Live Search] A API de pesquisa/categoria tem os seguintes limites e limites estáticos compatíveis:

### Indexação

* Indexa até 300 atributos de produto por exibição de loja.
* Indexa somente produtos do banco de dados do Adobe Commerce.
* As páginas CMS não são indexadas.

### Query

* [!DNL Live Search] O não tem acesso à taxonomia completa da árvore de categoria, o que torna alguns cenários de pesquisa de navegação em camadas fora de seu alcance.
* [!DNL Live Search] O usa um endpoint exclusivo do GraphQL para consultas, a fim de oferecer suporte a recursos como facetas inteligentes e pesquisa conforme o tipo. Embora semelhante à [API MAGENTO GRAPHQL](https://developer.adobe.com/commerce/webapi/graphql/)Existem algumas diferenças e alguns campos podem não ser totalmente compatíveis no momento.

### Regras

* O número máximo de regras por exibição de loja é 50.
* O número máximo de condições por regra é 10.
* O número máximo de eventos por regra é 25.

### Sinônimos

* [!DNL Live Search] O pode gerenciar até 200 sinônimos por exibição de loja.

### versão beta do PWA

* A implementação beta atual do PWA do Live Search requer mais tempo de processamento para retornar resultados de pesquisa do que o Live Search com a loja nativa do Commerce.
* A versão beta do PWA para [!DNL Live Search] não suporta [manipulação de eventos](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).
* Os seguintes atributos de produto não são compatíveis com o GraphQL quando usados em relação à versão beta do [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### Não suportado no momento

* A variável [Pesquisa avançada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) o módulo é desativado quando [!DNL Live Search] O está instalado e o link Pesquisa avançada no rodapé da loja é removido.
* [Grupos de preços personalizados](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-group.html)
* Várias localizações de estoque conforme usadas por [MCOM](https://experienceleague.adobe.com/docs/commerce-admin/systems/integrations/mcom.html) ou outras extensões OMS
* Os preços do produto não incluem [imposto sobre o valor acrescentado](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/taxes/vat.html) (IVA)
