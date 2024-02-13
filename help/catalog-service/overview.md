---
title: '[!DNL Catalog Service]'
description: '''[!DNL Catalog Service] O para Adobe Commerce fornece uma maneira de recuperar o conteúdo das Páginas de exibição do produto e das Páginas de lista de produtos com muito mais rapidez do que as consultas nativas do Adobe Commerce GraphQL."'
exl-id: 266faca4-6a65-4590-99a9-65b1705cac87
recommendations: noCatalog
source-git-commit: d9d9506b2555bc30d6fbec67c65fa220d9a51e91
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 0%

---

# [!DNL Catalog Service] para Adobe Commerce

A variável [!DNL Catalog Service] A extensão para Adobe Commerce fornece dados de catálogo do modelo de visualização avançado (somente leitura) para renderizar rápida e totalmente as experiências da loja relacionadas ao produto, incluindo:

* Páginas de detalhes do produto
* Páginas de lista de produtos e categoria
* Páginas de resultados da pesquisa
* Carrosséis de produtos
* Páginas de comparação do produto
* Qualquer outra página que renderize dados do produto, como carrinho, pedido e páginas de lista de desejos

A variável [!DNL Catalog Service] usos [GraphQL](https://graphql.org/) para solicitar e receber dados do produto. O GraphQL é uma linguagem de consulta que um cliente de front-end usa para se comunicar com a API (interface de programação de aplicativos) definida em um back-end, como o Adobe Commerce. O GraphQL é um método de comunicação popular porque é leve e permite que um integrador de sistemas especifique o conteúdo e a ordem de cada resposta.

O Adobe Commerce tem dois sistemas GraphQL. O sistema GraphQL principal fornece uma ampla variedade de consultas (operações de leitura) e mutações (operações de gravação) que permitem que um comprador interaja com vários tipos de páginas, incluindo produto, conta do cliente, carrinho, check-out e muito mais. No entanto, as consultas que retornam informações do produto não são otimizadas para velocidade. O sistema GraphQL de serviços só pode executar consultas em produtos e informações relacionadas. Esses queries têm mais desempenho do que queries principais semelhantes.

[!DNL Catalog Service] os clientes podem usar o novo [Indexador de preços SaaS](../price-index/index.md), que oferece atualizações de alteração de preço e tempo de sincronização mais rápidos.

## Arquitetura

O diagrama a seguir mostra os dois sistemas GraphQL:

![Diagrama da arquitetura de catálogo](assets/catalog-service-architecture.png)

No sistema GraphQL principal, o PWA envia uma solicitação para o aplicativo Commerce, que recebe cada solicitação, processa-a, possivelmente enviando uma solicitação por meio de vários subsistemas, e retorna uma resposta à loja. Essa viagem de ida e volta pode causar tempos lentos de carregamento da página, resultando potencialmente em taxas de conversão mais baixas.

[!DNL Catalog Service] é um Gateway de Serviços de Loja. O serviço acessa um banco de dados separado que contém detalhes do produto e informações relacionadas, como atributos do produto, variantes, preços e categorias. O serviço mantém o banco de dados sincronizado com o Adobe Commerce por meio de indexação.
Como o serviço ignora a comunicação direta com o aplicativo, é possível reduzir a latência do ciclo de solicitação e resposta.

Os sistemas GraphQL principais e de serviço não se comunicam diretamente entre si. Você acessa cada sistema de um URL diferente e as chamadas do exigem informações de cabeçalho diferentes. Os dois sistemas GraphQL foram projetados para serem usados juntos. A variável [!DNL Catalog Service] O sistema da GraphQL aumenta o sistema principal para agilizar as experiências da loja de produtos.

Opcionalmente, é possível implementar [Malha de API para o Construtor de aplicativos Adobe Developer](https://developer.adobe.com/graphql-mesh-gateway/) para integrar os dois sistemas Adobe Commerce GraphQL com APIs privadas e de terceiros e outras interfaces de software usando o Adobe Developer. A malha pode ser configurada para garantir que as chamadas roteadas para cada endpoint contenham as informações de autorização corretas nos cabeçalhos.

## Detalhes da arquitetura

As seções a seguir descrevem algumas das diferenças entre os dois sistemas GraphQL.

### Gerenciamento de esquema

Como o Serviço de catálogo funciona como um serviço, os integradores não precisam se preocupar com a versão subjacente do Commerce. A sintaxe dos queries é a mesma para todas as versões. Além disso, o esquema é consistente para todos os comerciantes. Essa consistência facilita o estabelecimento de práticas recomendadas e aumenta significativamente a reutilização de widgets da loja.

### Simplificação dos tipos do produto

O esquema reduz a diversidade de tipos de produtos a dois casos de uso:

* Produtos simples são aqueles que são definidos com um único preço e quantidade. O Serviço de catálogo mapeia os tipos de produto simples, virtuais, para download e de cartão-presente para `simpleProductViews`.

* Produtos complexos são compostos de vários produtos simples. Os produtos simples componentes podem ter preços diferentes. Um produto complexo também pode ser definido para que o comprador possa especificar a quantidade de produtos simples componentes. O Serviço de catálogo mapeia os tipos de produto configuráveis, agrupados e agrupados para `complexProductViews`.

Opções complexas de produto são unificadas e diferenciadas por seu comportamento, não pelo tipo. Cada valor de opção representa um produto simples. Esse valor de opção tem acesso aos atributos simples do produto, incluindo preço. Quando o comprador seleciona todas as opções de um produto complexo, a combinação de opções selecionadas aponta para um produto simples específico. O produto simples permanece ambíguo até que o comprador selecione um valor para todas as opções disponíveis.

### Preços

Produtos simples representam a unidade base de vendas com preço. [!DNL Catalog Service] O calcula o preço normal antes dos descontos, bem como o preço final após os descontos. Os cálculos de preço podem incluir impostos fixos do produto. Eles excluem promoções personalizadas.

Um produto complexo não tem um preço definido. Em vez disso, o Serviço de catálogo retorna os preços dos simples vinculados. Como exemplo, um comerciante pode atribuir inicialmente os mesmos preços a todas as variantes de um produto configurável. Se determinados tamanhos ou cores não forem populares, o comerciante poderá reduzir os preços dessas variantes. Assim, o preço do produto complexo (configurável) inicialmente mostra uma faixa de preço, refletindo o preço de variantes padrão e impopulares. Depois que o comprador selecionar um valor para todas as opções disponíveis, a vitrine exibe um único preço.

>[!NOTE]
>
> Clientes do Commerce com [!DNL Catalog Service] podem aproveitar as atualizações de alterações de preço e o tempo de sincronização mais rápidos em seus sites com o [Indexador de preços SaaS](../price-index/index.md).

## Implementação

O processo de instalação exige a configuração do [Conector dos Commerce Services](../landing/saas.md). Depois que isso for realizado, a próxima etapa é que o integrador de sistemas atualize o código da loja para incorporar o [!DNL Catalog Service] consultas. Todos [!DNL Catalog Service] as consultas são roteadas para o gateway do GraphQL. O URL é fornecido durante o processo de integração.
