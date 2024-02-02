---
title: '[!DNL Live Search] Eventos'
description: Saiba como os eventos coletam dados para [!DNL Live Search].
feature: Services, Eventing
exl-id: b0c72212-9be0-432d-bb8d-e4c639225df3
source-git-commit: 8d669cf6042340659574c86a43836a02954f24ce
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# [!DNL Live Search] Eventos

[!DNL Live Search] O usa eventos para potencializar algoritmos de pesquisa, como &quot;Mais visualizados&quot; e &quot;Visualizados isto, Visualizados aquilo&quot;. Enquanto os usuários da LUMA obtêm eventos prontos para uso, as implementações headless e outras implementações personalizadas precisam implementar eventos para suas próprias necessidades.

Desde [!DNL Live Search] e [!DNL Product Recommendations] usar o mesmo algoritmo de back-end, alguns eventos são compartilhados por ambos os serviços. Alguns eventos do Recommendations de produtos são necessários para preencher o Painel do Recommendations.

## Eventos

Esta tabela descreve os eventos usados pelo [!DNL Live Search] estratégias.

| Estratégia | Produtos | Eventos | Página |
| --- | --- | --- | ---|
| Mais visualizados | Live Search<br>Registros de produto | exibição de página<br>exibição do produto | Página de detalhes do produto |
| Mais comprados | Live Search<br>Registros de produto | exibição de página<br>concluir check-out | Carrinho/Check-out |
| Mais adicionados ao carrinho | Live Search<br>Registros de produto | exibição de página<br>adicionar ao carrinho | Página de detalhes do produto<br>Página da lista de produtos<br>Carrinho<br>Lista de desejos |
| Visualizou isto, visualizou aquilo | Live Search<br>Registros de produto | exibição de página<br>exibição do produto | Página de detalhes do produto |
| Tendências | Live Search<br>Registros de produto | exibição de página<br>exibição do produto | Página de detalhes do produto |
| Visualizou isto, comprou aquilo | Registros de produto | exibição de página<br>exibição do produto | Página de detalhes do produto<br>Carrinho/Check-out |
| Comprei isto, comprei aquilo | Registros de produto | exibição de página<br>exibição do produto | Página de detalhes do produto |
| Conversão: exibir para compra | Registros de produto | exibição de página<br>exibição do produto | Página de detalhes do produto |
| Conversão: exibir para compra | Registros de produto | exibição de página<br>concluir check-out | Carrinho/Check-out |
| Conversão: exibir para carrinho | Registros de produto | exibição de página<br>exibição do produto | Página de detalhes do produto |
| Conversão: exibir para carrinho | Registros de produto | exibição de página<br>adicionar ao carrinho | Página de detalhes do produto<br>Página da lista de produtos<br>Carrinho<br>Lista de desejos |

>[!NOTE]
>
>Recolha de dados para efeitos de [!DNL Live Search] não inclui informações de identificação pessoal (PII). Todos os identificadores de usuários, como IDs de cookies e endereços IP, são estritamente anônimos. [Saiba mais](https://www.adobe.com/privacy/experience-cloud.html).

## Eventos de painel obrigatórios

Alguns eventos são necessários para preencher o [Painel do Live Search](performance.md)

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

Todos os eventos exigem o `Page` e `Storefront` contextos. Isso deve acontecer no nível da página/camada do aplicativo da loja em vez de ao gerar eventos individuais (por exemplo, em uma loja PHP, o contêiner do aplicativo PHP é responsável por configurá-los no tempo de execução).

## Uso

Este é um exemplo de implementação do `search-request-sent` evento:

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

Os bloqueadores de anúncios e as configurações de privacidade podem impedir que eventos sejam capturados e podem causar o envolvimento e a receita [métricas](workspace.md) ser reportado de forma insuficiente.

O evento não captura todas as transações que ocorrem no site do comerciante. O objetivo do evento é dar ao comerciante uma ideia geral dos eventos que estão acontecendo no site.

As implementações headless devem implementar eventos para potencializar o [Painel do produto Recommendations](../product-recommendations/events.md).

>[!NOTE]
>
>Se [Modo de restrição de cookies](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) estiver ativado, a Adobe Commerce não coletará dados comportamentais até que o comprador consinta em usar cookies. Se o Modo de restrição de cookie estiver desativado, o Adobe Commerce coletará dados comportamentais por padrão.
