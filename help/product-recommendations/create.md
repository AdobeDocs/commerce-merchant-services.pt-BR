---
title: Criar Nova Recomendação
description: Saiba como criar uma unidade de recomendação de produto.
exl-id: d393ab78-0523-463f-9b03-ad3f523dce0f
source-git-commit: d56fd57281a5b675e128cca75d4057756a0bf4bf
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 0%

---

# Criar Nova Recomendação

Ao criar uma recomendação, você cria uma _unidade de recomendação_ que contém o produto recomendado _items_.

![Unidade de recomendação](assets/unit.png)
_Unidade de recomendação_

Quando você ativa a unidade de recomendação, o Adobe Commerce começa a [coletar dados](workspace.md) para medir impressões, visualizações, cliques e assim por diante. O [!DNL Product Recommendations] tabela exibe as métricas de cada unidade de recomendação para ajudá-lo a tomar decisões comerciais informadas.

1. No _Administrador_ barra lateral, vá para **Marketing** > _Promoções_ > **Recommendations do produto** para exibir o _Recommendations do produto_ espaço de trabalho.

1. Especifique a [Exibição da loja](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) onde deseja que as recomendações sejam exibidas.

   >[!NOTE]
   >
   > As unidades de recomendação do Page Builder devem ser criadas na exibição de loja padrão, mas podem ser usadas em qualquer lugar. Para saber mais sobre como criar recomendações de produto com o Page Builder, consulte [Adicionar conteúdo - Recommendations do produto](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html).

1. Clique em **Criar recomendação**.

1. No _Dê um nome à recomendação_ digite um nome descritivo para referência interna, como `Home page most popular`.

1. No _Selecionar tipo de página_ selecione a página onde deseja que a recomendação apareça a partir das seguintes opções:

   - Página inicial
   - Categoria
   - Detalhes do produto
   - Carrinho
   - Confirmação
   - [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html)

   É possível criar até cinco unidades de recomendação ativas para cada tipo de página e até 25 para o Construtor de página. O tipo de página é esmaecido quando o limite é atingido.

   ![Nome e página da recomendação](assets/create-recommendation.png)
   _Nome da recomendação e posicionamento da página_

1. No _Selecionar tipo de recomendação_ especifique a [tipo de recomendação](type.md) você deseja aparecer na página selecionada. Para algumas páginas, a variável [placement](placement.md) O de recomendações está limitado a certos tipos de recomendações.

   Alguns tipos de recomendação usam dados comportamentais de seus compradores para [modelos de aprendizagem de máquina de comboio](behavioral-data.md) para criar recomendações personalizadas. Para ajudá-lo a visualizar o progresso de treinamento de cada tipo de recomendação, esta seção exibe uma medida de disponibilidade para cada tipo. Esses indicadores de prontidão são calculados com base em dois fatores:

   - Tamanho suficiente do conjunto de resultados: Há resultados suficientes sendo retornados na maioria dos cenários para evitar o uso de [recomendações de backup](behavioral-data.md#backuprecs)?

   - Variedade suficiente do conjunto de resultados: Os produtos que estão sendo retornados representam uma variedade de produtos do seu catálogo? O objetivo com esse fator é evitar que uma minoria de produtos seja os únicos itens recomendados no site.

   Com base nos fatores acima, um valor de prontidão é calculado e exibido. Um tipo de recomendação é considerado pronto para ser implantado quando seu valor de prontidão for 75% ou superior. Um tipo de recomendação é considerado parcialmente pronto quando sua prontidão é de pelo menos 50%. Finalmente, um tipo de recomendação é considerado como não pronto para ser implantado quando seu valor de prontidão for inferior a 50%.

   ![Tipo de recomendação](assets/create-recommendation-select-type.png)
   _Tipo de recomendação_

1. No _Rótulo de exibição da frente de loja_ digite o [label](placement.md#recommendation-labels) que é visível para seus compradores, como &quot;Mais vendidos&quot;.

1. No _Escolha o número de produtos_ use o controle deslizante para especificar quantos produtos você deseja exibir na unidade de recomendação.

   O padrão é `5`, com um máximo de `20`.

1. No _Selecionar posicionamento_ , especifique o local onde a unidade de recomendação deve aparecer na página.

   - Na parte inferior do conteúdo principal
   - Na parte superior do conteúdo principal

1. (Opcional) Para alterar a ordem das recomendações, selecione e mova as linhas na _Escolher posição_ tabela.

   O _Escolher posição_ exibe todas as recomendações (se houver) criadas para o tipo de página selecionado.

   ![Ordem de recomendação](assets/create-recommendation-select-placement.png)
   _Ordem de recomendação na página_

1. (Opcional) Na seção _Filtros_ seção, [aplicar filtros](filters.md) para controlar quais produtos aparecem na unidade de recomendação.

   ![Filtros de recomendação](assets/create-recommendation-filter-products.png)
   _Filtros de produto de recomendação_

1. Ao concluir, clique em uma das seguintes opções:

   - **Salvar como rascunho** para editar a unidade de recomendação mais tarde. Não é possível modificar o tipo de página ou o tipo de recomendação para uma unidade de recomendação em um estado de rascunho.

   - **Ativar** para habilitar a unidade de recomendação na loja.

## Visualizar Recommendations {#preview}

O _Visualização de produtos recomendados_ O painel sempre está disponível com uma amostra de produtos que podem aparecer na unidade de recomendação quando for implantado na loja.

Para testar uma recomendação ao trabalhar em um ambiente que não seja de produção, você pode buscar dados de recomendação de um [fonte diferente](settings.md). Isso permite que os comerciantes experimentem as regras e visualizem as recomendações antes de implantá-las na produção.

| Campo | Descrição |
|---|---|
| Nome | O nome do produto. |
| SKU | Unidade de manutenção de estoque atribuída ao produto |
| Preço | O preço do produto. |
| Tipo de Resultado | Primário - indica que há dados de treinamento suficientes coletados para exibir uma recomendação.<br />Backup - indica que não há dados de treinamento suficientes coletados, de modo que uma recomendação de backup é usada para preencher o slot. Ir para [Dados comportamentais](behavioral-data.md) para saber mais sobre modelos de aprendizado de máquina e recomendações de backup. |

À medida que você cria a unidade de recomendação, experimente o tipo de página, o tipo de recomendação e os filtros para obter feedback imediato em tempo real sobre os produtos que serão incluídos. Assim que você começar a entender quais produtos aparecem, poderá configurar a unidade de recomendação para atender às suas necessidades comerciais.

Adobe Commerce [filtros](filters.md) recomendações para evitar a exibição de produtos duplicados quando várias unidades de recomendação forem implantadas em uma única página. Como resultado, os produtos que aparecem no painel de visualização podem ser diferentes daqueles que aparecem na loja.

>[!NOTE]
>
> Não é possível visualizar o `Recently viewed` tipo de recomendação porque os dados não estão disponíveis em Admin.
