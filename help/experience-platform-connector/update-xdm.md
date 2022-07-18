---
title: Adicionar grupos de campos ao esquema XDM
description: Saiba como adicionar grupos de campos específicos do Adobe Commerce a um esquema XDM.
source-git-commit: 4d6a4cec81dbb1e71718066be2ba13a4d292aea3
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Adicionar grupos de campos ao esquema XDM

Um dos [pré-requisitos](overview.md#prereqs) usar o conector do Experience Platform é acessar o espaço de trabalho do datastream e [criar um conjunto de dados](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) específico do Adobe Commerce. Ao criar esse armazenamento de dados, você também deve selecionar um esquema XDM que representa os dados que planeja assimilar. Este tópico fornece os grupos de campos que o esquema XDM deve incluir para coletar com sucesso os dados fornecidos pela loja da Adobe Commerce [events](events.md).

1. Se você ainda não tiver um esquema XDM, [criar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#create) um. Caso contrário, [editar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#edit) seu esquema XDM existente na interface do usuário do Adobe Experience Platform.
1. [Adicionar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html?lang=en#add-field-groups) os seguintes grupos de campos específicos de Comércio:

   - Comércio
   - Pesquisa do site
   - Visitar página da Web
   - Processo de logon do usuário
   - Teclas de referência
   - Detalhes de contato pessoal
   - Detalhes de comércio
   - Comércio de evento do Adobe Analytics Experience (se desejar enviar dados para o Adobe Analytics)
   - Identificador de pessoa

   Seu esquema XDM agora contém grupos de campos específicos de comércio para que os dados coletados da loja do Commerce [events](events.md) é representado no XDM.
1. Agora você deve [criar um conjunto de dados](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html?lang=en) e selecione o esquema XDM que contém os grupos de campos específicos de Comércio.
