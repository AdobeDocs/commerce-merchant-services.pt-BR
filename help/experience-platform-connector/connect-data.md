---
title: Conectar dados do Commerce ao Adobe Experience Platform
description: Saiba como conectar seus dados de Comércio à Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
source-git-commit: 386d5e4245401695d7123a87b7dfb703f1f849e9
workflow-type: tm+mt
source-wordcount: '1307'
ht-degree: 0%

---

# Conectar dados do Commerce ao Adobe Experience Platform

Quando você instala o conector Experience Platform, duas novas páginas de configuração são exibidas na **Sistema** menu em **Serviços** no Commerce _Administrador_.

- Conector do Commerce Services
- Conector Experience Platform

Para conectar sua instância do Adobe Commerce à Adobe Experience Platform, você deve configurar ambos os conectores, começando pelo conector do Commerce Services e terminando com o conector Experience Platform.

## Atualizar o conector do Commerce Services

Se você já instalou um serviço Adobe Commerce anteriormente, provavelmente já configurou o conector Commerce Services. Caso contrário, você deverá concluir as seguintes tarefas no [Conector do Commerce Services](../landing/saas.md) página:

1. Faça logon em sua conta do Commerce para [recuperar chaves de API de produção e sandbox](../landing/saas.md#credentials).
1. Selecione um [Espaço de dados SaaS](../landing/saas.md#saas-configuration).
1. Faça logon em sua conta do Adobe para [recuperar a ID da organização](../landing/saas.md#ims-organization-optional).

Depois de configurar o conector do Commerce Services, configure o conector Experience Platform.

## Atualize o conector de Experience Platform

Nesta seção, você conecta a instância do Adobe Commerce à Adobe Experience Platform usando a ID da organização. Em seguida, você pode especificar o tipo de dados - loja ou escritório traseiro - para enviar para a borda do Experience Platform.

![Configuração do conector Experience Platform](assets/epc-config-dc.png)

## Geral

1. Faça logon na sua conta do Adobe na [Conector do Commerce Services](../landing/saas.md#organizationid) e selecione a ID da organização.

   >[!NOTE]
   >
   >Se você configurou o conector do Commerce Services anteriormente, é possível ignorar essa etapa, pois a ID da organização já foi selecionada.

1. Em Admin, acesse **Sistema** > Serviços > **Conector Experience Platform**.

1. No **Escopo** , defina o contexto como **Site**.

1. No **ID da organização** verifique a ID associada à conta do Adobe Experience Platform, conforme configurado no campo [Conector do Commerce Services](../landing/saas.md#organizationid). A ID da organização é global. Somente uma ID de organização pode ser associada por instância do Adobe Commerce.

1. (Opcional) Se você já tiver uma [AEP Web SDK (liga)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) implantado em seu site, ative a caixa de seleção e adicione o nome do SDK da Web da AEP. Caso contrário, deixe esses campos em branco e o conector de Experience Platform implante um para você.

   >[!NOTE]
   >
   >Se você especificar seu próprio SDK da Web da AEP, o conector do Experience Platform usará a ID do armazenamento de dados associada a esse SDK e não a ID do armazenamento de dados especificada nessa página (se houver).

## Coleta de dados

Nesta seção, especifique o tipo de dados que deseja enviar para a borda do Experience Platform. Há dois tipos de dados: lado do cliente e lado do servidor.

Os dados do lado do cliente são capturados na loja. Isso inclui interações do comprador, como `View Page`, `View Product`, `Add to Cart`e [lista de requisições](events.md#b2b-events) informações (para comerciantes B2B). Dados do lado do servidor ou dados do back office são dados capturados nos servidores do Commerce. Isso inclui informações sobre o status de um pedido, como se ele tivesse sido feito, cancelado, reembolsado, enviado ou concluído.

No **Coleta de dados** selecione o tipo de dados que deseja enviar para a borda do Experience Platform. Para garantir que sua instância do Adobe Commerce possa iniciar a coleta de dados, analise a [pré-requisitos](overview.md#prerequisites).

Consulte o tópico de eventos para saber mais sobre [vitrine](events.md#storefront-events) e [back office](events.md#back-office-events) eventos.

>[!NOTE]
>
>Todos os campos na **Coleta de dados** aplicar à **Site** escopo ou superior.

1. Selecionar **Eventos de vitrine** se desejar enviar dados comportamentais da vitrine.

   >[!NOTE]
   >
   >O **Eventos de vitrine** A caixa de seleção é ativada automaticamente se o SDK da Web da AEP e a ID da organização forem válidos.

1. Selecionar **Eventos do back-office** se desejar enviar informações sobre o status do pedido, como se um pedido foi feito, cancelado, reembolsado ou enviado.

   >[!NOTE]
   >
   >Se você selecionar **Eventos do back-office**, todos os dados do back office são enviados para a borda do Experience Platform. Se um comprador optar por rejeitar a coleta de dados, você deverá definir explicitamente a preferência de privacidade do comprador no Experience Platform. Isso é diferente dos eventos de loja, onde o coletor já lida com o consentimento com base nas preferências do comprador. [Saiba mais](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) sobre como definir a preferência de privacidade de um comprador no Experience Platform.

1. Para garantir atualizações de dados de eventos de back-office com base em uma programação de acordo com uma [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) você deve alterar o `Sales Orders Feed` indexar para `Update by Schedule`.

   1. No _Administrador_ barra lateral, vá para **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. Marque a caixa de seleção para a `Sales Orders Feed` indexer.

   1. Definir **[!UICONTROL Actions]** para `Update by Schedule`.

   1. Se você estiver ativando os dados do back office pela primeira vez, execute os seguintes comandos para reindexar e acionar uma ressincronização. As ressincronizações subsequentes ocorrem automaticamente, desde que o temporizador [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) O trabalho está configurado corretamente.

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

1. (Pule esta etapa se estiver usando seu próprio SDK da Web da AEP.) [Criar](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/configure.html#create) um armazenamento de dados na Adobe Experience Platform ou selecione um armazenamento de dados existente que deseja usar para a coleta.

1. (Pule esta etapa se estiver usando seu próprio SDK da Web da AEP.) No **ID do fluxo de dados** , cole a ID desse armazenamento de dados novo ou existente.

## Descrições dos campos

| Campo | Descrição |
|--- |--- |
| Escopo | Site específico no qual você deseja que as configurações sejam aplicadas. |
| ID da organização (global) | ID que pertence à organização que comprou o produto Adobe DX. Essa ID vincula sua instância do Adobe Commerce ao Adobe Experience Platform. |
| O SDK da Web da AEP já foi implantado em seu site | Marque essa caixa de seleção se tiver implantado seu próprio SDK da Web da AEP no seu site |
| AEP Web SDK Name (Global) | Se você já tiver um SDK da Web do Experience Platform implantado em seu site, especifique o nome desse SDK neste campo. Isso permite que o Coletor de eventos de vitrine e o SDK de eventos de vitrine usem seu SDK da Web do Experience Platform em vez da versão implantada pelo conector do Experience Platform. Se você não tiver um SDK da Web do Experience Platform implantado em seu site, deixe este campo em branco e o conector do Experience Platform implante um para você. |
| Eventos de vitrine | É marcado por padrão, desde que a ID da organização e a ID do armazenamento de dados sejam válidas. Os eventos de vitrine coletam dados comportamentais anônimos dos compradores durante a navegação no site. |
| Eventos de back-office | Se marcado, a carga do evento contém informações de status de pedido anônimas, como se um pedido fosse feito, cancelado, reembolsado ou enviado. |
| ID do fluxo de dados (site) | ID que permite que os dados fluam do Adobe Experience Platform para outros produtos Adobe DX. Essa ID deve ser associada a um site específico na instância específica do Adobe Commerce. Se você especificar seu próprio SDK da Web do Experience Platform, não especifique uma ID de armazenamento de dados nesse campo. O conector Experience Platform usa a ID do armazenamento de dados associada a esse SDK e ignora qualquer ID do armazenamento de dados especificada nesse campo (se houver). |

>[!NOTE]
>
>Após a integração, os dados da loja começam a fluir para a borda do Experience Platform. Os dados do back-office levam cerca de 5 minutos para serem exibidos na borda. As atualizações subsequentes estão visíveis na borda com base na programação do cron.

## Confirmar se os dados do evento são coletados

Para confirmar se os dados estão sendo coletados da loja do Commerce, use a variável [Adobe Experience Platform Debugger](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) para examinar seu site do Commerce. Depois de confirmar que os dados estão sendo coletados, você pode verificar se os dados do evento de vitrine e back-office aparecem na borda executando um query que retorna dados do [conjunto de dados criado](overview.md#prerequisites).

1. Selecionar **Queries** na navegação à esquerda do Experience Platform e clique em [!UICONTROL Create Query].

   ![Editor de consultas](assets/query-editor.png)

1. Quando o Editor de consultas for aberto, insira uma consulta que selecione dados do conjunto de dados.

   ![Criar query](assets/create-query.png)

   Por exemplo, seu query pode ser semelhante ao seguinte:

   ```sql
   SELECT * from `your_dataset_name` ORDER by TIMESTAMP DESC
   ```

1. Após a execução da query, os resultados são exibidos na variável **Resultados** , ao lado do **Console** guia . Esta exibição mostra a saída tabular do seu query.

   ![Editor de consultas](assets/query-results.png)

Neste exemplo, você vê os dados do evento da variável [`commerce.productListAdds`](events.md#addtocart), [`commerce.productViews`](events.md#productpageview), [`web.webpagedetails.pageViews`](events.md#pageview)e assim por diante. Essa exibição permite verificar se os dados do Commerce chegaram à borda.

Se os resultados não forem o que você espera, abra seu conjunto de dados e procure por importações em lotes com falha. Saiba mais sobre [solução de problemas de importações em lote](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/troubleshooting.html).
