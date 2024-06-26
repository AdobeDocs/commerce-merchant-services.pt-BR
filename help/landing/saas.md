---
title: Commerce Services Connector
description: Saiba como integrar sua instância do Adobe Commerce ou Magento Open Source a serviços usando chaves de API de produção e sandbox.
exl-id: 28027a83-449b-4b96-b926-a7bfbfd883d8
feature: Services, Saas
role: Admin, User
source-git-commit: 3eb873c84edb56d2fc399c72296f2b545a78064e
workflow-type: tm+mt
source-wordcount: '1051'
ht-degree: 0%

---

# [!DNL Commerce Services Connector]

Alguns recursos do Adobe Commerce e do Magento Open Source são alimentados pela [!DNL Commerce Services] e implantado como SaaS (software como um serviço). Para usar esses serviços, você deve conectar seu [!DNL Commerce] usando chaves de API de sandbox e produção e especifique o espaço de dados na variável [configuração](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html). Você só precisa configurar isso uma vez.

## Serviços disponíveis {#availableservices}

A lista a seguir mostra os [!DNL Commerce] recursos que você pode acessar por meio da [!DNL Commerce Services Connector]:

| Serviço | Disponibilidade |
| ---|--- |
| [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) ativado por Adobe Sensei | Adobe Commerce |
| [[!DNL Live Search]](/help/live-search/overview.md) ativado por Adobe Sensei | Adobe Commerce |
| [[!DNL Payment Services]](/help/payment-services/overview.md) | ADOBE COMMERCE e MAGENTO OPEN SOURCE |
| [[!DNL Channel Manager]](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/intro-to-channel-manager/overview.html) | ADOBE COMMERCE e MAGENTO OPEN SOURCE |
| [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/intro.html) | Adobe Commerce |
| [[!DNL Catalog Service]](/help/catalog-service/overview.md) | Adobe Commerce |
| [[!DNL Data Connection]](/help/data-connection/overview.md) | Adobe Commerce |

## Arquitetura

A um nível elevado, a [!DNL Commerce Services Connector] O é composto pelos seguintes elementos principais:

![Arquitetura do Commerce Services Connector](assets/saas-config-sync-workflow.png)

As seções a seguir discutem cada um desses elementos com mais detalhes.

## Credenciais {#apikey}

As chaves de API de sandbox e produção são geradas a partir do [!DNL Commerce] conta do [proprietário da licença](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/start/onboarding) que é identificado por um único [!DNL Commerce] ID (MageID). Para passar na validação de direitos para serviços como [!DNL Product Recommendations] ou [!DNL Live Search], o proprietário da licença da organização do comerciante pode gerar o conjunto de chaves de API, desde que a conta esteja em bom estado.

As chaves podem ser compartilhadas com base no &quot;conhecimento necessário&quot; com o integrador de sistemas ou a equipe de desenvolvimento que gerencia projetos e ambientes em nome do titular da licença. Desenvolvedores que receberam permissão [!DNL Shared Access] pelo titular da licença não pode gerar as chaves em seu nome, mesmo que a organização do comerciante esteja presente no [!DNL Switch Accounts] na conta deles.

Além disso, os integradores de soluções também estão autorizados a usar o [!DNL Commerce Services]. Se você for um integrador de soluções, o signatário da [!DNL Commerce] o contrato de parceiro deve gerar as chaves de API.

>[!NOTE]
>
>O proprietário da licença normalmente é o contato principal na conta da Adobe Commerce e nem sempre é o mesmo Proprietário do projeto Adobe Commerce na infraestrutura em nuvem.

### Gerar as chaves de API de produção e sandbox {#genapikey}

1. Faça logon no [!DNL Commerce] conta em [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}.

1. No **Magento** selecione **Portal da API** na barra lateral.

1. No _Ambiente_ selecione **Produção** ou **Sandbox**.

1. Insira um nome no campo _Chaves de API_ e clique em **Adicionar novo**.

   Isso abre uma caixa de diálogo para baixar a nova chave.

   ![Baixar chave privada](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > Essa é a única oportunidade que você tem para copiar ou baixar suas chaves.

1. Clique em **Baixar** e clique em **Cancelar**.

1. Repita as etapas acima para cada ambiente (produção e sandbox).

   A variável **Chaves de API** A seção agora exibe suas chaves de API (Públicas). Você precisa das chaves de produção e de sandbox (Público+Privado) ao [selecionar ou criar um projeto SaaS](#createsaasenv).

## Configuração SaaS {#saasenv}

[!DNL Commerce] As instâncias devem ser configuradas com um projeto SaaS e um espaço de dados SaaS para que [!DNL Commerce Services] O pode enviar dados para o local correto. Um projeto SaaS agrupa todos os espaços de dados SaaS. Os Espaços de dados SaaS são usados para coletar e armazenar dados que permitem [!DNL Commerce Services] para trabalhar. Alguns desses dados podem ser exportados do [!DNL Commerce] e alguns podem ser coletados do comportamento do comprador na loja. Esses dados são mantidos para proteger o armazenamento na nuvem.

Para [!DNL Product Recommendations], o espaço de dados SaaS contém dados de catálogo e comportamentais. Você pode apontar um [!DNL Commerce] para um espaço de dados SaaS por [selecionando](https://docs.magento.com/user-guide/configuration/services/saas.html) no [!DNL Commerce] configuração.

>[!WARNING]
>
> Use o espaço de dados SaaS de produção somente na produção [!DNL Commerce] para evitar colisões de dados. Caso contrário, você corre o risco de poluir os dados do site de produção com dados de teste, o que causa atrasos de implantação. Por exemplo, os dados do produto de produção podem ser substituídos por engano dos dados de preparo, como URLs de preparo.

### Selecionar ou criar um projeto SaaS {#createsaasenv}

Para selecionar ou criar um projeto SaaS, solicite a [!DNL Commerce] Chave de API do [!DNL Commerce] proprietário da licença da sua loja:

>[!NOTE]
>
> Se você não vir a variável **[!UICONTROL Commerce Services Connector]** na seção [!DNL Commerce] , você deve instalar o [!DNL Commerce] módulos para o que desejar [[!DNL Commerce] serviço](#availableservices).

1. No _Admin_ barra lateral, vá para **Sistema** > Serviços > **Commerce Services Connector**.

   Se você não vir a variável **[!UICONTROL Commerce Services Connector]** na seção [!DNL Commerce] , instale o [!DNL Commerce] módulos para o que desejar [[!DNL Commerce] serviço](#availableservices). Além disso, verifique se o plug-in `magento/module-services-id` pacote está instalado.

1. No _Chaves da API de sandbox_ e _Chaves de API de produção_ cole os valores principais.

   As chaves privadas devem incluir `----BEGIN PRIVATE KEY---` no início da tecla e `----END PRIVATE KEY----` ao final da chave privada.

1. Clique em **Salvar**.

Qualquer projeto SaaS associado às suas chaves será exibido na **Projeto** no campo **Identificador SaaS** seção.

1. Se não existirem projetos SaaS, clique em **Criar projeto**. Em seguida, no **Projeto** insira um nome para o projeto SaaS.

   Ao criar um projeto SaaS, [!DNL Commerce] gera um ou mais espaços de dados SaaS dependendo do [!DNL Commerce] licença:
   - Adobe Commerce - Um espaço de dados de produção; dois espaços de dados de teste somente. Em projetos do Cloud Pro com vários ambientes de preparo, você pode solicitar espaços de dados de teste adicionais para cada ambiente de preparo ao [enviar uma solicitação de suporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket).
   - Magento Open Source - Um espaço de dados de produção; sem espaços de dados de teste

1. Selecione o **Espaço de dados** para usar com a configuração atual do seu [!DNL Commerce] armazenamento.

>[!NOTE]
>
>Se você tiver instâncias separadas para integrar aos Serviços da Commerce, [enviar um tíquete de suporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) para solicitar um novo Projeto SaaS para cada instância adicional. Depois que o suporte tiver criado o projeto SaaS, configure a integração dos Serviços da Commerce para a instância usando a mesma chave de API e selecionando o novo projeto SaaS para o espaço de dados.

>[!WARNING]
>
> Se você gerar novas chaves na seção Portal de API de Minha conta, atualize imediatamente as chaves de API na configuração de Administrador. Se você gerar novas chaves e não atualizá-las no Admin, suas extensões SaaS não funcionarão mais e você perderá dados valiosos.

Para alterar os nomes do projeto SaaS ou do espaço de dados, clique em **Renomear** ao lado de qualquer um. Alterar o nome não afeta seu serviço porque o nome é apenas um rótulo que ajuda a identificar e diferenciar entre projetos e espaços de dados.

## Organização IMS (opcional) {#organizationid}

Para conectar sua instância do Adobe Commerce à Adobe Experience Platform, faça logon em sua conta Adobe usando sua Adobe ID. Após fazer logon, a organização IMS associada à sua conta Adobe é exibida nesta seção.

## Exportação de dados SaaS

Quando o [!DNL Commerce] instância se conecta com sucesso ao [!DNL Commerce Services], o processo de exportação de dados SaaS exporta dados do Commerce do seu [!DNL Commerce] servidor para [!DNL Commerce SaaS Services] para que possa ser sincronizado com os serviços conectados da Commerce. No Admin, é possível verificar o status da sincronização usando o [Painel de gerenciamento de dados](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Para obter detalhes, consulte [Guia de exportação de dados SaaS](../data-export/overview.md).
