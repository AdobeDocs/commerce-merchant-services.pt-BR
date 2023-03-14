---
title: "Tipos de sinônimos"
description: "Unidirecional e bidirecional [!DNL Live Search] sinônimos expandem a definição de palavras-chave."
exl-id: 708d7b0d-7361-44f4-ae9e-b92f574ac975
source-git-commit: 9bacdb5fd232a3603bcb7abe2e93da9ead794d38
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%

---

# Tipos de sinônimos

Sinônimos unidirecionais e bidirecionais expandem a definição de palavras-chave. Alguns são intercambiáveis com a palavra-chave, enquanto outros representam um subconjunto da palavra-chave.

## Bidirecional

Sinônimos bidirecionais têm o mesmo significado e retornam os mesmos resultados de pesquisa. No exemplo a seguir, a primeira palavra mostrada em negrito é a palavra-chave usada no catálogo, seguida por palavras que têm o mesmo significado que a palavra-chave original. Você pode criar um par simples de sinônimos bidirecionais ou uma cadeia de vários sinônimos bidirecionais para a mesma palavra-chave.

**jaqueta** ![Seletor bidirecional](assets/btn-two-way.png) casaco
**calças** ![Seletor bidirecional](assets/btn-two-way.png) slacks ![Seletor bidirecional](assets/btn-two-way.png) calças

## Unidirecional

Um sinônimo unidirecional é um subconjunto de uma palavra-chave, mas com um significado mais específico. Por exemplo, capris e shorts são calças, mas nem todas as calças são capris ou shorts. Uma busca por calças inclui capris e shorts. No entanto, a busca por shorts não retorna capris.

**moletom** ![Seletor unidirecional](assets/btn-one-way.png) moletom
**calças** ![Seletor unidirecional](assets/btn-one-way.png) capris ![Seletor unidirecional múltiplo](assets/btn-multiple-one-way.png) calças de comprimento da panturrilha ![Seletor unidirecional múltiplo](assets/btn-multiple-one-way.png) empurradores de pedal

## Práticas recomendadas

Lembre-se das seguintes práticas recomendadas para aproveitar ao máximo o [!DNL Live Search] sinônimos.

### Evitar &quot;palavras de interrupção&quot;

[!DNL Live Search] filtra &quot;palavras de interrupção&quot; comuns em inglês de sinônimos, como:

a, an, and, são, como, at, be, mas, por, for, in, into, is, it, no, not, of, on, or, tal, que, o, seu, então, há, esses, eles, este, para, foi, será, com

As palavras de interrupção não tornam os sinônimos mais significativos, mas aumentam a quantidade de dados que devem ser processados.

### Usar palavras isoladas

Se um sinônimo contiver várias palavras, o espaço em branco entre as palavras faz com que elas sejam tratadas como sinônimos separados. Por exemplo, se você definir &quot;peça de tempo&quot; como um sinônimo para &quot;relógio&quot;, as palavras &quot;hora&quot; e &quot;peça&quot; serão tratadas como sinônimos separados.

### Uso do singular e do plural

Não é necessário definir as formas singular e plural de uma palavra como sinônimo. Se você tiver uma mistura de termos no singular e no plural no catálogo, a Pesquisa encontrará o conjunto correto de produtos. Por exemplo, se você usar a palavra &quot;pant&quot; no nome do produto e um comprador procurar &quot;pants&quot;, o conjunto correto de produtos será retornado e a palavra singular &quot;pant&quot; será oferecida como uma sugestão. O termo singular &quot;pant&quot; é frequentemente usado na indústria da moda e, às vezes, no varejo, embora a forma plural &quot;pants&quot; seja mais comumente usada em algumas áreas. (A palavra &quot;calça&quot; tecnicamente se refere à parte de uma peça de vestuário que cobre uma perna, por isso você precisa de um &quot;par de calças&quot; para cobrir ambas as pernas.)

### Consistência

Seja consistente com a forma como a terminologia é usada em seu catálogo. Lembre-se de que pode haver diferenças regionais no uso e, às vezes, diferenças em um setor.

### Mapeamento de palavra-chave

Essa técnica usa atributos de produto pesquisáveis, em vez de sinônimos, para criar associações baseadas em palavras-chave entre produtos. Como resultado, um produto mapeado pode aparecer nos resultados de pesquisa de outro produto. Para saber mais, consulte [Resultados da pesquisa](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html).
