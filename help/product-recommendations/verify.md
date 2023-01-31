---
title: Verificar Coleção de Eventos
description: Saiba como verificar se os dados comportamentais estão sendo enviados para o Adobe Commerce.
exl-id: c8c34db4-9d87-4012-b8f0-e9b1da214305
source-git-commit: d8be88f47f103c5d632540dae743ede398a9b7ad
workflow-type: tm+mt
source-wordcount: '451'
ht-degree: 0%

---

# Verificar Coleção de Eventos

Depois de [instalar e configurar](install-configure.md) o `magento/product-recommendations` , você pode verificar se os dados comportamentais estão sendo enviados para o Adobe Commerce. Você pode usar as ferramentas do desenvolvedor disponíveis no Chrome ou instalar a extensão Snowplow do Chrome. Se precisar de ajuda adicional, consulte [Solução de problemas [!DNL Product Recommendations] módulo](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) na Base de conhecimento de suporte.

## Verificar o uso das ferramentas do desenvolvedor no Chrome

Para garantir que o arquivo JS do coletor de eventos esteja sendo carregado em todas as páginas do site:

1. No Chrome, escolha **Personalizar e controlar o Google Chrome** em seguida, selecione **Mais ferramentas** > **Ferramentas do desenvolvedor**.
1. Escolha a **Rede** em seguida, selecione o **JS** tipo .
1. Filtrar para `ds.`
1. Recarregue a página.
1. Você deveria ver `ds.js` ou `ds.min.js` no **Nome** coluna.

![JS do coletor de eventos](assets/filter-ds.png)
_JS do Coletor de Eventos_

Para garantir que os eventos sejam acionados em páginas do seu site (página inicial, produto, check-out e assim por diante):

1. Desative bloqueadores de anúncios no navegador e aceite os cookies no site.
1. No Chrome, escolha **Personalizar e controlar o Google Chrome** (os três pontos verticais no canto superior direito do navegador) e selecione **Mais ferramentas** > **Ferramentas do desenvolvedor**.
1. Escolha a **Rede** e filtre por `tp2`.
1. Recarregue a página.
1. Você deve ver chamadas em `tp2` no **Nome** coluna.

![Acionamento de eventos](assets/filter-tp2.png)
_Verifique se os eventos estão sendo acionados_

## Verificar usando a extensão Snowplow do Chrome

Instale o [Extensão do Snowplow Analytics Debugger para Chrome](https://chrome.google.com/webstore/detail/snowplow-analytics-debugg/jbnlcgeengmijcghameodeaenefieedm). Essa extensão exibe os eventos que estão sendo coletados e enviados para o Adobe Commerce.

1. Desative bloqueadores de anúncios no navegador e aceite os cookies no site.

1. No Chrome, escolha **Personalizar e controlar o Google Chrome** (os três pontos verticais no canto superior direito do navegador) e selecione **Mais ferramentas** > **Ferramentas do desenvolvedor**.

1. Escolha a **Snowplow Analytics Debugger** guia .

1. Em **Evento** coluna, selecione **Evento estruturado**.

1. Role para baixo até ver **Dados de contexto _n_**. Procure a instância da loja na **Esquema**.

1. Verifique se a variável [ID do espaço de dados SaaS](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) está definida corretamente.

![Filtro Snowplow](assets/snowplow-filter.png)
_Filtro de apresentação de neve_

>[!NOTE]
>
> Um valor de `Data validity : NOT FOUND` no depurador indica um schema interno. O plug-in Snowplow do Chrome não pode validar os eventos com um esquema interno. Isso não afeta a funcionalidade real.

## Verifique se os eventos estão sendo acionados corretamente

Para verificar se os eventos usados para as métricas estão sendo acionados corretamente, procure a variável `impression-render`, `view`e `rec-click` no depurador do Snowplow Analytics. Consulte a [lista completa de eventos](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/events.html).

>[!NOTE]
>
> If [Modo de restrição de cookie](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html) estiver habilitado, o Adobe Commerce não coletará dados comportamentais até que o comprador aceite. Se o Modo de restrição de cookies estiver desativado, os dados comportamentais serão coletados por padrão.
