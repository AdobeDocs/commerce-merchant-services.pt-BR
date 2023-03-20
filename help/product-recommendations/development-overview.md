---
title: Desenvolvimento do administrador do Recommendations do produto
description: Uma visão geral da arquitetura do Recommendations do produto e dos recursos de desenvolvimento.
exl-id: caef5e0c-dd69-4846-8f85-b1c5e1c6a28f
source-git-commit: 78f226465b9d84707612596a5aa4622aa7869ee1
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Desenvolvimento do administrador do Recommendations do produto

O Product Recommendations é uma poderosa ferramenta de marketing que pode ser usada para aumentar as conversões, aumentar a receita e estimular o envolvimento do comprador. Os Recommendations de produtos são exibidos na loja, na forma de unidades como &quot;Clientes que visualizaram este produto também visualizaram&quot;, &quot;Clientes que compraram este produto também compraram&quot;, &quot;Recomendado para você&quot; e assim por diante. O Adobe Commerce Product Recommendations é fornecido por [Adobe Sensei](https://www.adobe.com/sensei.html), que usa inteligência artificial e algoritmos de aprendizado de máquina para executar uma análise profunda dos dados agregados do consumidor. Esses dados, quando combinados ao catálogo de Comércio, resultam em experiências altamente envolventes, relevantes e personalizadas para o comprador.

>[!NOTE]
>
>Se a loja estiver implementada usando o PWA Studio, consulte a [Documentação do PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Se você usar uma tecnologia de front-end personalizada, como React ou Vue JS, consulte o guia do usuário para saber como integrar o Recommendations do produto em uma [impiedoso](headless.md) ambiente.

## Visão geral da arquitetura

Em um alto nível, o Commerce Product Recommendations é implantado como SaaS. O lado Comércio inclui a loja, que contém o coletor de eventos e o modelo de layout de recomendações, e o back-end, que inclui os Serviços de dados, o módulo de Exportação SaaS e a Interface do usuário do administrador. Os serviços de inteligência Adobe Sensei são aproveitados no lado SaaS.

![Diagrama da arquitetura do Recommendations de produtos](assets/arch-diag-sensei.svg)

Depois que os módulos de recomendação forem instalados e configurados, sua loja começará a coletar dados comportamentais. O Adobe Sensei processa esses dados comportamentais junto com os dados do catálogo e calcula as associações de produtos que são aproveitadas pelo serviço do Recommendations. Neste ponto, o comerciante pode criar, gerenciar e implantar unidades de recomendação de produto em sua loja diretamente da interface do usuário do administrador.

## Tipos de dados

O Recommendations do produto exige os seguintes dados:

- **Comportamento** - Dados do envolvimento de um comprador no site, como exibições de produtos, itens adicionados a um carrinho e compras. O Commerce e o Adobe Sensei não coletam informações de identificação pessoal.

- **Catálogo** - Metadados do produto, como nome, preço, disponibilidade e assim por diante.

Ao instalar o `magento/product-recommendations` , o Adobe Sensei agrega os dados comportamentais e de catálogo, criando o Recommendations do Produto para cada tipo de recomendação. O serviço Recommendations do produto implanta essas recomendações na loja.

## Próximas etapas

Leia os seguintes tópicos para começar a usar o Recommendations do produto:

- [Como implementar o Recommendations do produto](implementation-workflow.md)

- [Instalar e configurar o Product Recommendations](install-configure.md)

- [Criar Recommendations de produto](create.md)
