---
title: O que é o [!DNL Live Search]?
description: "[!DNL Live Search] O da Adobe Commerce oferece uma experiência de pesquisa rápida, relevante e intuitiva."
exl-id: aca0ef19-ead1-4c79-90c3-db5ec48cb3c1
recommendations: noCatalog
source-git-commit: aba552808ea7af540f64f00a2ae4aeaf2b9cc52e
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 0%

---

# O que é o [!DNL Live Search]?

[!DNL Live Search] O é uma extensão que substitui os recursos de pesquisa padrão no Adobe Commerce. A variável [!DNL Live Search] é instalada com o Composer e conecta o [!DNL Commerce] instalação no [!DNL Live Search] [serviço](../landing/saas.md). Quando configurado, o campo de texto de pesquisa padrão é substituído pelo campo [!DNL Live Search] campo de texto. [!DNL Live Search] O também instala o widget Página de listagem de produtos (PLP), que fornece recursos robustos de filtragem ao navegar pelos resultados da pesquisa.

Com [!DNL Live Search], você pode:

- Crie experiências de pesquisa significativas para ajudar compradores e compradores a encontrar o que desejam com o menor esforço possível.
- Aproveite a faceta dinâmica alimentada por IA e a reclassificação dos resultados de pesquisa em resposta aos comportamentos do comprador na sessão.
- Use um serviço leve baseado em SaaS que ofereça atualizações fáceis e esteja incluído em sua licença, reduzindo o custo total de propriedade.
- Obtenha conhecimento técnico habilitando a API GraphQL, a flexibilidade headless, os ambientes de sandbox da API e o SaaS ultrarrápido.

>[!IMPORTANT]
>
>Quando se trata de pesquisa no site, o Adobe Commerce oferece opções. Certifique-se de ler [Limites e limites](boundaries-limits.md) antes da implementação, assegurar [!DNL Live Search] O é adequado às necessidades da sua empresa.

## Arquitetura

O lado da Adobe Commerce na arquitetura inclui hospedar a pesquisa *Admin*, sincronizando dados de catálogo e executando o serviço de consulta. Depois [!DNL Live Search] estiver instalado e configurado, o Adobe Commerce começará a compartilhar dados de pesquisa e catálogo com os serviços SaaS. Neste ponto, os usuários administradores podem configurar, personalizar e gerenciar a pesquisa [facetas](facets.md), [sinônimos](synonyms.md), e [regras de merchandising](category-merch.md).

![Fluxo de dados do Live Search](assets/ls-cs-data-flow.png)

## Tour rápido

Com foco na velocidade, relevância e facilidade de uso, [!DNL Live Search] O é um divisor de águas tanto para compradores quanto para comerciantes. Assista ao vídeo a seguir e faça um rápido tour pelo [!DNL Live Search] da loja.

>[!VIDEO](https://video.tv.adobe.com/v/3418679?quality=12&learn=on)

Para obter um vídeo mais detalhado sobre como usar e configurar o Live Search, consulte [Demonstração completa em [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/getting-started/capabilities/live-search-full-demonstration.html) tópico.

### Pesquisar enquanto digita

[!DNL Live Search] O responde com produtos sugeridos e uma imagem em miniatura dos principais resultados da pesquisa em uma [popover](storefront-popover.md) à medida que os compradores digitam consultas na variável [Pesquisar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#quick-search) caixa. A variável [detalhes do produto](https://experienceleague.adobe.com/docs/commerce-admin/start/storefront/storefront.html#product-page) é exibida quando os compradores clicam em um produto sugerido ou em destaque. A _Exibir todos_ no rodapé do popover exibe a página de resultados da pesquisa.

[!DNL Live Search] retorna resultados de &quot;pesquisa ao digitar&quot; para uma consulta de dois ou mais caracteres. Para uma correspondência parcial, o número máximo de caracteres por palavra é 20. O número de caracteres na consulta não é configurável. O popover inclui o`name`, `sku`, e `category_ids` campos.

![Exemplo de vitrine - pesquisar à medida que você digita](assets/storefront-search-as-you-type.png)

### Exibir todos os resultados da pesquisa

Para listar todos os produtos retornados pela consulta &quot;pesquisar ao digitar&quot;, clique em _Exibir todos_ no rodapé do popover.

![Exemplo de vitrine - aspectos de preço](assets/storefront-view-all-search-results.png)

### Pesquisa filtrada com facetas

A pesquisa filtrada usa várias dimensões de valores de atributo ou [facetas](facets.md), como critério de pesquisa. A seleção de filtros é definida pelo comerciante e muda de acordo com os produtos retornados, com as facetas mais usadas fixadas no topo da lista.

Usar facetas como parâmetros de URL:`http://yourwebsite.com?color=red`, e o Live Search filtra os resultados com base nesses valores de atributo.

### Sinônimos

[Sinônimos](synonyms.md) expanda o alcance e ajuste a nitidez do foco das consultas ao incluir palavras que os compradores podem usar diferentes daquelas no catálogo. Você pode ajustar o dicionário de sinônimo para manter os compradores envolvidos e no caminho para comprar.

### Regras de merchandising

Merchandising [regras](rules.md) molde a experiência de compra com instruções if-then que adicionam lógica e eventos a serem pesquisados. Você pode facilmente impulsionar ou enterrar produtos para uma promoção, temporada ou outro período de tempo.

### Suporte a termos de pesquisa

[!DNL Live Search] compatível com Commerce [redirecionamentos de termo de pesquisa](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html). Por exemplo, os usuários podem procurar por um termo como &quot;Taxas de envio&quot; e ser direcionados diretamente para a página de taxas de envio.

## Componentes do Live Search

- [!DNL Live Search] [widget popover](storefront-popover.md) é a caixa que é aberta no campo de pesquisa que contém os resultados da pesquisa.
- [Widget de página de listagem de produtos](plp-styling.md) O fornece uma página pesquisável da lista de produtos com suporte a aspectos e sinônimos.
- [[!DNL Live Search] Admin](workspace.md) é onde regras, facetas e sinônimos são configurados.

## [!DNL Live Search] espaço de trabalho

A variável [!DNL Live Search] [espaço de trabalho](workspace.md) é a área no Administrador em que você configura o [!DNL Live Search] recursos como sinônimos, facetas e merchandising por categoria.

## Eventos

[!DNL Live Search] usos [events](events.md) para calcular [Merchandising inteligente](category-merch.md) e [desempenho](performance.md) painéis. O evento é fornecido com implementações padrão. O evento para frente de loja headless deve ser ativado manualmente.
