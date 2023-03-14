---
title: "Gerenciar facetas"
description: "Saiba como gerenciar arquivos existentes [!DNL Live Search] aspectos."
exl-id: 1d51a36a-20d6-46b6-b379-11e46c8824a0
source-git-commit: 9bacdb5fd232a3603bcb7abe2e93da9ead794d38
workflow-type: tm+mt
source-wordcount: '461'
ht-degree: 0%

---

# Gerenciar facetas

Siga estas instruções para atualizar as propriedades dos aspectos existentes ou alterar sua apresentação na loja.

## Configurar agrupamentos de facetas de preço

Consulte [Configurações](settings.md) para configurar intervalos e agrupamentos de facetas de preços.

## Editar faceta

1. Localize a faceta que deseja editar.
1. Se houver muitas facetas na lista, defina *Filtrar por* a um dos seguintes:

   * Fixado
   * Dinâmico

   Para saber mais, acesse [Tipos de facetas](facets-type.md).

   ![Filtrar facetas](assets/facets-filter-by-cropped.png)

1. Para editar as propriedades da faceta, clique em **Mais** (...) opções.
1. Clique em **Editar**

   ![Editar opções](assets/facet-edit-menu.png)

1. Para editar o rótulo da faceta, siga um destes procedimentos:

   * Para um [!DNL Commerce] vitrine, edite o [rótulo do atributo](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html).
   * Para uma implementação headless, clique no valor na primeira coluna e edite o texto conforme necessário.

   ![Editar rótulo](assets/facet-edit-label.png)

1. (Somente headless) Para alterar o método usado para classificar valores de facetas, clique no valor na *Tipo de classificação* e escolha uma das seguintes opções:

   * Em ordem alfabética
   * Contagem

   ![Editar contagem](assets/facets-edit-count.png)

1. No **Valor máximo** defina o número máximo (de 0 a 10) de valores de filtro de facetas a serem exibidos na vitrine eletrônica.
1. Quando terminar, clique em **Salvar**.
Suas alterações não aparecerão na loja até que sejam publicadas.

## Fixar/desfixar faceta

O pino muda de cor quando clicado e é usado para mover a faceta para a *Facetas fixadas* ou o *Aspectos dinâmicos* seção.

1. Para fixar uma faceta na parte superior do *Filtros* , localize a faceta na *Aspectos dinâmicos* e clique no pino cinza (![Fixar seletor](assets/btn-pin-gray.png)).
O pino fica azul e a faceta se move para o *Facetas fixadas* seção.
1. Para desafixar uma faceta, localize a faceta na *Facetas fixadas* e clique no pino azul (![Fixar seletor](assets/btn-pin-blue.png)).
O pino fica cinza e a faceta se move para a *Aspectos dinâmicos* seção.

   ![Aspectos fixados e dinâmicos](assets/facets-pinned-unpinned.png)

## Mover faceta fixada

>[!NOTE]
>
>A ordenação de facetas fixadas só é suportada em implementações headless. Se facetas ordenadas forem necessárias, use o [!DNL Live Search] Widget PLP.

A ordem das facetas fixadas pode ser alterada movendo a linha para uma posição diferente. As facetas fixadas têm um *Mover* ícone (![Mover seletor](assets/btn-move.png)) no início da linha. Diferentemente das facetas fixadas, as facetas dinâmicas não podem ser movidas.

1. Encontre a faceta no *Facetas fixadas* seção da lista.
1. Use o **Mover** (![Mover seletor](assets/btn-move.png)) para arrastar a linha para uma nova posição na *Facetas fixadas* seção.
Depois que as alterações forem publicadas, as facetas reordenadas aparecerão na loja *Filtros* lista.

## Excluir faceta

1. Localize a faceta na lista e clique em **Mais** (...) opções.
1. Clique em **Excluir**.
1. Quando for solicitada a confirmação, clique em **Excluir faceta**.
A faceta é removida da loja após as alterações serem publicadas.

## Publicar alterações

1. Para atualizar a loja com suas alterações, clique em **Publicar alterações**.
1. Aguarde cerca de 15 minutos para que as atualizações apareçam em sua loja.
