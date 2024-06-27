---
title: 'Configurando o Live Search'
description: A variável [!DNL Live Search] O espaço de trabalho é usado para configurar, gerenciar e monitorar o desempenho da pesquisa.
exl-id: fb85974a-a5f9-4e6c-bd03-451e6457f2d2
source-git-commit: 5e79bb43449b95b4c6aa0e234a0dbc999c312e59
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 0%

---

# Configuração do Live Search

O espaço de trabalho é onde você configura, gerencia e monitora o desempenho do [!DNL Live Search]. O menu na parte superior fornece acesso às ferramentas em cada área funcional. Os recursos disponíveis refletem a seleção de menu atual.

![Workspace](assets/workspace.png)

## Coleta de dados

Para garantir que cada área funcional do espaço de trabalho contenha os dados corretos, é necessário configurar a coleta de dados com base na implementação de vitrine selecionada:

1. Luma - A coleção de dados está disponível e pronta para uso.
1. Headless - a coleta de dados deve ser configurada manualmente, dependendo da implementação da loja.

Se você estiver usando uma loja headless, consulte a seguinte documentação para obter mais informações sobre os eventos necessários que precisam ser adicionados:

- [Eventos obrigatórios](events.md) para o painel do Live Search.
- [Colecionador de eventos da vitrine eletrônica](https://developer.adobe.com/commerce/services/shared-services/storefront-events/collector/) que precisa ser adicionado como pré-requisito.
- [Exemplos](https://github.com/adobe/commerce-events/tree/main/examples) da estrutura de eventos.

## Definir o escopo

Inicialmente, o [escopo](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) de todos [!DNL Live Search] configurações está definida como `Default Store View`. Se o seu [!DNL Commerce] instalação inclui várias exibições de loja, definir **Escopo** para o [exibição de loja](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html) onde suas configurações de facetas se aplicam.

## Opções de Menu

| Opção | Descrição |
|--- |--- |
| [Desempenho](performance.md) | O Painel fornece informações sobre o desempenho da pesquisa de produtos. |
| [Facetagem](facets.md) | Filtragem de alto desempenho que usa várias dimensões de valores de atributo para refinar os critérios de pesquisa. |
| [Sinônimos](synonyms.md) | Estenda o alcance da pesquisa para incluir palavras que os compradores podem usar para encontrar produtos diferentes daqueles no catálogo. |
| [Pesquisar merchandising](rules.md) | Modelar a experiência de pesquisa com regras lógicas que acionam ações programadas. Impulsione, bloqueie, marque ou oculte produtos para calibrar os resultados da pesquisa e oferecer suporte às suas metas comerciais. |
| [Merchandising de categoria](category-merch.md) | Aplicar regras e Merchandising inteligente no nível da categoria. |
| [GraphQL](graphql.md) | Os desenvolvedores conectados ao Administrador da loja podem compor e testar consultas com dados reais do catálogo. Para saber mais, acesse [Visão geral do GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) no [!DNL Live Search] documentação do desenvolvedor. |
| [Configurações](settings.md) | Determine como os valores de facetas de preços são agrupados por intervalo de preços na loja e defina o idioma de indexação. |

## Definir atributos como pesquisáveis

Para produzir resultados altamente direcionados, revise o conjunto de [pesquisável](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) (`searchable=true`) atributos do produto. Para garantir relevância, torne os atributos pesquisáveis somente se eles tiverem conteúdo com significado claro e conciso. Evite usar atributos que contenham texto menos preciso e longo, como `description`, que embora ativadas por padrão para pesquisa, podem reduzir a precisão dos resultados da pesquisa. Por exemplo, se uma pessoa procurar por &quot;shorts&quot; e houver camisas com uma descrição que inclua o termo &quot;mangas curtas&quot;, as camisas serão incluídas nos resultados da pesquisa.

Para permitir que os atributos sejam pesquisáveis, conclua as seguintes etapas:

1. No Administrador, acesse **Lojas** > *Atributo* > **Produto**.
1. Selecione o atributo que deseja pesquisar, como `color`.
1. Selecionar **Propriedades da vitrine** e defina **Usar na pesquisa** para `yes`.

   ![Workspace](assets/attribute-searchable.png)

[!DNL Live Search] respeita igualmente a [peso](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html#weighted-search) de um atributo de produto, conforme definido no Adobe Commerce. Atributos com um peso maior aparecerão mais altos nos resultados da pesquisa.

Os seguintes atributos são sempre pesquisáveis:

- `sku`
- `name`
- `categories`

[Facetas](facets.md) são atributos de produto definidos no [!DNL Live Search] para ser filtrável. Você pode definir qualquer atributo filtrável como uma faceta no [!DNL Live Search], mas há [limites](boundaries-limits.md) para saber quantas facetas você pode pesquisar de uma vez.

[Sinônimos](synonyms.md) são termos que você pode definir para ajudar a orientar os usuários para o produto correto. Os usuários que procuram calças podem digitar &quot;calças&quot; ou &quot;pretas&quot;. É possível definir sinônimos para que esses termos de pesquisa direcionem os usuários aos resultados de &quot;calças&quot;.

## Configurações do Commerce

A seção a seguir descreve as definições de configuração do Commerce compatíveis e não compatíveis para o [!DNL Live Search].

### Valores de configuração compatíveis

| Definição da configuração do Commerce | Descrição | Suportado pelo Popover | Suportado pelo adaptador |
|---|---|---|---|
| Lojas > Configuração > Catálogo > Catálogo > Pesquisa no catálogo > Permitir todos os produtos por página | Se definida como `Yes`, inclui a `ALL` no controle &quot;Mostrar por página&quot;. | Sim. Máximo de 500 produtos | Sim. Máximo de 500 produtos |
| Lojas > Configuração > Catálogo > Catálogo > Pesquisa no catálogo > Duração mínima da consulta | O número mínimo de caracteres permitidos em uma pesquisa de catálogo. | Sim | Sim |
| Lojas > Configuração > Catálogo > Catálogo > Pesquisa no catálogo > Produtos por página em valores permitidos da grade | Determina o número de produtos exibidos na exibição de grade. | Sim | Sim |
| Lojas > Configuração > Catálogo > Catálogo > Pesquisa no catálogo > Produtos por página no valor padrão da grade | Determina o número de produtos exibidos por página por padrão na exibição de grade. | Sim. Máximo de 500 produtos | Sim. Máximo de 500 produtos |
| Lojas > Configuração > Catálogo > Inventário > Exibir Produtos Sem Estoque | Exibe os produtos que estão esgotados. | Sim com v2.0.4+ | Sim com v2.0.4+ |
| Lojas > Configuração > Moeda > Moeda de Exibição Padrão | A moeda principal usada para exibir preços. | Sim com 3.1.0+ | Sim com 3.1.0+ |
| Lojas > Configuração > Geral > Configuração de Moeda > Opções de Moeda > Moeda Base | A moeda principal usada para todas as transações de pagamento online. | Sim | Sim |

Os preços na Página de listagem de produtos do widget e Popover são convertidos para a Moeda de exibição padrão usando as Taxas de moeda configuradas.

### Valores de configuração não suportados

| Definição da configuração do Commerce | Descrição | Notas |
|---|---|---|
| Lojas > Configuração > Catálogo > Loja > Modo de lista | Determina o formato da lista de resultados da pesquisa. | É renderizado corretamente, mas os eventos não são enviados para algumas interações de página |
| Lojas > Configuração > Catálogo > Catálogo > Pesquisa no catálogo > Duração máxima da consulta | O número máximo de caracteres permitidos em uma pesquisa de catálogo. | Não implementado; os Serviços de Pesquisa aceitam até 255 caracteres |
| Configuração > Vendas > Imposto > Configurações De Exibição De Preço > Exibir Preços Do Produto No Catálogo | Determina se os preços dos produtos publicados no catálogo incluem ou excluem imposto, ou mostram duas versões do preço: uma com e outra sem imposto |  |
| Lojas > Configuração > Catálogo > Loja > Lista de Produtos Classificar por | Determina a ordem de classificação da lista de resultados da pesquisa. | Não se aplica à [!DNL Live Search] [Widget da página de listagem de produtos](plp-styling.md) |

### Pesquisar termos

[!DNL Live Search] suporta [redirecionamentos de termo de pesquisa](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html) em implementações em que o Adobe Commerce lida com o roteamento, como no Luma e outros temas baseados em php.
