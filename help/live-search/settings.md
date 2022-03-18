---
title: Configurações do Live Search
description: Configure intervalos de facetas de preço para facetas do Live Search.
exl-id: a0b63116-4b8f-490c-a54e-e21f1b02b634
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Configurações

Use o *Configurações* para configurar os intervalos e intervalos do aspecto de preço disponíveis como filtros de pesquisa na loja. As configurações de aspecto de preço são estáticas em vez de dinâmicas e não se baseiam em resultados de pesquisa.
Você pode especificar o número de grupos de faixa de preço e como os valores de preço são distribuídos entre eles. Cada intervalo de preço se sobrepõe ao grupo anterior em um. Por exemplo, cinco grupos com um intervalo de vinte criam os seguintes intervalos de preço: 0-20, 20-40, 40-60, 60-80 e >80. Se não houver produtos suficientes no catálogo para preencher todos os intervalos definidos, a exibição dos grupos disponíveis será ajustada adequadamente. Por exemplo: 0-20, 60-80, >80.

![Configurações](assets/settings.png)

## Configurar agrupamentos de facetas de preço

1. Em Admin, acesse **Marketing** > *SEO &amp; Pesquisar* > **Live Search**.
1. No **Configurações** guia em *Lapidamento de preço*, faça o seguinte:
   * Insira o **Número de seleções** ou agrupamentos de preços disponíveis. É possível definir até 50 agrupamentos de preços.
   * Insira o **Valor do intervalo** ou intervalo de preço para cada grupo. O valor máximo é 10.000.
1. Clique em **Salvar**.
Leva cerca de quinze minutos para as configurações atualizadas estarem disponíveis na loja.

## Descrições dos campos

| Campo | Descrição |
|--- |--- |
| Número de seleções | Especifica o número de agrupamentos de intervalo de preço que podem ser usados como filtros de pesquisa na loja. Valor padrão: 8, Valor máximo: 50º |
| Valor do intervalo | Especifica o intervalo de preço para cada grupo. Por exemplo, cinco seleções com um valor de intervalo de vinte criam cinco agrupamentos de 0-20, 20-40, 40-60, 60-80 e > 80. Valor padrão: 5, Valor máximo: 10.000 |
