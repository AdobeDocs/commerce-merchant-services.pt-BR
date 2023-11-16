---
title: Integrar o SDK do Adobe Experience Platform Mobile ao Commerce
description: Saiba como usar o SDK do Adobe Experience Platform Mobile com sua loja headless ou personalizada do Commerce.
role: Admin, Developer
feature: Personalization, Integration, Eventing
exl-id: d1340b15-e7de-42b5-ad64-d4c31f0db029
source-git-commit: 4a5877d6e1a5c7d840e36f4913306b0c440bbac5
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 0%

---

# Integrar o SDK do Adobe Experience Platform Mobile ao Commerce

>[!IMPORTANT]
>
>O SDK do Adobe Experience Platform Mobile para iOS é compatível com o iOS 11 ou posterior.

Integrando o [Adobe Experience Platform Mobile SDK](https://developer.adobe.com/client-sdks/home/) com o aplicativo móvel Commerce permite que os comerciantes enviem  [dados do evento](events.md) para a borda do Experience Platform.

Quando os dados do evento do Commerce estiverem disponíveis na borda, eles poderão ser acessados por outros aplicativos da Adobe Experience Cloud. Por exemplo, você pode usar os dados para criar públicos no Real-Time CDP e [usar esses públicos](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) para personalizar seu aplicativo móvel do Commerce.

## Configuração

Para começar a usar o Adobe Experience Platform Mobile SDK com o Commerce, instale e configure o SDK no Experience Platform. Em seguida, finalize sua configuração no Commerce.

### Experience Platform

1. Saiba mais sobre os recursos do aplicativo móvel revisando o [Tutorial do Adobe Experience Cloud em aplicativos para dispositivos móveis](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/overview.html).

1. [Instalar e configurar](https://developer.adobe.com/client-sdks/documentation/getting-started/) o SDK no Experience Platform.

   >[!NOTE]
   >
   >O esquema criado e configurado no Experience Platform é o mesmo esquema usado no código do aplicativo no aplicativo móvel do Commerce.

### Commerce

Após concluir a configuração do SDK para a Experience Platform, adicione a configuração do SDK ao Commerce.

1. Para enviar dados do evento do Commerce para o Experience Platform por meio do SDK, você deve fornecer um esquema XDM no código do aplicativo. Este esquema deve corresponder ao esquema [configurado](https://developer.adobe.com/client-sdks/home/getting-started/set-up-schemas-and-datasets/) para o SDK no Experience Platform.

   O exemplo a seguir mostra como rastrear o `web.webpagedetails.pageViews` e defina o `identityMap` usando o campo email.

   ```swift
   let stateName = "luma: content: ios: us: en: home"
   var xdmData: [String: Any] = [
       "eventType": "web.webpagedetails.pageViews",
       "web": [
           "webPageDetails": [
               "pageViews": [
                   "value": 1
               ],
               "name": "Home page"
           ]
       ]
   ]
   
   let experienceEvent = ExperienceEvent(xdm: xdmData)
   Edge.sendEvent(experienceEvent: experienceEvent)
   
   // Adobe Experience Platform - Update Identity
   
   let emailLabel = "mobileuser@example.com"
   
   let identityMap: IdentityMap = IdentityMap()
   identityMap.add(item: IdentityItem(id: emailLabel), withNamespace: "Email")
   Identity.updateIdentities(with: identityMap)
   ```

1. Conecte-se ao ambiente de Commerce Cloud.

   Nas configurações de criação do projeto, adicione o URL ao endpoint do Commerce GraphQL. Tais como:

   - Depuração: http://_depurar_.commercesite.cloud/graphql/
   - Versão: http://_versão_.commercesite.cloud/graphql/

1. Para recuperar dados dos endpoints do Commerce GraphQL, primeiro gere os arquivos e diretórios necessários em seu projeto usando o [Gerador de código Apollo](https://www.apollographql.com/docs/ios/).

   1. No diretório do projeto, [instalar](https://www.apollographql.com/docs/ios/get-started#1-install-the-apollo-frameworks) Apollo iOS.

   1. [Inicializar](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#initialize) a CLI do Codegen da Apollo.

      Isso cria uma `apollo-codegen-configuration.json` arquivo.

   1. Gere os arquivos e diretórios necessários do GraphQL em seu projeto substituindo o conteúdo do `apollo-codegen-configuration.json` arquivo com o seguinte:

      ```json
      {
      "schemaName" : "MagentoAPI",
      "input" : {
          "operationSearchPaths" : [
          "**/*.graphql"
          ],
          "schemaSearchPaths" : [
          "**/*.graphqls"
          ]
      },
      "output" : {
          "testMocks" : {
          "none" : {
          }
          },
          "schemaTypes" : {
          "path" : "../MagentoAPI",
          "moduleType" : {
              "swiftPackageManager" : {
              }
          }
          },
          "operations" : {
          "inSchemaModule" : {
          }
          }
      },
      "schemaDownloadConfiguration": {
          "downloadMethod": {
              "introspection": {
                  "endpointURL": "http://magento24.com/graphql/",
                  "httpMethod": {
                      "POST": {}
                  },
                  "includeDeprecatedInputValues": false,
                  "outputFormat": "SDL"
              }
          },
          "downloadTimeout": 60,
          "headers": [],
          "outputPath": "magento.graphqls"
      }
      }
      ```

   1. [Buscar](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#fetch-schema) o schema Commerce GraphQL.

      Certifique-se de que o caminho esteja para o estado `./apollo-codegen-config.json` arquivo, que contém a referência ao esquema Commerce GraphQL.

   1. [Gerar](https://www.apollographql.com/docs/ios/code-generation/codegen-cli/#generate) o código-fonte.

      Certifique-se de que o caminho esteja para o estado `./apollo-codegen-config.json` arquivo, que contém as informações de configuração para gerar os arquivos e diretórios necessários.

   1. Dentro do recém-criado **GraphQLGenerated** pasta, adicione ou edite tipos de GraphQL. Por exemplo, é possível adicionar um `DynamicBlocks.graphql` digite com o seguinte conteúdo:

      ```graphql
      query dynamicBlocks($input: DynamicBlocksFilterInput){
          dynamicBlocks(input: $input)
          {
              items {
                  content {
                      html
                  }
              }
          }
      }
      ```

   Agora você integrou o Adobe Experience Platform Mobile SDK ao seu aplicativo móvel do Commerce. Os dados do evento fluem do seu aplicativo para a borda do Experience Platform.

Para saber como recuperar públicos-alvo da Real-Time CDP no aplicativo móvel do Commerce para informar regras de preço do carrinho e blocos dinâmicos, consulte [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html).
