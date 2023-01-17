---
title: '[!DNL Catalog Service]'
description: '[!DNL Catalog Service] O para Adobe Commerce fornece uma maneira de recuperar o conteúdo das Páginas de exibição do produto e das Páginas de lista do produto muito mais rapidamente do que as consultas nativas do Adobe Commerce GraphQL.'
exl-id: 266faca4-6a65-4590-99a9-65b1705cac87
source-git-commit: 489de0f56cba06620c334e2b17040b32a72968ef
workflow-type: tm+mt
source-wordcount: '903'
ht-degree: 0%

---

# [!DNL Catalog Service] para Adobe Commerce

O [!DNL Catalog Service] A extensão para Adobe Commerce fornece dados de catálogo do modelo de visualização avançada (somente leitura) para renderizar rápida e totalmente as experiências de vitrine relacionadas ao produto, incluindo:

* Páginas de detalhes do produto
* Lista de produtos e páginas de categorias
* Pesquisar páginas de resultados
* Carrosséis de produtos
* Páginas de comparação do produto
* Quaisquer outras páginas que renderizem dados do produto, como páginas de carrinho, pedido e lista de desejos

O [!DNL Catalog Service] uses [GraphQL](https://graphql.org/) para solicitar e receber dados do produto. GraphQL é uma linguagem de consulta que um cliente front-end usa para se comunicar com a API (interface de programação de aplicativos) definida em um back-end como o Adobe Commerce. O GraphQL é um método popular de comunicação porque é leve e permite que um integrador de sistemas especifique o conteúdo e a ordem de cada resposta.

O Adobe Commerce tem dois sistemas GraphQL. O sistema GraphQL principal fornece uma grande variedade de consultas (operações de leitura) e mutações (operações de gravação) que permitem que o comprador interaja com muitos tipos de páginas, incluindo produto, conta do cliente, carrinho, check-out e muito mais. No entanto, as consultas que retornam informações do produto não são otimizadas para agilizar. O sistema GraphQL de serviços só pode realizar consultas sobre produtos e informações relacionadas. Essas consultas têm mais desempenho do que consultas principais semelhantes.

Você executa essas consultas enviando-as para o gateway em https://catalog-service.adobe.io/graphql.

## Arquitetura

O diagrama a seguir mostra os dois sistemas GraphQL:

![Diagrama de arquitetura do catálogo](assets/catalog-service-architecture.png)

No sistema GraphQL principal, o PWA envia uma solicitação para o aplicativo Commerce, que recebe cada solicitação, a processa, possivelmente enviando uma solicitação por meio de vários subsistemas, e depois retorna uma resposta à loja. Esse caminho de ida e volta pode causar tempos lentos de carregamento de página, resultando possivelmente em taxas de conversão mais baixas.

[!DNL Catalog Service] é um gateway de serviços de vitrine. O serviço acessa um banco de dados separado que contém detalhes do produto e informações relacionadas, como atributos do produto, variantes, preços e categorias. O serviço mantém o banco de dados sincronizado com a Adobe Commerce por meio da indexação.
Como o serviço ignora a comunicação direta com o aplicativo, ele pode reduzir a latência do ciclo de solicitação e resposta.

>[!NOTE]
>
>O gateway é para integração futura com o Product Recommendations. Nesta versão, você pode acessar o [!DNL Catalog Service GraphQL] e [!DNL Live Search] O consulta do mesmo endpoint se você tiver uma chave de licença válida para ambos os produtos.

Os sistemas GraphQL de núcleo e serviço não se comunicam diretamente uns com os outros. Você acessa cada sistema a partir de um URL diferente e as chamadas exigem informações de cabeçalho diferentes. Os dois sistemas GraphQL foram projetados para serem usados juntos. O [!DNL Catalog Service] O sistema GraphQL aumenta o sistema principal para tornar as experiências de loja de produtos mais rápidas.

Opcionalmente, é possível implementar [Mensagem de API para o Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/) para integrar os dois sistemas Adobe Commerce GraphQL com APIs privadas e de terceiros e outras interfaces de software usando o Adobe Developer. A malha pode ser configurada para garantir que as chamadas roteadas para cada endpoint contenham as informações de autorização corretas nos cabeçalhos.

## Detalhes da arquitetura

As seções a seguir descrevem algumas das diferenças entre os dois sistemas GraphQL.

### Gerenciamento de esquemas

Como o Serviço de catálogo opera como um serviço, os integradores não precisam se preocupar com a versão subjacente do Commerce. A sintaxe dos queries é a mesma para todas as versões. Além disso, o schema é consistente para todos os comerciantes. Essa consistência facilita o estabelecimento de práticas recomendadas e aumenta significativamente o reuso de widgets de vitrine.

### Simplificação dos tipos de produtos

O esquema reduz a diversidade de tipos de produtos para dois casos de uso:

* Produtos simples são aqueles definidos com um único preço e quantidade. O Serviço de catálogo mapeia os tipos de produtos simples, virtuais, baixáveis e de cartão-presente para `simpleProductViews`.

* Produtos complexos são compostos de vários produtos simples. O componente produtos simples pode ter preços diferentes. Um produto complexo também pode ser definido para que o comprador possa especificar a quantidade de produtos simples do componente. O Serviço de catálogo mapeia os tipos de produto configuráveis, agrupados e agrupados para `complexProductViews`.

Opções de produto complexas são unificadas e distinguidas pelo seu comportamento, não pelo tipo. Cada valor de opção representa um produto simples. Esse valor de opção tem acesso aos atributos simples do produto, incluindo o preço. Quando o comprador seleciona todas as opções para um produto complexo, a combinação das opções selecionadas aponta para um produto simples específico. O produto simples permanece ambíguo até que o comprador selecione um valor para todas as opções disponíveis.

### Preços

Produtos simples representam a unidade de venda básica que tem um preço. O Serviço de Catálogo calcula o preço normal antes dos descontos, bem como o preço final após os descontos. Os cálculos de preços podem incluir impostos fixos do produto. Eles excluem promoções personalizadas.

Um produto complexo não tem um preço definido. Em vez disso, o Serviço de catálogo retorna os preços do simples vinculado. Como exemplo, um comerciante pode inicialmente atribuir os mesmos preços a todas as variantes de um produto configurável. Se determinados tamanhos ou cores forem impopulares, o comerciante pode reduzir os preços dessas variantes. Assim, o preço do produto complexo (configurável) mostra inicialmente um intervalo de preços, refletindo o preço das variantes padrão e impopulares. Depois que o comprador tiver selecionado um valor para todas as opções disponíveis, a loja exibirá um único preço.

## Implementação

O processo de instalação requer a configuração do [Conector do Commerce Services](../landing/saas.md). Depois disso, a próxima etapa é que um integrador de sistemas atualize o código da loja para incorporar a [!DNL Catalog Service] consultas. Todos [!DNL Catalog Service] as consultas são roteadas para o gateway do GraphQL. O URL é fornecido durante o processo de integração.
