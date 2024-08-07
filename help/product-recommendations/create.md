---
title: Criar nova recomendação
description: Saiba como criar uma unidade de recomendação de produto.
exl-id: d393ab78-0523-463f-9b03-ad3f523dce0f
source-git-commit: 51ff52eba117fe438d592ca886dbca25304a0d15
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 0%

---

# Criar nova recomendação

Ao criar uma recomendação, você cria uma _unidade de recomendação_ que contém o produto recomendado _itens_.

![Unidade de recomendação](assets/unit.png)
_Unidade de recomendação_

Quando você ativa a unidade de recomendação, o Adobe Commerce começa a [coletar dados](workspace.md) para medir impressões, exibições, cliques e assim por diante. A tabela [!DNL Product Recommendations] exibe as métricas de cada unidade de recomendação para ajudá-lo a tomar decisões de negócios conscientes.

1. Na barra lateral _Admin_, vá para **Marketing** > _Promoções_ > **Recommendations de Produtos** para exibir o espaço de trabalho do _Recommendations de Produtos_.

1. Especifique o [Modo de Exibição de Armazenamento](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) onde deseja que as recomendações sejam exibidas.

   >[!NOTE]
   >
   > As unidades de recomendação do Page Builder devem ser criadas na exibição de armazenamento padrão, mas podem ser usadas em qualquer lugar. Para saber mais sobre como criar recomendações de produto com o Page Builder, consulte [Adicionar conteúdo - Recommendations do produto](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html).

1. Clique em **Criar recomendação**.

1. Na seção _Nomeie sua recomendação_, digite um nome descritivo para referência interna, como `Home page most popular`.

1. Na seção _Selecionar tipo de página_, selecione a página na qual deseja que a recomendação seja exibida a partir das seguintes opções:

   >[!NOTE]
   >
   > Não há suporte para Recommendations de produto na página Carrinho quando sua loja está configurada para [exibir a página do carrinho de compras imediatamente após adicionar um produto ao carrinho](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/cart/cart-configuration.html#redirect-to-cart).

   * Página inicial
   * Categoria
   * Detalhes do produto
   * Carrinho
   * Confirmação
   * [Construtor de páginas](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html)

   Você pode criar até cinco unidades de recomendação ativas para cada tipo de página e até 25 para o Page Builder. O tipo de página fica esmaecido quando o limite é atingido.

   ![Nome e página de recomendação](assets/create-recommendation.png)
   _Nome de recomendação e posicionamento da página_

1. Na seção _Selecionar tipo de recomendação_, especifique o [tipo de recomendação](type.md) que você deseja exibir na página selecionada. Para algumas páginas, o [posicionamento](placement.md) das recomendações está limitado a certos tipos.

1. Na seção _Rótulo de exibição da vitrine_, digite o [rótulo](placement.md#recommendation-labels) que está visível para os seus compradores, como &quot;Mais vendidos&quot;.

1. Na seção _Escolher número de produtos_, use o controle deslizante para especificar quantos produtos você deseja exibir na unidade de recomendação.

   O padrão é `5`, com um máximo de `20`.

1. Na seção _Selecionar posicionamento_, especifique o local em que a unidade de recomendação deve aparecer na página.

   * Na parte inferior do conteúdo principal
   * Na parte superior do conteúdo principal

1. (Opcional) Para alterar a ordem das recomendações, selecione e mova as linhas na tabela _Escolher posição_.

   A seção _Escolher posição_ exibe todas as recomendações (se houver) criadas para o tipo de página selecionado.

   ![Ordem de recomendação](assets/create-recommendation-select-placement.png)
   _Ordem de recomendação na página_

1. (Opcional) Na seção _Filtros_, [aplique filtros](filters.md) para controlar quais produtos aparecem na unidade de recomendação.

   ![Filtros de recomendação](assets/create-recommendation-filter-products.png)
   _Filtros de produto de recomendação_

1. Quando terminar, clique em uma das opções a seguir:

   * **Salvar como rascunho** para editar a unidade de recomendação mais tarde. Não é possível modificar o tipo de página ou de recomendação de uma unidade de recomendação em um estado de rascunho.

   * **Ative** para habilitar a unidade de recomendação na sua vitrine eletrônica.

## Indicadores de disponibilidade

Alguns tipos de recomendações usam dados comportamentais dos compradores para [treinar modelos de aprendizado de máquina](behavioral-data.md) para criar recomendações personalizadas.

Requer apenas dados de catálogo. Não são necessários dados comportamentais para:

* _Mais artigos como este_
* _Visualizado recentemente_
* _Similaridade visual_

Com base nos últimos seis meses de dados comportamentais da loja:

* _Visualizou isto, visualizou aquilo_
* _Visualizou isto, comprou aquilo_
* _Comprei isto, comprei aquilo_
* _Recomendado para você_

Os tipos de recomendação baseados em popularidade usam os últimos sete dias dos dados comportamentais da loja:

* Mais visualizados
* Mais comprados
* Adicionado ao carrinho
* Tendências

Espera-se que os valores do indicador de disponibilidade flutuem devido a fatores como o tamanho geral do catálogo, o volume de eventos de interação do produto (visualizações, adições ao carrinho, compras) e a porcentagem de skus que registram esses eventos em uma determinada janela de tempo, conforme listado acima. Por exemplo, durante o pico do tráfego na temporada de festas, os indicadores de disponibilidade podem mostrar valores mais altos do que nos momentos de volume normal.

Para ajudá-lo a visualizar o progresso do treinamento de cada tipo de recomendação, a seção _Selecionar tipo de Recomendação_ exibe uma medida de prontidão para cada tipo. Esses indicadores de prontidão são calculados com base em dois fatores:

* Tamanho suficiente do conjunto de resultados: há resultados suficientes sendo retornados na maioria dos cenários para evitar o uso de [recomendações de backup](behavioral-data.md#backuprecs)?

* Variedade suficiente do conjunto de resultados: os produtos retornados representam uma variedade de produtos do catálogo? O objetivo com esse fator é evitar que uma minoria de produtos seja os únicos itens recomendados no site.

Com base nos fatores acima, um valor de disponibilidade é calculado e exibido. Um tipo de recomendação é considerado pronto para implantação quando seu valor de disponibilidade é de 75% ou superior. Um tipo de recomendação é considerado parcialmente pronto quando sua disponibilidade é de pelo menos 50%. Um tipo de recomendação é considerado não pronto para implantação quando seu valor de disponibilidade é inferior a 50%. Essas são diretrizes gerais, mas cada caso individual pode diferir com base na natureza dos dados coletados, conforme descrito acima.

![Tipo de recomendação](assets/create-recommendation-select-type.png)
_Tipo de recomendação_

>[!NOTE]
>
>Os indicadores podem nunca atingir 100%.

## Visualizar Recommendations {#preview}

O painel _Visualização de produtos recomendada_ está sempre disponível com uma amostra de seleção de produtos que podem aparecer na unidade de recomendação quando ela for implantada na loja.

Para testar uma recomendação ao trabalhar em um ambiente de não produção, você pode buscar dados de recomendação de uma [fonte diferente](settings.md). Isso permite que os comerciantes experimentem com regras e visualizem as recomendações antes de implantar na produção.

| Campo | Descrição |
|---|---|
| Nome | O nome do produto. |
| SKU | A Unidade de Manutenção de Estoque atribuída ao produto |
| Preço | O preço do produto. |
| Tipo de resultado | Principal - indica que há dados de treinamento suficientes coletados para exibir uma recomendação.<br />Backup - indica que não há dados de treinamento suficientes coletados, portanto, uma recomendação de backup é usada para preencher o slot. Acesse [Dados comportamentais](behavioral-data.md) para saber mais sobre modelos de aprendizado de máquina e recomendações de backup. |

À medida que você cria sua unidade de recomendação, experimente o tipo de página, o tipo de recomendação e os filtros para obter feedback imediato em tempo real sobre os produtos que serão incluídos. À medida que você começa a entender quais produtos aparecem, é possível configurar a unidade de recomendação para atender às suas necessidades comerciais.

Recomendações de [filtros](filters.md) do Adobe Commerce para evitar a exibição de produtos duplicados quando várias unidades de recomendação são implantadas em uma única página. Como resultado, os produtos exibidos no painel de visualização podem ser diferentes daqueles exibidos na loja.

>[!NOTE]
>
> Você não pode visualizar o tipo de recomendação `Recently viewed` porque os dados não estão disponíveis no Administrador.
