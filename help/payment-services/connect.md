---
title: Conecte sua instância
description: Conecte sua instância do Commerce usando uma chave API e uma chave privada, e especifique o espaço de dados na configuração.
exl-id: 5038fd31-bac5-419e-a172-66919a9b5272
source-git-commit: 9596815e31402f23b399b223f3221074331c1773
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 0%

---

# Conecte sua instância

[!DNL Payment Services] O é alimentado pelos Commerce Services e implantado como SaaS (software como um serviço). Você conecta sua instância do Commerce usando uma chave API e uma chave privada, e especifica o espaço de dados na configuração. Você configura essa conexão apenas uma vez.

Consulte [Conector do Commerce Services](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;} no guia do usuário principal para obter informações detalhadas sobre esse serviço.

## Obter credenciais da API

Para consumir um serviço Commerce SaaS, você deve usar as chaves da API da instância, que são criadas e gerenciadas em seu [Painel Minha conta](https://account.magento.com/customer/account/login){target=&quot;_blank&quot;}. Dois pares de chaves de API diferentes podem ser criados para uma conta do Commerce, um para sandbox e um para produção (pagamentos em tempo real), embora apenas um par possa ser usado ativamente de cada vez.

>[!NOTE]
>
>Precisa de ajuda para acessar seu [!UICONTROL My Account] painel? Consulte [Criar uma conta comercial](https://docs.magento.com/user-guide/magento/magento-account-create.html){target=&quot;_blank&quot;} no guia do usuário principal.

Um determinado par de chaves de API é válido para todos os Commerce Services em um ambiente, portanto, se você já tiver os Commerce Services configurados para sua instância do Commerce, seu par de chaves de API já estará presente no Administrador. Se sua chave de API privada for perdida, um novo par de chaves de API deverá ser gerado e aplicado à configuração do Commerce Services no Administrador.

Para saber como gerar uma chave de API para ambientes de sandbox ou de produção, consulte [Conector do Commerce Services](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;} no guia do usuário principal.

>[!IMPORTANT]
>
>Se você gerar novamente um par de chaves de API e alterar o Identificador SaaS, todos os Commerce Services usados por essa instância se conectarão a um armazenamento de dados diferente e seu acesso (incluindo dados armazenados anteriormente) será perdido. É recomendável não gerar novamente um par de chaves de API e alterar o Identificador de SaaS em uma instância de produção ativa.

### Chave de API de comércio e chave privada

Algumas [!DNL Adobe Commerce] e [!DNL Magento Open Source] Os recursos são implantados como SaaS (software como um serviço) — conhecidos como Commerce Services. Para usar esses serviços, você deve conectar sua instância do Commerce a esses serviços usando uma chave de API e uma chave privada, e especificar o espaço de dados desejado na [configuração](https://docs.magento.com/user-guide/configuration/services/saas.html){target=&quot;_blank&quot;}.

Ao criar uma conta comercial, identificada por uma MageID, é possível gerar uma chave de API de comércio e uma chave privada. Para usar os Commerce Services, como [!DNL Payment Services], [!DNL Product Recommendations]ou [!DNL Live Search], o titular da licença deve gerar essas chaves para passar na validação do direito. Essas chaves podem então ser enviadas para o integrador de sistemas ou a equipe de desenvolvimento que gerencia os projetos e ambientes em nome do titular da licença. Se você for um integrador de soluções, também terá direito a usar esses serviços para suas próprias necessidades. Nesse caso, o signatário do contrato do parceiro comercial deve gerar as chaves.

### Gerar uma chave de API e chave privada

1. Faça logon em sua conta do Commerce em [https://account.magento.com/customer/account/login](https://account.magento.com/customer/account/login).
1. Em **[!UICONTROL Magento]** guia , selecione **[!UICONTROL API Portal]** na barra lateral.
1. No _[!UICONTROL Environment]_selecione **[!UICONTROL Sandbox]**, em seguida **[!UICONTROL Production]**.

   >[!IMPORTANT]
   >
   >As chaves da API são necessárias para ambos os ambientes.

1. Insira um nome no _[!UICONTROL API Keys]_e clique em **[!UICONTROL Add New]**.

   Essa ação abre uma caixa de diálogo para baixar a nova chave.

   >[!IMPORTANT]
   >
   >Essa caixa de diálogo é a única oportunidade que você tem para copiar ou baixar sua chave.

1. Clique em **[!UICONTROL Download]** em seguida, clique em **[!UICONTROL Cancel]**.

   O _[!UICONTROL API Keys]_agora exibe sua chave de API.

1. Copie a chave da API e a chave privada ao selecionar ou criar um projeto SaaS.

   Consulte [SaaS](https://docs.magento.com/user-guide/system/saas.html){target=&quot;_blank&quot;} no guia do usuário principal para obter informações mais detalhadas.

A mesma chave de API pode ser usada em instâncias, mas cada instância deve ter seu próprio espaço de dados SaaS.

Quando você cria um projeto SaaS, o Commerce gera um ou mais espaços de dados SaaS, dependendo da sua licença do Commerce:

* [!DNL Adobe Commerce] - Um espaço de dados de produção; dois espaços de dados de teste
* [!DNL Magento Open Source] - Um espaço de dados de produção; sem espaços de dados de teste

### Configurar projeto SaaS

>[!NOTE]
>
>Se você não vir a variável _[!UICONTROL Commerce Services Connector]_na seção Configuração do Commerce, você deve instalar os módulos de Comércio para o Serviço do Commerce desejado, como [[!DNL Payment Services]](install.md).

Para selecionar ou criar um projeto SaaS, solicite a chave da API do Commerce ao titular da licença do Commerce da sua loja.

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. No painel esquerdo, expanda **[!UICONTROL Services]** e escolha **[!UICONTROL Commerce Services Connector]**.
1. No _[!UICONTROL API Keys]_cole seus valores principais.

   >[!IMPORTANT]
   >
   >Adicionar valores principais para ambos **[!UICONTROL sandbox]** e **[!UICONTROL production]** ambientes .

1. Clique em **[!UICONTROL Save Config]**.

   Ao salvar, se houver projetos SaaS associados à sua chave de API, esses projetos serão exibidos na variável _[!UICONTROL SaaS Project]_no campo_[!UICONTROL SaaS Identifier]_ seção.

1. Se não houver nenhum projeto SaaS, clique em **[!UICONTROL Create Project]**. Em seguida, insira um nome para o projeto SaaS no **[!UICONTROL Project Name]** campo.
1. Para usar a configuração atual do seu Commerce store, selecione a variável **[!UICONTROL SaaS Data Space]**.

>[!IMPORTANT]
>
>Se você regenerar suas chaves na seção Portal da API de Minha Conta, atualize imediatamente as chaves da API na configuração de Administração. Se você gerar novas chaves e não as atualizar no Administrador, suas extensões do SaaS não funcionarão mais e você perderá dados valiosos.

Você pode alterar os nomes clicando no botão **[!UICONTROL Rename this Project]** ou **[!UICONTROL Rename Data Space]** , respectivamente.

## Configurar serviços do Commerce

O primeiro passo na integração [!DNL Payment Services] O é configurar seus Commerce Services no Admin.

1. No _Administrador_ barra lateral, vá para **[!UICONTROL Sales]** > **[!UICONTROL [!DNL Payment Services]]**.
1. Clique em **[!UICONTROL Configure Commerce Services]**.

   Essa opção estará visível se você ainda não tiver configurado os Commerce Services para sua conta.

   Você é direcionado para a área de configuração em Admin, **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**>**[!UICONTROL Commerce Services Connector]**, para configurar o Conector de serviços do Commerce.

1. Para configurar seus Commerce Services, siga as etapas descritas em [Commerce Services](https://docs.magento.com/user-guide/system/saas.html#createsaasenv){target=&quot;_blank&quot;}.
