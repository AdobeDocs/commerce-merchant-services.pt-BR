---
title: Coletar dados
description: Saiba como os eventos coletam dados para recomendações de produto.
exl-id: b827d88c-327f-4986-8239-8f1921d8383c
source-git-commit: 78f226465b9d84707612596a5aa4622aa7869ee1
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Coletar dados

Ao instalar e configurar recursos Adobe Commerce baseados em SaaS, como [Recommendations do produto](install-configure.md) ou [Live Search](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html), os módulos implantam a coleta de dados comportamentais na loja. Esse mecanismo coleta dados comportamentais anônimos de seus compradores e alimenta as recomendações do produto. Por exemplo, a variável `view` é usado para calcular o `Viewed this, viewed that` tipo de recomendação e o `place-order` é usado para calcular o `Bought this, bought that` tipo de recomendação.

>[!NOTE]
>
>A coleta de dados para fins de recomendações do Produto não inclui informações de identificação pessoal (PII). Todos os identificadores de usuário, como IDs de cookies e endereços IP, são estritamente anonimizados. [Saiba mais](https://www.adobe.com/privacy/experience-cloud.html).

Os seguintes eventos não são específicos do Recommendations do produto, mas são solicitados a retornar resultados:

- `view`
- `add-to-cart`
- `place-order`

O [Coletor de eventos de vitrine do Adobe Commerce](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/#quick-start) lista todos os eventos implantados em sua loja. A partir dessa lista, no entanto, há um subconjunto de eventos específicos do Recommendations do produto. Esses eventos coletam dados quando os compradores interagem com unidades de recomendação na loja e potencializam as métricas usadas para ajudá-lo a analisar o desempenho de suas recomendações.

| Evento | Descrição | [Usado para métricas?](workspace.md) |
| --- | --- | --- |
| `impression-render` | A unidade de recomendação é renderizada na página. | Sim |
| `rec-add-to-cart-click` | O cliente clica no **Adicionar ao carrinho** botão para um item na unidade de recomendação. | Sim, quando uma **Adicionar ao carrinho** está presente no modelo de recomendações. |
| `rec-click` | O cliente clica em um produto na unidade de recomendação. | Sim |
| `view` | A unidade de recomendação fica visível na página, por exemplo, ao rolar para a exibição. | Sim |

Se a loja estiver implementada com o PWA Studio, consulte a [Documentação do PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Se você usar uma tecnologia de front-end personalizada, como React ou Vue JS, consulte o guia do usuário para saber como integrar o Recommendations do produto em uma [impiedoso](headless.md) ambiente.

Bloqueadores de anúncios e configurações de privacidade podem impedir que o `magento/product-recommendations` módulo de captura de eventos e pode causar envolvimento e receita [métricas](workspace.md) ser subnotificados.

>[!NOTE]
>
>If [Modo de restrição de cookie](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) estiver habilitado, o Adobe Commerce não coletará dados comportamentais até que o comprador aceite usar cookies. Se o Modo de restrição de cookies estiver desativado, o Adobe Commerce coletará dados comportamentais por padrão.
