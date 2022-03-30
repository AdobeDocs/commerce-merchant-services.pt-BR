---
title: Filtrar produtos
description: Defina as condições que incluem ou excluem produtos de serem usados como recomendações.
source-git-commit: 7fe89df32dc5363817f957180e5b75e7217fc14a
workflow-type: tm+mt
source-wordcount: '693'
ht-degree: 0%

---

# Filtrar produtos

O Adobe Commerce aplica automaticamente filtros padrão não configuráveis a unidades de recomendação. Se você tiver várias unidades de recomendação implantadas em uma página, o Adobe Commerce filtra todos os produtos que são repetidos nas unidades. Só é utilizada a primeira referência a um produto repetido, para permitir que outros produtos sejam recomendados. A Adobe Commerce também filtra todos os produtos comprados anteriormente e aqueles que estão no carrinho.

Quando você [criar](create.md) em uma unidade de recomendação, você pode definir filtros que controlam quais produtos podem ser exibidos nas recomendações. Esses filtros são baseados em um conjunto de condições de inclusão ou exclusão definidas por você. Somente os produtos que correspondem a todas as condições de inclusão são exibidos nas recomendações. Produtos que correspondem a qualquer uma das condições de exclusão não são recomendados.

Você pode configurar vários filtros e ativar apenas aqueles que deseja, selecionando o botão em cada página de filtro. Isso permite que você crie rascunhos de filtros para uso futuro. O número de filtros ativados é exibido em cada guia.

## Condições

As condições podem ser estáticas ou dinâmicas.

- Uma condição estática usa atributos de produto existentes para determinar quais produtos podem aparecer na unidade. Por exemplo, você pode especificar que apenas produtos em estoque com um preço maior que US$ 25 sejam exibidos na unidade. As condições estáticas estão disponíveis em todos os tipos de página.

- Uma condição dinâmica determina o contexto atual de um comprador, como a categoria ou o produto visualizado no momento. Por exemplo, ao criar uma recomendação de produto para ser implantada nas páginas de detalhes do produto, você pode criar uma condição para recomendar apenas produtos que estejam dentro de um intervalo de preço relativo do produto visualizado no momento. As condições dinâmicas estão disponíveis em cada tipo de página, exceto na Página inicial e em páginas com recomendações que são colocadas com o Construtor de páginas.

### Operadores lógicos

Os operadores lógicos `AND` e `OR` são usadas para unir várias condições. Se estiver usando filtros de inclusão e exclusão, as inclusões serão avaliadas primeiro para determinar todos os produtos possíveis que podem ser recomendados, em seguida, os produtos que correspondem a qualquer filtro de exclusão serão removidos da lista.

- `AND` - Associa-se a duas condições de filtragem de inclusão
- `OR` - Une duas condições de filtragem de exclusão

>[!NOTE]
>
> Os filtros de inclusão e exclusão substituem as exclusões de categoria herdada nas versões 3.2.2 e posteriores da `magento/product-recommendations` módulo. Consulte a [notas de versão](release-notes.md) para saber mais sobre as versões do Adobe Commerce.

## Tipos de filtros {#filtertypes}

![Filtros](assets/rec-conditions.png)

### Categoria

Os filtros baseados na categoria de um produto usam atribuições diretas de categoria e suas subcategorias. Por exemplo, ativar uma condição de exclusão para a categoria `Gear` exclui produtos `Gear` e todas as suas subcategorias, como `Gear/Bags` ou `Gear/Fitness Equipment`. Para comerciantes B2B, o filtro Categoria adere a qualquer [categorias de produtos específicas do cliente](https://docs.magento.com/user-guide/catalog/category-permissions.html) você configurou.

A Adobe Commerce recomenda usar a seguinte configuração de filtro de categoria ao implantar recomendações nos tipos de página:

| Página | Filtrar por |
|---|---|
| Início | Não filtre produtos. |
| Categoria | Filtre produtos na categoria específica. |
| Detalhes do produto | Filtre produtos nas mesmas categorias. |
| Carrinho | Filtre categorias de produtos no carrinho. |
| Confirmação do pedido | Filtrar categorias de produtos comprados. |

### Produto

Os filtros de produto especificam quais produtos específicos estão qualificados ou não para serem exibidos nas recomendações. Não é possível selecionar produtos que estão desativados ou invisíveis individualmente, pois esses produtos nunca podem aparecer nas recomendações.

### Tipo

Um filtro baseado no tipo de produto inclui ou exclui todos os produtos de um tipo específico. Os tipos suportados incluem _Simples_, _Configurável_, _Virtual_, _Baixável_ ou _Cartão de presente_. _Pacote_ e _Agrupado_ os produtos ainda não são compatíveis.

### Visibilidade

Filtra produtos com base na visibilidade, como: _Catálogo_, _Pesquisar_ ou ambos.

### Preço

Um filtro baseado no preço do produto usa o preço final para executar a comparação. O preço final inclui quaisquer descontos ou preços especiais disponíveis para compradores anônimos. Para comerciantes B2B, o preço exibido reflete o [preços de grupo específicos do cliente](https://docs.magento.com/user-guide/catalog/pricing-advanced.html#customer-group-price) você configurou.

### Status do estoque

Os seguintes filtros de exclusão podem ser usados para filtrar produtos com base no status do estoque:

- Fora de estoque - (Somente exclusão) Exclui produtos indisponíveis.
- Baixo estoque - (Exclusão somente) Exclui produtos que estão em estoque. O status de estoque baixo é baseado na variável _Limite esquerdo de apenas X_ valor em [Configuração do inventário](https://docs.magento.com/user-guide/configuration/catalog/inventory.html).
