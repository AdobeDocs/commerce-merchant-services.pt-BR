---
title: "Tipos de facetas"
description: "[!DNL Live Search] As facetas são dinâmicas e aparecem na lista Filtros quando relevante."
exl-id: 49fb7609-64b3-4ae8-928d-54c99032d919
source-git-commit: f96f94a16e1926b7dd2f1ee94f124ac0c823a9e0
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# Tipos de facetas

[!DNL Live Search] O usa uma variedade de tipos de facetas e eles aparecem no *Filtros* listar somente quando relevante. A lista de aspectos disponíveis muda de acordo com os produtos retornados. As seguintes características afetam sua apresentação e comportamento:

* Facetas fixadas - As facetas mais usadas podem ser fixadas no topo da lista. As facetas restantes são listadas em *Tipo de classificação* pedido depois das facetas fixadas.
* Aspectos dinâmicos - Atributos de produto que [Adobe Sensei](https://www.adobe.com/sensei.html) O considera mais relevante para um conjunto de produtos e uma consulta. O cálculo leva em conta os metadados do atributo de todo o catálogo e determina, no momento da consulta, os aspectos mais relevantes da consulta.
* Aspectos populares - Atributos de produto que estão presentes com mais frequência nos resultados da pesquisa.
* Facetas de preço - Devolver produtos por faixa de preço. Você pode especificar o número de seleções e o intervalo de preços na [*Configurações*](settings.md) espaço de trabalho.

No momento da consulta, [!DNL Live Search] O gera os resultados da pesquisa em grupos de facetas dinâmicas e populares.

![Facetas - Preço](assets/storefront-search-results-run-price.png)

## Opções de frente de loja e headless

Facetas renderizadas para o [!DNL Commerce] a loja é processada pelo adaptador de pesquisa, que encaminha solicitações e renderiza os resultados na loja. Todos [!DNL Commerce] as facetas de loja são classificadas alfabeticamente com opções de seleção única, independentemente do tipo de entrada atribuído ao atributo correspondente. Os aspectos disponíveis na loja são renderizados de acordo com o tema atual e refletem as personalizações feitas na apresentação da navegação em camadas.

Em contrapartida, [headless](https://developer.adobe.com/commerce/php/architecture/technical-vision/web-api/) As implementações do são processadas pela API e oferecem suporte a opções adicionais. As facetas headless podem ser classificadas alfabeticamente ou por contagem, e podem ter opções de seleção única ou múltipla.

### Rótulos de facetas

Para [!DNL Commerce] vitrines, o rótulo das facetas é determinado pela variável [*Propriedades do atributo*](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html). Para lojas com várias exibições, rótulos adicionais podem ser definidos em *Gerenciar rótulos*. Para implementações headless, os rótulos são editados do [espaço de trabalho faceting](faceting-workspace.md).

### Tipo de classificação

Todas as facetas renderizadas para a loja são classificadas alfabeticamente. Para implementações headless, os aspectos podem ser classificados em ordem alfabética ou por contagem.

| Tipo de classificação | Descrição |
|--- |--- |
| Em ordem alfabética | Na vitrine *Filtros* , as facetas são classificadas alfabeticamente. |
| Contagem | (Somente headless) Para implementações headless, as facetas também podem ser classificadas pelo número de valores encontrados por faceta no conjunto atual de produtos retornados. |
