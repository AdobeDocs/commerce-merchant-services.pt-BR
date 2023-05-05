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

Alguns tipos de recomendação usam dados comportamentais dos compradores para treinar modelos de aprendizado de máquina para criar recomendações personalizadas. Outros tipos de recomendação usam somente dados de catálogo e não usam dados comportamentais. Se quiser iniciar rapidamente, você pode usar os seguintes tipos de recomendação somente de catálogo:

- `More like this`
- `Visual similarity`

Então quando você pode começar a usar tipos de recomendação que usam dados comportamentais? Depende. Isso é conhecido como _Início frio_ problema.

O _Início frio_ O problema é uma medida do tempo que um modelo precisa para treinar antes que possa ser considerado de alta qualidade. Nas recomendações de produto, significa esperar que o Adobe Sensei treine seus modelos de aprendizado de máquina antes de implantar unidades de recomendação no site. Quanto mais dados esses modelos tiverem, mais precisas e úteis serão as recomendações. A coleta desses dados leva tempo e varia de acordo com o volume de tráfego. Como esses dados podem ser coletados somente em um site de produção, é de seu interesse implantar a coleta de dados lá o mais rápido possível. Você pode fazer isso ao [instalação e configuração](install-configure.md) o `magento/production-recommendations` módulo.

A tabela a seguir fornece algumas orientações gerais para a quantidade de tempo necessária para coletar dados suficientes para cada tipo de recomendação:

| Tipo de recomendação | Tempo de treinamento | Notas |
|---|---|---|
| Baseado em popularidade (`Most viewed`, `Most purchased`, `Most added to cart`) | Varia | Depende do volume de eventos - as visualizações são mais comuns e, portanto, aprendem mais rápido; em seguida, adiciona ao carrinho e, em seguida, compra |
| `Viewed this, viewed that` | Requer mais treinamento | As visualizações de produto são frequentemente altas em volume |
| `Viewed this, bought that`, `Bought this, bought that` | Requer o máximo de treinamento | Os eventos de compra são os eventos mais raros no site de comércio, especialmente em comparação às visualizações de produto |
| `Trending` | Requer três dias de dados para estabelecer uma linha de base de popularidade | A tendência é uma medida do dinamismo recente na popularidade de um produto em comparação com sua própria linha de base de popularidade. A pontuação de tendência de um produto é calculada usando um conjunto em primeiro plano (popularidade recente em 24 horas) e um conjunto em segundo plano (linha de base de popularidade em 72 horas). Se um item se tornou muito mais popular nas últimas 24 horas, em comparação com sua popularidade da linha de base, ele recebe uma pontuação de tendência alta. Cada produto tem essa pontuação e os mais altos a qualquer momento compõem o conjunto dos principais produtos de tendência. |

Outras variáveis que podem afetar o tempo necessário para treinar:

- O maior volume de tráfego contribui para um aprendizado mais rápido
- Alguns tipos de recomendação treinam mais rápido que outros
- O Adobe Commerce recomenda dados comportamentais a cada quatro horas. O Recommendations se torna mais preciso quanto mais tempo for usado em seu site.

Para ajudá-lo a visualizar o progresso de treinamento de cada tipo de recomendação, a variável [criar recomendação](create.md) exibe indicadores de prontidão.

Embora os dados sejam coletados na produção e os modelos de aprendizado por máquina sejam treinados, é possível implementar a variável [tarefas restantes](implementation-workflow.md) necessário para implantar recomendações na loja. Quando você terminar de testar e configurar as recomendações, os modelos de aprendizado de máquina coletarão e calcularão dados suficientes para criar recomendações relevantes, permitindo que você implante as recomendações na loja.

Se não houver tráfego suficiente (exibições, produtos comprados, tendências) para a maioria dos SKUs, talvez não haja dados suficientes para concluir o processo de aprendizado. Isso pode fazer com que o indicador de prontidão no Administrador pareça estar preso.
Os indicadores de prontidão são destinados a fornecer aos comerciantes outro ponto de dados na escolha do tipo de recomendações que é melhor para sua loja. Os números são um guia e podem nunca chegar a 100%.

## Recomendações de backup {#backuprecs}

Se não houver dados de entrada suficientes para fornecer todos os itens de recomendação solicitados em uma unidade, o Adobe Commerce fornece recomendações de backup para preencher unidades de recomendação. Por exemplo, se você implantar a variável `Recommended for you` tipo de recomendação para sua página inicial, um comprador pela primeira vez no site não gerou dados comportamentais suficientes para direcionar com precisão os produtos personalizados. Nesse caso, o Adobe Commerce exibe itens com base na variável `Most viewed` tipo de recomendação para este comprador.

Os seguintes tipos de recomendação são fallback para `Most viewed` tipo de recomendação se não houver dados de entrada suficientes coletados:

- `Recommended for you`
- `Viewed this, viewed that`
- `Viewed this, bought that`
- `Bought this, bought that`
- `Trending`
- `Conversion (view to purchase)`
- `Conversion (view to cart)`
