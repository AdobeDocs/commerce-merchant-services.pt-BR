---
title: "[!DNL Live Search] Limites e limites"
description: "Saiba mais sobre os limites e as limitações do [!DNL Live Search] para garantir que atenda às necessidades da sua empresa."
role: Admin, Developer
source-git-commit: 8aca09aba13e32afb191169729dfc1fbd0087262
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---

# Limites e limites

Quando se trata de pesquisa no site, o Adobe Commerce oferece opções. Revise os seguintes limites e limites para garantir que [!DNL Live Search] e [!DNL Catalog Service] atenda às necessidades da sua empresa. Se você precisar de recursos de pesquisa avançada, como pesquisa de conteúdo, BYOA (traga seu próprio algoritmo) ou merchandising baseado em atributos, considere uma solução de pesquisa de terceiros.

## Geral

- A variável [Pesquisa avançada](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) o módulo é desativado quando [!DNL Live Search] O está instalado e o link Pesquisa avançada no rodapé da loja é removido.
- [Preços da camada](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-tier) e [Preços Especiais](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) não são compatíveis com o [!DNL Live Search] Widget de página de listagem de campo e produto.
- [!DNL Live Search] O não pode agregar dados de inventário de várias fontes.
- Os preços dos produtos não incluem o imposto sobre o valor acrescentado (IVA).
- A pesquisa de conteúdo não é suportada.
- Há um limite de 10 mil produtos que podem ser paginados.

## Indexação

- [!DNL Live Search] [índices](indexing.md) até 450 atributos de produto por exibição de loja. Elas são distribuídas da seguinte maneira:
   - 50 atributos classificáveis
   - 200 atributos filtráveis
   - 200 atributos pesquisáveis
- [!DNL Live Search] indexa somente produtos do banco de dados do Adobe Commerce.
- As páginas CMS não são indexadas.

## Facetas

- Um máximo de 100 atributos podem ser configurados como facetas dos 200 atributos filtráveis que podem ser indexados.
- Dentro de uma faceta, um máximo de 30 intervalos podem ser retornados. Se mais de 30 compartimentos precisarem ser retornados, [criar um tíquete de suporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) assim, o Adobe pode analisar o impacto no desempenho e determinar se é viável aumentar esse limite no seu ambiente.
- Os aspectos dinâmicos podem causar problemas de desempenho em índices grandes e índices com alta ordinalidade. Se você tiver criado facetas dinâmicas e notar qualquer deterioração de desempenho ou carregamento de página sem erros de tempo limite, tente alterar suas facetas para fixado para determinar se isso resolve seu problema de desempenho.
- Status do estoque (`quantity_and_stock_status`) não é compatível como uma faceta. Você pode usar `inStock: 'true'` para filtrar produtos de falta de estoque. Esse recurso já vem com suporte pronto para uso no `LiveSearchAdapter` módulo quando &quot;Exibir produtos esgotados&quot; estiver definido como &quot;Verdadeiro&quot; na variável [!DNL Commerce] Admin.

## Query

- [!DNL Live Search] O não tem acesso à taxonomia completa da árvore de categoria, o que torna alguns cenários de pesquisa de navegação em camadas fora de seu alcance.
- [!DNL Live Search] usa um único [endpoint do GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/) para consultas que oferecem suporte a recursos como facetas dinâmicas e pesquisa conforme o tipo. Embora semelhante à [API do GraphQL](https://developer.adobe.com/commerce/webapi/graphql/)Existem algumas diferenças e alguns campos podem não ser totalmente compatíveis.
- O número máximo de resultados que podem ser retornados em uma consulta de pesquisa é 10.000.

## Regras

- O número máximo de merchandising de pesquisa [regras](rules.md) por exibição de loja é 50.
- O merchandising por categoria pode ter uma regra por categoria.
- O número máximo de condições por regra é 10.
- O número máximo de eventos por regra é 25.

## Sinônimos

- [!DNL Live Search] pode gerenciar até 200 [sinônimos](synonyms.md) por exibição da loja.
- Sinônimos de várias palavras não são suportados.

## Merchandising de categoria

- Uma regra por categoria pode ser criada para cada exibição de loja. Cada regra pode ter:
   - Até dez condições
   - Até 25 eventos

## Permissões B2B e de categoria

- Os produtos não serão exibidos se não forem adicionados a um catálogo compartilhado padrão.
- Para restringir grupos de clientes usando permissões de Catálogo:
   - Os produtos devem ser atribuídos à categoria Raiz.
   - O grupo de clientes &quot;Não conectado&quot; deve receber permissões de navegação &quot;Permitir&quot;.
   - Para restringir produtos ao grupo de clientes &quot;Não conectado&quot;, vá para cada categoria e defina as permissões para cada grupo de clientes.
- No momento, não há suporte para B2B com Live Search para PWA Studio.
