---
title: '[!DNL Live Search] Eventos'
description: Saiba como os eventos coletam dados para  [!DNL Live Search].
feature: Services, Eventing
exl-id: b0c72212-9be0-432d-bb8d-e4c639225df3
source-git-commit: 0d966c8dbd788563fa453912961fdc62a5a6c23e
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# [!DNL Live Search] Eventos

[!DNL Live Search] usa eventos para potencializar algoritmos de pesquisa como &quot;Mais visualizados&quot; e &quot;Visualizou isto, Visualizou aquilo&quot;. Enquanto os usuários da LUMA obtêm eventos prontos para uso, as implementações headless e outras implementações personalizadas precisam implementar eventos para suas próprias necessidades.

Como [!DNL Live Search] e [!DNL Product Recommendations] usam o mesmo algoritmo de back-end, alguns eventos são compartilhados por ambos os serviços. Alguns eventos do Recommendations de produtos são necessários para preencher o Painel do Recommendations.

Esta tabela descreve os eventos usados por [!DNL Live Search] estratégias.

| Estratégia | Produtos | Eventos | Página |
| --- | --- | --- | ---|
| Mais visualizados | Live Search<br>Registros de Produtos | exibição de página<br>exibição de produto | Página de detalhes do produto |
| Mais comprados | Live Search<br>Registros de Produtos | exibição de página<br>concluir check-out | Carrinho/Check-out |
| Mais adicionados ao carrinho | Live Search<br>Registros de Produtos | exibição de página<br>adicionar ao carrinho | Página de detalhes do produto<br>Página de listagem do produto<br>Carrinho<br>Lista de desejos |
| Visualizou isto, visualizou aquilo | Live Search<br>Registros de Produtos | exibição de página<br>exibição de produto | Página de detalhes do produto |
| Tendências | Live Search<br>Registros de Produtos | exibição de página<br>exibição de produto | Página de detalhes do produto |
| Visualizou isto, comprou aquilo | Registros de produto | exibição de página<br>exibição de produto | Página de detalhes do produto<br>Carrinho/Check-out |
| Comprei isto, comprei aquilo | Registros de produto | exibição de página<br>exibição de produto | Página de detalhes do produto |
| Conversão: exibir para compra | Registros de produto | exibição de página<br>exibição de produto | Página de detalhes do produto |
| Conversão: exibir para compra | Registros de produto | exibição de página<br>concluir check-out | Carrinho/Check-out |
| Conversão: exibir para carrinho | Registros de produto | exibição de página<br>exibição de produto | Página de detalhes do produto |
| Conversão: exibir para carrinho | Registros de produto | exibição de página<br>adicionar ao carrinho | Página de detalhes do produto<br>Página de listagem do produto<br>Carrinho<br>Lista de desejos |

>[!NOTE]
>
>A coleta de dados para os fins de [!DNL Live Search] não inclui informações de identificação pessoal (PII). Todos os identificadores de usuários, como IDs de cookies e endereços IP, são estritamente anônimos. [Saiba mais](https://www.adobe.com/privacy/experience-cloud.html).

## Eventos de painel obrigatórios

Alguns eventos são necessários para preencher o [painel do Live Search](performance.md)

| Área do painel | Eventos | Ingressar no campo |
| ------------------- | ------------- | ---------- |
| Pesquisas únicas | `page-view`, `search-request-sent`, | searchRequestId |
| Nenhuma pesquisa de resultados | `page-view`, `search-request-sent`, | searchRequestId |
| Taxa de resultados zero | `page-view`, `search-request-sent`, | searchRequestId |
| Pesquisas populares | `page-view`, `search-request-sent`, | searchRequestId |
| Média posição do clique | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | searchRequestId |
| Taxa de cliques | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click` | searchRequestId, sku |
| Índice de conversão | `page-view`, `search-request-sent`, `search-response-received`, `search-results-view`, `search-product-click`, `product-view`, `add-to-cart`, `place-order` | searchRequestId, sku |

### Contextos obrigatórios

Todos os eventos exigem os contextos `Page` e `Storefront`. Isso deve acontecer no nível da página/camada do aplicativo da loja em vez de ao gerar eventos individuais (por exemplo, em uma loja PHP, o contêiner do aplicativo PHP é responsável por configurá-los no tempo de execução).

## Uso

Esta é uma amostra de implementação do evento `search-request-sent`:

```javascript
const mse = window.magentoStorefrontEvents;

/* set in application container */
// mse.context.page(pageCtx);
// mse.context.setStorefrontInstance(storefrontCtx);

/* set before firing event */
mse.context.setSearchInput(searchInputCtx);
mse.publish.searchRequestSent("search-bar");
```

## Avisos

Os bloqueadores de anúncios e as configurações de privacidade podem impedir que eventos sejam capturados e podem fazer com que as [métricas](workspace.md) de envolvimento e receita sejam reportadas incorretamente.

O evento não captura todas as transações que ocorrem no site do comerciante. O objetivo do evento é dar ao comerciante uma ideia geral dos eventos que estão acontecendo no site.

As implementações headless devem implementar eventos para alimentar o [painel do Product Recommendations](../product-recommendations/events.md).

>[!NOTE]
>
>Se o [Modo de restrição de cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) estiver habilitado, a Adobe Commerce não coletará dados comportamentais até que o comprador consente em usar cookies. Se o Modo de restrição de cookie estiver desativado, o Adobe Commerce coletará dados comportamentais por padrão.
