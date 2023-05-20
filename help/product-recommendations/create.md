---
title: Criar nova recomendação
description: Saiba como criar uma unidade de recomendação de produto.
exl-id: d393ab78-0523-463f-9b03-ad3f523dce0f
source-git-commit: d56fd57281a5b675e128cca75d4057756a0bf4bf
workflow-type: tm+mt
source-wordcount: '853'
ht-degree: 0%

---

# Criar nova recomendação

Ao criar uma recomendação, você cria uma _unidade de recomendação_ que contém o produto recomendado _itens_.

![Unidade de recomendação](assets/unit.png)
_Unidade de recomendação_

Quando você ativa a unidade de recomendação, o Adobe Commerce começa a [coletar dados](workspace.md) para medir impressões, visualizações, cliques, etc. A variável [!DNL Product Recommendations] A tabela exibe as métricas de cada unidade de recomendação para ajudá-lo a tomar decisões de negócios informadas.

1. No _Admin_ barra lateral, vá para **Marketing** > _Promoções_ > **Recommendations do produto** para exibir o _Recommendations do produto_ espaço de trabalho.

1. Especifique a [Exibição da loja](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) onde você deseja que as recomendações sejam exibidas.

   >[!NOTE]
   >
   > As unidades de recomendação do Page Builder devem ser criadas na exibição de armazenamento padrão, mas podem ser usadas em qualquer lugar. Para saber mais sobre como criar recomendações de produto com o Page Builder, consulte [Adicionar conteúdo - Recommendations do produto](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html).

1. Clique em **Criar recomendação**.

1. No _Nomeie sua recomendação_ insira um nome descritivo para referência interna, como `Home page most popular`.

1. No _Selecionar tipo de página_ selecione a página onde deseja que a recomendação seja exibida a partir das seguintes opções:

   - Página inicial
   - Categoria
   - Detalhes do produto
   - Carrinho
   - Confirmação
   - [Page Builder](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html)

   Você pode criar até cinco unidades de recomendação ativas para cada tipo de página e até 25 para o Page Builder. O tipo de página fica esmaecido quando o limite é atingido.

   ![Nome e página da recomendação](assets/create-recommendation.png)
   _Nome da recomendação e posicionamento da página_

1. No _Selecionar tipo de recomendação_ especifique a [tipo de recomendação](type.md) que você deseja que apareça na página selecionada. Para algumas páginas, a variável [inserção](placement.md) de recomendações está limitado a certos tipos.

   Alguns tipos de recomendações usam dados comportamentais de seus compradores para [treinar modelos de aprendizado de máquina](behavioral-data.md) para criar recomendações personalizadas. Para ajudá-lo a visualizar o progresso do treinamento de cada tipo de recomendação, esta seção exibe uma medida de disponibilidade para cada tipo. Esses indicadores de prontidão são calculados com base em dois fatores:

   - Tamanho suficiente do conjunto de resultados: há resultados suficientes sendo retornados na maioria dos cenários para evitar o uso de [recomendações de backup](behavioral-data.md#backuprecs)?

   - Variedade suficiente do conjunto de resultados: os produtos retornados representam uma variedade de produtos do catálogo? O objetivo com esse fator é evitar que uma minoria de produtos seja os únicos itens recomendados no site.

   Com base nos fatores acima, um valor de disponibilidade é calculado e exibido. Um tipo de recomendação é considerado pronto para implantação quando seu valor de disponibilidade é de 75% ou superior. Um tipo de recomendação é considerado parcialmente pronto quando sua disponibilidade é de pelo menos 50%. Finalmente, um tipo de recomendação é considerado não pronto para implantação quando seu valor de disponibilidade é inferior a 50%.

   ![Tipo de recomendação](assets/create-recommendation-select-type.png)
   _Tipo de recomendação_

1. No _Rótulo de exibição da loja_ , insira o [rótulo](placement.md#recommendation-labels) visível para seus compradores, como &quot;Mais vendidos&quot;.

1. No _Escolha o número de produtos_ use o controle deslizante para especificar quantos produtos você deseja exibir na unidade de recomendação.

   O padrão é `5`, com um máximo de `20`.

1. No _Selecionar posicionamento_ especifique o local onde a unidade de recomendação deve aparecer na página.

   - Na parte inferior do conteúdo principal
   - Na parte superior do conteúdo principal

1. (Opcional) Para alterar a ordem das recomendações, selecione e mova as linhas na _Escolher posição_ tabela.

   A variável _Escolher posição_ exibe todas as recomendações (se houver) criadas para o tipo de página selecionado.

   ![Ordem de recomendação](assets/create-recommendation-select-placement.png)
   _Ordem de recomendação na página_

1. (Opcional) Na _Filtros_ seção, [aplicar filtros](filters.md) para controlar quais produtos aparecem na unidade de recomendação.

   ![Filtros de recomendação](assets/create-recommendation-filter-products.png)
   _Filtros de produto do Recommendation_

1. Quando terminar, clique em uma das opções a seguir:

   - **Salvar como rascunho** para editar a unidade de recomendação mais tarde. Não é possível modificar o tipo de página ou de recomendação de uma unidade de recomendação em um estado de rascunho.

   - **Ativar** para ativar a unidade de recomendação na loja.

## Visualizar Recommendations {#preview}

A variável _Visualização de produtos recomendada_ O painel está sempre disponível com uma amostra de seleção de produtos que podem aparecer na unidade de recomendação quando ela for implantada na loja.

Para testar uma recomendação ao trabalhar em um ambiente de não produção, você pode buscar dados de recomendação de uma [origem diferente](settings.md). Isso permite que os comerciantes experimentem com regras e visualizem as recomendações antes de implantar na produção.

| Campo | Descrição |
|---|---|
| Nome | O nome do produto. |
| SKU | A Unidade de Manutenção de Estoque atribuída ao produto |
| Preço | O preço do produto. |
| Tipo de resultado | Principal - indica que há dados de treinamento suficientes coletados para exibir uma recomendação.<br />Backup - indica que não há dados de treinamento suficientes coletados, de modo que uma recomendação de backup é usada para preencher o slot. Ir para [Dados comportamentais](behavioral-data.md) para saber mais sobre modelos de aprendizado de máquina e recomendações de backup. |

À medida que você cria sua unidade de recomendação, experimente o tipo de página, o tipo de recomendação e os filtros para obter feedback imediato em tempo real sobre os produtos que serão incluídos. À medida que você começa a entender quais produtos aparecem, é possível configurar a unidade de recomendação para atender às suas necessidades comerciais.

Adobe Commerce [filtros](filters.md) recomendações para evitar a exibição de produtos duplicados quando várias unidades de recomendação são implantadas em uma única página. Como resultado, os produtos exibidos no painel de visualização podem ser diferentes daqueles exibidos na loja.

>[!NOTE]
>
> Não é possível visualizar o `Recently viewed` tipo de recomendação porque os dados não estão disponíveis no Administrador.
