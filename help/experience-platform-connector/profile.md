---
title: Fazer upload de perfis de comprador para o Adobe Experience Platform
description: Saiba como fazer upload de perfis de comprador para o Adobe Experience Platform.
exl-id: fd0ee7fa-5274-4640-ba00-bcb2ec78f314
source-git-commit: 9bf28159fdac3a7237956a536f6a522b4e2918fe
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Fazer upload do perfil de comprador para o Adobe Experience Platform

Os comerciantes da Adobe Commerce podem fazer upload dos dados de perfil do cliente para [Perfil do cliente em tempo real](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html), que faz parte do Adobe Experience Platform. O perfil permite consolidar os dados do cliente em uma visualização unificada, oferecendo uma conta acionável e com carimbo de data e hora de cada interação com o cliente.

>[!NOTE]
>
> Os dados do perfil devem incluir um endereço de email, pois é assim que o link entre um comprador e seus dados comportamentais da loja é criado.

Depois de fazer upload dos perfis do comprador, os dados do evento associados a quaisquer interações que seus compradores fazem no site são enviados ao Perfil por meio do conector de Experience Platform e vinculados ao perfil do comprador.

>[!NOTE]
>
> O `createAccount` [evento storefront](events.md) O não cria automaticamente um perfil de cliente no Perfil. Isso é restrito por motivos de segurança e é intencional.

Neste tópico, você aprenderá a fazer upload dos perfis de clientes do Adobe Commerce para o Perfil do cliente em tempo real no Experience Platform.

1. Determine onde você armazena os dados do cliente. Para alguns comerciantes, esses dados são armazenados no Adobe Commerce e podem ser [exportado](https://docs.magento.com/user-guide/system/data-export.html) como um arquivo CSV. Para outros, pode estar em um sistema de gerenciamento de relacionamento com o cliente (CRM) separado.

1. Depois de determinar onde você armazena os dados do cliente, localize as [conector de origem](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html) com base em onde os dados do cliente são armazenados. Se você não vir um conector de origem apropriado, use o [upload de arquivo local](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html) e importe seus perfis de comprador de um arquivo CSV.

   >[!NOTE]
   >
   > Se você usar o conector de upload de arquivo local, deverá ativar o **Conjunto de dados de perfil** opção ao [definição do conjunto de dados](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/local-system/local-file-upload.html#use-an-existing-dataset). Isso identifica o conjunto de dados como dados de perfil.

Depois de criar os perfis de comprador no Perfil, todos os dados de loja associados a esse comprador serão vinculados ao perfil.

## Fazer upload de perfis com frequência

Para garantir uma experiência aprimorada do comprador, você deve importar os dados do perfil periodicamente. Alguns conectores de origem permitem importar dados de perfil de acordo com uma programação.
