---
title: Editar recomendação
description: Saiba como editar uma recomendação de produto.
exl-id: 36fd6d3a-74f8-4510-a187-a2a91742cd1a
source-git-commit: e7c3d1ab49ee9469e3312321f6d96446840d0778
workflow-type: tm+mt
source-wordcount: '427'
ht-degree: 0%

---

# Editar recomendação

A página Editar recomendação oferece a capacidade de ajustar as configurações individuais que compõem a recomendação. Todas as configurações podem ser editadas, exceto o tipo de página e o tipo de recomendação. As seguintes configurações podem ser editadas:

- [Nome da recomendação](#name)
- [Rótulo da vitrine](#label)
- [Número de produtos](#number)
- [Posicionamento e Posição](#placement)
- [Filtrar produtos](#filters)

A visualização no lado direito da página mostra como a recomendação com as configurações atuais pode aparecer na loja. A variável _Visualização de produtos recomendada_ O permanece visível para referência à medida que você rolar a página para baixo. A visualização exibe uma imagem do produto em miniatura, o nome do produto, SKU, preço e tipo de resultado para cada produto retornado. O tipo de resultado indica se há dados comportamentais primários suficientes para gerar a recomendação ou se está usando dados comportamentais de backup.

![Editar Recommendations](assets/edit-recommendation.png)

## Editar uma recomendação

1. No _Admin_ barra lateral, vá para **Marketing** > _Promoções_ > **Recommendations do produto**.

1. Selecione a recomendação que deseja editar.

1. Clique em **Editar**. Em seguida, siga as instruções abaixo para fazer as alterações necessárias.

1. Quando terminar, clique em **Salvar alterações**.

### Nome da recomendação {#name}

Escolha um nome descritivo que indique a finalidade da recomendação. O nome é para referência interna e não aparece na loja.

![Editar nome](assets/edit-name.png)

### Rótulo da vitrine {#label}

Insira o texto que deseja usar como rótulo para a unidade de recomendação na vitrine.

![Editar rótulo](assets/edit-storefront-label.png)

### Número de produtos {#number}

Ajuste o controle deslizante para exibir até 20 produtos na unidade de recomendação.

![Editar número de produtos](assets/edit-number-of-products.png)

### Posicionamento e posição {#placement}

1. Escolha o local da página onde a unidade de recomendação deve aparecer na loja.

   - Na parte inferior do conteúdo principal
   - Na parte superior do conteúdo principal

   ![Editar inserção](assets/edit-placement.png)

1. Para alterar a ordem das recomendações incluídas na unidade, use o **Mover** ![Mover seletor](assets/icon-move.png) controle para arrastar as recomendações para a posição.

   ![Editar posição](assets/edit-position.png)

### Filtrar produtos {#filters}

Quaisquer alterações feitas no produto [filtros](filters.md) são refletidos na _Visualização de produtos recomendada_. Somente os produtos que correspondem aos filtros de inclusão podem ser recomendados. Os produtos que correspondem a qualquer filtro de exclusão não são recomendados.

A variável _Inclusões_ e _Exclusões_ As guias listam os filtros disponíveis de cada tipo. Na lista, cada filtro ativo é marcado com um ponto azul.

- Para exibir os detalhes sobre cada filtro, clique no nome do filtro.
- Para alterar o status do filtro, defina a variável **Ativar filtro** alternar para a variável `on` ou `off` posição.

![Editar filtros](assets/edit-filters.png)

As configurações de filtro descrevem os produtos a serem incluídos ou excluídos na unidade de recomendação. Por exemplo, a variável _Categoria_ as configurações de inclusão de filtro informam o sistema para incluir produtos somente das categorias selecionadas.

![Editar filtro de categorias](assets/edit-filter-category.png)
