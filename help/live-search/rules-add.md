---
title: "Adicionar regras"
description: "Saiba como criar [!DNL Live Search] regras."
exl-id: c6b92ef5-3b08-47f9-8412-955a9c95a9ee
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 0%

---

# Adicionar regras

Para criar uma regra, a primeira etapa é usar o editor de regras para definir as condições no texto de consulta do comprador que acionam os eventos associados. Em seguida, complete os detalhes da regra, teste os resultados e publique a regra.

## Etapa 1: Adicionar uma regra

1. Em Admin, acesse **Marketing** > SEO &amp; Pesquisar > **Live Search**.
1. Defina as **Escopo** para identificar [exibição de loja](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html#scope-settings) em que a regra se aplica.
1. Clique no botão **Regras** guia .
1. Clique em **Adicionar regra** para iniciar o editor de regras.

   ![Espaço de trabalho Regras](assets/rules-workspace-add-rule.png)

## Etapa 2: Descreva as condições

As condições são os requisitos para acionar um evento. Uma regra pode ter até dez condições e 25 eventos.

![Regra - Criar sua regra](assets/rules-add-workspace.png)

### Condição única

1. Em *Criar sua regra*, selecione o **Condição** para ser atendido e siga as instruções para concluir a instrução.

   * Consulta de pesquisa contém - Insira a cadeia de caracteres de texto que deve estar na consulta do comprador. A configuração Correspondência determina o grau em que a consulta do comprador corresponde ao catálogo. Opções:<br /> Qualquer - Qualquer parte do texto de consulta do comprador pode corresponder à condição.<br />All - Toda a consulta do comprador deve corresponder à condição.
   * A consulta de pesquisa é - digite uma string de texto que corresponda exatamente à consulta do comprador. Por exemplo: &quot;calças de yoga&quot;. Regras com `Search query is` e Corresponder `All` pode ter apenas uma condição.
   * A consulta de pesquisa começa com - Insira um caractere ou uma string de texto que deve estar no início da consulta do comprador.
   * A consulta de pesquisa termina com - Insira um caractere ou uma string de texto que deve estar no final da consulta do comprador.

   Os resultados aparecem imediatamente no *Testar sua regra* e são numerados por prioridade. Você pode usar o *Resultados por linha* controle deslizante no canto superior direito para alterar o número de produtos em cada linha.

   ![Regra - simples](assets/rule-simple-test.png)

1. Para testar outras consultas, altere o texto da consulta no *Testar sua regra* caixa de pesquisa e pressione **Retorno**.
Inicialmente, o painel de teste renderiza a consulta na caixa de pesquisa Condições . Mas agora está renderizando o query da caixa de query de teste. O painel de teste renderiza apenas uma consulta por vez.

   ![Regra - atualizar teste](assets/rule-update-test.png)

1. Se desejar o resultado, atualize o texto na *Condições* caixa de pesquisa. Em seguida, clique em qualquer lugar na página para atualizar os resultados no painel de teste.
1. Para criar uma regra simples com uma condição, vá para a Etapa 3: [Adicionar eventos](#events).

### Várias condições

1. Para criar uma regra com várias condições, clique em **Adicionar condição**.
Uma regra pode ter até dez condições. O operador lógico que une duas condições se baseia no *Corresponder* configuração. Por padrão, *Corresponder* é `All` e o operador lógico é `AND`.

   ![Regras - A consulta de pesquisa contém](assets/rules-search-query-contains-and.png)

1. Selecione a segunda condição e insira o texto de consulta necessário.

   ![Condições da regra](assets/rules-add-condition.png)

1. Para alterar a lógica da regra, altere a variável **Corresponder** para determinar o grau de correspondência entre os critérios de pesquisa do comprador e a condição da consulta. Definir **Corresponder** para um dos seguintes:

   * Qualquer - (Padrão) Todos os operadores lógicos na regra são definidos como `OR` e os resultados serão exibidos no painel de teste.
   * Todos - Todos os operadores lógicos na regra são definidos como `AND` e os resultados serão exibidos no painel de teste.

   O *Corresponder* determina o operador lógico usado para unir várias condições. Alteração do *Corresponder* definir altera todos os operadores lógicos na regra. Não é possível combinar `AND` e `OR` na mesma regra.

   Neste exemplo, em vez de pesquisar por &quot;calças de yoga&quot;, há duas consultas separadas que pesquisam por &quot;yoga&quot; ou &quot;calças&quot;. Essa regra é menos específica e é acionada com mais frequência na loja do que na outra.

   ![Regras - Corresponder](assets/rules-match.png)

1. Para adicionar outra condição, clique em **Adicionar condição** e repita o processo.

## Etapa 3: Adicionar eventos

são ações que alteram os resultados da pesquisa quando as condições são cumpridas. Uma única regra pode ter até 25 eventos.

1. Em *Eventos*, escolha o **Evento** para ocorrer quando as condições associadas forem cumpridas.

   Por exemplo, escolha `Pin a product`. Em seguida, insira o nome do produto que deseja prender. Se precisar de ajuda, poderá encontrar o nome no painel de teste.
Em seguida, insira o *Position* onde deve aparecer o produto fixado. O produto é movido para a nova posição no painel de ensaio e marcado com uma *Fixo* selo de visualização.

   ![Regras - Corresponder](assets/rule-event-pin-product.png)

1. Para vários eventos, escolha quaisquer outros eventos que você deseja acionar quando as condições forem atendidas.

   * Aumentar - Selecione Aumentar. Em seguida, insira o nome do produto ou SKU que você deseja mover para cima nos resultados da pesquisa. No painel de teste, cada produto impulsionado tem um *Reforçado* selo de visualização.
   * Bury - Move um SKU para baixo nos resultados da pesquisa. Cada SKU está marcada com uma *Enterrado* selo de visualização no painel de teste.
   * Fixar um produto - Insira o nome do produto ou SKU. Em seguida, selecione a Posição nos resultados da pesquisa, onde o produto deve aparecer. O produto está marcado com um *Fixo* selo de visualização no painel de teste.
   * Ocultar um produto - exclui um SKU dos resultados da pesquisa.

## Etapa 4: Preencha os detalhes

As informações inseridas aqui aparecem no [Detalhes da regra](rules-workspace.md) painel.

1. Em *Detalhes*, insira um **Nome** para a regra. Todos os nomes de regras devem ser exclusivos.
1. Insira um resumo **Descrição** da regra.
1. Insira o **Data inicial** e **Data final** para a regra estar ativa ou escolher as datas do calendário.

   Para selecionar um intervalo de datas, clique na primeira data e arraste para selecionar o intervalo.

   ![Regra - Concluída](assets/rule-add-details.png)

## Etapa 5: Testar a regra

1. Examine os resultados da regra no painel de teste.
1. Se a regra tiver várias consultas, teste cada uma que possa ser afetada pela regra.

## Etapa 6: Salvar e publicar

1. Ao concluir, clique em **Salvar e publicar**.

   A regra é adicionada à lista no espaço de trabalho de regras.

1. Embora as regras ativas entrem em vigor imediatamente, talvez seja necessário aguardar até 15 minutos para que os resultados da consulta em cache sejam atualizados na loja.

## Descrições dos campos

### Condições (if)

| Condição | Descrição |
|--- |--- |
| A consulta de pesquisa contém | Um caractere ou uma string de texto incluída no query do comprador. A consulta do comprador precisa corresponder apenas a um único caractere para atender a essa condição. |
| A consulta de pesquisa é | Um caractere ou uma string de texto que corresponde exatamente à consulta do comprador. Consultas complexas com várias condições não podem ser compostas quando essa condição é usada. |
| A consulta de pesquisa começa com | A consulta do comprador começa com esse caractere ou string de texto. |
| A consulta de pesquisa termina com | A consulta do comprador termina com esse caractere ou string de texto. |

### Operadores lógicos

| Operador | Descrição |
|--- |--- |
| OU | (Padrão) O operador lógico `OR` compara duas condições e atende aos requisitos para acionar um evento se pelo menos uma condição for verdadeira. |
| E | O operador lógico `AND` compara duas condições e atende aos requisitos para acionar um evento se ambas as condições forem verdadeiras. |

### Operadores de correspondência

| Operador | Descrição |
|--- |--- |
| Qualquer | Altera todos os operadores lógicos na regra para `OR` e retorna o conjunto de produtos correspondentes. |
| Todos | Altera todos os operadores lógicos na regra para `AND` e retorna o conjunto de produtos correspondentes. |

### Eventos

| Evento | Descrição |
|--- |--- |
| Aumento | Move um SKU ou intervalo de SKUs para cima nos resultados da pesquisa. Cada um é marcado com um selo de visualização &quot;potencializado&quot; nos resultados da pesquisa de teste. |
| Bury | Move um SKU ou intervalo de SKUs para baixo nos resultados da pesquisa. Cada uma é marcada com um selo de visualização &quot;enterrado&quot; nos resultados da pesquisa de teste. |
| Fixar um produto | Anexa um único SKU a uma posição específica nos resultados da pesquisa. O produto é marcado com um selo de visualização &quot;fixado&quot; nos resultados da pesquisa de teste. |
| Ocultar um produto | Exclui um SKU, ou um intervalo de SKUs, dos resultados da pesquisa. |

### Detalhes

| Campo | Descrição |
|--- |--- |
| Nome | O nome da regra. Os nomes de regras devem ser exclusivos. |
| Data de início | A data de início da regra, se agendada. |
| Data final | A data final da regra, se agendada. |
| Descrição | Uma breve descrição da regra. |
