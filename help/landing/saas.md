---
title: Conector do Commerce Services
description: Saiba como integrar sua instância do Adobe Commerce ou Magento Open Source a serviços usando chaves de API de produção e de sandbox.
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
source-git-commit: e7b12a80d6c4ec18ec784fd674363a728ee73a67
workflow-type: tm+mt
source-wordcount: '850'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Alguns recursos de Adobe Commerce e Magento Open Source são fornecidos por [!DNL Commerce Services]  e implantado como SaaS (software como um serviço). Para usar esses serviços, você deve conectar [!DNL Commerce] usando chaves de API de sandbox e de produção, e especifique o espaço de dados na [configuração](https://docs.magento.com/user-guide/configuration/services/saas.html). Você só precisa configurar isso uma vez.

## Serviços disponíveis {#availableservices}

A seguir, é exibida a lista [!DNL Commerce] recursos que você pode acessar por meio do [!DNL Commerce Services Connector]:

| Serviço | Disponibilidade |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) Com a tecnologia Adobe Sensei | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) Com a tecnologia Adobe Sensei | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | Adobe Commerce e Magento Open Source |
| [[!DNL Channel Manager]](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/intro-to-channel-manager/overview.html) | Adobe Commerce e Magento Open Source |
| [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html) | Adobe Commerce |
| [Conector Experience Platform](/help/experience-platform-connector/overview.md) | Adobe Commerce |

## Arquitetura

Em um alto nível, a variável [!DNL Commerce Services Connector] é composto pelos seguintes elementos principais:

![Arquitetura do conector do Commerce Services](assets/saas-config-sync-workflow.png)

As seções a seguir discutem cada um desses elementos com mais detalhes.

## Credenciais {#apikey}

As chaves da API de produção e de sandbox são geradas a partir do [!DNL Commerce] conta do titular da licença, identificada por um único [!DNL Commerce] ID (MageID). Para passar a validação de direito para serviços como [!DNL Product Recommendations] ou [!DNL Live Search], o titular da licença da organização do comerciante pode gerar o conjunto de chaves API, desde que a conta esteja em bom estado. As chaves podem ser compartilhadas com o integrador de sistemas ou a equipe de desenvolvimento que gerencia projetos e ambientes em nome do titular da licença. Além disso, os integradores de soluções também têm direito a usar [!DNL Commerce Services]. Se você for um integrador de soluções, o assinante da [!DNL Commerce] o contrato do parceiro deve gerar as chaves da API.

### Gerar as chaves de API de produção e de sandbox {#genapikey}

1. Faça logon no [!DNL Commerce] conta em [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}.

1. Em **Magento** guia , selecione **Portal da API** na barra lateral.

1. No _Ambiente_ selecione **Produção** ou **Sandbox**.

1. Insira um nome no _Chaves de API_ e clique em **Adicionar novo**.

   Isso abre uma caixa de diálogo para baixar a nova chave.

   ![Baixar chave privada](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > Essa é a única oportunidade que você tem para copiar ou baixar suas chaves.

1. Clique em **Baixar** em seguida, clique em **Cancelar**.

1. Repita as etapas acima para cada ambiente (produção e sandbox).

   O **Chaves de API** agora exibe suas chaves de API. Você precisa das chaves de produção e de sandbox quando [selecionar ou criar um projeto SaaS](#createsaasenv).

## Configuração de SaaS {#saasenv}

[!DNL Commerce] As instâncias devem ser configuradas com um Projeto SaaS e um Espaço de dados SaaS para que [!DNL Commerce Services] O pode enviar dados para o local certo. Um Projeto SaaS agrupa todos os Espaços de Dados SaaS. Os Espaços de Dados SaaS são usados para coletar e armazenar dados que permitem [!DNL Commerce Services] para trabalhar. Alguns desses dados podem ser exportados da [!DNL Commerce] e alguns podem ser coletados do comportamento do comprador na loja. Esses dados são mantidos para proteger o armazenamento em nuvem.

Para [!DNL Product Recommendations], o espaço de dados SaaS contém dados de catálogo e comportamento. Você pode apontar um [!DNL Commerce] para um espaço de dados SaaS por [selecionando-a](https://docs.magento.com/user-guide/configuration/services/saas.html) no [!DNL Commerce] configuração.

>[!WARNING]
>
> Use o espaço de dados SaaS de produção somente na produção [!DNL Commerce] para evitar colisões de dados. Caso contrário, você corre o risco de poluir os dados do site de produção com os dados de teste, o que causa atrasos na implantação. Por exemplo, seus dados de produto de produção podem ser substituídos por dados de preparo, por engano, como URLs de preparo.

### Selecionar ou criar um projeto SaaS {#createsaasenv}

>[!NOTE]
>
> Se você não vir a variável **[!UICONTROL Commerce Services Connector]** na seção [!DNL Commerce] você deve instalar o [!DNL Commerce] para seus [[!DNL Commerce] service](#availableservices).

Para selecionar ou criar um projeto SaaS, solicite o [!DNL Commerce] Chave da API do [!DNL Commerce] titular da licença da sua loja.

1. No _Administrador_ barra lateral, vá para **Sistema** > Serviços > **Conector do Commerce Services**.

1. No _Chaves da API de sandbox_ e _Chaves da API de produção_ , cole seus valores principais.

   As chaves privadas devem incluir `----BEGIN PRIVATE KEY---` no início da chave e `----END PRIVATE KEY----` no final da chave privada.

1. Clique em **Salvar**.

Qualquer projeto SaaS associado às suas chaves será exibido na **Projeto** no campo **Identificador SaaS** seção.

1. Se não houver nenhum projeto SaaS, clique em **Criar projeto**. Em seguida, na **Projeto** , insira um nome para o projeto SaaS.

   Ao criar um projeto SaaS, [!DNL Commerce] gera um ou mais espaços de dados SaaS dependendo de seu [!DNL Commerce] licença:
   - Adobe Commerce - um espaço de dados de produção; dois espaços de dados de teste
   - Magento Open Source - Um espaço de dados de produção; sem espaços de dados de teste

1. Selecione o **Espaço de dados** para usar na configuração atual de seu [!DNL Commerce] armazenar.

>[!WARNING]
>
> Se você gerar novas chaves na seção Portal da API de Minha Conta, atualize imediatamente as chaves da API na configuração de Administração. Se você gerar novas chaves e não as atualizar no Administrador, suas extensões do SaaS não funcionarão mais e você perderá dados valiosos.

Para alterar os nomes do projeto SaaS ou do espaço de dados, clique em **Renomear**.

## Organização IMS (opcional) {#organizationid}

Para conectar sua instância do Adobe Commerce à Adobe Experience Platform, faça logon em sua conta do Adobe usando a Adobe ID. Após fazer logon, a organização IMS associada à sua conta do Adobe é exibida nesta seção.

## Sincronização de catálogo

Quando o [!DNL Commerce] instância se conecta com êxito ao [!DNL Commerce Services], o processo de sincronização de catálogo exporta dados do produto do seu [!DNL Commerce] para [!DNL Commerce Services]. [Saiba mais](catalog-sync.md) sobre o processo de sincronização de catálogo.
