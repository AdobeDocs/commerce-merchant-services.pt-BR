---
title: Conector do Commerce Services
description: Saiba como integrar sua instância do Adobe Commerce ou Magento Open Source a serviços usando uma chave de API e uma chave privada.
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
source-git-commit: 6d0c7c749fe90c7c204afe47446f3483d8668b53
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Alguns recursos de Adobe Commerce e Magento Open Source são fornecidos por [!DNL Commerce Services]  e implantado como SaaS (software como um serviço). Para usar esses serviços, você deve conectar [!DNL Commerce] instância usando uma chave API e uma chave privada, e especifique o espaço de dados na [configuração](https://docs.magento.com/user-guide/configuration/services/saas.html). Você só precisa configurar isso uma vez.

## Serviços disponíveis

A seguir, é exibida a lista [!DNL Commerce] recursos que você pode acessar por meio do [!DNL Commerce Services Connector]:

| Serviço | Disponibilidade |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) Com a tecnologia Adobe Sensei | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) Com a tecnologia Adobe Sensei | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | Adobe Commerce e Magento Open Source |

## Arquitetura

Em um alto nível, a variável [!DNL Commerce Services Connector] é composto pelos seguintes elementos principais:

![Arquitetura do conector do Commerce Services](assets/saas-config-sync-workflow.png)

As seções a seguir discutem cada um desses elementos com mais detalhes.

## Credenciais {#apikey}

A chave da API e a chave privada são geradas a partir do [!DNL Commerce] conta do titular da licença, identificada por um único [!DNL Commerce] ID (MageID). Para passar a validação de direito para serviços como [!DNL Product Recommendations] ou [!DNL Live Search], o titular da licença da organização do comerciante pode gerar o conjunto de chaves API, desde que a conta esteja em bom estado. As chaves podem ser compartilhadas com o integrador de sistemas ou a equipe de desenvolvimento que gerencia projetos e ambientes em nome do titular da licença. Além disso, os integradores de soluções também têm direito a usar [!DNL Commerce Services]. Se você for um integrador de soluções, o assinante da [!DNL Commerce] o contrato do parceiro deve gerar as chaves da API.

### Gerar uma chave de API e chave privada {#genapikey}

1. Faça logon no [!DNL Commerce] conta em [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}.

1. Em **Magento** guia , selecione **Portal da API** na barra lateral.

1. No _Ambiente_ selecione **Produção** ou **Sandbox**.

   >[!NOTE]
   >
   > Para [!DNL _Recommendations do produto_] e [!DNL _Live Search_], selecione **Produção**. As chaves de produção fornecem acesso aos espaços de dados de produção e não de produção. As chaves de sandbox não são usadas para esses serviços.

1. Insira um nome no _Chaves de API_ e clique em **Adicionar novo**.

   Isso abre uma caixa de diálogo para baixar a nova chave.

   ![Baixar chave privada](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > Essa é a única oportunidade que você tem para copiar ou baixar sua chave.

1. Clique em **Baixar** em seguida, clique em **Cancelar**.

   O **Chaves de API** agora exibe sua chave de API. Você precisa da chave da API e da chave privada quando [selecionar ou criar um projeto SaaS](#createsaasenv).

## Configuração de SaaS {#saasenv}

[!DNL Commerce] As instâncias devem ser configuradas com um Projeto SaaS e um Espaço de dados SaaS para que [!DNL Commerce Services] O pode enviar dados para o local certo. Um Projeto SaaS agrupa todos os Espaços de Dados SaaS. Os Espaços de Dados SaaS são usados para coletar e armazenar dados que permitem [!DNL Commerce Services] para trabalhar. Alguns desses dados podem ser exportados da [!DNL Commerce] e alguns podem ser coletados do comportamento do comprador na loja. Esses dados são mantidos para proteger o armazenamento em nuvem.

Para [!DNL Product Recommendations], o espaço de dados SaaS contém dados de catálogo e comportamento. Você pode apontar um [!DNL Commerce] para um espaço de dados SaaS por [selecionando-a](https://docs.magento.com/user-guide/configuration/services/saas.html) no [!DNL Commerce] configuração.

>[!WARNING]
>
> Use o espaço de dados SaaS de produção somente na produção [!DNL Commerce] para evitar colisões de dados. Caso contrário, você corre o risco de poluir os dados do site de produção com os dados de teste, o que causa atrasos na implantação. Por exemplo, seus dados de produto de produção podem ser substituídos por dados de preparo, por engano, como URLs de preparo.

### Selecionar ou criar um projeto SaaS {#createsaasenv}

>[!NOTE]
>
> Se você não vir a variável **[!UICONTROL Commerce Services Connector]** na seção [!DNL Commerce] você deve instalar o [!DNL Commerce] para seus [!DNL Commerce] , como [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md).

Para selecionar ou criar um projeto SaaS, solicite o [!DNL Commerce] Chave da API do [!DNL Commerce] titular da licença da sua loja.

1. No _Administrador_ barra lateral, vá para **Lojas** > _Configurações_ > **Configuração**.

1. No painel esquerdo, expanda **Serviços** e escolha **Conector do Commerce Services**.

1. No _Chaves de API_ cole seus valores principais para a seção **Chave da API de produção** e **Chave privada de produção**.

   As chaves privadas devem incluir `----BEGIN PRIVATE KEY---` no início da chave e `----END PRIVATE KEY----` no final da chave privada.

1. Clique em **Salvar configuração**.

Qualquer projeto SaaS associado à sua chave de API é exibido na variável **Projeto SaaS** campo.

1. Se não houver nenhum projeto SaaS, clique em **Criar projeto**. Em seguida, na **Nome do projeto** , insira um nome para o projeto SaaS.

   Ao criar um projeto SaaS, [!DNL Commerce] gera um ou mais espaços de dados SaaS dependendo de seu [!DNL Commerce] licença:
   - Adobe Commerce - um espaço de dados de produção; dois espaços de dados de teste
   - Magento Open Source - Um espaço de dados de produção; sem espaços de dados de teste

1. Selecione o **Espaço de dados SaaS** para usar na configuração atual de seu [!DNL Commerce] armazenar.

>[!WARNING]
>
> Se você gerar novas chaves na seção Portal da API de Minha Conta, atualize imediatamente as chaves da API na configuração de Administração. Se você gerar novas chaves e não as atualizar no Administrador, suas extensões do SaaS não funcionarão mais e você perderá dados valiosos.

Para alterar os nomes do projeto SaaS ou do espaço de dados, clique no botão **Renomear este projeto** ou **Renomear espaço de dados** respectivamente.

## Sincronização de catálogo

Quando o [!DNL Commerce] instância se conecta com êxito ao [!DNL Commerce Services], o processo de sincronização de catálogo exporta dados do produto do seu [!DNL Commerce] para [!DNL Commerce Services]. [Saiba mais](catalog-sync.md) sobre o processo de sincronização de catálogo.
