---
title: Adicionar grupos de campos ao esquema XDM
description: Saiba como adicionar grupos de campos específicos do Adobe Commerce a um esquema XDM.
exl-id: 4401bbe7-1ccc-4349-a998-9e9ee9db590f
source-git-commit: c9b1d7e34632f7a54544bc6944144b1833ecc5a5
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# Adicionar grupos de campos ao esquema XDM

Um dos [etapas de integração](overview.md#onboarding-steps) usar o conector do Experience Platform é acessar o espaço de trabalho do datastream e [criar um conjunto de dados](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) específico do Adobe Commerce. Ao criar esse armazenamento de dados, você também deve selecionar um esquema XDM que representa os dados que planeja assimilar. Este tópico fornece os grupos de campos que o esquema XDM deve incluir para coletar com sucesso os dados fornecidos pela loja da Adobe Commerce [events](events.md).

1. Se você ainda não tiver um esquema XDM, [criar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) um. Caso contrário, [editar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#edit) seu esquema XDM existente na interface do usuário do Adobe Experience Platform.

1. [Adicionar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) os seguintes grupos de campos específicos de Comércio:

   - Pesquisa do site
   - Visitar página da Web
   - Processo de logon do usuário
   - Teclas de referência
   - Detalhes de contato pessoal
   - Detalhes de comércio
   - Comércio de evento do Adobe Analytics Experience (se desejar enviar dados para o Adobe Analytics)
   - Mapa de identidade

   >[!NOTE]
   >
   > Não defina nenhum grupo de campos específico de Comércio como `Primary identity`. Isso identifica o campo como obrigatório e o Experience Platform espera esse campo em cada evento. Se esse campo estiver ausente, a assimilação de dados falhará.

   Seu esquema XDM agora contém grupos de campos específicos de comércio para que os dados coletados da loja do Commerce [events](events.md) é representado no XDM.

1. [Criar um conjunto de dados](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) com base no esquema criado ou atualizado.

   Um conjunto de dados é uma construção de armazenamento e gerenciamento para uma coleção de dados, normalmente uma tabela, que contém um esquema (colunas) e campos (linhas). Os conjuntos de dados também contêm metadados que descrevem vários aspectos dos dados armazenados.

1. [Criar um conjunto de dados](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) e selecione o esquema XDM que contém os grupos de campos específicos de Comércio e o conjunto de dados correspondente.

   O datastream encaminha os dados coletados para o conjunto de dados. Os dados são representados no conjunto de dados com base no schema selecionado.
