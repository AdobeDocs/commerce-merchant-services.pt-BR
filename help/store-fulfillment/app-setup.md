---
title: Configuração do aplicativo
description: '"Configure o [!DNL Store Assist] aplicativo para gerenciar fluxos de trabalho e processos completos de preenchimento de lojas para compra online, recuperação em pedidos de lojas." '
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Configuração do aplicativo

O Store Assist é um aplicativo de plataforma de atendimento como serviço (FaaS) desenvolvido pela Walmart Commerce Technologies. O aplicativo fornece recursos de preenchimento na loja para lidar com [!DNL buy online], [!DNL pick up in store] (BOPIS) ordens.

O aplicativo recebe todas as informações do pedido e do cliente, desde detalhes do pedido até horários de coleta, e disponibiliza os dados para armazenar associados online, por meio de dispositivos móveis. Com o Store Assist, os associados de loja podem ver quais itens os clientes pediram, selecionar os itens corretos mais rápido e configurar pedidos cumpridos para entrega de retirada na loja ou na área de transferência para os clientes.

Os Associados de Loja usam o Assistente de Loja [!UICONTROL Pick], [!UICONTROL Stage], [!UICONTROL Handoff]e [!UICONTROL Orders] para concluir o seguinte gerenciamento do processo de delivery e handoff:

- Atribuir datas e horas de entrega do pedido
- Obter notificações dos clientes quando eles chegarem à loja para retirada de pedidos
- Encomendar pedidos de transferência para clientes
- Rastrear o status do pedido para todos os pedidos em seus locais de armazenamento atribuídos

Consulte [Fluxos de trabalho de cumprimento da Assistência de Armazenamento](store-assist-modules.md) para saber mais sobre o aplicativo Store Assist.


## Configurar o aplicativo de assistência da loja

O aplicativo Store Assist requer dois tipos de configuração:

- Configurações do administrador do Adobe Commerce para [Gerenciar contas de usuário, funções de usuário e permissões de recurso das configurações do sistema de administração do Adobe Commerce](user-setup.md).

- Enfrente as configurações para personalizar a interface do aplicativo de assistência da loja e outras configurações, incluindo:

   - **Marca o aplicativo de assistência da loja**—Personalize a interface do usuário do aplicativo com o logotipo e as cores de sua empresa

   - **Atualizar as instruções padrão**—Personalize as instruções exibidas nas interfaces do Store Assist para os módulos de Escolha, Estágio, Passagem e Pedido, de modo que seus associados saibam exatamente o que fazer durante cada etapa do processo de atendimento.

   - **Localização**—Selecione o idioma disponível para o aplicativo, escolha o formato de data e hora, selecione as unidades de medição padrão e selecione a moeda padrão

   - **Tempo de inatividade**—Especifique o tempo em que o aplicativo deve estar inativo antes de fazer logoff

   - **Cancelamento da loja**—Especifique se os pedidos podem ser cancelados da loja e quais funções têm permissões de cancelamento

   - **Janela de limpeza do pedido**—Especifique por quanto tempo passou o tempo agendado de retirada em que uma ordem selecionada permanece em preparação antes de ser rebloqueada — por exemplo, três dias.

   - Personalizar tudo nas instruções do aplicativo (selecionar, preparar, desativar)

   - **Notificações por separação**-Configure se desejar que notificações por push comecem a selecionar quando um pedido for feito

   - **Notificações de check-in**-Configure se desejar ter notificações por push depois que um cliente fizer o check-in / estiver aguardando X min / ou nenhuma notificação

   - **Processo de desativação da mão**—Habilite a assinatura do cliente, habilite um prompt para verificar a ID do cliente antes de entregar o pedido

   - **Ativar rejeição de item ao passar o mouse**

   Trabalhe com a equipe de Serviços ao Cliente de Tecnologias do Walmart para concluir a configuração Frontend para o aplicativo de assistência da loja.

## Download e instalação do aplicativo

Depois que a configuração do aplicativo Store Assist for concluída, os Store Associates poderão baixar e instalar o aplicativo Store Assist em seus dispositivos móveis e fazer logon.

- Baixe o aplicativo Store Assist no [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id16092815390) ou na loja da Google Play.

- As Associações de Armazenamento exigem as seguintes informações para fazer logon:

   - O nome da Empresa associado à sua conta de Ajuda da loja

   - Armazenar credenciais de conta do Auxiliar—credenciais de nome de usuário e senha de sua conta.
   Um administrador do Adobe Commerce pode criar contas de usuário do aplicativo de assistência da loja para locais da loja que tenham [Seleção na loja](merchant-store-configuration.md#pickup-location-configuration) habilitado nas configurações das Lojas de administração.

