---
title: Atualizar esquemas de evento de série de tempo para assimilação de dados do Commerce
description: Saiba como criar um esquema, conjunto de dados e sequência de dados para coletar e enviar dados do evento de série de tempo para assimilação de dados do Commerce.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: d5824e11b4961b518e35fcf56ff2c7ee00480617
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 0%

---

# Atualizar esquemas de evento de série de tempo para assimilação de dados do Commerce

Um dos [etapas de integração](overview.md#onboarding-steps) para usar o [!DNL Data Connection] extensão é para acessar o espaço de trabalho de sequência de dados e [criar um fluxo de dados](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) específico do Adobe Commerce. Ao criar esse fluxo de dados, você também deve selecionar um esquema que descreva os dados que planeja assimilar. Esse esquema deve incluir grupos de campos específicos do comércio.

Este artigo fornece os grupos de campos que seu esquema deve incluir para coletar com êxito os seguintes dados de série temporal fornecidos pelos eventos do Adobe Commerce:

- [Comportamento](events.md) - Inclui eventos da loja, perfil, pesquisa e B2B.
- [Back office](events-backoffice.md) - Inclui o status do pedido e os eventos do perfil.

Saiba mais sobre [dados de série temporal](data-ingestion.md).

Saiba mais sobre o [noções básicas da composição do esquema](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/composition.html).

## Atualizar esquema com dados comportamentais de série temporal e de evento de back office

Nesta seção, você aprenderá a atualizar seu esquema existente ou criar um esquema para incluir dados de evento comportamentais e de back office.

>[!NOTE]
>
>Consulte [dados do evento de perfil de série temporal](#time-series-profile-event-data) para saber como adicionar campos específicos de perfil.

1. Se você ainda não tiver um esquema, [criar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) um com a classe definida como **Evento de experiência**.

1. [Adicionar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) os seguintes grupos de campos específicos do Commerce (ou edite o esquema existente e adicione esses grupos de campos):

   - Pesquisa no site
   - Visitar página da Web
   - Processo de logon do usuário
   - Chaves de referência
   - Detalhes de contato pessoal
   - Detalhes do canal
   - Detalhes do comércio
   - Adobe Analytics ExperienceEvent Commerce (se desejar enviar dados para o Adobe Analytics)

   >[!NOTE]
   >
   > Não definir grupos de campos específicos do Commerce como `Primary identity`. Isso identifica o campo como obrigatório e o Experience Platform espera esse campo em cada evento. Se esse campo estiver ausente, a assimilação de dados falhará.

   Seu esquema agora contém grupos de campos específicos do Commerce para que os dados de série de tempo coletados do Commerce [comportamental](events.md) e [back office](events-backoffice.md) events é representado no esquema.

1. [Ativar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) o schema para o Perfil.

   Quando um esquema é ativado para o Perfil, qualquer conjunto de dados criado a partir desse esquema participa do Real-Time CDP, que mescla dados de fontes diferentes para criar uma visualização completa de cada cliente.

1. [Criar um conjunto de dados](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) com base no esquema criado ou atualizado.

   Um conjunto de dados é uma construção de armazenamento e gerenciamento para uma coleção de dados, normalmente uma tabela que contém um esquema (colunas) e campos (linhas). Os conjuntos de dados também contêm metadados que descrevem vários aspectos dos dados armazenados.

1. [Criar um fluxo de dados](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) e selecione o esquema que contém os grupos de campos específicos do Commerce e o conjunto de dados correspondente.

   O fluxo de dados encaminha os dados coletados para o conjunto de dados. Os dados são representados no conjunto de dados com base no esquema selecionado.

1. **Beta** (Opcional) Você pode usar atributos personalizados se quiser transmitir dados de evento de back office personalizados da sua instância do Commerce para o Experience Platform. Esse recurso está na versão beta. Se você quiser participar do programa beta, envie uma solicitação para [dataconnection@adobe.com](mailto:dataconnection@adobe.com). Em sua solicitação, inclua o seguinte:

   - Seu [ID da Organização Adobe](https://experienceleague.adobe.com/docs/core-services/interface/administration/organizations.html#concept_EA8AEE5B02CF46ACBDAD6A8508646255). Por exemplo `organization_id@AdobeOrg`.
   - Lista de atributos personalizados no nível do pedido.
   - Lista de atributos no nível do Item da Ordem.

   A equipe da Adobe Commerce entrará em contato com você para obter mais informações e as próximas etapas.

Com os esquemas, conjuntos de dados e fluxos de dados configurados para dados comportamentais e de back office, você pode [configurar](connect-data.md#data-collection) sua instância do Commerce para coletar e enviar esses dados para o Experience Platform.

Para incluir as informações do perfil do comprador, consulte a próxima seção.

## Dados do evento de perfil de série temporal

>[!NOTE]
>
>Esse recurso está na versão beta. Se você quiser participar do programa beta, envie uma solicitação para [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

Os dados do evento de perfil de série temporal são gerados a partir dos seguintes eventos:

- [&quot;accountCreated&quot;](events-backoffice.md#accountcreated)
- [&quot;accountUpdated&quot;](events-backoffice.md#accountupdated)
- [&quot;accountDeleted&quot;](events-backoffice.md#accountdeleted)

Se quiser assimilar os dados do evento de perfil do cliente no Experience Platform, atualize o esquema existente do Commerce e use o mesmo fluxo de dados já configurado, ou crie um fluxo de dados e um esquema específicos do perfil. Essa decisão se baseia na governança de dados da sua empresa. As próximas duas seções o guiarão em ambos os casos.

### Enviar dados do evento de perfil de série temporal para o Experience Platform usando sua sequência de dados existente

Se quiser adicionar séries de tempo [dados do evento de perfil do lado do servidor](events-backoffice.md#customer-profile-events-server-side) ao seu fluxo de dados existente do Commerce, adicione o `Demographic Details` grupo de campos ao seu esquema. Seu esquema agora contém os seguintes grupos de campos específicos do Commerce:

- Pesquisa no site
- Visitar página da Web
- Processo de logon do usuário
- Chaves de referência
- Detalhes de contato pessoal
- Detalhes do canal
- Detalhes do comércio
- Adobe Analytics ExperienceEvent Commerce (se desejar enviar dados para o Adobe Analytics)
- Novo: **Detalhes demográficos**

Com a adição da variável `Demographic Details` grupo de campos no esquema do Commerce existente, o conjunto de dados e a sequência de dados já associados ao esquema do Commerce são usados para os dados do perfil desta série temporal.

### Enviar dados do evento de perfil de série temporal para o Experience Platform em um fluxo de dados separado

Se quiser adicionar [dados do evento de perfil do lado do servidor](events-backoffice.md#customer-profile-events-server-side) para adicionar um novo datastream e esquema específicos do perfil, conclua as etapas a seguir.

1. [Criar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) um esquema e defina a classe como **Evento de experiência**.

1. [Adicionar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) os seguintes grupos de campos específicos do perfil:

   - Detalhes demográficos
   - Detalhes de contato pessoal
   - Detalhes do canal
   - Detalhes do comércio

1. [Ativar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) o schema para o Perfil.

   Quando um esquema é ativado para o Perfil, qualquer conjunto de dados criado a partir desse esquema participa do Real-Time CDP, que mescla dados de fontes diferentes para criar uma visualização completa de cada cliente.

1. [Criar um conjunto de dados](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) com base no esquema criado.

   Um conjunto de dados é uma construção de armazenamento e gerenciamento para uma coleção de dados, normalmente uma tabela que contém um esquema (colunas) e campos (linhas). Os conjuntos de dados também contêm metadados que descrevem vários aspectos dos dados armazenados.

1. [Criar um fluxo de dados](https://experienceleague.adobe.com/docs/experience-platform/datastreams/overview.html) e selecione o esquema XDM que contém os grupos de campos específicos do Commerce e o conjunto de dados correspondente.

   O fluxo de dados encaminha os dados coletados para o conjunto de dados. Os dados são representados no conjunto de dados com base no esquema selecionado.

Com os esquemas, conjuntos de dados e fluxos de dados configurados para dados de perfil do cliente, você pode [configurar](connect-data.md#data-collection) sua instância do Commerce para coletar e enviar esses dados para o Experience Platform.

Para criar um esquema, conjunto de dados e sequência de dados para dados de registro do perfil, consulte [enviar dados de registro de perfil para o Experience Platform](profile-data.md).
