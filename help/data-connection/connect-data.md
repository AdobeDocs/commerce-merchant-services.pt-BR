---
title: Conectar dados do Commerce ao Adobe Experience Platform
description: Saiba como conectar os dados do Commerce à Adobe Experience Platform.
exl-id: 87898283-545c-4324-b1ab-eec5e26a303a
feature: Personalization, Integration, Configuration
source-git-commit: 89607d22ba8e69e0c98fce97e041022e33d01c07
workflow-type: tm+mt
source-wordcount: '2486'
ht-degree: 0%

---

# Conectar dados do Commerce ao Adobe Experience Platform

Ao instalar o [!DNL Data Connection] extensão do, duas novas páginas de configuração são exibidas na tag **Sistema** menu em **Serviços** no Commerce _Admin_.

- Conector dos Commerce Services
- [!DNL Data Connection]

Para conectar sua instância do Adobe Commerce à Adobe Experience Platform, você deve configurar ambos os conectores, começando com o conector do Commerce Services e terminando com o [!DNL Data Connection] extensão.

## Configurar o conector de serviços do Commerce

Se você tiver instalado anteriormente um serviço do Adobe Commerce, provavelmente já terá configurado o conector de Serviços do Commerce. Caso contrário, você deverá concluir as seguintes tarefas no [Conector de serviços do Commerce](../landing/saas.md) página:

1. Faça logon na sua conta da Commerce para [recuperar as chaves de API de produção e sandbox](../landing/saas.md#credentials).
1. Selecione um [Espaço de dados SaaS](../landing/saas.md#saas-configuration).
1. Faça logon na sua conta Adobe para [recuperar a ID da organização](../landing/saas.md#ims-organization-optional).

Após configurar o conector de Serviços da Commerce, configure o [!DNL Data Connection] extensão.

## Configure o [!DNL Data Connection] extensão

Nesta seção, você aprenderá a configurar o [!DNL Data Connection] extensão.

### Adicionar conta de serviço e detalhes da credencial

Se você planeja coletar e enviar [dados históricos do pedido](#send-historical-order-data) ou [dados do perfil do cliente](#send-customer-profile-data), você deve adicionar a conta de serviço e os detalhes da credencial. Além disso, se você estiver configurando o [Audience Activation](https://experienceleague.adobe.com/docs/commerce-admin/customers/audience-activation.html) extensão, você deve concluir essas etapas.

Se você estiver coletando e enviando apenas dados da loja ou do back office, pule para a [geral](#general) seção.

#### Etapa 1: criar um projeto no Console do Adobe Developer

Crie um projeto no Console do Adobe Developer que autentica o Commerce para que ele possa fazer chamadas de API de Experience Platform.

Para criar o projeto, siga as etapas descritas na seção [Autenticar e acessar APIs de Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html) tutorial.

À medida que você avança pelo tutorial, certifique-se de que seu projeto tenha o seguinte:

- Acesso aos seguintes [perfis de produto](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#select-product-profiles): **Acesso total à produção padrão** e **AEP Todos os acessos padrão**.
- O correto [funções e permissões estão configuradas](https://experienceleague.adobe.com/docs/experience-platform/landing/platform-apis/api-authentication.html#assign-api-to-a-role).
- Se você decidir usar JSON Web Tokens (JWT) como método de autenticação de servidor para servidor, também deverá carregar uma chave privada.

O resultado dessa etapa cria um arquivo de configuração que você usa na próxima etapa.

#### Etapa 2: baixar arquivo de configuração

Baixe o [arquivo de configuração do espaço de trabalho](https://developer.adobe.com/commerce/extensibility/events/project-setup/#download-the-workspace-configuration-file). Copie e cole o conteúdo desse arquivo na **Detalhes da Conta de Serviço/Credencial** página do Administrador do Commerce.

1. No Administrador do Commerce, navegue até **Lojas** > Configurações > **Configuração** > **Serviços** > **[!DNL Data Connection]**.

1. Selecione o método de autorização de servidor para servidor que você implementou na **Tipo de autorização do Adobe Developer** menu. O Adobe recomenda usar o OAuth. O JWT foi descontinuado. [Saiba mais](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration/).

1. (Somente JWT) Copie e cole o conteúdo do `private.key` arquivo na **Segredo do cliente** campo. Use o comando a seguir para copiar o conteúdo.

   ```bash
   cat config/private.key | pbcopy
   ```

   Consulte [Autenticação da conta de serviço (JWT)](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/) para obter mais informações sobre o `private.key` arquivo.

1. Copie o conteúdo de `<workspace-name>.json` arquivo na **Detalhes da Conta de Serviço/Credencial** campo.

   ![[!DNL Data Connection] Configuração de administração](./assets/epc-admin-config.png){width="700" zoomable="yes"}

1. Clique em **Salvar configuração**.

### Geral

1. No Administrador, acesse **Sistema** > Serviços > **[!DNL Data Connection]**.

1. No **Configurações** em **Geral**, verifique a ID associada à sua conta do Adobe Experience Platform, conforme configurado na [Conector dos Commerce Services](../landing/saas.md#organizationid). A ID da organização é global. Somente uma ID de organização pode ser associada por instância do Adobe Commerce.

1. No **Escopo** , defina o contexto como **Site**.

1. (Opcional) Se você já tiver um [AEP Web SDK (liga)](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) implantado no site, ative a caixa de seleção e adicione o nome do AEP Web SDK. Caso contrário, deixe esses campos em branco e [!DNL Data Connection] A extensão implanta um para você.

   >[!NOTE]
   >
   >Se você especificar seu próprio AEP Web SDK, a variável [!DNL Data Connection] A extensão do usa a ID de sequência de dados associada a esse SDK e não a ID de sequência de dados especificada nessa página (se houver).

### Coleta de dados

Nesta seção, você especifica o tipo de dados que deseja coletar e enviar para a borda do Experience Platform. Há três tipos de dados:

- **Comportamento** (dados do lado do cliente) são dados capturados na loja. Isso inclui interações do comprador, como `View Page`, `View Product`, `Add to Cart`, e [lista de requisições](events.md#b2b-events) informações (para os comerciantes B2B).

- **Back office** (dados do lado do servidor) são dados capturados nos servidores da Commerce. Isso inclui informações sobre o status de um pedido, como se um pedido tivesse sido feito, cancelado, reembolsado, remetido ou concluído. Também inclui [dados históricos do pedido](#send-historical-order-data).

- **Perfil (Beta)** são dados relacionados às informações de perfil do comprador. Saiba mais [mais](#send-customer-profile-data).

Para garantir que sua instância do Adobe Commerce possa iniciar a coleta de dados, revise a [pré-requisitos](overview.md#prerequisites).

Consulte o tópico de eventos para saber mais sobre [vitrine](events.md#storefront-events), [back office](events-backoffice.md), e [perfil](events-backoffice.md#customer-profile-events-server-side) eventos.

>[!NOTE]
>
>Todos os campos no **Coleta de dados** aplica-se à **Site** escopo ou superior.

1. Selecionar **Eventos da loja** se desejar enviar dados comportamentais da loja.

1. Selecionar **Eventos de back office** se desejar enviar informações sobre o status da ordem, como se uma ordem foi feita, cancelada, reembolsada ou entregue.

   >[!NOTE]
   >
   >Se você selecionar **Eventos de back office**, todos os dados do back office são enviados para a borda do Experience Platform. Se um comprador optar por recusar a coleta de dados, você deverá definir explicitamente a preferência de privacidade do comprador no Experience Platform. Isso é diferente dos eventos da loja em que o coletor já lida com o consentimento com base nas preferências do comprador. Saiba mais [mais](https://experienceleague.adobe.com/docs/experience-platform/landing/governance-privacy-security/consent/adobe/dataset.html) sobre como definir a preferência de privacidade de um comprador no Experience Platform.

1. (Ignore esta etapa se estiver usando seu próprio SDK da Web da AEP.) [Criar](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html#create) uma sequência de dados na Adobe Experience Platform ou selecione uma sequência de dados existente que deseja usar para a coleção. Insira essa ID de sequência de dados na **ID da sequência de dados** campo.

1. Insira o **ID do conjunto de dados** que você deseja conter seus dados do Commerce. Para localizar a ID do conjunto de dados:

   1. Abra a interface do Experience Platform e selecione **Conjuntos de dados** no painel de navegação esquerdo para abrir a **Conjuntos de dados** painel. O painel lista todos os conjuntos de dados disponíveis para sua organização. Os detalhes são exibidos para cada conjunto de dados listado, incluindo o nome, o esquema ao qual o conjunto de dados pertence e o status da execução de assimilação mais recente.
   1. Abra o conjunto de dados associado à sua sequência de dados.
   1. No painel direito, exiba os detalhes sobre o conjunto de dados. Copie a ID do conjunto de dados.

1. Para garantir atualizações de dados de eventos de back office com base em um agendamento de acordo com uma [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) tarefa, você deve alterar a `Sales Orders Feed` índice para `Update by Schedule`.

   1. No _Admin_ barra lateral, vá para **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Index Management]**.

   1. Marque a caixa de seleção da `Sales Orders Feed` indexador.

   1. Definir **[!UICONTROL Actions]** para `Update by Schedule`.

   1. Se você estiver ativando os dados de back office pela primeira vez, execute os seguintes comandos para reindexar e acionar uma ressincronização. As ressincronizações subsequentes ocorrem automaticamente desde que o [cron](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cron.html) a tarefa está configurada corretamente.

      ```bash
      bin/magento index:reindex sales_order_data_exporter_v2
      ```

      ```bash
      bin/magento saas:resync --feed orders
      ```

#### Descrições dos campos

| Campo | Descrição |
|--- |--- |
| Escopo | Site específico no qual você deseja aplicar as configurações. |
| ID da organização (global) | ID que pertence à organização que adquiriu o produto Adobe DX. Essa ID vincula sua instância do Adobe Commerce ao Adobe Experience Platform. |
| O AEP Web SDK já foi implantado no site? | Marque essa caixa de seleção se você implantou seu próprio AEP Web SDK no site |
| Nome do SDK da Web da AEP (global) | Se você já tiver um SDK da Web do Experience Platform implantado em seu site, especifique o nome desse SDK neste campo. Isso permite que o Coletor de eventos da loja e o SDK de eventos da loja usem o SDK da Web do Experience Platform em vez da versão implantada pelo [!DNL Data Connection] extensão. Se você não tiver um SDK da Web do Experience Platform implantado em seu site, deixe esse campo em branco e a variável [!DNL Data Connection] A extensão implanta um para você. |
| Eventos da loja | É marcado por padrão, desde que a ID da organização e a ID do fluxo de dados sejam válidas. Os eventos da loja coletam dados comportamentais anônimos dos compradores enquanto eles navegam pelo site. |
| Eventos de back office | Se marcado, a carga do evento conterá informações anônimas sobre o status do pedido, como se um pedido tivesse sido feito, cancelado, reembolsado ou remetido. |
| ID da sequência de dados (site) | ID que permite que os dados fluam do Adobe Experience Platform para outros produtos Adobe DX. Essa ID deve ser associada a um site específico em sua instância específica do Adobe Commerce. Se você especificar seu próprio SDK da Web do Experience Platform, não especifique uma ID de fluxo de dados neste campo. A variável [!DNL Data Connection] A extensão do usa a ID de sequência de dados associada a esse SDK e ignora qualquer ID de sequência de dados especificada nesse campo (se houver). |
| ID do conjunto de dados (site) | ID do conjunto de dados que contém seus dados do Commerce. Este campo é obrigatório, a menos que você tenha desmarcado a opção **Eventos da loja** ou **Eventos de back office** caixas de seleção. Além disso, se você estiver usando seu próprio SDK da Web do Experience Platform e, portanto, não tiver especificado uma ID de sequência de dados, ainda será necessário adicionar a ID do conjunto de dados associada à sequência de dados. Caso contrário, você não poderá salvar este formulário. |

Após a integração, os dados da loja começam a fluir para a borda do Experience Platform. Os dados de back office levam cerca de cinco minutos para serem exibidos na borda do. As atualizações subsequentes ficam visíveis na borda com base na programação do cron.

### Enviar dados de perfil do cliente

>[!IMPORTANT]
>
>Esse recurso está na versão beta.

Há dois tipos de dados de perfil que você pode enviar para o Experience Platform: registros de perfil e eventos de perfil de série temporal.

Um registro de perfil contém dados que são salvos quando um comprador cria um perfil na instância do Commerce, como o nome do comprador. Quando o esquema e o conjunto de dados são [configurado corretamente](profile-data.md), um registro de perfil é enviado ao Experience Platform e encaminhado ao serviço de gerenciamento e segmentação de perfis do Adobe: [Real-Time CDP](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/intro/rtcdp-intro/overview.html?lang=pt-BR).

Os eventos de perfil de série temporal contêm dados sobre as informações de perfil do comprador, como se ele criasse, editasse ou excluísse uma conta no site. Quando os dados do evento de perfil são enviados para o Experience Platform, eles ficam em um conjunto de dados onde podem ser usados por outros produtos DX.

1. Verifique se você tem [fornecido](#add-service-account-and-credential-details) conta de serviço e detalhes da credencial.

1. Verifique se você tem um esquema e um conjunto de dados especificados para [assimilação de dados do registro de perfil](profile-data.md) e [assimilação de dados do evento de perfil de série temporal](update-xdm.md#time-series-profile-event-data).

1. Coloque uma marca de seleção na **Perfis de cliente** se desejar enviar dados de perfil para o Experience Platform.

1. Insira o **ID do conjunto de dados do perfil**.

   Os dados do registro de perfil devem usar um conjunto de dados diferente do que você está usando atualmente para dados de evento comportamentais e de back office.

1. Se você não quiser transmitir eventos de perfil por meio da mesma ID de fluxo de dados que está usando para dados comportamentais e de back office, remova a marca de seleção da variável **Transmitir perfis de clientes por meio da mesma ID de sequência de dados** e insira a ID do fluxo de dados que deseja usar.

Pode levar cerca de 10 minutos para que um registro de perfil fique disponível no Real-Time CDP. Os eventos de perfil começam a ser transmitidos imediatamente.

#### Descrições dos campos

| Campo | Descrição |
|--- |--- |
| Perfis de cliente | Marque essa caixa de seleção se desejar coletar e enviar registros de perfil do cliente. |
| ID do conjunto de dados do perfil | Um registro de perfil deve usar um conjunto de dados diferente do usado para eventos comportamentais e de back office. |
| Transmitir perfis de clientes por meio da mesma ID de sequência de dados | Decida se deseja usar o mesmo fluxo de dados usado atualmente para seus eventos comportamentais e de back office ou não. |
| Sequência de dados para perfis de clientes | Especifique a sequência de dados específica do registro de perfil do cliente. |

### Enviar dados históricos do pedido

A Adobe Commerce coleta até cinco anos de [dados e status históricos do pedido](events-backoffice.md#back-office-events). Você pode usar o [!DNL Data Connection] extensão para enviar esses dados históricos ao Experience Platform para enriquecer os perfis do cliente e personalizar as experiências do cliente com base nesses pedidos anteriores. Os dados são armazenados em um conjunto de dados no Experience Platform.

Embora a Commerce já colete os dados históricos do pedido, há várias etapas que você deve concluir para enviar esses dados para o Experience Platform.

Assista a este vídeo para saber mais sobre pedidos históricos e, em seguida, conclua as etapas a seguir para implementar a coleção de pedidos históricos.

>[!VIDEO](https://video.tv.adobe.com/v/3424672)

#### Configurar o serviço de sincronização de pedidos

O serviço de sincronização de pedidos usa o [Estrutura da fila de mensagens](https://developer.adobe.com/commerce/php/development/components/message-queues/) e RabbitMQ. Após concluir essas etapas, os dados do status do pedido podem ser sincronizados com o SaaS, que é necessário antes de ser enviado para o Experience Platform.

1. Verifique se você tem [fornecido](#add-service-account-and-credential-details) conta de serviço e detalhes da credencial.

1. [Ativar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq.html) RabbitMQ.

   >[!NOTE]
   >
   >O RabbitMQ já está configurado para o Commerce versões 2.4.7 e mais recentes, mas você deve habilitar os consumidores.

1. Habilitar consumidores da fila de mensagens por trabalho cron em `.magento.env.yaml` usar `CRON_CONSUMERS_RUNNER` variável de ambiente.

   ```yaml
      stage:
        deploy:
          CRON_CONSUMERS_RUNNER:
            cron_run: true
   ```

   >[!NOTE]
   >
   >Consulte a [implantar documentação de variáveis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#cron_consumers_runner) para saber mais sobre todas as opções de configuração disponíveis.

Com o serviço de sincronização de pedidos ativado, você pode especificar o intervalo de datas do pedido histórico no **[!UICONTROL [!DNL Data Connection]]** página.

#### Especificar intervalo de datas do histórico da ordem

Especifique o intervalo de datas para as ordens históricas que você deseja enviar para o Experience Platform.

1. No Administrador, acesse **Sistema** > Serviços > **[!DNL Data Connection]**.

1. Selecione o **Histórico de pedidos** guia.

1. Em **Sincronização do histórico do pedido**, o **Copiar ID do conjunto de dados das configurações** a caixa de seleção já está ativada. Isso garante que você esteja usando o mesmo conjunto de dados especificado na **Configurações** guia.

1. No **De** e **Para** especifique o intervalo de datas para os dados históricos de pedido que deseja enviar. Não é possível selecionar um intervalo de datas que exceda cinco anos.

1. Selecionar **[!UICONTROL Start Sync]** para acionar o início da sincronização. Os dados históricos de pedidos são dados em lote, e não dados de vitrine e back-office que estão transmitindo dados. Os dados em lote levam cerca de 45 minutos para chegar no Experience Platform.

##### Descrições dos campos

| Campo | Descrição |
|--- |--- |
| Copiar ID do conjunto de dados das configurações | Copia a ID do conjunto de dados inserida na **Configurações** guia. |
| ID do conjunto de dados (site) | ID do conjunto de dados que contém seus dados do Commerce. Este campo é obrigatório, a menos que você tenha desmarcado a opção **Eventos da loja** ou **Eventos de back office** caixas de seleção. Além disso, se você estiver usando seu próprio SDK da Web do Experience Platform e, portanto, não tiver especificado uma ID de sequência de dados, ainda será necessário adicionar a ID do conjunto de dados associada à sequência de dados. Caso contrário, você não poderá salvar este formulário. |
| De | Data a partir da qual você deseja começar a coletar dados do histórico do pedido. |
| Para | Data a partir da qual você deseja terminar a coleta de dados do histórico da ordem. |
| Iniciar sincronização | Inicia o processo de sincronização dos dados do histórico do pedido com a borda do Experience Platform. Esse botão estará desativado se a variável **[!UICONTROL Dataset ID]** estiver em branco ou a ID do conjunto de dados for inválida. |

## Confirmar se os dados do evento foram coletados

Para confirmar se os dados estão sendo coletados no armazenamento do Commerce, use o [Adobe Experience Platform Debugger](https://experienceleague.adobe.com/docs/experience-platform/debugger/home.html) para examinar o site do Commerce. Depois de confirmar que os dados estão sendo coletados, é possível verificar se os dados do evento da loja e do back office aparecem na borda executando uma consulta que retorna dados do [conjunto de dados que você criou](overview.md#prerequisites).

1. Selecionar **Consultas** na navegação à esquerda de Experience Platform e clique em [!UICONTROL Create Query].

   ![Editor de consultas](assets/query-editor.png)

1. Quando o Editor de consultas for aberto, insira uma consulta que selecione dados do conjunto de dados.

   ![Criar consulta](assets/create-query.png)

   Por exemplo, sua consulta pode ser semelhante ao seguinte:

   ```sql
   SELECT * from `your_dataset_name` ORDER by TIMESTAMP DESC
   ```

1. Após a execução da consulta, os resultados são exibidos no **Resultados** , ao lado da guia **Console** guia. Essa exibição mostra a saída em tabela da sua query.

   ![Editor de consultas](assets/query-results.png)

Neste exemplo, você vê dados de evento do [`commerce.productListAdds`](events.md#addtocart), [`commerce.productViews`](events.md#productpageview), [`web.webpagedetails.pageViews`](events.md#pageview)e assim por diante. Essa visualização permite verificar se os dados do Commerce chegaram à borda.

Se os resultados não forem os esperados, abra o conjunto de dados e procure qualquer importação de lotes com falha. Saiba mais sobre [solução de problemas de importações de lote](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/troubleshooting.html).

## Próximas etapas

Quando os dados do Commerce são enviados para a borda do Experience Platform, outros produtos da Adobe Experience Cloud, como o Adobe Journey Optimizer, podem usar esses dados. Por exemplo, você pode configurar o Journey Optimizer para acompanhar determinados eventos e, com base nesses dados, acionar um email para um usuário pela primeira vez ou se houver um carrinho abandonado. Saiba como estender sua plataforma do Commerce [criação de jornadas do cliente](using-ajo.md) no Journey Optimizer.
