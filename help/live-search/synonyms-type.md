---
title: '"Tipos de sinônimos"'
description: '"Um e dois sentidos [!DNL Live Search] os sinônimos expandem a definição de palavras-chave."'
exl-id: 708d7b0d-7361-44f4-ae9e-b92f574ac975
source-git-commit: cd1b40ffb350a87ea1317be82789f702922881b9
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Tipos de sinônimos

Sinônimos de mão única e bidirecional expandem a definição de palavras-chave. Alguns são intercambiáveis com a palavra-chave, enquanto outros representam um subconjunto da palavra-chave.

## Dois sentidos

Sinônimos bidirecionais têm o mesmo significado e retornam os mesmos resultados de pesquisa. No exemplo a seguir, a primeira palavra mostrada em negrito é a palavra-chave usada no catálogo, seguida por palavras que têm o mesmo significado da palavra-chave original. Você pode criar um par simples de sinônimos bidirecionais ou uma cadeia de vários sinônimos bidirecionais para a mesma palavra-chave.

**casaco** ![Seletor bidirecional](assets/btn-two-way.png) casaco
**calça** ![Seletor bidirecional](assets/btn-two-way.png) slides ![Seletor bidirecional](assets/btn-two-way.png) calça

## Unidirecional

Um sinônimo unidirecional é um subconjunto de uma palavra-chave, mas com um significado mais específico. Por exemplo, capris e shorts são calças, mas nem todas as calças são capris ou shorts. A busca por calças inclui capris e shorts. No entanto, a busca por shorts não retorna capris.

**camisola** ![Seletor unidirecional](assets/btn-one-way.png) capuz
**calça** ![Seletor unidirecional](assets/btn-one-way.png) capris ![Seletor unidirecional múltiplo](assets/btn-multiple-one-way.png) calcinha ![Seletor unidirecional múltiplo](assets/btn-multiple-one-way.png) empurradores de pedalar

## Práticas recomendadas

Lembre-se das seguintes práticas recomendadas para aproveitar ao máximo os sinônimos do Live Search.

### Evite &quot;palavras inativas&quot;

O Live Search filtra &quot;palavras inúteis&quot; comuns em inglês de sinônimos, como:

a, an, e, são, como, ser, mas, por exemplo, se, in, for, é, não, não, de, on, ou, tal, os, seus, então, lá, esses, eles, isto, para, era, vontade, com

Palavras de interrupção não fazem os sinônimos mais significativos, mas aumentam a quantidade de dados que devem ser processados.

### Usar palavras simples

Se um termo de sinônimo contiver várias palavras, o espaço em branco entre as palavras fará com que sejam tratadas como sinônimos separados. Por exemplo, se você definir &quot;peça de tempo&quot; como sinônimo de &quot;relógio&quot;, as palavras &quot;hora&quot; e &quot;peça&quot; serão tratadas como sinônimos separados.

### Uso de singular e plural

Não é necessário definir as formas singular e plural de uma palavra como sinônimo. Se você tiver uma mistura de termos de singular e plural em seu catálogo, o Search encontra o conjunto correto de produtos. Por exemplo, se você usar a palavra &quot;pant&quot; no nome do produto e um comprador pesquisar por &quot;calça&quot;, o conjunto correto de produtos será retornado e a palavra singular &quot;pant&quot; será oferecida como sugestão. O termo singular &quot;despensa&quot; é frequentemente utilizado na indústria da moda e, por vezes, no comércio a retalho, embora a forma plural &quot;calça&quot; seja mais utilizada em algumas áreas. (Tecnicamente, a palavra &quot;pant&quot; refere-se à parte de um vestuário que cobre uma perna, razão pela qual é necessário um &quot;par de calças&quot; para cobrir ambas as pernas.)

### Consistência

Seja consistente com a maneira como a terminologia é usada no catálogo. Lembre-se de que pode haver diferenças regionais no uso e, às vezes, diferenças dentro de um setor.

### Mapeamento de palavra-chave

Essa técnica usa atributos de produto pesquisáveis, em vez de sinônimos, para criar associações baseadas em palavras-chave entre produtos. Como resultado, um produto mapeado pode aparecer nos resultados de pesquisa de outro produto. Para saber mais, consulte [Resultados da pesquisa](https://docs.magento.com/user-guide/catalog/search-results.html).
