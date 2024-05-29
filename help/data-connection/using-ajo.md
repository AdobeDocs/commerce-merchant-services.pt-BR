---
title: Usar o Adobe Journey Optimizer para enviar um email de carrinho abandonado
description: Saiba como usar o Adobe Journey Optimizer para enviar um email de carrinho abandonado.
role: Admin, Developer
feature: Personalization, Integration
exl-id: 5e4e7c0a-c00b-4278-bd73-6b6f2fcbe770
source-git-commit: a94f75dfab1f88f02e217b0e021cc2dfc94244c7
workflow-type: tm+mt
source-wordcount: '1429'
ht-degree: 0%

---

# Usar o Adobe Journey Optimizer para enviar um email de carrinho abandonado

Saiba como fornecer um email personalizado de reengajamento ou notificação se uma sessão do carrinho ou do navegador for abandonada. Neste artigo, você usa dados gerados de clientes que visualizaram vários produtos e categorias, interagiram com um produto ou gastaram tempo em uma página.

## Quais dados devo considerar usar?

Crie um carrinho abandonado, navegue por e-mail ou envie notificações usando dados de eventos da loja e do back office.

| Tipos de dados | Dados da vitrine (Eventos comportamentais) | Dados de back office (eventos do lado do servidor) |
|---|---|---|
| **Definição** | Cliques ou ações que os clientes realizam no site. | Informações sobre o ciclo de vida e detalhes de cada pedido (passado e atual). |
| **Eventos capturados pelo Adobe Commerce** | [pageView](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#pageview)<br>[productPageView](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events)<br>[addToCart](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#addtocart)<br>[openCart](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#opencart)<br>[startCheckout](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#startcheckout)<br>[completeCheckout](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events#completecheckout) | [orderPlaced](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/event-forwarding/events-backoffice#orderplaced)<br>[Histórico de pedidos](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/data-connection/fundamentals/connect-data#send-historical-order-data) |

### O que posso fazer apenas com o Adobe Commerce?

Usar Adobe [!DNL Commerce] para configurar lembretes de email baseados em regras, que podem servir como carrinho ou navegar em emails de abandono. Saiba mais aqui.

### O que posso fazer com o Adobe [!DNL Commerce] e Experience Cloud?

- **Adobe [!DNL Commerce] com o Adobe Journey Optimizer** - Utilização do Adobe [!DNL Commerce] com o Adobe Journey Optimizer permite usar [!DNL Commerce] como acionador de uma jornada de abandono omnicanal. Você pode personalizar essa jornada com base nos atributos do cliente, nos itens que eles abandonaram, em outros comportamentos de compras e em comportamentos de compras anteriores.

- **Adobe Commerce, Adobe Journey Optimizer e Adobe Real-Time CDP** : a adição do Real-Time CDP permite refinar ainda mais as campanhas de abandono com base em perfis unificados de clientes e públicos gerenciados centralmente com base em regras ou AI. Por exemplo, você pode criar:

   - Um público-alvo de &quot;conversores fortes&quot; com uma baixa taxa de abandono
   - Um público-alvo de &quot;alta consideração&quot; que revisitou determinadas categorias várias vezes
   - Um público-alvo de &quot;alto potencial&quot; com altos gastos e fidelidade, mas que abandonou recentemente

### O que outros clientes conquistaram?

Adobe [!DNL Commerce] Os clientes do atingiram impactos significativos nos negócios ao implementar campanhas personalizadas de abandono de produtos usando o Adobe [!DNL Commerce], ADOBE [!DNL Journey Optimizer], e ADOBE [!DNL Real-Time CDP].

Um varejista global de vestuário de várias marcas obteve:

- Conversão 1.9x ao clicar em novas campanhas
- Aumento de 57% na receita proveniente de jornadas de abandono omnicanal
- 41% de aumento na taxa de conversão de campanhas de reengajamento
- Mais de 1000 novos compradores contratados por semana

Uma empresa global de bebidas conseguiu:

- 36% de taxas de abertura de email de reengajamento
- Aumento de 21% nas taxas de clickthrough
- Aumento de 8,5% na taxa de conversão
- 89% dos abandonadores reengajados convertem

## Vamos começar

Esse caso de uso específico se concentra na criação de um email de carrinho abandonado usando dados de seu [!DNL Commerce] instância e enviá-la para o Adobe [!DNL Journey Optimizer].

### O que é o Adobe Journey Optimizer?

[Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html) O ajuda a personalizar a experiência comercial para seus compradores. Por exemplo, você pode usar o Journey Optimizer para criar e entregar campanhas de marketing programadas, como promoções semanais para uma loja de varejo, ou gerar um email de carrinho abandonado se um cliente tiver adicionado um produto a um carrinho, mas não concluído o processo de finalização.

Neste tópico, você aprenderá a criar um email de carrinho abandonado ouvindo uma `checkout` evento gerado pelo seu [!DNL Commerce] instância e respondendo a esse evento no Journey Optimizer.

>[!IMPORTANT]
>
>Para fins de demonstração, use o seu [!DNL Commerce] ambiente de sandbox para que você não dilua os dados do evento de produção com os dados do evento da loja e do back office enviados para o Experience Platform.

### Pré-requisitos

Antes de começar com essas etapas, verifique se:

- Você está provisionado para usar o Adobe [!DNL Journey Optimizer]. Se não tiver certeza, consulte o integrador de sistemas ou a equipe de desenvolvimento que gerencia projetos e ambientes.
- Você [instalado](install.md) e [configurado](connect-data.md) o [!DNL Data Connection] extensão no [!DNL Commerce].
- Você [confirmado](connect-data.md#confirm-that-event-data-is-collected) que o seu [!DNL Commerce] os dados do evento estão chegando à borda do Experience Platform.

## Etapa 1: criar um usuário no [!DNL Commerce] ambiente de sandbox

Crie um usuário em seu ambiente de sandbox e confirme se as informações da conta do usuário aparecem no Experience Platform. Verifique se o email especificado é válido, pois é usado posteriormente nesta seção para enviar o email do carrinho abandonado.

1. Entre ou crie uma conta na sua [!DNL Commerce] ambiente de sandbox.

   ![Fazer logon em sua conta de teste](assets/sign-in-account.png){width="700" zoomable="yes"}

   Com o [!DNL Data Connection] extensão instalada e configurada, essas informações de conta são enviadas para o Experience Platform como um perfil.

1. Confirme se as informações da sua conta de usuário aparecem no **[!UICONTROL Profile]** seção do Experience Platform.

   Ir para **[!UICONTROL Profiles]** no Adobe Experience Platform. Clique em **[!UICONTROL Detail]** no perfil para ver o perfil que você criou.

   ![Confirmar perfil](assets/check-event-profile.png){width="700" zoomable="yes"}

## Etapa 2: Exibir eventos no Journey Optimizer

No seu [!DNL Commerce] ambiente de sandbox, acione eventos na loja visualizando páginas de produtos, adicionando itens a um carrinho e concluindo várias outras atividades que um comprador executaria. Em seguida, confirme se esses eventos estão fluindo para o Journey Optimizer.

1. Launch [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).
1. Selecionar **[!UICONTROL Profiles]**.
1. Definir **[!UICONTROL Identity namespace]** para `Email`.
1. Defina o **[!UICONTROL Identity value]** ao seu endereço de email.
1. Selecione o seu perfil e, em seguida, a **[!UICONTROL Events]** guia.

   ![Verificar detalhes do evento](assets/check-event-details.png){width="700" zoomable="yes"}

   Procure o `commerce.checkouts` e examine a carga útil do evento:

       &quot;json
       &quot;personID&quot;: &quot;84281643067178465783746543501073369488&quot;,
       &quot;eventType&quot;: &quot;commerce.checkouts&quot;,
       &quot;_id&quot;: &quot;4b41703f-e42e-485b-8d63-7001e3580856-0&quot;,
       &quot;commerce&quot;: {
       &quot;cart&quot;: {},
       &quot;check-outs&quot;: {
       &quot;value&quot;: 1
       }
       &quot;
   
   Como você pode ver, a carga útil completa do evento contém dados avançados do evento. Na próxima seção, você configurará eventos no Journey Optimizer para acompanhar e responder aos eventos `commerce.checkouts` evento gerado pelo seu [!DNL Commerce] vitrine eletrônica.

## Etapa 3: configurar eventos no Journey Optimizer

Configure dois eventos no Journey Optimizer: um evento escuta a `commerce.checkouts` do Commerce e o outro é um evento básico de tempo limite que aguarda um tempo específico para passar antes de acionar um email de carrinho abandonado.

### Criar um evento de ouvinte

1. Launch [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/user-interface.html).

1. Clique em **[!UICONTROL Configurations]** no **[!UICONTROL Administration]** do painel esquerdo.

1. No **[!UICONTROL Events]** bloco, clique em **[!UICONTROL Manage]**.

   ![Configuração de evento do Journey Optimizer](assets/ajo-config.png){width="700" zoomable="yes"}

1. No **[!UICONTROL Events]** clique em **[!UICONTROL Create Event]**.

1. Na navegação à direita, configure seu evento da seguinte maneira:

   1. Defina o **[!UICONTROL Name]** para: `firstname_lastname_checkout`.
   1. Definir **[!UICONTROL Type]** para **[!UICONTROL Unitary]**.
   1. Definir **[!UICONTROL Event id typ]e** para **[!UICONTROL Rule based]**.
   1. Definir **[!UICONTROL Schema]** ao seu [!DNL Commerce] [schema](update-xdm.md).
   1. Selecionar **[!UICONTROL Fields]** para abrir o **[!UICONTROL Fields]** página. Em seguida, selecione os campos úteis para esse evento. Por exemplo, selecione todos os campos sob a **[!UICONTROL Product list items]**, **[!UICONTROL Commerce]**, **[!UICONTROL eventType]**, e **[!UICONTROL Web]**.
   1. Clique em **[!UICONTROL OK]** para salvar os campos selecionados.
   1. Clique dentro do **[!UICONTROL Event id condition]** campo. Em seguida, crie uma condição: `eventType` é igual a `commerce.checkouts` E `personalEmail.address` é igual ao endereço de email usado ao criar o perfil na seção anterior.

      ![Condição de definição Journey Optimizer](assets/ajo-set-condition.png){width="700" zoomable="yes"}

   1. Clique em **[!UICONTROL OK]**.
   1. Clique em **[!UICONTROL Save]** para salvar o evento.

### Criar um evento de tempo limite

1. Crie um evento no Journey Optimizer como você fez antes.

1. Na navegação à direita, configure seu evento da seguinte maneira:

   1. Defina o **[!UICONTROL Name]** para: `firstname_lastname_timeout`.
   1. Definir **[!UICONTROL Type]** para **[!UICONTROL Unitary]**.
   1. Definir **[!UICONTROL Event id type]** para **[!UICONTROL Rule based]**.
   1. Definir **[!UICONTROL Schema]** ao seu [!DNL Commerce] [schema](update-xdm.md).
   1. Defina o **[!UICONTROL Schema]**, **[!UICONTROL Fields]**, e **[!UICONTROL Event id condition]** o mesmo que acima.
   1. Clique em **[!UICONTROL Save]** para salvar o evento.

Com esses dois eventos configurados, crie uma jornada que envie um email de carrinho abandonado.

## Etapa 4: criar uma jornada de check-out

Crie uma jornada que acompanhe o `commerce.checkouts` e envia um email de carrinho abandonado após um período especificado.

1. No Journey Optimizer, selecione **[!UICONTROL Journeys]** em **J[!UICONTROL OURNEY MANAGEMENT]**.
1. Clique em **[!UICONTROL Create Journey]**.
1. Especifique o nome da jornada.
1. Clique em **[!UICONTROL OK]** para salvar a jornada.
1. Na navegação à esquerda, sob o **[!UICONTROL EVENTS]** procure o evento de check-out criado anteriormente: `firstname_lastname_checkout` e arraste-o e solte-o na tela.

   >[!TIP]
   >
   >Clicar duas vezes no evento adiciona-o automaticamente à tela.

1. Procure o evento de tempo limite e adicione-o à tela.
1. Clique duas vezes no evento de tempo limite.

   1. No **[!UICONTROL Timeout]** , selecione a **[!UICONTROL Define the event time]** caixa de seleção
   1. No **[!UICONTROL Wait for]** campo inserir `1` e `Minute`.
   1. Selecione o **[!UICONTROL Set a timeout path]** caixa de seleção

   Com essa configuração de tempo limite, um comprador que realiza um check-out, mas não conclui o pedido em um minuto, aciona essa ramificação de tempo limite. Em um ambiente de produção real, isso seria definido por um período mais longo, como 24 horas.

1. Na navegação à esquerda, em **[!UICONTROL ACTIONS]**, adicione o **[!UICONTROL Email]** ação para a ramificação de tempo limite. Sua jornada deve ser semelhante ao seguinte:

   ![Tela do Journey Optimizer](assets/ajo-canvas.png){width="700" zoomable="yes"}

### Criar email de carrinho abandonado

Crie um email de carrinho abandonado que é enviado quando um carrinho abandonado é detectado.

1. Na jornada criada acima, clique duas vezes na guia **[!UICONTROL Email]** ícone na tela.

1. Siga as [etapas](https://experienceleague.adobe.com/docs/journey-optimizer/using/content-management/personalization/personalization-use-cases/personalization-use-case-helper-functions.html#configure-email) no guia do Journey Optimizer para criar o email de carrinho abandonado.

Agora você tem uma jornada no Journey Optimizer que escuta as `commerce.checkouts` evento do seu [!DNL Commerce] armazenamento e um email de carrinho abandonado que é enviado após um período. A próxima seção mostra como testar a jornada.

## Etapa 5: acionar o evento de finalização em tempo real

Nesta seção, teste o evento em tempo real.

1. No Journey Optimizer, alterne para o modo Teste.

   ![Ativar modo de teste](assets/ajo-enable-test.png){width="700" zoomable="yes"}

1. Para testar essa jornada em tempo real, abra outra guia do navegador e vá para a [!DNL Commerce] no seu ambiente de sandbox.

   1. Adicione um produto ao carrinho.
   1. Vá para a página de check-out.
   1. Na página de check-out, abandone o carrinho voltando para a página principal ou fechando sua guia.

      A jornada agora é acionada. Para confirmar, abra a guia que tem a jornada no Journey Optimizer. Você deve ver uma seta verde que mostra o caminho pelo qual o usuário passou.

1. Verifique o email na sua caixa de entrada.
