---
title: Introdução ao [!DNL Live Search]
description: "[!DNL Live Search] O da Adobe Commerce oferece uma experiência de pesquisa rápida, relevante e intuitiva."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: 51ff52eba117fe438d592ca886dbca25304a0d15
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 0%

---

# Introdução ao [!DNL Live Search]

[!DNL Live Search] O é um serviço para o Adobe Commerce que substitui os recursos de pesquisa padrão. A variável [!DNL Live Search] O módulo é instalado com o Composer e conecta o [!DNL Commerce] instalação no [!DNL Live Search] [serviço](../landing/saas.md). Quando configurado, o campo de texto de pesquisa padrão é substituído pelo campo [!DNL Live Search] campo de texto. [!DNL Live Search] O também instala o widget Página de listagem de produtos (PLP), que fornece recursos robustos de filtragem ao navegar pelos resultados da pesquisa.

[!DNL Live Search] aparece no *Marketing* menu em *SEO e pesquisa* no [!DNL Commerce] *Admin*.

O lado da Adobe Commerce na arquitetura inclui hospedar a pesquisa *Admin*, sincronizando dados de catálogo e executando o serviço de consulta. Depois [!DNL Live Search] estiver instalado e configurado, o Adobe Commerce começará a compartilhar dados de pesquisa e catálogo com os serviços SaaS. Neste ponto, os usuários administradores podem configurar, personalizar e gerenciar a pesquisa [facetas](facets.md), [sinônimos](synonyms.md), e [regras de merchandising](category-merch.md).

## Componentes do Live Search

* [!DNL Live Search] [widget popover](storefront-popover.md) é a caixa que é aberta no campo de pesquisa que contém os resultados da pesquisa.
* [Widget de página de listagem de produtos](plp-styling.md) O fornece uma página pesquisável da lista de produtos com suporte a aspectos e sinônimos.
* AEM Componentes CIF: o [Widget do Popover](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/live-search-popover.html?lang=en) e a variável [Widget do PLP](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/live-search-plp.html) permitir que sites AEM aproveitem as [!DNL Live Search].
* [[!DNL Live Search] Admin](workspace.md) é onde regras, facetas e sinônimos são configurados.

## Visão geral do fluxo de trabalho

[!DNL Live Search] O funciona movendo dados de catálogo para a infraestrutura SaaS do Adobe Commerce e criando índices que são usados para fornecer resultados de pesquisa rapidamente à medida que os usuários digitam.

### 1. Instalação

[!DNL Live Search] é [instalado](install.md) na instância do Adobe Commerce por meio de [Compositor](https://getcomposer.org/). Isso instala os módulos necessários que se conectam ao serviço e configura a instância do Commerce para substituir o campo de pesquisa padrão. Ele também instala as opções de Administrador do Commerce para configurar o serviço.

### 2. Sincronizar dados

[!DNL Live Search] O move dados do catálogo para a infraestrutura SaaS do Adobe. Os dados são indexados e os resultados da pesquisa são enviados desse índice diretamente para a loja. Dependendo do tamanho e da complexidade, a indexação pode levar de 30 minutos a algumas horas.

### 3. Configurar dados

A configuração correta dos dados do produto garante bons resultados de pesquisa para os clientes. Há algumas etapas de configuração necessárias: atribuição de categorias e configuração de atributos.

#### Atribuir categorias

Produto devolvido em [!DNL Live Search] deve receber um [categoria](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html). Na Luma, por exemplo, os produtos são colocados em categorias como &quot;Homens&quot;, &quot;Mulheres&quot; e &quot;Engrenagens&quot;. As subcategorias também são configuradas para &quot;Topos&quot;, &quot;Partes inferiores&quot; e &quot;Inspeções&quot;. Isso permite uma melhor granularidade ao filtrar.

#### Campos pesquisáveis e filtráveis

Os produtos são atribuídos [atributos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) que pode ser usado para pesquisa e filtragem. Atributos são coisas como &quot;Cor&quot;, &quot;Tamanho&quot;, &quot;Tipo de material&quot;. Com esses atributos, os usuários podem procurar por &quot;tops verdes&quot;. Cada produto pode ter muitos atributos definidos no administrador do Commerce.

Cada um desses atributos pode ser definido como [&quot;pesquisável&quot;](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html) no admin. Quando definidos como &quot;pesquisáveis&quot;, esses atributos estão disponíveis para serem pesquisados por [!DNL Live Search].

[Facetas](facets.md) são atributos de produto definidos no [!DNL Live Search] para ser filtrável. Qualquer atributo filtrável pode ser definido como uma faceta no [!DNL Live Search] mas há limites para quantas facetas podem ser pesquisadas de uma vez.

[Sinônimos](synonyms.md) são termos que você pode definir para ajudar a orientar os usuários para o produto correto. Os usuários que procuram calças podem digitar &quot;calças&quot; ou &quot;pretas&quot;. É possível definir sinônimos para que esses termos de pesquisa direcionem os usuários aos resultados de &quot;calças&quot;.

## [!DNL Live Search] espaço de trabalho

A variável [!DNL Live Search] [espaço de trabalho](workspace.md) é a área no Administrador em que você configura o [!DNL Live Search] recursos como sinônimos, facetas e merchandising por categoria.

## Eventos

[!DNL Live Search] usos [events](events.md) para calcular [Merchandising inteligente](category-merch.md) e [desempenho](performance.md) painéis. O evento é fornecido com implementações padrão. O evento para frente de loja headless deve ser ativado manualmente.

## Personalização de widgets

A maioria dos proprietários de lojas desejará garantir que a [!DNL Live Search] os widgets estão em conformidade com a aparência e comportamento da loja.

Os widgets popover e PLP podem ser estilizados definindo regras CSS personalizadas, conforme necessário. Consulte [Elementos Popover de estilo](storefront-popover-styling.md) e [Widget da página de listagem de produtos](plp-styling.md).

Se você quiser estender a funcionalidade dos widgets, o código-fonte de cada um deles estará disponível em um repositório público.
Nesse cenário, você pode personalizar o JavaScript de acordo com suas necessidades e, em seguida, hospedar seu código personalizado no CDN. Este script personalizado se comunica com a variável [!DNL Live Search] e retorna os resultados normalmente, permitindo que você controle a funcionalidade do widget.

* [repositório de widgets PLP](https://github.com/adobe/storefront-product-listing-page)
* [Pesquisar repositório de barras](https://github.com/adobe/storefront-search-as-you-type)

Obter mais detalhes sobre [!DNL Live Search] no [Visão geral técnica](technical-overview.md).

## [!DNL Live Search] demonstração

Assista a este vídeo para saber mais sobre [!DNL Live Search]:

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

Para obter um vídeo mais detalhado sobre como usar e configurar o Live Search, consulte [Demonstração completa em [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration.html) tópico.
