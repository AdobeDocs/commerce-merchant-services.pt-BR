---
title: "[!DNL Live Search] Configurações"
description: "Configurar intervalos e faixas de preços facetados para [!DNL Live Search] aspectos."
exl-id: a0b63116-4b8f-490c-a54e-e21f1b02b634
source-git-commit: 9bacdb5fd232a3603bcb7abe2e93da9ead794d38
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Configurações

Use o *Configurações* guia para configurar os intervalos e os intervalos das facetas de preços que estão disponíveis como filtros de pesquisa na loja. As configurações de facetas de preço são estáticas em vez de dinâmicas e não se baseiam nos resultados da pesquisa.

Você pode especificar o número de grupos de faixas de preços e como os valores de preços são distribuídos entre eles. Cada faixa de preços sobrepõe o grupo anterior em um. Por exemplo, cinco grupos com um intervalo de vinte criam as seguintes faixas de preço: 0-20, 20-40, 40-60, 60-80 e >80. Se não houver produtos suficientes no catálogo para preencher todos os intervalos definidos, a exibição dos grupos disponíveis será ajustada de acordo. Por exemplo: 0-20, 60-80, >80.

![Configurações](assets/settings.png)

## Configurar agrupamentos de facetas de preço

1. No Administrador, acesse **Marketing** > *SEO e pesquisa* > **[!DNL Live Search]**.
1. No **Configurações** em *Faceting de preço*, faça o seguinte:
   * Insira o **Número de seleções** ou grupos de preços a serem disponibilizados. Até 50 agrupamentos de preços podem ser definidos.
   * Insira o **Valor do intervalo** ou faixa de preços para cada grupo. O valor máximo é 10.000.
1. Clique em **Salvar**.

   Leva aproximadamente 15 minutos para as configurações atualizadas estarem disponíveis na loja.

## Descrições dos campos

| Campo | Descrição |
|--- |--- |
| Número de seleções | Especifica o número de agrupamentos de intervalo de preços que podem ser usados como filtros de pesquisa na loja. Valor padrão: 8, Valor máximo: 50 |
| Valor do intervalo | Especifica o intervalo de preço para cada grupo. Por exemplo, cinco seleções com um valor de intervalo de vinte cria cinco agrupamentos de 0-20, 20-40, 40-60, 60-80 e >80. Valor padrão: 5, Valor máximo: 10.000 |
