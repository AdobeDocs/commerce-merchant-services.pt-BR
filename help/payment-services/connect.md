---
title: Conecte sua instância
description: Conecte sua instância do Commerce usando uma chave API e uma chave privada, e especifique o espaço de dados na configuração.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '621'
ht-degree: 0%

---

# Conecte sua instância

[!DNL Payment Services] O é alimentado pelos Commerce Services e implantado como SaaS (software como um serviço). Você conecta sua instância do Commerce usando uma chave de API e uma chave privada, e especifica o espaço de dados na configuração usando o [Conector do Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html). **Você configura essa conexão apenas uma vez.**

* Se tiver *já conectou sua instância*, obtendo e usando suas credenciais de API e configurando os Commerce Services, é possível prosseguir para [configuração da sandbox de teste](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/sandbox.html).
* Se você ainda *precisa conectar sua instância*, consulte as informações neste tópico sobre [como obter credenciais da API](#obtain-api-credentials) e [configuração do Commerce Services](#configure-commerce-services).
* Se você *não tem certeza se sua instância está conectada*, navegue até **Sistema** > Serviços > **Conector do Commerce Services** e exibir os valores da chave de API pública e privada na [!UICONTROL Sandbox Keys] e [!UICONTROL Production Keys] seções e *Projeto* e *Espaço de dados* nos campos [!UICONTROL SaaS Identifier] seção. Se esses valores estiverem presentes, sua instância será conectada.

## Obter credenciais da API

Para consumir um serviço Commerce SaaS, você deve usar as chaves da API da instância (chave da API pública do Commerce e uma chave privada) para sandbox e produção, que são criadas e gerenciadas em sua [Painel Minha conta](https://account.magento.com/customer/account/login). [O par de chaves](https://docs.magento.com/user-guide/configuration/services/saas.html) O pode ser criado para uma conta do Commerce, uma para sandbox e outra para produção, embora apenas um par possa ser usado ativamente de cada vez.

>[!NOTE]
>
>Precisa de ajuda para acessar seu [!UICONTROL My Account] painel? Consulte [Criar uma conta comercial](https://docs.magento.com/user-guide/magento/magento-account-create.html).

Uma chave de API pública, uma vez criada, estará sempre disponível no Painel da minha conta. Ele pode ser copiado ou excluído conforme necessário. A chave de API privada fica visível ao criar uma chave de API pública para sandbox ou produção; ele só está disponível para copiar ou salvar da caixa de diálogo subsequente e não pode ser acessado posteriormente.

Um determinado par de chaves de API é válido para todos os Commerce Services em um ambiente. Dessa forma, se você já tiver o Commerce Services configurado para sua instância, seu par de chaves de API já estará presente no Commerce Services Connector.

Se sua chave de API for perdida, um novo par de chaves de API deverá ser [gerado](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#generate-an-api-key-and-private-key) e [aplicado](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/connect.html#configure-saas-project) à configuração do Commerce Services Connector no Admin. Se as chaves incorretas estiverem configuradas ou não existirem na configuração, uma caixa de diálogo de erro de verificação de conta será exibida nos Serviços de Pagamento notificando que a conta não foi verificada.

Consulte um [lista de Commerce Services disponíveis que usam a API](https://docs.magento.com/user-guide/system/saas.html#available-services).

Para saber como gerar uma chave de API para ambientes de sandbox ou de produção, consulte [Credenciais](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#apikey).

>[!IMPORTANT]
>É recomendável não gerar novamente um par de chaves de API *e* altere o identificador SaaS e/ou o espaço de dados em uma instância de produção ativa. Você perderá os dados da sua instância se eles forem modificados.

## Configurar serviços do Commerce

A mesma chave de API pode ser usada em instâncias, mas cada instância deve ter sua própria [Espaço de dados SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/saas.html#saasenv).

Agora que você obteve suas credenciais, é possível configurar seu projeto SaaS e o Espaço de dados Saas.

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Clique em **[!UICONTROL Configure Commerce Services]**.

   Essa opção estará visível se você ainda não tiver configurado os Commerce Services para sua conta.

   Você é direcionado para a área de configuração em Admin, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**, para configurar o Conector de serviços do Commerce.

1. Para configurar seus Commerce Services, siga as etapas descritas em [Configuração de SaaS](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#saasenv).
