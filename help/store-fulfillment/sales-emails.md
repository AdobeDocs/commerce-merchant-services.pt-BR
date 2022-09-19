---
title: Emails de vendas
description: Configure os modelos de email transacional para comunicação com clientes e administradores de armazenamento durante o processo de atendimento dos pedidos de retirada da loja.
role: User, Admin
level: Intermediate
exl-id: 688732e3-06f0-4613-a589-2d465597eb28
source-git-commit: 31ad67d3f3d11c68341de0306eea37f231b2d9b9
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Emails de vendas

O Cumprimento da Loja oferece um conjunto estendido de modelos de email transacionais para dar suporte a workflows de pedido e cumprimento. Eles oferecem comunicações e mensagens consistentes e automatizadas em todos os canais — notificando os administradores de clientes e lojas sobre alterações no status do pedido, instruções para pedidos de retirada na loja e muito mais.

Os modelos de email de Preenchimento da Loja são configurados com mensagens e configurações padrão. Os administradores de merchant no Adobe Commerce podem gerenciar e modificar configurações e selecionar os modelos de email para se comunicar com os clientes em diferentes cenários. Os administradores também podem configurar e personalizar modelos.

Configure os modelos de Email de vendas no Administrador: **[!UICONTROL Stores > Configuration > Sales > Sales Emails]**.

## Emails - Configurações gerais

<table>
<thead>
<tr>
<th><strong>Campo</strong></th>
<th><strong>Descrição</strong></th>
<th><strong>Escopo</strong></th>
<th><strong>Obrigatório</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Envio assíncrono</strong></td>
<td>Desative este recurso. Não há suporte para envio assíncrono de email. Para obter a comunicação e o tempo de resposta mais rápidos para a retirada da loja, envie emails imediatamente em vez de agrupá-los em lote. </td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
</tbody></table>

## Pedido pronto para retirada na loja

<table>
<thead>
<tr>
<th><strong>Campo</strong></th>
<th><strong>Descrição</strong></th>
<th><strong>Escopo</strong></th>
<th><strong>Obrigatório</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Ativado</strong></td>
<td>Este email é enviado ao cliente quando o associado da loja concluiu a separação do pedido. Defina como "Não" para desativar a notificação por email. Se o template de email estiver desativado, ele não impede que um pedido seja escolhido pelo associado da loja.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Pedido pronto para retirada do remetente de email</strong></td>
<td>A identidade do remetente usada ao enviar a notificação por email.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Pedido Pronto Para Obter Modelo De Email</strong></td>
<td>O template de mensagem de email usado para notificar clientes registrados. Um template padrão é fornecido com a integração .</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<td><strong>Pedido pronto para retirada de modelo de email para convidado</strong></td>
<td>O modelo de mensagem de email usado para notificar clientes convidados. Um template padrão é fornecido com a integração .</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Pedido pronto para retirada de modelo de email para contato de retirada alternativo</strong></td>
<td>O template de mensagem de email usado para notificar contatos adicionais nomeados no pedido. Um template padrão é fornecido com a integração .</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Enviar Pedido Pronto Para Obter Cópia De Correio Eletrônico Para</strong></td>
<td>Uma lista delimitada por vírgulas de endereços de email para envio de uma cópia de cada notificação.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Enviar Pedido Pronto Para O Método De Cópia De Correio Eletrônico De Escolha</strong></td>
<td>O método de cópia de email — cópia de carbono — a ser usado.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
</tbody></table>


## O pedido foi recebido na Loja

<table>
<thead>
<tr>
<th><strong>Campo</strong></th>
<th><strong>Descrição</strong></th>
<th><strong>Escopo</strong></th>
<th><strong>Obrigatório</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Ativado</strong></td>
<td>Este email é enviado ao cliente quando para confirmar que ele retirou seu pedido da loja. Defina como "Não" para desativar a notificação por email. Se o template de email estiver desativado, isso não impede que um pedido seja recebido pelo cliente.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Pedido Foi Selecionado Remetente de Email</strong></td>
<td>A identidade do remetente usada ao enviar a notificação por email.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>O Pedido Foi Selecionado No Modelo De Email</strong></td>
<td>O template de mensagem de email usado para notificar clientes registrados. Um template padrão é fornecido com a integração</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<td><strong>O Pedido foi Selecionado Modelo de Email para Convidado</strong></td>
<td>O modelo de mensagem de email usado para notificar clientes convidados. Um template padrão é fornecido com a integração .</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Enviar Foi Selecionado E-Mail Copy Para</strong></td>
<td>Uma lista delimitada por vírgulas de endereços de email para envio de uma cópia de cada notificação.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>O Enviar Foi Selecionado Por Método De Cópia De Email</strong></td>
<td>O método de cópia de email — cópia de carbono — a ser usado.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
</tbody></table>

## Pedido atrasado

<table>
<thead>
<tr>
<th><strong>Campo</strong></th>
<th><strong>Descrição</strong></th>
<th><strong>Escopo</strong></th>
<th><strong>Obrigatório</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Ativado</strong></td>
<td>Esse email é enviado ao cliente para notificá-lo sobre um atraso no processamento ou na escolha de seu pedido na loja de produtos. Defina como "Não" para desativar a notificação por email. Se o modelo de email estiver desativado, o recurso não impedirá que um pedido seja atrasado.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Remetente de email atrasado do pedido
</strong></td>
<td>A identidade do remetente usada ao enviar a notificação por email.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Modelo de email de pedido atrasado</strong></td>
<td>O template de mensagem de email usado para notificar clientes registrados. Um template padrão é fornecido com a integração .</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<td><strong>Solicitar modelo de email atrasado para o convidado</strong></td>
<td>O modelo de mensagem de email usado para notificar clientes convidados. Um template padrão é fornecido com a integração .</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Enviar cópia de email atrasada do pedido para</strong></td>
<td>Uma lista delimitada por vírgulas de endereços de email para envio de uma cópia de cada notificação.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Enviar Método de Cópia Atrasada do Pedido</strong></td>
<td>O método de cópia de email — cópia de carbono — a ser usado.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
</tbody></table>



## Pedido Cancelado

<table>
<thead>
<tr>
<th><strong>Campo</strong></th>
<th><strong>Descrição</strong></th>
<th><strong>Escopo</strong></th>
<th><strong>Obrigatório</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Ativado</strong></td>
<td>Esse email é enviado ao cliente para notificá-lo de que seu pedido foi cancelado na loja de merchant. Defina como <code>No</code> para desativar a notificação por email. Se o template de email estiver desativado, o recurso não impede o cancelamento de um pedido.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Solicitar Remetente de Email Cancelado
</strong></td>
<td>A identidade do remetente usada ao enviar a notificação por email.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Pedido Cancelado Modelo de Email</strong></td>
<td>O template de mensagem de email usado para notificar clientes registrados. Um template padrão é fornecido com a integração .</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<td><strong>Pedido Cancelado para Convidado</strong></td>
<td>O modelo de mensagem de email usado para notificar clientes convidados. Um template padrão é fornecido com a integração .</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Enviar Pedido Cancelou Cópia de Correio Eletrônico para</strong></td>
<td>Uma lista delimitada por vírgulas de endereços de email para envio de uma cópia de cada notificação.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Método de Cópia Cancelada do Pedido de Envio</strong></td>
<td>O método de cópia de email — cópia de carbono — a ser usado.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
</tbody></table>


## Pedido parcialmente cancelado

<table>
<thead>
<tr>
<th><strong>Campo</strong></th>
<th><strong>Descrição</strong></th>
<th><strong>Escopo</strong></th>
<th><strong>Obrigatório</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Ativado</strong></td>
<td>Este email é enviado ao cliente para notificá-lo de que parte de seu pedido foi cancelada na loja de merchant. Defina como <code>No</code> para desativar a notificação por email. Se o template de email estiver desativado, isso não impede que um pedido seja parcialmente cancelado.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Solicitar Remetente de Email Parcialmente Cancelado
</strong></td>
<td>A identidade do remetente usada ao enviar a notificação por email.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Solicitar Modelo de Email Parcialmente Cancelado</strong></td>
<td>O template de mensagem de email usado para notificar clientes registrados. Um template padrão é fornecido com a integração .</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<td><strong>Solicitar Modelo de Email Parcialmente Cancelado para Contato de Seleção Alternativo</strong></td>
<td>O template de mensagem de email usado para notificar contatos adicionais nomeados no pedido. Um template padrão é fornecido com a integração .</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Pedido parcialmente cancelado para convidado</strong></td>
<td>O modelo de mensagem de email usado para notificar clientes convidados. Um template padrão é fornecido com a integração .</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Enviar Pedido Parcialmente Cancelado Cópia de Correio Eletrônico para</strong></td>
<td>Uma lista delimitada por vírgulas de endereços de email para envio de uma cópia de cada notificação.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Enviar Pedido Parcialmente Cancelado Método de Cópia</strong></td>
<td>O método de cópia de email — cópia de carbono — a ser usado.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
</tbody></table>

## Entregar para Armazenamento

<table>
<thead>
<tr>
<th><strong>Campo</strong></th>
<th><strong>Descrição</strong></th>
<th><strong>Escopo</strong></th>
<th><strong>Obrigatório</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>A Ordem Enviou Para Armazenar Produtos Remetente de Email</strong></td>
<td>Email enviado para a equipe de merchant especificada como um relatório agregado de todos os pedidos em aberto que não podem ser separados em um armazenamento de merchant até que seu inventário esteja disponível. </br></br> Os comerciantes podem usar esse relatório para iniciar e gerenciar transferências de inventário ou reposição de armazenamento para armazenamento. </br></br>Esta notificação só se aplica quando a variável [!DNL Ship-to-Store] estão ativados.
</br></br>Este rótulo não afeta a transportadora selecionada nem os rótulos disponíveis do método de entrega.</br></br></td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Enviar para armazenamento de destinatários de email</strong></td>
<td>Uma lista delimitada por vírgulas de endereços de email para envio de uma cópia de cada notificação.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Modelo de email</strong></td>
<td>O template de mensagem de email usado para notificar os recipients. Um template padrão é fornecido com a integração .</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
</tbody></table>

>[!NOTE]
>
>Se você permitir backorders, deverá fornecer um endereço de email de administrador para receber notificações sobre esses pedidos. Adicione o endereço às seguintes configurações: **[!UICONTROL Send Order Delayed Email Copy To]** no [Atraso no pedido](#order-delayed) modelo e [!UICONTROL Ship To Store Email Recipients] no [Entregar para Armazenamento](#ship-to-store) modelo .



