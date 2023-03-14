---
title: "Adicionar facetas"
description: "Saiba como adicionar atributos de produto filtráveis como [!DNL Live Search] aspectos."
exl-id: 0df6c21b-55b3-41ce-94f4-f70b70ffb84e
source-git-commit: 10edbb6127405d45c06d4c8ffc89d92a6ca061c3
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 0%

---

# Adicionar facetas

Qualquer atributo de produto filtrável pode ser usado como uma faceta. A variável *Adicionar facetas* O painel lista as facetas atuais e facilita a atribuição de atributos de produto adicionais como facetas. Durante esse processo de três etapas, um atributo é escolhido para ser usado como uma faceta, as propriedades são editadas, se necessário, e as alterações são publicadas na loja.

![Espaço de trabalho facetado](assets/facets-add.png)

## Etapa 1: adicionar uma faceta

1. No Administrador, acesse **Marketing** > SEO E Pesquisa > **[!DNL Live Search]**.
1. No *Facetagem* clique em **Adicionar facetas**.
1. No *Adicionar facetas* , cada atributo disponível tem um ![Botão Adicionar](assets/btn-add.png). Conclua uma das opções a seguir:

   * No *Atributos de faceta* escolha o atributo de produto que deseja usar como faceta e clique em **Adicionar**.
   * Para localizar um atributo de produto específico, insira os primeiros caracteres do nome do atributo na *Pesquisar* caixa. Em seguida, clique em **Adicionar**.

      Para configurar intervalos e agrupamentos de facetas de preços, consulte [Configurações](settings.md). Para saber mais, acesse [Tipos de facetas](facets-type.md).
A faceta é adicionada à parte inferior do *Aspectos dinâmicos* e a *Publicar alterações* fica disponível.

1. Se a faceta que você deseja adicionar não puder ser encontrada, acesse **Lojas** > Atributos > **Produto** e verificar se o atributo tem a [propriedades obrigatórias](facets.md) para ser usado como faceta. Se necessário, atualize as seguintes propriedades da loja do atributo:

   * Usar na pesquisa - `Yes`
   * Usar na navegação em camadas dos resultados da pesquisa - `Yes`
   * Usar na navegação em camadas - `Filterable (with results)`

1. Quando solicitado, atualize o cache.

   A faceta fica disponível na loja na próxima vez que o catálogo for sincronizado com o [!DNL Live Search]. Se a faceta não estiver disponível após duas horas, consulte [Sincronizar dados do catálogo](install.md#synchronize-catalog-data).

## Etapa 2: Editar propriedades da faceta (Opcional)

1. Para editar as propriedades da faceta, clique em **Mais** (![Mais seletores](assets/btn-more.png)) na coluna à direita.
1. No menu, clique em **Editar**. Em seguida, ajuste as seguintes propriedades, conforme necessário.

   * Rótulo - ([Headless](facets-type.md) somente) Insira o rótulo da faceta que deseja usar.
   * Tipo de classificação - As facetas são classificadas alfabeticamente para todos [!DNL Commerce] vitrines. Para implementações headless, os aspectos podem ser classificados em ordem alfabética ou por contagem. Opções: alfabética, contagem (somente headless)
   * Valor máximo - Insira o número máximo de valores de facetas exibidos na loja. Entradas válidas: 0 - 30; Padrão: 8

1. Quando terminar, clique em **Salvar**.

   ![Espaço de trabalho facetado](assets/facet-edit.png)

1. Para fixar a faceta na parte superior do *Filtros* clique no pino cinza (![Fixar seletor](assets/btn-pin-gray.png)).
1. Para alterar a ordem da faceta fixada, clique no link **Mover** (![Mover seletor](assets/btn-move.png)) e arraste a linha para uma nova posição na *Facetas fixadas* seção.

## Etapa 3: publicar alterações

1. Quando a faceta estiver concluída, clique em **Publicar alterações**.
1. Aguarde até que a faceta apareça no armazenamento.
Se a faceta não estiver disponível após duas horas, consulte [Verificar exportação](install.md#synchronize-catalog-data) nas instruções de instalação.

## Descrições dos campos

| Campo | Descrição |
|--- |--- |
| Rótulo | ([Headless](facets-type.md) apenas) A [rótulo da faceta](facets-type.md) que está visível na loja pode ser editado para manter a consistência com sua marca. |
| Tipo de classificação | O método usado para [sort](facets-type.md) aspectos. Todos [!DNL Commerce] vitrines classificam os aspectos somente alfabeticamente. As implementações headless também podem classificar por `Count`. Opções:<br />Alfabético - Classifica os aspectos em ordem alfabética.<br />Contagem - (Somente headless) Classifica facetas com base no número de correspondências encontradas. |
| Valor máximo | O número máximo de valores que podem ser exibidos na loja para cada faceta. Os aspectos que representam um intervalo de valores são distribuídos uniformemente. Entradas válidas: 0 - 30; Padrão: 8 |

### Controles

| Controle | Descrição |
|--- |--- |
| ![Fixar seletor](assets/btn-pin-blue.png) | Fixa ou desfixa uma faceta na parte superior do *Filtros* lista. |
| ![Mais seletores](assets/btn-more.png) | Exibe um menu de mais ações que podem ser aplicadas à faceta selecionada. Opções: Editar, Excluir |
| ![Mover seletor](assets/btn-move.png) | Use o *Mover* ícone para arrastar uma faceta fixada para outro local na *Facetas fixadas* seção. |
