---
title: Coletar dados
description: Saiba como os eventos coletam dados para recomendações de produto.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: 67296ea42bfddb10b0c86cb1ca47324f5fec7825
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# Coletar dados

Quando você instala e configura recursos do Adobe Commerce baseados em SaaS, como o [Product Recommendations](install-configure.md) ou o [Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html), os módulos implantam a coleção de dados comportamentais na loja. Esse mecanismo coleta dados comportamentais anônimos dos compradores e oferece recomendações de produtos. Por exemplo, o evento `view` é usado para calcular o tipo de recomendação `Viewed this, viewed that`, e o evento `place-order` é usado para calcular o tipo de recomendação `Bought this, bought that`.

>[!NOTE]
>
>A coleta de dados para os fins das recomendações de produto não inclui informações de identificação pessoal (PII). Todos os identificadores de usuários, como IDs de cookies e endereços IP, são estritamente anônimos. Saiba [mais](https://www.adobe.com/privacy/experience-cloud.html).

Os eventos a seguir não são específicos do Recommendations do produto, mas são necessários para retornar resultados:

- `view`
- `add-to-cart`
- `place-order`

O [Coletor de Eventos da Adobe Commerce Storefront](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) lista todos os eventos implantados na sua loja. Nessa lista, no entanto, há um subconjunto de eventos específicos do Recommendations do produto. Esses eventos coletam dados quando os compradores interagem com as unidades de recomendação na loja e potencializam as métricas usadas para ajudar você a analisar o desempenho de suas recomendações.

| Evento | Descrição | Usado para métricas? |
| --- | --- | --- |
| `impression-render` | A unidade de recomendação é renderizada na página. | Sim |
| `rec-add-to-cart-click` | O cliente clica no botão **Adicionar ao carrinho** para um item na unidade de recomendação. | Sim, quando um botão **Adicionar ao carrinho** estiver presente no modelo de recomendações. |
| `rec-click` | O cliente clica em um produto na unidade de recomendação. | Sim |
| `view` | A unidade de recomendação se torna visível na página, como ao rolar a tela para exibição. | Sim |

Os eventos a seguir são necessários para preencher corretamente o painel.

| Coluna do painel | Eventos | Ingressar no campo |
| ---------------- | --------- | ----------- |
| Impressões | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render` | unitId |
| Visualizações | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view` | unitId |
| Cliques | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click` | unitId |
| Receita | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId, sku |
| Receita LT | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId, sku |
| CTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-item-click`, `recs-add-to-cart-click` | unitId, sku |
| vCTR | `page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view`, `recs-item-click`, `recs-add-to-cart-click` | unitId, sku |

Se sua loja foi implementada com o PWA Studio, consulte a [documentação do PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Se você usar uma tecnologia de front-end personalizada, como o React ou o Vue JS, consulte o guia do usuário para saber como integrar o [Product Recommendations em um ambiente headless](headless.md).

## Avisos

Os bloqueadores de anúncios e as configurações de privacidade podem impedir que o módulo `magento/product-recommendations` capture eventos e podem fazer com que as [métricas](workspace.md) de envolvimento e receita sejam reportadas incorretamente.

O evento não captura todas as transações que ocorrem no site do comerciante. O objetivo do evento é dar ao comerciante uma ideia geral dos eventos que estão acontecendo no site.

As implementações headless devem implementar eventos para acionar o painel de produtos do Recommendations.

>[!NOTE]
>
>Se o [Modo de restrição de cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) estiver habilitado, a Adobe Commerce não coletará dados comportamentais até que o comprador consente em usar cookies. Se o Modo de restrição de cookie estiver desativado, o Adobe Commerce coletará dados comportamentais por padrão.
