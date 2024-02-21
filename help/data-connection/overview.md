---
title: Visão geral do Guia
description: Saiba como integrar dados do Adobe Commerce ao Adobe Experience Platform usando o [!DNL Data Connection] extensão.
exl-id: a8362e71-e21c-4b1d-8e3f-336e748e1018
recommendations: noCatalog
source-git-commit: af54529ad037dc99dbc07cf1a6ac270d17f16870
workflow-type: tm+mt
source-wordcount: '1732'
ht-degree: 0%

---

# [!DNL Data Connection] Introdução

>[!IMPORTANT]
>
>O conector Experience Platform foi renomeado para [!DNL Data Connection].

A variável [!DNL Data Connection] A extensão do conecta sua instância da Web do Adobe Commerce à Adobe Experience Platform e à Rede de borda. Saiba como [integrar](./mobile-sdk-epc.md) o SDK do Adobe Experience Platform Mobile com Commerce.

Sua loja de Commerce contém uma grande variedade de dados. As informações sobre como seus compradores navegam, visualizam e compram os produtos em seu site podem revelar oportunidades para criar uma experiência de compra mais personalizada. Embora esses dados possam informar recursos nativos do Commerce, como regras de preço do carrinho e blocos dinâmicos, os dados permanecem em silos na instância do Commerce.

A Adobe Experience Platform fornece um conjunto de tecnologias que, quando hidratadas com os dados da sua loja de Commerce, podem distribuir esses dados pela Edge Network para outros produtos Adobe DX a fim de desbloquear insights sobre o comportamento de compra do seu comprador. Com esses insights profundos, você pode criar uma experiência de compras mais personalizada em todos os canais.

A imagem a seguir mostra como seus dados do Commerce fluem de sua loja para outros produtos Adobe DX:

![Como os dados fluem para a borda do Experience Platform](assets/commerce-edge.png)

Na imagem acima, seus dados comportamentais, de back office e de perfil do cliente são enviados para a borda do Experience Platform usando um SDK, uma API e um conector de origem. Não é necessário entender totalmente como essas partes funcionam, pois a extensão lida com a complexidade do compartilhamento de dados para você. Quando os dados do evento estiverem na borda, você poderá puxá-los para outros aplicativos Experience Platform. Por exemplo:

| Aplicativo | Finalidade | Casos de uso |
|---|---|---|
| [Adobe [!DNL Real-Time CDP]](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html) | Serviço de gerenciamento e segmentação de perfil | **Segmentação do histórico de compras**: os comerciantes podem identificar clientes que compram um item com base em um período específico (mensal, trimestral, anual e assim por diante). Os comerciantes podem então criar segmentos para esses clientes e direcioná-los para promoções, campanhas e conforme _parte superior do funil_ dados para clientes potenciais para serviços de assinatura.<br> **Segmentação baseada em categorias**: os comerciantes podem ver qual categoria de produtos foi comprada.<br> **Segmentação baseada em oferta**: os comerciantes podem identificar clientes que devolvem produtos de maneira consistente. As ofertas e os descontos dados a eles agora podem ser mais inteligentes. Por exemplo, o frete grátis pode ser removido para um cliente que devolve produtos o tempo todo.<br> **Segmentação por semelhança**: A _Público-alvo semelhante_ O é uma metodologia adotada por um comerciante para que suas promoções cheguem a novas pessoas que provavelmente estarão interessadas em seus negócios, pois compartilham características semelhantes às de seus clientes existentes. Segmentos semelhantes podem ser criados com base em dados comportamentais e transacionais.<br> **Propensão do cliente**: as alterações no comportamento do cliente podem ser identificadas como resultado dos perfis de cliente mais profundos que podem ser criados a partir dos dados transacionais. Haverá uma maior confiança na pontuação de propensão, pois há mais dados fluindo para os cálculos, como retornos de produtos e configurações de produtos.<br> **Venda cruzada**: um comerciante pode identificar fortes oportunidades de venda cruzada e venda adicional com base nas informações granulares capturadas no Commerce. |
| [Cliente [!DNL Journey Analytics]](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html) | Análise profunda da jornada completa do Commerce | **Tendências sazonais**: um comerciante pode identificar tendências sazonais, o que os ajuda a se preparar para a alteração periódica na demanda de produtos específicos. Além disso, os comerciantes podem identificar mudanças na popularidade geral de qualquer produto ao longo dos anos.<br> **Análise de conversão**: ao saber quando um produto foi comprado, juntamente com o acesso a eventos de impressão da loja, os comerciantes podem gerar um perfil avançado do cliente para executar a análise de conversão. |
| [Adobe [!DNL Analytics]](https://experienceleague.adobe.com/docs/analytics/analyze/admin-overview/analytics-overview.html) | Análise detalhada do comportamento do cliente e do desempenho da campanha | **Devoluções de pedidos**: os comerciantes podem identificar clientes e os maiores segmentos de clientes que têm um padrão de devolução de produtos. Isso ajuda os comerciantes a melhorar sua estratégia comercial, pois entendem como o comportamento da base de clientes se parece.<br> **Endereço do pedido**: com base no endereço de entrega, um comerciante pode entender se os pedidos estão sendo feitos pelos próprios clientes ou se é para outro indivíduo ou entidade.<br> **Tendências de sazonalidade**: um comerciante pode identificar tendências sazonais, o que os ajuda a se preparar para a alteração periódica na demanda de produtos específicos. Além disso, os comerciantes podem identificar mudanças na popularidade geral de qualquer produto ao longo dos anos.<br> **Análise de conversão**: ao saber quando um produto foi comprado, juntamente com o acesso a eventos de impressão da loja, os comerciantes podem gerar um perfil avançado do cliente para executar a análise de conversão. **Nota** O Adobe Analytics aceita somente dados de eventos comportamentais (loja). O Adobe Analytics não oferece suporte a dados de eventos transacionais (backoffice). |
| [Adobe [!DNL Journey Optimizer]](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) | Orquestração de campanha entre canais | **Jornadas baseadas em comportamento**: os comerciantes podem direcionar um cliente que comprou um telefone celular há dois anos, sugerindo que comprem o novo modelo. Os comerciantes podem criar campanhas e promoções personalizadas para esses clientes e usar a funcionalidade de email e SMS para entrar em contato com o. Além disso, os comerciantes podem usar dados históricos de ordem e comportamento para identificar tendências. Por exemplo, um cliente que comprou um item com uma configuração específica no passado e agora deseja comprar o mesmo produto novamente pode ter sua jornada de compra aprimorada ao fornecer visibilidade e acesso às mesmas configurações de produto.<br> **Personalização**: com acesso às informações de perfil do cliente, [!DNL Journey Optimizer] O pode desbloquear jornadas altamente personalizadas, permitindo que os comerciantes entrem em contato com os clientes em vários canais diferentes.<br> **Novo perfil criado**: emails de boas-vindas e atividades promocionais podem incentivar e influenciar novos clientes em suas jornadas de compras.<br> **Perfil excluído**: os comerciantes podem optar por interromper o envio de emails promocionais para clientes que fecharam a conta. Como alternativa, os comerciantes também podem criar campanhas para recuperar clientes perdidos. |

## Enviar dados do Experience Platform de volta para o Commerce

Enviar os dados do Commerce para o Experience Platform usando o [!DNL Data Connection] A extensão do é um lado dos recursos de compartilhamento de dados do Commerce. O outro lado, que é uma extensão opcional, é chamado [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html). Essa extensão permite criar públicos-alvo no Real-Time CDP e implantá-los na loja do Commerce para informar regras de preço do carrinho, regras de produto relacionadas (beta) e blocos dinâmicos.

Em um alto nível, o fluxo de dados da sua loja Commerce para o Experience Platform e de volta para a extensão Audience Activation é semelhante ao seguinte:

![[!DNL Data Connection] fluxo](assets/data-connection.png)

Após configurar a conexão entre o Commerce e o Experience Platform e o Experience Platform para o Commerce, os dados continuam a fluir. Você não precisa se reconectar, a menos que isso seja exigido por uma atualização.

## Conceitos

O compartilhamento de dados entre esses dois sistemas requer a compreensão de vários conceitos.

* **Dados** - Os dados compartilhados com o Experience Platform são os dados coletados dos eventos do navegador na loja, dos eventos do back office no servidor e dos dados de registro do perfil. Os eventos de vitrine eletrônica são capturados das interações dos compradores no site e incluem eventos como [`addToCart`](events.md#addtocart), [`pageView`](events.md#pageview), [`createAccount`](events.md#createaccount), [`editAccount`](events.md#editaccount), [`startCheckout`](events.md#startcheckout), [`completeCheckout`](events.md#completecheckout), [`signIn`](events.md#signin), [`signOut`](events.md#signout)e assim por diante. Consulte [eventos da loja](events.md#storefront-events) para obter a lista completa dos eventos da loja. Os eventos do lado do servidor ou de back-office incluem [status do pedido](events-backoffice.md#order-status) informações, como [`orderPlaced`](events-backoffice.md#orderplaced), [`orderReturned`](events-backoffice.md#orderitemreturncompleted), [`orderShipped`](events-backoffice.md#ordershipmentcompleted), [`orderCancelled`](events-backoffice.md#ordercancelled)e assim por diante. Consulte [eventos de back office](events-backoffice.md) para obter a lista completa de eventos de back office. Os dados de registro do perfil contêm informações quando um novo perfil é criado, atualizado ou excluído. Consulte [dados de registro do perfil](events-profilerecord.md) para saber mais.

* **Rede de Experience Platform e de borda** - Data warehouse para a maioria dos produtos Adobe DX. Os dados enviados para o Experience Platform são então propagados para os produtos Adobe DX através da Experience Platform Edge Network. Por exemplo, você pode iniciar o Journey Optimizer, recuperar seus dados de evento do Commerce específicos da borda e criar um email de carrinho abandonado no Journey Optimizer. O Journey Optimizer pode enviar esse email se houver carrinhos abandonados em sua loja de Commerce. Saiba mais sobre o [Experience Platform e a rede de borda](https://experienceleague.adobe.com/docs/platform-learn/data-collection/web-sdk/overview.html).

* **Esquema** - O esquema é o que descreve a estrutura dos dados que estão sendo enviados. Antes que o Experience Platform possa assimilar seus dados do Commerce, você deve compor um esquema para descrever a estrutura dos dados e fornecer restrições ao tipo de dados que pode estar contido em cada campo. Os esquemas consistem em uma classe base e zero ou mais grupos de campos de esquema. O esquema usa a estrutura XDM, que todos os produtos Adobe DX podem ler. Assim, ao enviar seus dados para o Experience Platform, você pode ter certeza de que eles serão compreendidos em todos os produtos DX. Saiba mais sobre [schemas](https://experienceleague.adobe.com/docs/experience-platform/xdm/home.html).

* **Conjunto de dados** - Uma construção de armazenamento e gerenciamento para uma coleção de dados, normalmente uma tabela que contém um esquema (colunas) e campos (linhas). Os conjuntos de dados também contêm metadados que descrevem vários aspectos dos dados armazenados. Todos os dados assimilados com sucesso na Adobe Experience Platform estão contidos em conjuntos de dados. Saiba mais sobre [conjuntos de dados](https://experienceleague.adobe.com/docs/experience-platform/catalog/datasets/overview.html).

* **Sequência de dados** - ID que permite o fluxo de dados do Adobe Experience Platform para outros produtos Adobe DX. Essa ID deve ser associada a um site específico em sua instância específica do Adobe Commerce. Ao criar esse fluxo de dados, especifique o esquema XDM criado acima. Saiba mais sobre [sequências de dados](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html).

## Arquitetura com suporte

A variável [!DNL Data Connection] A extensão do está disponível nas seguintes arquiteturas:

* PHP/Luma
* [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/adobe-commerce/aep/)
* [AEM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/integrations/aep.html)

## Pré-requisitos

Para usar o [!DNL Data Connection] extensão, você deve ter o seguinte:

* Adobe Commerce 2.4.4 ou mais recente
* Adobe ID e ID da organização
* [Camada de dados de clientes Adobe (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html), que é necessário para coletar dados do evento da loja
* Qualificações para outros produtos Adobe DX.

## Etapas de integração

A um nível superior, permitindo a [!DNL Data Connection] A extensão do envolve as seguintes etapas:

1. [Instalar](install.md) o [!DNL Data Connection] extensão.
1. [Fazer logon](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) para sua conta Adobe e [exibir para confirmar](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255) sua ID da organização. A ID da organização é a ID associada à empresa de Experience Cloud provisionada. A ID é uma sequência de 24 caracteres alfanuméricos seguidos por (e deve incluir) `@AdobeOrg`.
1. Verifique se você tem [permissão para coleta de dados no Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/collection/permissions.html).
1. Revise o [tipos de dados](data-ingestion.md) você pode coletar e enviar.
1. Criar ou atualizar seu [esquema de evento de série temporal](update-xdm.md) ou [esquema de dados de registro de perfil](profile-data.md) com grupos de campos específicos do Commerce.
1. [Criar um conjunto de dados](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) com base no esquema criado ou atualizado. Esse conjunto de dados contém os dados do Commerce enviados para o Experience Platform Edge.
1. [Criar um fluxo de dados](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) e selecione o esquema XDM que contém os grupos de campos específicos do Commerce.
1. [Conectar-se a Commerce Services](../landing/saas.md).
1. [Conectar-se ao Adobe Experience Platform](connect-data.md).

O restante deste guia aborda todas essas etapas com mais detalhes para que você possa se atualizar e começar a usar o poder dos produtos Adobe DX na sua loja de Commerce.

>[!NOTE]
>
>Para desenvolvedores móveis, saiba como [integrar](./mobile-sdk-epc.md) o SDK do Adobe Experience Platform Mobile com Commerce.

## Público-alvo

Este guia foi projetado para o comerciante do Adobe Commerce que deseja enriquecer e personalizar sua loja do Commerce para aprimorar a experiência de compra de seus clientes.

## Suporte

Se você precisar de informações ou tiver dúvidas que não são abordadas neste guia, use os seguintes recursos:

* [Central de ajuda](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/overview.html){target="_blank"}
* [Tíquetes de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket){target="_blank"}—Envie um tíquete para receber ajuda adicional.
