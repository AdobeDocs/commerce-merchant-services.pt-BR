---
title: Atualizar esquema de registro de perfil para assimilação de dados do Commerce
description: Saiba como criar um esquema, conjunto de dados e sequência de dados para coletar e enviar dados de registro de perfil do Commerce para o Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 86a3ba12-7f26-4f7e-98a0-9af0d1d8d881
source-git-commit: 813be62b366b1c76a2b909079cfba31ef8000617
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%

---

# Atualizar esquema de registro de perfil para Assimilação de dados do Commerce (Beta)

Quando os compradores criam um perfil no site do Commerce, um registro de perfil é criado e os dados são capturados. Você deve criar um esquema e um conjunto de dados específicos para esse registro de perfil antes de poder transmitir esses dados de perfil para o Experience Platform.

1. [Criar](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) um esquema e defina a classe como **Perfil individual**.

1. [Adicionar](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) os seguintes grupos de campos específicos do perfil:

   - identityMap
   - Detalhes demográficos
   - Detalhes de contato pessoal
   - Detalhes da conta do usuário

1. [Ativar](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas) o schema para o Perfil.

   Quando um esquema é ativado para o Perfil, qualquer conjunto de dados criado a partir desse esquema participa do Real-Time CDP, que mescla dados de fontes diferentes para criar uma visualização completa de cada cliente.

1. [Criar um conjunto de dados](https://experienceleague.adobe.com/en/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform) com base no schema criado ou atualizado.

   Um conjunto de dados é uma construção de armazenamento e gerenciamento para uma coleção de dados, normalmente uma tabela que contém um esquema (colunas) e campos (linhas). Os conjuntos de dados também contêm metadados que descrevem vários aspectos dos dados armazenados.

1. Criar um [namespace personalizado](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces#create-namespaces) em Experience Platform com os seguintes valores:

   - **Nome de exibição**: _ID de cliente do Commerce_
   - **Símbolo de identidade**: _CustomerId_
   - **Tipo**: _ID individual entre dispositivos_

   ![Criar namespace personalizado](assets/custom-namespace.png){width="700" zoomable="yes"}

   Clique em **[!UICONTROL Create]**. Um namespace personalizado é usado pelo Serviço de perfil unificado para unir fragmentos de perfil.

Com o esquema, o conjunto de dados e o namespace personalizado configurados para dados de registro do perfil do cliente, é possível [configurar](connect-data.md#data-collection) sua instância do Commerce para coletar e enviar esses dados para o Experience Platform.

Para criar um esquema, conjunto de dados e fluxo de dados para dados de evento comportamentais e de back office, consulte [atualizar esquemas de evento de série temporal para assimilação de dados do Commerce](update-xdm.md).
