---
title: Tipos de facetas
description: Os aspectos da Pesquisa ao vivo são dinâmicos e são exibidos na lista de Filtros , quando relevante.
exl-id: 49fb7609-64b3-4ae8-928d-54c99032d919
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Tipos de aspectos

Todos [!DNL Live Search] as facetas são dinâmicas e são exibidas na variável *Filtros* listar somente quando pertinente. A lista de aspectos disponíveis muda de acordo com os produtos retornados. As seguintes características afetam a sua apresentação e comportamento:

* Facetas fixadas - As facetas mais usadas podem ser fixadas ao topo da lista. As facetas restantes estão listadas em *Tipo de classificação* ordenar depois das facetas fixadas.
* Facetas inteligentes - Atributos do produto que [Adobe Sensei](https://www.adobe.com/sensei.html) O encontra o mais relevante para um conjunto de produtos e query. O cálculo leva em conta os metadados do atributo de todo o catálogo e determina, no momento da consulta, os aspectos mais relevantes para o query.
* Facetas populares - Atributos de produto que geralmente estão presentes nos resultados da pesquisa.
* Fatores de preço - Retorne produtos por faixa de preço. Você pode especificar o número de seleções e o intervalo de intervalo de preço no [*Configurações*](settings.md) guia .

No momento da consulta, [!DNL Live Search] O gera os resultados da pesquisa em grupos de facetas inteligentes e populares.

![Facetas - Preço](assets/storefront-search-results-run-price.png)

## Opções de vitrine e sem periféricos

Facetas renderizadas para a [!DNL Commerce] o storefront é processado pelo adaptador de pesquisa, que roteia as solicitações e renderiza os resultados na loja. Todos [!DNL Commerce] os aspectos de vitrine são classificados alfabeticamente com opções de seleção única, independentemente do tipo de entrada atribuído ao atributo correspondente. As facetas disponíveis na loja são renderizadas de acordo com o tema atual e refletem quaisquer personalizações feitas na apresentação de navegação em camadas.

Em contrapartida, [impiedoso](https://devdocs.magento.com/guides/v2.4/architecture/archi_perspectives/webapi-vision.html) as implementações são processadas pela API e oferecem suporte a opções adicionais. As facetas sem cabeçalho podem ser classificadas alfabeticamente ou por contagem e podem ter opções de seleção única ou múltipla.

### Selecionar tipo

Para implementações sem cabeçalho, as facetas podem ser definidas como `single select` ou `multi-select` com operadores lógicos que determinam o conjunto de produtos retornado. Por exemplo, `green AND blue` ou `green OR blue`.

![Aspectos - Selecionar tipo](assets/facets-select-type.png)

| Selecionar tipo | Descrição |
|--- |--- |
| Seleção única | Uma faceta de seleção única oferece várias opções, mas permite que o comprador escolha apenas um valor. |
| Seleção múltipla (ou) | (Somente cabeçalho) Os compradores podem escolher mais de uma opção e os produtos retornados podem corresponder a qualquer valor selecionado. Exemplo: `green OR blue` |
| Seleção múltipla (e) | (Somente cabeçalho) Os compradores podem escolher mais de uma opção, e os produtos retornados devem corresponder a todos os valores selecionados. Exemplo: `green AND blue` |

### Rótulos de facetas

Para [!DNL Commerce] vitrines, o rótulo da faceta é determinado pelo [*Propriedades do atributo*](https://docs.magento.com/user-guide/stores/attribute-product-create.html). Para lojas com várias exibições, rótulos adicionais podem ser definidos em *Gerenciar rótulos*. Para implementações sem cabeçalho, os rótulos são editados da variável [facting workspace](faceting-workspace.md).

### Tipo de classificação

Todas as facetas renderizadas para a loja são classificadas alfabeticamente. Para implementações sem cabeçalho, as facetas podem ser classificadas alfabeticamente ou por contagem.

| Tipo de classificação | Descrição |
|--- |--- |
| Alfabético | Na loja *Filtros* lista, as facetas são classificadas alfabeticamente. |
| Contagem | (Somente headless) Para implementações sem periféricos, as facetas também podem ser classificadas pelo número de valores encontrados por faceta no conjunto atual de produtos retornados. |
