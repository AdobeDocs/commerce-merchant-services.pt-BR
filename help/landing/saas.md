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

Alguns recursos do Adobe Commerce e do Magento Open Source são fornecidos pelo [!DNL Commerce Services] e implantados como SaaS (software como um serviço). Para usar esses serviços, você deve conectar sua instância do [!DNL Commerce] usando chaves de API de sandbox e produção e especificar o espaço de dados na [configuração](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html). Você só precisa configurar isso uma vez.

## Serviços disponíveis {#availableservices}

Veja a seguir uma lista dos recursos do [!DNL Commerce] que você pode acessar por meio do [!DNL Commerce Services Connector]:

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

Em um nível superior, o [!DNL Commerce Services Connector] é composto dos seguintes elementos principais:

![Arquitetura do Commerce Services Connector](assets/saas-config-sync-workflow.png)

As seções a seguir discutem cada um desses elementos com mais detalhes.

## Credenciais {#apikey}

As chaves de API de sandbox e produção são geradas a partir da conta [!DNL Commerce] do [proprietário da licença](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/start/onboarding), que é identificada por uma ID [!DNL Commerce] exclusiva (MageID). Para passar na validação de direito para serviços como [!DNL Product Recommendations] ou [!DNL Live Search], o proprietário da licença para a organização do comerciante pode gerar o conjunto de chaves de API, desde que a conta esteja em bom estado.

As chaves podem ser compartilhadas com base no &quot;conhecimento necessário&quot; com o integrador de sistemas ou a equipe de desenvolvimento que gerencia projetos e ambientes em nome do titular da licença. Os desenvolvedores aos quais o proprietário da licença concedeu [!DNL Shared Access] não podem gerar as chaves em seu nome, mesmo que a organização do comerciante esteja presente na lista suspensa [!DNL Switch Accounts] em sua conta.

Além disso, os integradores de soluções também podem usar o [!DNL Commerce Services]. Se você for um integrador de soluções, o signatário do contrato de parceiro [!DNL Commerce] deve gerar as chaves de API.

>[!NOTE]
>
>O proprietário da licença normalmente é o contato principal na conta da Adobe Commerce e nem sempre é o mesmo Proprietário do projeto Adobe Commerce na infraestrutura em nuvem.

### Gerar as chaves de API de produção e sandbox {#genapikey}

1. Faça logon em sua conta do [!DNL Commerce] em [https://account.magento.com](https://account.magento.com/){:target=&quot;_blank&quot;}.

1. Na guia **Magento**, selecione **Portal de API** na barra lateral.

1. No menu _Ambiente_, selecione **Produção** ou **Sandbox**.

1. Insira um nome na seção _Chaves de API_ e clique em **Adicionar novo**.

   Isso abre uma caixa de diálogo para baixar a nova chave.

   ![Baixar chave privada](assets/download-api-private-key.png)

   >[!WARNING]
   >
   > Essa é a única oportunidade que você tem para copiar ou baixar suas chaves.

1. Clique em **Baixar** e em **Cancelar**.

1. Repita as etapas acima para cada ambiente (produção e sandbox).

   A seção **Chaves de API** agora exibe suas chaves de API (Públicas). Você precisa das chaves de produção e de sandbox (Público+Privado) ao [selecionar ou criar um projeto SaaS](#createsaasenv).

## Configuração SaaS {#saasenv}

[!DNL Commerce] instâncias devem ser configuradas com um projeto SaaS e um espaço de dados SaaS para que [!DNL Commerce Services] possa enviar os dados para o local correto. Um projeto SaaS agrupa todos os espaços de dados SaaS. Os Espaços de dados SaaS são usados para coletar e armazenar dados que permitem que o [!DNL Commerce Services] funcione. Alguns desses dados podem ser exportados da instância [!DNL Commerce] e outros podem ser coletados do comportamento do comprador na loja. Esses dados são mantidos para proteger o armazenamento na nuvem.

Para [!DNL Product Recommendations], o espaço de dados SaaS contém dados de catálogo e comportamentais. Você pode apontar uma instância [!DNL Commerce] para um espaço de dados SaaS ao [selecioná-la](https://docs.magento.com/user-guide/configuration/services/saas.html) na configuração [!DNL Commerce].

>[!WARNING]
>
> Use o espaço de dados SaaS de produção somente na instalação da produção [!DNL Commerce] para evitar colisões de dados. Caso contrário, você corre o risco de poluir os dados do site de produção com dados de teste, o que causa atrasos de implantação. Por exemplo, os dados do produto de produção podem ser substituídos por engano dos dados de preparo, como URLs de preparo.

### Selecionar ou criar um projeto SaaS {#createsaasenv}

Para selecionar ou criar um projeto SaaS, solicite a chave de API [!DNL Commerce] ao proprietário da licença [!DNL Commerce] da sua loja:

>[!NOTE]
>
> Se você não vir a seção **[!UICONTROL Commerce Services Connector]** na configuração [!DNL Commerce], instale os módulos [!DNL Commerce] do [[!DNL Commerce] serviço](#availableservices) desejado.

1. Na barra lateral _Admin_, vá para **System** > Services > **Commerce Services Connector**.

   Se você não vir a seção **[!UICONTROL Commerce Services Connector]** na configuração [!DNL Commerce], instale os módulos [!DNL Commerce] do [[!DNL Commerce] serviço](#availableservices) desejado. Além disso, verifique se o pacote `magento/module-services-id` está instalado.

1. Nas seções _Chaves de API de sandbox_ e _Chaves de API de produção_, cole os valores de chave.

   As chaves privadas devem incluir `----BEGIN PRIVATE KEY---` no início da chave e `----END PRIVATE KEY----` no final da chave privada.

1. Clique em **Salvar**.

Qualquer projeto SaaS associado às suas chaves é exibido no campo **Projeto** da seção **Identificador SaaS**.

1. Se não existirem projetos SaaS, clique em **Criar projeto**. Em seguida, no campo **Projeto**, digite um nome para o projeto SaaS.

   Ao criar um projeto SaaS, o [!DNL Commerce] gera um ou mais espaços de dados SaaS dependendo da sua licença do [!DNL Commerce]:
   - Adobe Commerce - Um espaço de dados de produção; dois espaços de dados de teste somente. Em projetos do Cloud Pro com vários ambientes de preparo, você pode solicitar espaços de dados de teste adicionais para cada ambiente de preparo [enviando uma solicitação de suporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket).
   - Magento Open Source - Um espaço de dados de produção; sem espaços de dados de teste

1. Selecione o **Espaço de Dados** a ser usado para a configuração atual do seu repositório [!DNL Commerce].

>[!NOTE]
>
>Se você tiver instâncias separadas para integrar com os Serviços Commerce, [envie um tíquete de Suporte](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) para solicitar um novo Projeto SaaS para cada instância adicional. Depois que o suporte tiver criado o projeto SaaS, configure a integração dos Serviços da Commerce para a instância usando a mesma chave de API e selecionando o novo projeto SaaS para o espaço de dados.

>[!WARNING]
>
> Se você gerar novas chaves na seção Portal de API de Minha conta, atualize imediatamente as chaves de API na configuração de Administrador. Se você gerar novas chaves e não atualizá-las no Admin, suas extensões SaaS não funcionarão mais e você perderá dados valiosos.

Para alterar os nomes do projeto SaaS ou do espaço de dados, clique em **Renomear**. Alterar o nome não afeta seu serviço porque o nome é apenas um rótulo que ajuda a identificar e diferenciar entre projetos e espaços de dados.

## Organização IMS (opcional) {#organizationid}

Para conectar sua instância do Adobe Commerce à Adobe Experience Platform, faça logon em sua conta Adobe usando sua Adobe ID. Após fazer logon, a organização IMS associada à sua conta Adobe é exibida nesta seção.

## Exportação de dados SaaS

Quando a instância do [!DNL Commerce] é conectada com êxito ao [!DNL Commerce Services], o processo de exportação de dados SaaS exporta os dados do Commerce do servidor [!DNL Commerce] para o [!DNL Commerce SaaS Services] para que ele possa ser sincronizado com os Commerce Services conectados. No Administrador, você pode verificar o status da sincronização usando o [painel de Gerenciamento de Dados](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Para obter detalhes, consulte o [Guia de Exportação de Dados SaaS](../data-export/overview.md).
