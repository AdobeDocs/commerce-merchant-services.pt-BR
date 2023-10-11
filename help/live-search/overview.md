---
title: Introdução ao [!DNL Live Search]
description: "[!DNL Live Search] O da Adobe Commerce oferece uma experiência de pesquisa ultrarrápida, relevante e intuitiva."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 4eddad715405f35ea063bab3cf4651fec3beeae5
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Introdução ao [!DNL Live Search]

[!DNL Live Search] O é um serviço para o Adobe Commerce que substitui os recursos de pesquisa padrão. A variável [!DNL Live Search] O módulo é instalado com o Composer e conecta o [!DNL Commerce] instalação no [!DNL Live Search] [serviço](../landing/saas.md). Quando configurado, o campo de texto de pesquisa padrão é substituído pelo campo [!DNL Live Search] campo de texto.

[!DNL Live Search] aparece no *Marketing* menu em *SEO e pesquisa* no [!DNL Commerce] *Admin*.

O lado da Adobe Commerce na arquitetura inclui hospedar a pesquisa *Admin*, sincronizando dados de catálogo e executando o serviço de consulta. Depois [!DNL Live Search] estiver instalado e configurado, o Adobe Commerce começará a compartilhar dados de pesquisa e catálogo com os serviços SaaS. Neste ponto, os usuários administradores podem configurar, personalizar e gerenciar a pesquisa [facetas](facets.md), [sinônimos](synonyms.md), e [regras de merchandising](category-merch.md).

![Diagrama de arquitetura do Live Search](assets/architecture-diagram.svg)

## Componentes do Live Search

* [!DNL Live Search] [popover](storefront-popover.md) é a caixa que é aberta no campo de pesquisa que contém os resultados da pesquisa.
* [Widget de página de listagem de produtos](plp-styling.md) O fornece uma página pesquisável da lista de produtos com suporte a aspectos e sinônimos.
* O AEM [Componente CIF](https://github.com/adobe/aem-cif-guides-venia/pull/319) permite que os sites AEM aproveitem as [!DNL Live Search].
* [[!DNL Live Search] Admin](workspace.md) é onde regras, facetas e sinônimos são configurados.
* O Adaptador de pesquisa é a implementação padrão do [!DNL Live Search].

## [!DNL Live Search] demonstração

Assista a este vídeo para saber mais sobre [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

Para obter um vídeo mais detalhado sobre como usar e configurar o Live Search, consulte [Demonstração completa em [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/marketing/live-search-full-demonstration.html) tópico.
