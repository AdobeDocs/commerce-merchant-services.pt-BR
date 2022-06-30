---
title: Cabeça
description: Saiba como integrar [!DNL Product Recommendations] em uma vitrine sem cabeça.
exl-id: 316d0b0c-5938-4e2f-9d0d-747746cf6056
source-git-commit: ce437d7a991affd2665c86c9e91bb7f39ec626c0
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Cabeça

É possível integrar [!DNL Product Recommendations] em uma loja sem interface usando [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/) ou uma tecnologia de primeiro plano personalizada, como React ou Vue JS.

[!DNL Product Recommendations] exigir [dados comportamentais e de catálogo](https://devdocs.magento.com/recommendations/product-recs.html#typesofdata) para operar. O processo de sincronização de dados do catálogo permanece inalterado em uma implementação sem cabeçalho, mas as alterações são necessárias para a coleta de dados comportamentais.

Para integrar [!DNL Product Recommendations] em uma vitrine sem interface, você deve:

1. Envie dados comportamentais ao Adobe Sensei para analisar e calcular os resultados da Recomendação do produto. Também é possível enviar dados adicionais para ativar a recomendação do produto [relatórios de métricas](workspace.md).

1. Busque resultados de recomendações de produtos e renderize esses resultados na página.

Você pode executar ambas as ações usando os SDKs disponíveis, conforme descrito no seguinte workflow.

1. [Instalar](install-configure.md) o [!DNL Product Recommendations] módulo.

1. Instalar e usar o [SDK do evento de loja da Adobe Commerce](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) para acionar a [eventos comportamentais](https://devdocs.magento.com/recommendations/events.html).

   Os eventos mínimos necessários para retornar [!DNL Product Recommendations] resultados:

   | Evento | Categoria |
   |--- | ---|
   | `view` | produto |
   | `add-to-cart` | produto |
   | `place-order` | checkout |

   Para ativar [relatórios de métricas](workspace.md), os seguintes eventos adicionais são obrigatórios:

   | Evento | Categoria |
   |--- | ---|
   | `impression-render` | unidade de recomendação |
   | `view` | unidade de recomendação |
   | `rec-click` | unidade de recomendação |
   | `rec-add-to-cart-click` | unidade de recomendação (se um botão adicionar ao carrinho estiver presente no modelo de recomendações) |

1. Quando os eventos forem acionados, use a variável [Coletor de eventos de vitrine do Adobe Commerce](https://devdocs.magento.com/shared-services/storefront-event-collector.html) para lidar com os eventos e enviá-los para o Adobe Sensei.

1. Depois que os dados comportamentais forem coletados, você poderá [criar](create.md) [!DNL Product Recommendations] em Admin.

1. Use o [Recommendations SDK](https://devdocs.magento.com/recommendations/recs-api.html) para buscar as unidades de recomendação na loja. O SDK retorna os dados de produto necessários para renderizar unidades de recomendação em uma página.
