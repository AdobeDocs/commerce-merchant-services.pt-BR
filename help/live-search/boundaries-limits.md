---
title: 'Limites e limites'
description: Saiba mais sobre os limites do  [!DNL Live Search]  para garantir que ele atenda às necessidades da sua empresa.
role: Admin, Developer
exl-id: ad6737f9-6ecd-4d82-89e7-d95425e4ba53
source-git-commit: 4898d426a3d5fd2ea9059d200ebf8ba45d0d65df
workflow-type: tm+mt
source-wordcount: '777'
ht-degree: 0%

---

# Limites e limites

Quando se trata de pesquisa no site, o Adobe Commerce oferece opções. Revise os limites e limites a seguir para garantir que o [!DNL Live Search] e o [!DNL Catalog Service] atendam às necessidades da sua empresa. Se você precisar de recursos de pesquisa avançada, como pesquisa de conteúdo, BYOA (traga seu próprio algoritmo) ou merchandising baseado em atributos, considere uma solução de pesquisa de terceiros.

## Geral

- O módulo [Pesquisa Avançada](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) é desabilitado quando [!DNL Live Search] é instalado e o link Pesquisa Avançada no rodapé da loja é removido.
- Não há suporte para [Preços da Camada](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) e [Preços Especiais](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) no campo [!DNL Live Search] e no Widget de página de listagem de produtos.
- Os preços dos produtos não incluem o imposto sobre o valor acrescentado (IVA).
- A pesquisa de conteúdo não é suportada.
- Há um limite de 10 mil produtos que podem ser paginados.
- Há um limite rígido de 1 MB por atributo, incluindo descrição e atributos personalizados.
- O adaptador de pesquisa não oferece suporte a atributos de produto criados com um modelo de origem personalizado e usados como facetas. Para oferecer suporte a esta funcionalidade, você deve usar o [Widget de página de listagem de produtos](plp-styling.md).

## Indexação

- [!DNL Live Search] [indexa](indexing.md) até um total de 450 atributos de produto por exibição de loja. Elas são distribuídas da seguinte maneira:
   - 50 atributos classificáveis
   - 200 atributos filtráveis
   - 200 atributos pesquisáveis
- [!DNL Live Search] indexa somente produtos do banco de dados do Adobe Commerce.
- As páginas do CMS não são indexadas.
- Os atributos SKU, nome e categoria podem ser pesquisados por padrão e não podem ser excluídos da pesquisa. Cancele a atribuição dos produtos às categorias se eles não forem destinados a essas categorias.

## Facetas

- Um máximo de 100 atributos podem ser configurados como facetas dos 200 atributos filtráveis que podem ser indexados.
- Dentro de uma faceta, um máximo de 100 grupos podem ser retornados. Se você precisar retornar mais de 100 compartimentos, [crie um tíquete de suporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) para que o Adobe possa analisar o impacto no desempenho e determinar se é viável aumentar esse limite no seu ambiente.
- Os aspectos dinâmicos podem causar problemas de desempenho em índices grandes e índices com alta ordinalidade. Se você tiver criado facetas dinâmicas e notar qualquer deterioração de desempenho ou carregamento de página sem erros de tempo limite, tente alterar suas facetas para fixado para determinar se isso resolve seu problema de desempenho.
- O status do estoque (`quantity_and_stock_status`) não tem suporte como uma faceta. Você pode usar o `inStock: 'true'` para filtrar por produtos de falta de estoque. Isso é suportado imediatamente no módulo `LiveSearchAdapter` quando &quot;Exibir produtos esgotados&quot; está definido como &quot;Verdadeiro&quot; no Administrador [!DNL Commerce].
- Atributos de tipo de data não são suportados como uma faceta.

## Query

- [!DNL Live Search] usa um [ponto de extremidade do GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/) exclusivo para as consultas a fim de oferecer suporte a recursos como facetas dinâmicas e search-as-you-type. Embora semelhante à [API do GraphQL](https://developer.adobe.com/commerce/webapi/graphql/), há algumas diferenças e alguns campos podem não ser totalmente compatíveis.
- O número máximo de resultados que podem ser retornados em uma consulta de pesquisa é 10.000.
- Não é possível filtrar resultados usando um atributo de tipo de data.

## Regras

- O número máximo de [regras](rules.md) de merchandising por exibição de loja é 50.
- O merchandising por categoria pode ter uma regra por categoria.
- O número máximo de condições por regra é 10.
- O número máximo de eventos por regra é 25.
- Para evitar resultados imprevisíveis em respostas paginadas, o número de produtos fixados não deve exceder o tamanho de página solicitado.

## Sinônimos

- [!DNL Live Search] pode gerenciar até 200 [sinônimos](synonyms.md) por exibição de armazenamento.
- Sinônimos de várias palavras podem nem sempre funcionar como esperado. Certifique-se de testar esses sinônimos no ambiente de preparo antes de usá-los na produção, pois eles podem ter um efeito adverso na relevância.

## Merchandising de categoria

- Uma regra por categoria pode ser criada para cada exibição de loja. Cada regra pode ter:
   - Até dez condições
   - Até 25 eventos

## Permissões B2B e de categoria

- Os produtos não serão exibidos se não forem adicionados a um catálogo compartilhado padrão.
- Para restringir grupos de clientes usando [permissões de categoria](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/category-permissions):
   - Os produtos devem ser atribuídos à categoria raiz.
   - O grupo de clientes &quot;Não conectado&quot; deve receber permissões de navegação &quot;Permitir&quot;.
   - Para restringir produtos ao grupo de clientes &quot;Não conectado&quot;, vá para cada categoria e defina as permissões para cada [grupo de clientes](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage).
- No momento, não há suporte pronto para uso para B2B com o widget PLP no PWA Studio. No entanto, você pode [usar a API](install.md#pwa-support) para implementar essa funcionalidade.
- Os aspectos da categoria em [!DNL Live Search] podem exibir categorias que não podem ser exibidas para um [grupo de clientes](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/shared-catalogs/catalog-shared-manage) específico.
- O [!DNL Live Search] pode oferecer suporte a até 1.000 grupos de clientes.

## [!DNL Storefront popover]

- O [[!DNL popover]](storefront-popover.md) está disponível somente para lojas que usam o tema *Luma* ou um tema personalizado baseado no *Luma*. As navegações estruturais na página de resultados da pesquisa não terão o estilo *Luma*.
- O [!DNL popover] não oferece suporte ao tema *Em branco*.
- Não há suporte para [!DNL popover] no formulário de Pedido rápido.
- As listas de desejos e as comparações de produtos não são compatíveis.
