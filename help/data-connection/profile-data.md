---
title: Atualizar esquema de registro de perfil para assimilação de dados do Commerce
description: Saiba como criar um esquema, conjunto de dados e sequência de dados para coletar e enviar dados de registro de perfil do Commerce para o Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 8456f9b81812cf8ace55b7406d8b4fe50332c17a
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# Atualizar esquema de registro de perfil para assimilação de dados do Commerce

>[!NOTE]
>
>Esse recurso está na versão beta. Se você quiser participar do programa beta, envie uma solicitação para [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

Quando seus compradores criam um perfil no site do Commerce, um registro de perfil é criado e os dados são capturados. Você deve criar um esquema e um conjunto de dados específicos para esse registro de perfil antes de poder transmitir esses dados de perfil para o Experience Platform.

1. [Criar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#create) um esquema e defina a classe como **Perfil individual**.

1. [Adicionar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#add-field-groups) os seguintes grupos de campos específicos do perfil:

   - identityMap
   - Detalhes demográficos
   - Detalhes de contato pessoal
   - Detalhes da conta do usuário

1. [Ativar](https://experienceleague.adobe.com/docs/experience-platform/xdm/ui/resources/schemas.html#profile) o schema para o Perfil.

   Quando um esquema é ativado para o Perfil, qualquer conjunto de dados criado a partir desse esquema participa do Real-Time CDP, que mescla dados de fontes diferentes para criar uma visualização completa de cada cliente.

1. [Criar um conjunto de dados](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) com base no esquema criado ou atualizado.

   Um conjunto de dados é uma construção de armazenamento e gerenciamento para uma coleção de dados, normalmente uma tabela que contém um esquema (colunas) e campos (linhas). Os conjuntos de dados também contêm metadados que descrevem vários aspectos dos dados armazenados.

Com o esquema e o conjunto de dados configurados para dados de registro do perfil do cliente, você pode [configurar](connect-data.md#data-collection) sua instância do Commerce para coletar e enviar esses dados para o Experience Platform.

Para criar um esquema, conjunto de dados e fluxo de dados para dados de evento comportamentais e de back office, consulte [atualizar esquemas de evento de série temporal para assimilação de dados do Commerce](update-xdm.md).
