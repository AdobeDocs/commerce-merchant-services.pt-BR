---
title: Visão geral da integração
description: Fluxo de integração do Live Search, requisitos do sistema, limites e limitações
source-git-commit: 6220824c6032a33a760fe5c2bb5d2346e00a074b
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Visão geral da integração

Para começar a usar o Live Search for Adobe Commerce, você deve concluir algumas etapas de integração para instalar a extensão, configurar as chaves da API e sincronizar o catálogo.

## Fluxo de integração

![Diagrama de integração do Live Search](assets/onboarding-flow.svg)

## Requisitos {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3 / 7.4
* [!DNL Composer]

### Plataformas compatíveis

* Adobe Commerce no local (EE) : 2.4.x
* Adobe Commerce on Cloud (ECE) : 2.4.x

## Limites e limites

No momento, a API de categoria/pesquisa do Live Search tem os seguintes limites compatíveis e limites estáticos:

### Indexação

* Índices até 300 atributos de produto por visualização de loja
* Indexa somente produtos do banco de dados do Adobe Commerce
* Não indexa páginas CMS

### Limites da consulta

* O Live Search não tem acesso à taxonomia completa da árvore de categorias, o que faz com que alguns cenários de pesquisa de navegação em camadas estejam além de seu alcance.
* O Live Search usa um endpoint GraphQL exclusivo para consultas para oferecer suporte a recursos como lapidamento inteligente e pesquisa por tipo. Embora semelhantes ao [API Magento GraphQL](https://devdocs.magento.com/guides/v2.4/graphql), há algumas diferenças e alguns campos podem não ser totalmente compatíveis no momento.

### Versão beta do PWA

* A versão beta do PWA para Live Search não é compatível [tratamento de evento](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).
* Os atributos de produto a seguir não são suportados pelo GraphQL quando usados em relação à versão beta de [PWA](https://developer.adobe.com/commerce/pwa-studio/): `description`, `name`, `short_description`

### Não suportado no momento

* O [Pesquisa avançada](https://docs.magento.com/user-guide/catalog/search-advanced.html) é desativado quando o Live Search é instalado e o link Pesquisa avançada no rodapé da loja é removido.
* [Grupos de clientes](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [Grupos de preços personalizados](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* Várias localizações de inventário, conforme usado por [MCOM](https://docs.magento.com/user-guide/mcom.html) ou outras extensões OMS
* [Recursos B2B integrados](https://business.adobe.com/products/magento/b2b-ecommerce.html)
