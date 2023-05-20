---
title: Conectar a Solução de Abastecimento da Loja
description: Estabeleça as conexões entre o Adobe Commerce e a solução Store Fulfillment criando e autorizando uma integração do Adobe Commerce e adicionando as credenciais da conta Store Fulfillment à configuração do serviço do Adobe Commerce.
role: User, Admin
level: Intermediate
exl-id: 74c71c43-305a-4ea7-84f8-95f3ce0a9482
source-git-commit: e7493618e00e28e2de5043ae2d7e05a81110d8f1
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Conectar a Solução de Abastecimento da Loja

Conecte os Serviços de Abastecimento de Loja com o Adobe Commerce adicionando as credenciais de autenticação e os dados de conexão necessários ao Administrador do Adobe Commerce.

- **[Configurar [!DNL Commerce integration settings]](#create-an-adobe-commerce-integration)**-Crie uma integração do Adobe Commerce para os serviços de Atendimento da Loja e gere os tokens de acesso para autenticar solicitações recebidas dos servidores de Atendimento da Loja.

- **[Configurar credenciais de conta para Serviços de Atendimento de Repositório](#configure-store-fulfillment-account-credentials)**-Adicione suas credenciais para conectar o Adobe Commerce à sua conta Store Fulfillment.

>[!NOTE]
>
>Conclua a configuração da conexão e valide a conexão com êxito antes de começar o teste.

## Criar uma integração do Adobe Commerce

Para integrar o Adobe Commerce aos serviços de Atendimento da loja, crie uma integração do Commerce e gere tokens de acesso que possam ser usados para autenticar solicitações dos servidores de Atendimento da loja. Você também deve atualizar o Adobe Commerce [!UICONTROL Consumer Settings] opções para impedir `The consumer isn't authorized to access %resources.` erros de resposta em solicitações do Adobe Commerce para [!DNL Store Fulfillment] serviços.

1. No Administrador, crie a Integration for Store Fulfillment.

   - Nomear a extensão
   - Insira seu endereço de email
   - Digite a senha da sua conta de administrador

1. Configurar [!UICONTROL API Resource Access permissions] para a integração - selecione `[!UICONTROL All]`

1. Gere os tokens de acesso para autenticação salvando e ativando a integração.

1. Copie e salve os tokens de acesso em um local seguro e criptografado.

1. Trabalhe com seu Gerente de conta para concluir a configuração no lado de Atendimento da loja e autorizar a integração.

1. Ativar o Adobe Commerce [!UICONTROL Consumer Settings] opção para [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens].

   - No Administrador, acesse **[!UICONTROL Stores]** >  [!UICONTROL Configuration] > **[!UICONTROL Services]** >  **[!UICONTROL OAuth]** > **[!UICONTROL Consumer Settings]**

   - Defina o [!UICONTROL Allow OAuth Access Tokens to be used as standalone Bearer tokens] opção para **[!UICONTROL Yes]**.

>[!IMPORTANT]
>
> O token de integração é específico do ambiente. Se você restaurar o banco de dados para um ambiente com os dados de origem de um ambiente diferente, por exemplo, restaurando os dados de produção de um ambiente de preparo, exclua o `oauth_token` da exportação do banco de dados para que os detalhes do token de integração não sejam substituídos durante a operação de restauração.


## Configurar credenciais da conta de Abastecimento do Repositório

Depois de preencher o formulário de entrada, uma conta de Atendimento de Loja Walmart é criada para você. Você receberá as seguintes credenciais quando elas estiverem disponíveis:

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] (geralmente o mesmo que a configuração acima)

Essas credenciais são necessárias para configurar e usar o Atendimento da Loja.

>[!NOTE]
>
>O processo de criação de conta pode levar algum tempo para ser concluído. Enquanto você aguarda as credenciais, [revisar e definir outras configurações para a solução Store Fulfillment](service-config-settings-overview.md).

### Adicionar credenciais para se conectar ao Atendimento da Loja

1. Configurar [credenciais da conta](enable-general.md) para os ambientes de Produção e Sandbox.

1. No Administrador, acesse **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. Insira as credenciais de conta fornecidas para o **[!UICONTROL Production environment]**. Todos os campos são obrigatórios.

1. Selecionar **[!UICONTROL Save Config]**.

1. Testar a conexão selecionando **[!UICONTROL Validate Credentials]**.

>[!NOTE]
>
>Se as credenciais forem inválidas, verifique se você inseriu os valores corretos para cada ambiente e revalide. Entre em contato com o representante de conta se ainda tiver problemas de conexão.
