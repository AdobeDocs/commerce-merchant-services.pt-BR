---
title: Coletar dados
description: Saiba como os eventos coletam dados para recomendações de produto.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
feature: Services, Recommendations, Eventing
source-git-commit: 7ed9321a2f4e58a7476aa91e74611fe896e1a7b1
workflow-type: tm+mt
source-wordcount: '417'
ht-degree: 0%

---

# Coletar dados

Ao instalar e configurar recursos SaaS do Adobe Commerce, como [Recommendations do produto](install-configure.md) ou [Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html), os módulos implantam a coleção de dados comportamentais na loja. Esse mecanismo coleta dados comportamentais anônimos dos compradores e oferece recomendações de produtos. Por exemplo, a variável `view` evento é usado para calcular o `Viewed this, viewed that` tipo de recomendação e a `place-order` evento é usado para calcular o `Bought this, bought that` tipo de recomendação.

>[!NOTE]
>
>A coleta de dados para os fins das recomendações de produto não inclui informações de identificação pessoal (PII). Todos os identificadores de usuários, como IDs de cookies e endereços IP, são estritamente anônimos. Saiba mais [mais](https://www.adobe.com/privacy/experience-cloud.html).

Os eventos a seguir não são específicos do Recommendations do produto, mas são necessários para retornar resultados:

- `view`
- `add-to-cart`
- `place-order`

A variável [Coletor de eventos da vitrine Adobe Commerce](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) lista todos os eventos implantados em sua loja. Nessa lista, no entanto, há um subconjunto de eventos específicos do Recommendations do produto. Esses eventos coletam dados quando os compradores interagem com as unidades de recomendação na loja e potencializam as métricas usadas para ajudar você a analisar o desempenho de suas recomendações.

| Evento | Descrição | Usado para métricas? |
| --- | --- | --- |
| `impression-render` | A unidade de recomendação é renderizada na página. | Sim |
| `rec-add-to-cart-click` | O cliente clica no link **Adicionar ao carrinho** para um item na unidade de recomendação. | Sim, quando um **Adicionar ao carrinho** O botão está presente no modelo de recomendações. |
| `rec-click` | O cliente clica em um produto na unidade de recomendação. | Sim |
| `view` | A unidade de recomendação se torna visível na página, como ao rolar a tela para exibição. | Sim |

Os eventos a seguir são necessários para preencher corretamente o painel.
| Coluna do painel | Eventos | Ingressar no campo | | — | — | — | | Impressões |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render` | unitId | | Visualizações |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view` | unitId | | Cliques |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`    | unitId | | Receita |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId, sku | | Receita LT |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-item-click`, `recs-add-to-cart-click`, `place-order` | unitId, sku | | CTR |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-item-click`, `recs-add-to-cart-click`  | unitId, sku | | vCTR |`page-view`, `recs-request-sent`, `recs-response-received`, `recs-unit-render`, `recs-unit-view`, `recs-item-click`, `recs-add-to-cart-click` | unitId, sku |

Se sua loja for implementada com o PWA Studio, consulte a [Documentação do PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Se você usar uma tecnologia de front-end personalizada, como React ou Vue JS, consulte o guia do usuário para saber como integrar [Recommendations de produtos em um headless](headless.md) ambiente.

## Avisos

Os bloqueadores de anúncios e as configurações de privacidade podem impedir a `magento/product-recommendations` da captura de eventos e pode causar o envolvimento e a receita de [métricas](workspace.md) ser subcomunicados.

O evento não captura todas as transações que ocorrem no site do comerciante. O objetivo do evento é dar ao comerciante uma ideia geral dos eventos que estão acontecendo no site.

As implementações headless devem implementar eventos para acionar o painel de produtos do Recommendations.

>[!NOTE]
>
>Se [Modo de restrição de cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) estiver ativado, a Adobe Commerce não coletará dados comportamentais até que o comprador consinta em usar cookies. Se o Modo de restrição de cookie estiver desativado, o Adobe Commerce coletará dados comportamentais por padrão.
