---
title: Filtrar produtos
description: Defina condições que incluam ou excluam produtos de serem usados como recomendações.
exl-id: baab28ff-b529-4cbc-adb7-4fa225e87d4a
source-git-commit: 78f226465b9d84707612596a5aa4622aa7869ee1
workflow-type: tm+mt
source-wordcount: '698'
ht-degree: 0%

---

# Filtrar produtos

O Adobe Commerce aplica automaticamente filtros padrão não configuráveis a unidades de recomendação. Se você tiver várias unidades de recomendação implantadas em uma página, o Adobe Commerce filtra todos os produtos que são repetidos nas unidades. Somente a primeira referência a um produto repetido é usada para abrir espaço para outros produtos a serem recomendados. O Adobe Commerce também filtra todos os produtos comprados anteriormente e aqueles que estão no carrinho.

Quando você [criar](create.md) Em uma unidade de recomendação, é possível definir filtros que controlam quais produtos podem ser exibidos nas recomendações. Esses filtros se baseiam em um conjunto de condições de inclusão ou exclusão definidas por você. Somente os produtos que correspondem a todas as condições de inclusão aparecem nas recomendações. Os produtos que correspondem a qualquer uma das condições de exclusão não são recomendados.

Você pode configurar vários filtros e ativar apenas aqueles que desejar selecionando a alternância em cada página de filtro. Isso permite criar rascunhos de filtros para uso futuro. O número de filtros ativados é exibido em cada guia.

## Condições

As condições podem ser estáticas ou dinâmicas.

- Uma condição estática usa atributos de produto existentes para determinar quais produtos podem aparecer na unidade. Por exemplo, você pode especificar que apenas os produtos em estoque com um preço superior a US$ 25 apareçam na unidade. As condições estáticas estão disponíveis em todos os tipos de página.

- Uma condição dinâmica é destacada do contexto atual de um comprador, como a categoria ou o produto visualizado no momento. Por exemplo, ao criar uma recomendação de produto para ser implantada nas páginas de detalhes do produto, você pode criar uma condição para recomendar apenas produtos que estejam dentro de uma faixa de preço relativo do produto visualizado no momento. As condições dinâmicas estão disponíveis em todos os tipos de página, exceto a Página inicial, e em páginas com recomendações inseridas com o Page Builder.

### Operadores lógicos

Os operadores lógicos `AND` e `OR` são usados para unir várias condições. Se estiver usando filtros de inclusão e exclusão, as inclusões serão avaliadas primeiro para determinar todos os produtos possíveis que podem ser recomendados, e os produtos que correspondem a qualquer filtro de exclusão serão removidos da lista.

- `AND` - Associa duas condições de filtragem de inclusão
- `OR` - Associa duas condições de filtragem por exclusão

>[!NOTE]
>
> Os filtros de inclusão e exclusão substituem as exclusões de categoria herdada nas versões 3.2.2 e posteriores do `magento/product-recommendations` módulo. Consulte a [notas de versão](release-notes.md) para saber mais sobre as versões do Adobe Commerce.

## Tipos de filtros {#filtertypes}

![Filtros](assets/rec-conditions.png)

### Categoria

Os filtros baseados na categoria de um produto usam atribuições diretas de categoria e suas subcategorias. Por exemplo, ativar uma condição de exclusão para categoria `Gear` exclui produtos atribuídos a `Gear` e todas as suas subcategorias, como `Gear/Bags` ou `Gear/Fitness Equipment`. Para comerciantes B2B, o filtro Categoria segue qualquer [categorias de produto específicas do cliente](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html) você configurou o.

A Adobe Commerce recomenda usar a seguinte configuração de filtro de categoria ao implantar recomendações para seus tipos de página:

| Página | Filtrar por |
|---|---|
| Início | Não filtre produtos. |
| Categoria | Filtrar produtos na categoria específica. |
| Detalhes do produto | Filtrar produtos nas mesmas categorias. |
| Carrinho | Filtre categorias de produtos no carrinho. |
| Confirmação do pedido | Filtrar categorias de produtos comprados. |

### Produto

Os filtros de produto especificam quais produtos específicos estão qualificados ou não para serem exibidos nas recomendações. Você não pode selecionar produtos que estão desativados ou que não estão visíveis individualmente porque esses produtos nunca podem aparecer nas recomendações.

### Tipo

Um filtro com base no tipo de produto inclui ou exclui todos os produtos de um tipo específico. Os tipos suportados incluem _Simples_, _Configurável_, _Virtual_, _Baixável_ ou _Cartão-presente_. _Pacote_ e _Agrupado_ Os produtos da ainda não são compatíveis.

### Visibilidade

Filtra produtos com base na visibilidade, como: _Catálogo_, _Pesquisar_, ou ambos.

### Preço

Um filtro com base no preço do produto usa o preço final para executar a comparação. O preço final inclui descontos ou preços especiais disponíveis para compradores anônimos. Para os comerciantes B2B, o preço exibido reflete o [preço de grupo específico do cliente](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) você configurou o.

### Status do estoque

Os seguintes filtros de exclusão podem ser usados para filtrar produtos com base no status do estoque:

- Fora de estoque - (Somente exclusão) Exclui produtos que estão fora de estoque.
- Baixo em estoque - (Somente exclusão) Exclui produtos com baixo estoque. O status de estoque baixo se baseia na variável _Limite esquerdo somente X_ valor em [Configuração de inventário](https://experienceleague.adobe.com/docs/commerce-admin/config/catalog/inventory.html).
