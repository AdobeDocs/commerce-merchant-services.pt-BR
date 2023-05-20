---
title: Dados comportamentais
description: Saiba mais sobre dados comportamentais e quando você pode começar a usá-los.
exl-id: d68a97b9-1497-4603-a72c-4aaaf6e048cb
source-git-commit: 840b091638aedd3f6ac097a010d035eff997ffe2
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# Dados comportamentais

Alguns tipos de recomendações usam dados comportamentais de seus compradores para treinar modelos de aprendizado de máquina para criar recomendações personalizadas. Outros tipos de recomendações usam apenas dados de catálogo e não usam dados comportamentais. Se quiser iniciar rapidamente, você poderá usar os seguintes tipos de recomendações somente de catálogo:

- `More like this`
- `Visual similarity`

Quando você pode começar a usar tipos de recomendação que usam dados comportamentais? Depende. Esse processo é conhecido como _Inicialização a frio_ problema.

A variável _Inicialização a frio_ O problema é uma medida de quanto tempo um modelo precisa para treinar antes de ser considerado de alta qualidade. Nas recomendações de produtos, significa aguardar que o Adobe Sensei treine seus modelos de aprendizado de máquina antes de implantar unidades de recomendação no site. Quanto mais dados esses modelos tiverem, mais precisas e úteis serão as recomendações. A coleta desses dados leva tempo e varia de acordo com o volume de tráfego. Como esses dados podem ser coletados somente em um site de produção, é do seu interesse implantar a coleta de dados lá o mais rápido possível. Você pode fazer isso ao [instalação e configuração](install-configure.md) o `magento/production-recommendations` módulo.

A tabela a seguir fornece algumas orientações gerais sobre o tempo necessário para coletar dados suficientes para cada tipo de recomendação:

| Tipo de recomendação | Tempo de treinamento | Notas |
|---|---|---|
| Baseado em popularidade (`Most viewed`, `Most purchased`, `Most added to cart`) | Varia | Depende do volume de eventos — as exibições são mais comuns e, portanto, aprende mais rápido; depois, adiciona ao carrinho e, em seguida, às compras |
| `Viewed this, viewed that` | Requer mais treinamento | O volume das visualizações de produto é decentemente alto |
| `Viewed this, bought that`, `Bought this, bought that` | Requer mais treinamento | Os eventos de compra são os eventos mais raros no site de comércio, especialmente em comparação às visualizações de produto |
| `Trending` | Requer três dias de dados para estabelecer uma linha de base de popularidade | As tendências são uma medida do impulso recente na popularidade de um produto em comparação com sua própria linha de base de popularidade. A pontuação de tendência de um produto é calculada usando um conjunto de primeiro plano (popularidade recente em 24 horas) e um conjunto de segundo plano (popularidade na linha de base em 72 horas). Se um item se tornou muito mais popular nas últimas 24 horas em comparação com sua popularidade na linha de base, ele receberá uma alta pontuação de tendência. Cada produto tem essa pontuação e os mais altos a qualquer momento compõem o conjunto dos principais produtos em tendência. |

Outras variáveis que podem afetar o tempo necessário para treinar:

- Maior volume de tráfego contribui para uma aprendizagem mais rápida
- Alguns tipos de recomendações são treinados mais rapidamente do que outros
- O Adobe Commerce recalcula dados comportamentais a cada quatro horas. O Recommendations se torna mais preciso quanto mais tempo eles forem usados no site.

Para ajudá-lo a visualizar o progresso do treinamento de cada tipo de recomendação, a variável [criar recomendação](create.md) exibe indicadores de prontidão.

Embora os dados sejam coletados na produção e os modelos de aprendizado de máquina sejam treinados, você pode implementar o [tarefas restantes](implementation-workflow.md) necessário para implantar recomendações na loja. Quando você terminar de testar e configurar as recomendações, os modelos de aprendizado de máquina terão coletado e calculado dados suficientes para criar recomendações relevantes, permitindo que você implante as recomendações na loja.

Se o tráfego for insuficiente (exibições, produtos comprados, tendências) para a maioria das SKUs, talvez não haja dados suficientes para concluir o processo de aprendizado. Isso pode fazer com que o indicador de prontidão no Admin pareça travado.
Os indicadores de prontidão devem fornecer aos comerciantes outro ponto de dados para escolher qual tipo de recomendações é melhor para sua loja. Os números são um guia e podem nunca chegar a 100%.

## Recomendações de backup {#backuprecs}

Se não houver dados de entrada suficientes para fornecer todos os itens de recomendação solicitados em uma unidade, a Adobe Commerce fornecerá recomendações de backup para preencher as unidades de recomendação. Por exemplo, se você implantar o `Recommended for you` tipo de recomendação para sua página inicial, um comprador pela primeira vez no site não gerou dados comportamentais suficientes para recomendar com precisão produtos personalizados. Nesse caso, o Adobe Commerce exibe itens com base no `Most viewed` tipo de recomendação para este comprador.

Os seguintes tipos de recomendações fazem fallback para `Most viewed` tipo de recomendação se não houver dados de entrada suficientes coletados:

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`
