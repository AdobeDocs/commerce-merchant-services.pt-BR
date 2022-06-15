---
title: Conecte a solução de preenchimento da loja
description: Estabeleça as conexões entre o Adobe Commerce e a solução de fornecimento de armazenamento, criando e autorizando uma integração do Adobe Commerce e adicionando as credenciais da conta de fornecimento de armazenamento à configuração do serviço Adobe Commerce.
role: User, Admin
level: Intermediate
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Conecte a solução de preenchimento da loja

Estabeleça a conexão entre os serviços Adobe Commerce e Store Fulfillment configurando as credenciais de autenticação necessárias e os dados de conexão do Administrador.

- **[Configurar [!DNL Commerce integration settings]](#create-the-commerce-integration)**-Crie uma integração do Adobe Commerce para os serviços de Atendimento da loja e gere os tokens de acesso para autenticar solicitações recebidas dos servidores de Atendimento da loja.

- **[Configurar as credenciais da conta para os serviços de fornecimento de armazenamento](#configure-store-fulfillment-account-credentials)**-Adicione suas credenciais para conectar o Adobe Commerce à conta de Atendimento da loja.

>[!NOTE]
>
>Conclua a configuração da conexão e valide a conexão com êxito antes de começar a testar.

## Criar uma integração com o Adobe Commerce

Para integrar o Adobe Commerce aos serviços de Entrega da loja, crie uma integração do Commerce e gere tokens de acesso que possam ser usados para autenticar solicitações de servidores de Entrega da loja.

1. Em Admin, crie a Integração para o Atendimento da loja.

   - Dê um nome para a extensão
   - Insira seu endereço de email
   - Digite a senha da conta do administrador

1. Configurar [!UICONTROL API Resource Access permissions] para a integração — selecione `[!UICONTROL All]`

1. Gere os tokens de acesso para autenticação salvando e ativando a integração.

1. Copie e salve os tokens de acesso em um local seguro e criptografado.

1. Trabalhe com seu Gerente de conta para concluir a configuração no lado do Atendimento da loja e autorizar a integração.


>[!NOTE]
>
>Para obter instruções detalhadas, consulte [Integrações](https://docs.magento.com/user-guide/system/integrations.html) no _Guia do usuário do Adobe Commerce_.

## Configurar as credenciais da conta de preenchimento da loja

Após preencher o formulário de entrada, uma conta de Atendimento da loja Walmart é criada para você. Você receberá as seguintes credenciais quando estiverem disponíveis:

- [!DNL Merchant ID]
- [!DNL Consumer ID]
- [!DNL Consumer Secret]
- [!DNL API Server URL]
- [!DNL Token Auth Server URL] (geralmente o mesmo que a configuração acima)

Essas credenciais são necessárias para configurar e usar o Cumprimento da loja.

>[!NOTE]
>
>O processo de criação da conta pode levar algum tempo para ser concluído. Enquanto espera por credenciais, [revise e configure outras configurações para a solução Store Fulfillment](service-config-settings-overview.md).

### Adicionar credenciais para se conectar ao Cumprimento da Loja

1. Configurar [credenciais da conta](enable-general.md) para os ambientes de produção e sandbox.

1. Em Admin, acesse **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**

1. Insira as credenciais de conta fornecidas para a **[!UICONTROL Production environment]**. Todos os campos são obrigatórios.

1. Selecionar **[!UICONTROL Save Config]**.

1. Teste a conexão selecionando **[!UICONTROL Validate Credentials]**.

>[!NOTE]
>
>Se as credenciais forem inválidas, verifique se você inseriu os valores corretos para cada ambiente e revalide. Entre em contato com seu representante de conta caso ainda tenha problemas para se conectar.








