---
title: Desenvolvimento de administradores de Recommendations de produtos
description: Uma visão geral da arquitetura do Recommendations de produtos e dos recursos de desenvolvimento.
exl-id: caef5e0c-dd69-4846-8f85-b1c5e1c6a28f
source-git-commit: a433d970e83792a9f53b2a09afd84c335d980024
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# Desenvolvimento de administradores de Recommendations de produtos

O Recommendations de produtos é uma poderosa ferramenta de marketing que pode ser usada para aumentar as conversões, aumentar a receita e estimular o engajamento do comprador. O Recommendations do produto é exibido na loja na forma de unidades, como &quot;Clientes que viram este produto também viram&quot;, &quot;Clientes que compraram este produto também compraram&quot;, &quot;Recomendado para você&quot; e assim por diante. O Adobe Commerce Product Recommendations é desenvolvido pela [Adobe Sensei](https://www.adobe.com/sensei.html), que usa inteligência artificial e algoritmos de aprendizado de máquina para executar uma análise profunda de dados agregados de compradores. Esses dados, quando combinados com seu catálogo do Commerce, resultam em experiências altamente envolventes, relevantes e personalizadas para o comprador.

>[!NOTE]
>
>Se a sua loja for implementada usando o PWA Studio, consulte a [documentação do PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Se você usa uma tecnologia de front-end personalizada, como o React ou o Vue JS, consulte o guia do usuário para saber como integrar o Product Recommendations em um ambiente [headless](headless.md). As instâncias headless devem implementar eventos para potencializar o espaço de trabalho de recomendação do produto.

## Visão geral da arquitetura

Em um alto nível, o Commerce Product Recommendations é implantado como SaaS. O lado do Commerce inclui a loja, que contém o coletor de eventos e o modelo de layout de recomendações, e o back-end, que inclui os módulos Data Services, SaaS Export e a interface do usuário do administrador. Os serviços de inteligência da Adobe Sensei são aproveitados no lado do SaaS.

![Diagrama de arquitetura de recomendações de produto](assets/arch-diag-sensei.svg)

Depois que os módulos de recomendação forem instalados e configurados, sua loja começará a coletar dados comportamentais. O Adobe Sensei processa esses dados comportamentais junto com seus dados de catálogo e calcula associações de produtos que são aproveitadas pelo serviço de recomendações. Neste ponto, o comerciante pode criar, gerenciar e implantar unidades de recomendação de produto em sua vitrine diretamente da interface do usuário do administrador.

## Tipos de dados

O Recommendations do produto exige os seguintes dados:

- **Comportamento** - Dados do envolvimento de um comprador no seu site, como exibições de produtos, itens adicionados ao carrinho e compras. A Commerce e a Adobe Sensei não coletam informações de identificação pessoal.

- **Catálogo** - Metadados do produto, como nome, preço, disponibilidade etc.

Quando você instala o módulo `magento/product-recommendations`, o Adobe Sensei agrega os dados comportamentais e de catálogo, criando Recommendations de Produto para cada tipo de recomendação. O serviço Recommendations do produto implanta essas recomendações na loja.

>[!NOTE]
>
>Para produtos configuráveis, o Recommendations do produto usa a imagem do produto principal na unidade de recomendação. Se o produto configurável não tiver uma imagem especificada, a unidade de recomendação ficará vazia para esse produto específico.

## Próximas etapas

Leia os seguintes tópicos para começar a usar o Recommendations de produto:

- [Como implementar o Recommendations do produto](implementation-workflow.md)

- [Instalar e configurar o Recommendations do produto](install-configure.md)

- [Criar Recommendations de produto](create.md)
