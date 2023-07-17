---
title: Conectar sua instância
description: Conecte sua instância do Commerce usando uma chave de API e uma chave privada e especifique o espaço de dados na configuração.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
feature: Payments, Checkout, Configuration, Saas
source-git-commit: 90bfa7099924feb308397960cff76bdf177bbe49
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# Conectar sua instância

[!DNL Payment Services] O é disponibilizado pelo Commerce Services e implantado como SaaS (software como um serviço). Você conecta sua instância do Commerce usando uma chave de API e uma chave privada e especifica o espaço de dados na configuração usando o [Conector dos Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **Você configura essa conexão apenas uma vez.**

* Se você tiver *já conectou sua instância*, obtendo e usando suas credenciais de API e configurando os Serviços do Commerce, você pode prosseguir para [configuração da sandbox de teste](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* Se você ainda *precisa conectar sua instância*, consulte as informações sobre [obtenção de credenciais de API](#obtain-api-credentials) e [configuração de Commerce Services](#configure-commerce-services).
* Se você estiver *não tenho certeza se sua instância está conectada*, navegue até **Sistema** > Serviços > **Conector dos Commerce Services** e exibir os valores de chave da API pública e privada na variável [!UICONTROL Sandbox Keys] e [!UICONTROL Production Keys] seções e o *Projeto* e *Espaço de dados* campos no [!UICONTROL SaaS Identifier] seção. Se esses valores estiverem presentes, sua instância será conectada.

## Obter credenciais de API

Para consumir um serviço SaaS do Commerce, você deve usar as chaves de API da instância (chave de API pública do Commerce e uma chave privada) para sandbox e produção, que são criadas e gerenciadas no [Painel Minha conta](https://account.magento.com/customer/account/login). [O par de chaves](https://docs.magento.com/user-guide/configuration/services/saas.html) pode ser criado para uma conta do Commerce, uma para sandbox e outra para produção, embora somente um par possa ser usado ativamente de cada vez.

>[!NOTE]
>
>Precisa de ajuda para acessar seu [!UICONTROL My Account] painel? Consulte [Criar uma conta do Commerce](https://docs.magento.com/user-guide/magento/magento-account-create.html).

Uma chave de API pública, uma vez criada, está sempre disponível no Painel Minha conta. Ela pode ser copiada ou excluída, conforme necessário. A chave de API privada torna-se visível quando você cria uma chave de API pública para sandbox ou produção; ela só está disponível para copiar ou salvar da caixa de diálogo subsequente e não pode ser acessada posteriormente.

Um determinado par de chaves de API é válido para todos os Commerce Services em um ambiente, portanto, se você já tiver o Commerce Services configurado para sua instância, seu par de chaves de API já estará presente no Commerce Services Connector.

Se a chave de API for perdida, um novo par de chaves de API deverá ser [gerado](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) e [aplicado](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) à configuração do Commerce Services Connector no Administrador. Se as chaves incorretas estiverem configuradas ou não houver nenhuma na configuração, uma caixa de diálogo de erro de verificação de conta será exibida nos Serviços de pagamento, notificando-o de que a conta não foi verificada.

Consulte uma [lista de Commerce Services disponíveis que usam a API](https://docs.magento.com/user-guide/system/saas.html#available-services).

Para saber como gerar uma chave de API para ambientes de sandbox ou produção, consulte [Credenciais](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>É recomendável não gerar novamente um par de chaves de API *e* alterar o identificador SaaS e/ou o espaço de dados em uma instância de produção ativa. Você perderá os dados da sua instância se eles forem modificados.

## Configurar Commerce Services

A mesma chave de API pode ser usada em várias instâncias, mas cada instância deve ter sua própria [Espaço de dados SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

Agora que obteve as credenciais, é possível configurar o projeto SaaS e o Espaço de dados Saas.

1. No _Admin_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Clique em **[!UICONTROL Configure Commerce Services]**.

   Esta opção estará visível se você ainda não tiver configurado os Commerce Services para sua conta.

   Você é direcionado para a área de configuração no Administrador, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**, para configurar o Commerce Services Connector.

1. Para configurar os Commerce Services, siga as etapas descritas em [Configuração SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).
