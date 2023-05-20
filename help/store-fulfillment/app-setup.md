---
title: Configuração do aplicativo
description: Configurar o [!DNL Store Assist] aplicativo para gerenciar fluxos de trabalho e processos completos de atendimento de lojas para compras online, retirada em pedidos de lojas.
role: User, Admin
level: Intermediate
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '623'
ht-degree: 0%

---

# Configuração do aplicativo

O Store Assist é um aplicativo de plataforma de preenchimento como serviço (FaaS) desenvolvido pela Walmart Commerce Technologies. O aplicativo fornece recursos de preenchimento na loja para lidar com [!DNL buy online, pick up in store] (BOPIS). Com o Store Assist, os associados da loja podem ver quais itens os clientes solicitaram, escolher os itens corretos mais rapidamente e configurar ordens preenchidas para entrega de coleta na loja ou na beira da calçada aos clientes.

O aplicativo Store Assist recebe todas as informações de pedidos e clientes, desde detalhes do pedido até os horários de coleta, e disponibiliza os dados para armazenar associados online, por meio de dispositivos móveis. O aplicativo inclui [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff], e [!UICONTROL Orders] módulos para ajudar a Store Associates com atividades de preenchimento, como o seguinte:

- Atribuir datas e horas de entrega da ordem.
- Receba notificações dos clientes quando eles chegarem para retirada de pedido.
- Faça pedidos de transferência para os clientes.
- Rastrear status de ordem para todas as ordens em seus locais de armazenamento atribuídos.

>[!NOTE]
>
>Consulte [Fluxos de trabalho de atendimento do Auxílio de armazenamento](store-assist-modules.md) para saber mais sobre o aplicativo Store Assist.

## Configurar o aplicativo de assistência da loja

O aplicativo Store Assist requer dois tipos de configuração:

- Configurações do sistema de administração do Adobe Commerce para [gerenciar contas de usuário, funções de usuário, permissões de recursos](user-setup.md), e [a marca do carro e as seleções do modelo disponíveis para os clientes durante o processo de check-in](check-in-experience-setup.md).

- Configurações de front-end para personalizar a interface do aplicativo Store Assist e outras configurações, incluindo:

   - **Marque o aplicativo Store Assist**—Personalize a interface do usuário do aplicativo com o logotipo e as cores da sua empresa.

   - **Atualizar as instruções padrão**—Personalize as instruções nos módulos Store Assist Pick, Stage, Handoff e Order para orientar a Store Associates em cada etapa do fluxo de trabalho de preenchimento da sua empresa.

   - **Localização**—Selecione o idioma disponível para o aplicativo. Escolha o formato de data e hora e selecione as unidades de medida padrão e a moeda padrão.

   - **Tempo de inatividade**—Especifique por quanto tempo o aplicativo deve estar inativo antes de fazer logoff.

   - **Cancelamento da loja**— Especifica se os pedidos podem ser cancelados na loja e quais funções têm permissões de cancelamento

   - **Janela Limpeza da ordem**—Especificar quanto tempo passou a [Lead Time de Retirada Estimado](enable-general.md#delivery-method-title-configuration) que uma ordem separada permanece na preparação antes de ser reabastecida — por exemplo, três dias. O valor padrão é sete dias. Se essa configuração estiver ativada, a ordem será automaticamente cancelada quando esse tempo expirar. Os itens são reabastecidos e o comerciante recebe um email de cancelamento.

   - Personalize tudo nas instruções do aplicativo (seleção, preparo, entrega).

   - **Notificações de separação**—Especifique se deseja enviar uma notificação por push para iniciar o processo de separação depois que um cliente colocar um pedido.

   - **Notificações de check-in**—Especifique se deseja enviar uma notificação por push durante o processo de check-in para retiradas de pedidos - após o check-in, depois que o tempo de espera do cliente exceder um período especificado. Ou desative a notificação.

   - **Processo de entrega**—Habilite processos opcionais quando a Store Associate entrega ordens ao cliente, por exemplo, exigir uma assinatura do cliente ou solicitar que a associada verifique a ID do cliente.

   - **Ativar rejeição de item na entrega**—Permite que os clientes devolvam ou cancelem itens do pedido durante a entrega do pedido.
   Trabalhe com a equipe de Serviços ao Cliente do Walmart Commerce Technologies para concluir a configuração de front-end para o aplicativo Store Assist.

## Download e instalação do aplicativo

Após a instalação e configuração do aplicativo Store Assist, os associados da loja poderão baixar, instalar e fazer logon no aplicativo Store Assist a partir de seus dispositivos móveis.

- Verifique se o dispositivo móvel atende às [requisitos de hardware e software](solution-requirements.md#store-assist-app-requirements) para a solução Store Fulfillment.

- Baixe o aplicativo Store Assist no [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or the [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.

- Os associados da loja exigem as seguintes informações para fazer logon:

   - **[!UICONTROL Company name]** associado à conta do Store Assist

   - **Credenciais da conta de Assistência de Armazenamento**—as credenciais de nome de usuário e senha da conta.
   Um administrador do Adobe Commerce pode criar e gerenciar [!DNL Store Assist app] contas de usuário para todas as localizações de loja que tenham [Coleta na loja](merchant-store-configuration.md#pickup-location-configuration) ativado nas configurações de Admin Stores.
