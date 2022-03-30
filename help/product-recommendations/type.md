---
title: Tipos de recomendação
description: Saiba mais sobre as recomendações que você pode implantar em várias páginas do seu site.
source-git-commit: 7fe89df32dc5363817f957180e5b75e7217fc14a
workflow-type: tm+mt
source-wordcount: '1383'
ht-degree: 0%

---

# Tipos de recomendação

O Adobe Commerce fornece um grande conjunto de recomendações que você pode implantar em várias páginas do site. Para facilitar a referência, os tipos de recomendação são agrupados da seguinte maneira:

- [Personalizado](#personalized)
- [Vendas cruzadas e vendas adicionais](#crossup)
- [Popularidade](#popularity)
- [Alto desempenho](#highperf)

Como prática recomendada, o Adobe recomenda as seguintes diretrizes ao usar as recomendações:

- Diversifique seus tipos de recomendação. Os clientes começam a ignorar as recomendações se sugerirem os mesmos produtos repetidamente.

- Não implante as mesmas recomendações na página do carrinho e na página de confirmação do pedido. Considere usar `Most Added to Cart` para a página do carrinho e `Bought This, Bought That` para obter a página de confirmação do pedido.

- Mantenha seu site arrumado. Não implante mais de três unidades de recomendação na mesma página.

- Se sua loja vende roupas, a variável `More like this` recomendação pode sugerir itens específicos de gênero que não correspondam ao gênero do produto que está sendo visualizado. Considere usar somente esse tipo de recomendação para categorias que não sejam de roupas.

## Personalizado {#personalized}

| Tipo | Descrição |
|---|---|
| Recomendado para você | Recomenda itens com base no comportamento atual e anterior de cada comprador no local. Exibe recomendações altamente relevantes com base no histórico de navegação e compra do comprador. Esse tipo de recomendação entra em vigor na página inicial, onde a maioria dos compradores inicia a jornada em um site. Para compradores pela primeira vez em seu site que não geraram nenhum sinal para personalizar sua experiência, o Adobe Commerce mostra itens com base no tipo de recomendação Mais visualizado . No entanto, quando o comprador começa a interagir com os produtos no site, os produtos recomendados ajustam-se em tempo real ao seu comportamento.<br /><br />Foram utilizados:<br /><br />- Página inicial<br />- Categoria<br /><br />Rótulos sugeridos:<br /><br /> - Apenas para você<br />- Recomendado para você<br />- Inspirado pelas suas tendências de compras |
| Visualizados recentemente | Exibe os produtos visualizados mais recentemente pelo comprador, com base no histórico do navegador. Qualquer produto excluído é removido pela unidade de recomendação. A unidade de recomendação não será exibida se não houver histórico do navegador ou se não houver histórico suficiente quando as regras de filtro forem aplicadas. Se os resultados contiverem menos produtos do que estão configurados, a unidade de recomendação exibirá apenas os produtos retornados.<br /><br />Quando usado:<br /><br />- Página inicial<br />- Categoria<br />- Detalhes do produto<br />- Carrinho<br />- Confirmação<br /><br />Rótulos sugeridos:<br /><br />- Visualizados recentemente<br />- Dê outra olhada |

## Vendas cruzadas e vendas adicionais {#crossup}

| Tipo | Descrição |
|---|---|
| Visualizou isso, viu que | Recomenda itens vistos com mais frequência por outros compradores que visualizaram o mesmo item. Geralmente chamada de recomendação de prova social que ajuda os compradores a encontrar produtos como outros compradores.<br /><br />Quando usado:<br />- Detalhes do produto<br />- Carrinho<br />- Confirmação<br /><br />Rótulos sugeridos:<br ><br />- Clientes que visualizaram este item também visualizaram (PDP) |
| Visualizou isto, comprou aquilo | Recomenda itens comprados com mais frequência por compradores que visualizaram o item especificado. Ajuda a orientar os compradores a descobrir produtos que eles talvez não tenham notado de outra forma.<br /><br />Quando usado:<br /><br />- Detalhes do produto<br />- Carrinho<br />- Confirmação<br /><br />Rótulos sugeridos:<br /><br />- Clientes que viram este último produto comprado<br />- Clientes que acabaram comprando<br />- O que outras pessoas compram após verem este item? |
| Comprou isto, comprou aquilo | Recomenda itens comprados com mais frequência por compradores que compraram o item especificado. Usada com mais frequência na página de detalhes do carrinho ou do produto para aumentar a exposição de produtos relacionados de venda cruzada para aumentar o valor médio de pedido. Exibe produtos altamente relevantes que os compradores podem adicionar ao carrinho agregando o que outros compradores compraram com o produto atual.<br /><br />Quando usado:<br /><br />- Detalhes do produto<br />- Carrinho<br />- Confirmação<br /><br />Rótulos sugeridos:<br /><br />- Obtenha tudo o que você precisa<br />- Não esqueça estes<br />- Frequentemente comprados juntos |
| Mais artigos como este | Recomenda itens com base em conteúdo e atributos semelhantes. Ao avaliar os atributos dos produtos que estão sendo visualizados, a recomenda produtos semelhantes na mesma categoria. Por exemplo, se um comprador estiver navegando por correspondências de ioga, outros produtos da categoria de equipamento são recomendados. Como esse tipo de recomendação não diferencia gêneros, não é recomendado para vestuário, moda ou outros ramos específicos de gênero.<br /><br />Quando usado:<br /><br />- Detalhes do produto<br />- Carrinho<br />- Confirmação<br /><br />Rótulos sugeridos:<br /><br /> - Mais itens como este<br />- Semelhante a este |
| [Similaridade visual](#visualsim) | Recomenda produtos com aparência semelhante ao produto que está sendo visualizado. Esse tipo de recomendação é mais útil se imagens e os aspectos visuais dos produtos forem importantes para a experiência de compras. |

## Popularidade {#popularity}

| Tipo | Descrição |
|---|---|
| Mais visualizados | Recomenda produtos que foram mais vistos contando o número de sessões em que uma ação de exibição ocorreu nos últimos sete dias.<br /><br />Quando usado:<br /><br />- Página inicial<br />- Categoria<br />- Detalhes do produto<br />- Carrinho<br />- Confirmação<br /><br />Rótulos sugeridos:<br /><br />- Mais popular<br />- Tendências<br />- Popular agora<br />- Recentemente popular<br />- Itens populares inspirados neste item (PDP)<br />- Mais vendidos |
| Tendência | Recomenda itens com base na dinâmica recente da popularidade de um produto no seu site.<br /><br />O Adobe Sensei agrega dados de navegação e compra em seu site para determinar e classificar quais produtos são os mais populares recentemente com seus compradores. Como a Tendência analisa a dinâmica recente do produto, é um tipo de recomendação eficaz para catálogos que têm um alto faturamento. Se o catálogo for mais estático, pode não ser tão útil quanto os padrões de compra do público-alvo são altamente variáveis.<br /><br />Quando usado na página inicial, a Tendência recomenda itens que são populares recentemente em todo o site. As tendências não exibem produtos que são consistentemente populares, mas aqueles que se tornaram populares recentemente. Por exemplo, se você tiver uma campanha de marketing por email promovendo determinados produtos, o aumento da popularidade gerado pelo email aumenta a probabilidade dos produtos promovidos se classificarem como tendências.<br /><br />Quando usado:<br /><br />- Página inicial<br />- Categoria<br />- Detalhes do produto<br />- Carrinho<br />- Confirmação<br /><br />Rótulos sugeridos:<br /><br />- Tendências<br />- Tendências agora<br />- Tendências recentes<br />- Itens quentes<br />- Produtos relacionados com a tendência (PDP) |

## Alto desempenho {#highperf}

| Tipo | Descrição |
|---|---|
| Exibir para conversão de compra | Recomenda produtos com a maior taxa de conversão de exibição para compra. De todas as sessões de compras que visualizaram o produto, a porcentagem que comprou o produto.<br /><br />Quando usado:<br /><br />- Página inicial<br />- Categoria<br />- Detalhes do produto<br />- Carrinho<br />- Confirmação<br /><br />Rótulos sugeridos:<br /><br /> -Mais vendidos<br />- Itens populares<br />- Você pode estar interessado em |
| Exibir para conversão do carrinho | Recomenda produtos com a maior taxa de conversão de exibição em carrinho. De todas as sessões de compras que visualizaram o produto, a porcentagem que adicionou o produto ao carrinho.<br /><br />Quando usado:<br /><br />- Página inicial<br />- Categoria<br />- Detalhes do produto<br />- Carrinho<br />- Confirmação<br /><br />Rótulos sugeridos:<br /><br /> - Mais vendidos<br />- Itens populares<br />- Você pode estar interessado em |
| Mais comprados | Geralmente chamada de &quot;Mais vendidos&quot;, esse tipo de recomendação conta o número de sessões em que uma ação de pedido local ocorreu nos últimos sete dias. Esse tipo de recomendação pode ser usado em todas as páginas.<br /><br />Quando usado:<br /><br />- Página inicial<br />- Categoria<br />- Detalhes do produto<br />- Carrinho<br />- Confirmação<br /><br />Rótulos sugeridos:<br /><br /> - Mais popular<br />- Tendências<br />- Popular agora<br />- Recentemente popular<br />- Itens populares inspirados neste item (PDP)<br />- Mais vendidos |
| Mais adicionado ao carrinho | Recomenda itens adicionados com mais frequência aos carrinhos pelos compradores nos últimos sete dias. Esse tipo de recomendação pode ser usado em todas as páginas.<br /><br />Quando usado:<br /><br />- Página inicial<br />- Categoria<br />- Detalhes do produto<br />- Carrinho<br />- Confirmação<br /><br />Rótulos sugeridos:<br /><br /> - Mais popular<br />- Tendências<br />- Popular agora<br />- Recentemente popular<br />- Itens populares inspirados neste item (PDP)<br />- Mais vendidos |

## Similaridade visual {#visualsim}

O _Similaridade visual_ o tipo de recomendação recomenda produtos com aparência semelhante ao produto que está sendo visualizado. Esse tipo de recomendação é mais útil quando imagens e aspectos visuais dos produtos são partes importantes da experiência de compras.

### Como funciona

O _Similaridade visual_ o tipo de recomendação oferece recomendações para outros produtos em seu catálogo que têm uma semelhança visual com as imagens que estão sendo visualizadas no momento. A semelhança visual inclui aspectos como:

- Cor
- Forma
- Tamanho
- Textura
- Material
- Estilo

O Adobe Sensei usa a IA para processar e analisar as imagens em seu catálogo e criar atributos usados para determinar semelhanças visuais.

>[!NOTE]
>
> Se você estiver testando esse tipo de recomendação em um ambiente de não produção, verifique se os URLs de imagem estão acessíveis publicamente.

>[!NOTE]
>
> Atualmente, as imagens do produto devem ter 10 MB ou menos.

Como esse tipo de recomendação não se aplica à maioria dos catálogos, ele não é ativado por padrão. Você deve ativar explicitamente esse tipo de recomendação.

### Ativar o tipo de recomendação de semelhança visual

>[!NOTE]
>
> O _Similaridade visual_ o tipo de recomendação está disponível quando você [instalar](install-configure.md) como um módulo opcional.

1. No _Administrador_ barra lateral, vá para **Marketing** > _Promoções_ > **Recommendations do produto** para exibir o _Recommendations do produto_ painel.

1. Clique em **Configurações** (ícone de engrenagem) para exibir o _Configurações_ página.

1. No _Visual Recommendations_ selecione para **Habilitar o Visual Recommendations**.

1. Clique em **Salvar alterações** quando você terminar.

   O [Criar Nova Recomendação](create.md) agora é exibida **Similaridade visual** como um tipo de recomendação selecionável quando o tipo de página é **Detalhes do produto**.

Depois de ativar as recomendações visuais, o Adobe Sensei inicia o processamento da imagem. Quanto tempo leva depende do tamanho do catálogo.

### Onde usado

- Detalhes do produto

### Rótulos de vitrine sugeridos

- Você também pode
- Encontramos outros produtos que você pode desejar
- Inspirado por este estilo

### Exemplo

A imagem a seguir mostra a página de detalhes do produto da _Relógio_:

![Relógio](assets/visual-sim-pdp.png)

O exemplo a seguir mostra o _Similaridade visual_ unidade de recomendação para _Relógio_:

![Unidade de semelhança visual](assets/visual-sim-unit.png)
