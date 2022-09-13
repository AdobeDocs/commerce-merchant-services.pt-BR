---
title: Configuração do aplicativo
description: Configure o [!DNL Store Assist] aplicativo para gerenciar fluxos de trabalho e processos completos de preenchimento de lojas para compra online, recuperação em pedidos de lojas.
role: User, Admin
level: Intermediate
exl-id: bcb5b02b-0141-407a-ad55-6e10e8e1aa90
source-git-commit: fda4620f57aa7aa9fb930b10f5717fee98983378
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# Configuração do aplicativo

O Store Assist é um aplicativo de plataforma de atendimento como serviço (FaaS) desenvolvido pela Walmart Commerce Technologies. O aplicativo fornece recursos de preenchimento na loja para lidar com [!DNL buy online, pick up in store] (BOPIS) ordens. Com o Store Assist, os associados de loja podem ver quais itens os clientes pediram, selecionar os itens corretos mais rápido e configurar pedidos cumpridos para entrega de retirada na loja ou na área de transferência para os clientes.

O aplicativo Store Assist recebe todas as informações do pedido e do cliente, desde detalhes do pedido até horários de coleta, e disponibiliza os dados para armazenar associados online, por meio de dispositivos móveis. O aplicativo inclui [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff]e [!UICONTROL Orders] módulos para ajudar a Armazenar Associadas com atividades de atendimento, como o seguinte:

- Atribuir datas e horas de entrega do pedido.
- Receba notificações dos clientes quando eles chegarem para a retirada do pedido.
- Preparar pedidos de transferência para clientes.
- Rastrear o status do pedido para todos os pedidos em seus locais de armazenamento atribuídos.

>[!NOTE]
>
>Consulte [Fluxos de trabalho de cumprimento da Assistência de Armazenamento](store-assist-modules.md) para saber mais sobre o aplicativo Store Assist.

## Configurar o aplicativo de assistência da loja

O aplicativo Store Assist requer dois tipos de configuração:

- Configurações do sistema de administração do Adobe Commerce para [gerenciar contas de usuário, funções de usuário, permissões de recurso](user-setup.md)e [a marca do automóvel e as seleções de modelo disponíveis para os clientes durante o processo de registro](check-in-experience-setup.md).

- Enfrente as configurações para personalizar a interface do aplicativo de assistência da loja e outras configurações, incluindo:

   - **Marca o aplicativo de assistência da loja**—Personalize a interface do usuário do aplicativo com o logotipo e as cores de sua empresa.

   - **Atualizar as instruções padrão**—Personalize as instruções nos módulos Store Assist Pick, Stage, Handoff e Order para orientar os Associados de Loja em cada etapa do fluxo de trabalho de cumprimento para sua empresa.

   - **Localização**—Selecione o idioma disponível para o aplicativo. Escolha o formato de data e hora e selecione as unidades de medida padrão e a moeda padrão.

   - **Tempo de inatividade**—Especifique o tempo em que o aplicativo deve estar inativo antes de fazer logoff.

   - **Cancelamento da loja**—Especifique se os pedidos podem ser cancelados da loja e quais funções têm permissões de cancelamento

   - **Janela de limpeza do pedido**—Especifique por quanto tempo passou [Lead Time de retirada estimado](enable-general.md#delivery-method-title-configuration) que um pedido selecionado permanece em preparação antes de ser rearmazenado, por exemplo, três dias. O valor padrão é de 7 dias. Se essa configuração estiver ativada, a ordem será automaticamente cancelada quando esse tempo expirar. Os itens são rearmazenados e o comerciante recebe um email de cancelamento.

   - Personalize todas as instruções no aplicativo (escolha, preparo, entrega).

   - **Notificações por separação**—Especifique se deseja enviar uma notificação por push para iniciar o processo de separação depois que o cliente colocar um pedido.

   - **Notificações de check-in**—Especifique se deseja enviar uma notificação por push durante o processo de check-in para pedidos de compra após check-in, depois que o tempo de espera do cliente exceder um período especificado. Ou desative a notificação.

   - **Processo de desativação da mão**—Ative processos opcionais quando a Store Associate fornecer ordem ao cliente, por exemplo, exigir uma assinatura do cliente ou solicitar que o associado verifique a ID do cliente.

   - **Ativar rejeição de item ao passar o mouse**—Permitir que os clientes devolvam ou anulem itens de pedido durante o processamento do pedido.
   Trabalhe com a equipe de Serviços ao Cliente de Tecnologias do Walmart para concluir a configuração de primeiro plano do aplicativo de assistência da loja.

## Download e instalação do aplicativo

Depois que o aplicativo Store Assist é configurado e configurado, os Store Associates podem baixar, instalar e fazer logon no aplicativo Store Assist a partir de seus dispositivos móveis.

- Verifique se o dispositivo móvel atende à função [requisitos de hardware e software](solution-requirements.md#store-assist-app-requirements) para a solução Store Fulfillment.

- Baixe o aplicativo Store Assist no [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target=&quot;_blank&quot;} ou o [Loja Google Play](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target=&quot;_blank&quot;}.

- As Associações de Armazenamento exigem as seguintes informações para fazer logon:

   - **[!UICONTROL Company name]** associado à conta de assistência de loja

   - **Credenciais da conta do Auxiliar de Armazenamento**—credenciais de nome de usuário e senha para sua conta.
   Um administrador do Adobe Commerce pode criar uma conta de usuário e definir permissões para o [!DNL Store Assist app] contas de usuário para locais de armazenamento que tenham [Seleção na loja](merchant-store-configuration.md#pickup-location-configuration) habilitado nas configurações das Lojas de administração.
