---
title: Testar e implantar o fornecimento da loja
description: Testar plano para verificar a funcionalidade de fornecimento de armazenamento. Os testes abrangem a API de Sincronização de inventário, o fluxo de trabalho de preenchimento completo para pedidos cancelados, o gerenciamento de usuários do aplicativo Store Fulfillment e a experiência de Check-in do cliente.
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '2652'
ht-degree: 0%

---


# Testar e implantar o fornecimento da loja no Adobe Commerce

Depois de concluir o processo de integração no ambiente de desenvolvimento, você pode iniciar o processo para testar e implantar a solução de preenchimento da loja no ambiente de produção.

**Pré-requisitos**

Antes de testar ou sincronizar quaisquer informações, lojas ou pedidos, verifique se você concluiu as seguintes tarefas:

- Concluído o [Configuração geral](enable-general.md) para serviços de fornecimento de armazenamento.

- [Adicione e valide as credenciais da conta e os detalhes da conexão para seus ambientes de sandbox e de produção](connect-set-up-service.md#configure-store-fulfillment-account-credentials)

- Confirme se a variável [Integração do Adobe Commerce](connect-set-up-service.md#configure-store-fulfillment-account-credentials) para a solução Store Fulfillment está disponível e autorizada.

## Preparar para teste

A configuração da conexão deve ser concluída antes que você possa criar quaisquer pedidos de teste ou executar testes de integração. Antes de testar, você também deve verificar se os dados da loja estão sincronizados.

1. Sincronizar fontes de fornecimento de armazenamento.

   - Ir para **[!UICONTROL Stores > Sources]**.

   - Selecionar **[!UICONTROL Synchronize Store Fulfillment Sources]**.

1. Na grade da loja, verifique se as lojas foram marcadas como `Synced` antes de criar pedidos de teste.

## Exemplo de plano de teste

Os varejistas validam a funcionalidade básica da solução Store Fulfillment durante as fases de configuração e teste de uma implantação. Este plano de teste de amostra fornece um ponto de partida para os testes. Adicione cenários adicionais com base em suas necessidades.

>[!NOTE]
>
>Depois de concluir a integração inicial para a solução Store Fulfillment ou atualizar uma instalação existente, sempre teste o aplicativo em um ambiente que não seja de produção antes de implantar na produção.

Este plano de ensaio de amostra abrange as seguintes áreas funcionais:

| Área funcional | Função | Função |
|-------------------------------------|------------------------------------------|----------------------------------|
| Sincronização de inventário e pedido | Sincronização da API de inventário | Administrador do Adobe Commerce |
| Fim a fim | Fluxos de Trabalho de Cancelamento de Ordem | Cliente, Administrador, Store Associate |
| Administrador | Armazenar permissões do aplicativo de preenchimento | Administrador |
| Adobe Commerce Frontend | Tipos de produto | Cliente, Administrador |
| Check-out de fronteira</br>Formulário de check-in | Experiência de Check-in | Cliente, Administrador |
| Aplicativo de assistência de loja | Pedido</br>Selecionar</br>Fase</br>e Handoff | Store Associate |




### Sincronização da API de inventário

Esta seção do plano de teste abrange a sincronização de inventário e pedido para verificar se as atualizações para fontes e estoques de coleta são sincronizadas corretamente entre o Adobe Commerce e a solução de disponibilização de armazenamento.

**Área funcional**: Sincronização de inventário e pedido</br>
**Função:** Administrador</br>
**Tipo de teste:** Todos positivos

<table>
<thead>
<tr>
<th>Função</th>
<th>Cenário de teste</th>
<th>Resultados esperados</th>
</tr>
</thead>
<tbody>
<tr>
<td><strong>Adicionar origem de estoque de retirada</strong></td>
<td>Salve uma nova fonte de estoque de retirada.</td>
<td>A sincronização em tempo real envia os detalhes da origem para o serviço do Walmart GIF em 5 minutos.</td>
</tr>
<tr>
<td><strong>Atualizar fonte de estoque de retirada existente</strong></td>
<td>Salve as atualizações em uma fonte de estoque de retirada existente.</td>
<td>A operação de sincronização em tempo real envia os detalhes para o GIF Walmart em 5 minutos</td>
</tr>
<tr>
<td><strong>Origem do estoque de retirada</br><code>Is Synced</code> status</br><code>Is Synced</code></strong></td>
<td>Salve as atualizações em uma fonte de estoque de retirada existente.</td>
<td>Após uma operação bem-sucedida, a variável <code>Is Synced</code> coluna da página Gerenciar Origem é atualizada de <code>No</code> para <code>Yes</code>.</td>
</tr>
<tr>
<td><strong>Processo de reserva de estoque modificado</strong></td>
<td>Crie e envie um novo pedido para um produto.</td>
<td>A quantidade comercializável do produto diminui em conformidade.</td>
</tr>
<tr>
<td><strong>Nova Envio de Pedido, Sincronização de API — Pedido do Cliente</strong></td>
<td>O cliente envia uma ordem de retirada de loja.</td>
<td><ul><li>Na exibição da Ordem de administração, uma <strong>Usuário administrador do Adobe Commerce</strong> vê que o status da Sincronização de pedidos foi atualizado para <code>Sent</code></li><li>O log de detalhes do pedido inclui a mensagem <code>Order was sent to BOPIS solution for sync, it’s not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>Nova Envio de Pedido, Sincronização de API — Envio de ordem de administrador</strong></td>
<td>Uma Adobe Commerce <strong>Administrador</strong> envia uma ordem de retirada.</td>
<td><ul><li>Na exibição Ordem de administração, o status da Sincronização de pedido é atualizado para <code>Sent</code>.</li><li>O log de detalhes do pedido inclui a mensagem <code>Order was sent to BOPIS solution for sync, it’s not yet acknowledged yet.</code></li></ul></td>
</tr>
<tr>
<td><strong>Nova Envio de Ordem, Fila de Exceção<strong></td>
<td>Identifique vários produtos virtuais e baixáveis no Administrador do Adobe Commerce que podem ser preenchidos por meio do Adobe Commerce sem exigir interação com o Serviço de preenchimento (FaaS).</td>
<td>Esses produtos são removidos ou sinalizados adequadamente na exportação para evitar um conflito de downstream com as FaaS.</td>
</tr>
</tbody>
</table>

### Fluxos de trabalho de Cancelamento de Ordem

Esta seção do plano de teste inclui cenários para testar o fluxo de trabalho completo para pedidos que são cancelados por meio do Adobe Commerce.

**Área funcional:** Administrador do Adobe Commerce</br>
**Função:** End-to-End (Administrador, Associado de Loja, Cliente)</br>
**Tipo de resultado do teste:** Positivo para todos os cenários

<table style="table-layout:fixed">
<tr>
<th>Função</th>
<th>Cenário</th>
<th>Resultados esperados</th>
</tr>
<tr>
<td><strong>Cancelamento de pedido completo</strong></td>
<td><ol>
<li>Colocar pedido.</li>
<li>Aguarde até que a ordem seja sincronizada.</li>
<li>Verifique o recebimento de criação de fatura (se autorizar e capturar) de email de fatura.</li>
<li>Criar Aviso de Crédito com todos os produtos solicitados na exibição NFF.</li>
</ol>
</td>
<td>
<ul>
<td>
<li>Histórico de pedidos atualizado com <code>We refunded $X online. Transaction ID: transactionID</code> e <code>Received Cancel acknowledgment from the BOPIS solution.</code></li>
<li>O status do pedido é <code>Closed</code>. (Definimos a REVISÃO DE PAGAMENTO agora.)</li>
<li>Aviso de crédito criado no Adobe Commerce. (Aguarde até que o cron funcione.)</li>
<li>Se todos os itens tiverem sido selecionados, estará pronto para receber email <code>DISPLAY COMMENT HISTORY</code> shows <code>Order is ready for pickup</code> (<code>CUSTOMER NOTIFIED</code> sinalizador é <code>true</code>.)</li>
<li>Se todos os itens não forem selecionados, o email de cancelamento e EXIBIR HISTÓRICO DE COMENTÁRIOS serão exibidos <code>Order has been canceled - all items were not available</code></li>
<li><code>CUSTOMER NOTIFIED</code> sinalizador é <code>true</code>.)</li>
</ul>
</td>
</tr>
<tr><td><strong>Cancelamento parcial de pedido<strong></td>
<td>
<ol>
<li>Fazer pedido com pelo menos dois produtos.</li>
<li>Aguarde até que a ordem seja sincronizada.</li>
<li>Verifique se a fatura foi criada (se autorizada e capturada) e se o email de fatura foi recebido.</li>
<li>Aguarde duas horas para a liquidação da transação.</li>
<li>Criar Aviso de Crédito com apenas parte dos produtos solicitados na exibição NFF.</li>
</td>
<td>
<ul>
<li>Atualização do histórico do pedido: <code>We refunded $X online. Transaction ID: transactionID</code></li>
<li>Atualização do histórico do pedido: <code>Order notified as partly canceled at: Date and Hour</code></li>
<li>Recebimento do email de reembolso de pedidos: <code>$x amount was refunded</code></li>
<li>O status do pedido é <code>Processing</code>.</li>
<li>Aviso de crédito criado no Adobe Commerce (aguarde até que o cron funcione).</li>
<li>Se alguns itens não foram selecionados, confirme se a variável [!UICONTROL Ready for Pickup] é exibido um email com a seção de separação ou reembolso. <code>DISPLAY COMMENT HISTORY</code> shows <code>Order is ready for pickup, but some items not available.</code>.</li>
<li><code>CUSTOMER NOTIFIED</code> sinalizador é <code>true</code>.</li>
</ul>
</td>
</tr>
<td><strong>Pronto para retirada</br></br>Cancelamento total</br>(todos os produtos são definidos como separados com 0 qty)</br></strong></td>
<td>
<ol>
<li>Coloque o pedido.</li>
<li>Aguarde até que a ordem seja sincronizada.</li>
<li>Verifique se a fatura foi criada (se autorizada e capturada) e se o email de fatura foi recebido.</li>
<li>Vá para a Postman e execute a solicitação Ready for Pickup com todos os produtos definidos como <code>picked</code> com <code>0 qty</code>.</li>
</ol>
</td>
<td>
<ul>
<li>Histórico de pedidos atualizado: <code>We refunded $X offline</code></li>
<li>O status do pedido é <code>CLOSED</code>.
<li>O Aviso de Crédito é criado. (Aguarde até que o cron funcione.)</li>
<li>E-mail de reembolso recebido: <code>$x amount was refunded</code></li>
<li>Email de cancelamento do pedido enviado.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Pronto para retirada - Cancelamento parcial</strong></br></br><strong>(Alguns produtos são escolhidos e alguns são escolhidos com <code>0 qty</code>)</strong>
</td>
<td>
<ol>
<li>Coloque o pedido.</li>
<li>Aguarde até que a ordem seja sincronizada.</li>
<li>Verifique se a fatura foi criada (se autorizada e capturada) e se o email de fatura foi recebido.</li>
<li>Vá para a Postman e execute a solicitação Ready for Pickup com parte dos produtos definidos como escolhidos com 0 quantidade e o restante foi selecionado.</li>
</ol>
</td>
<td>
<ul>
<li><code>Your order is ready for pickup</code> com [!UICONTROL Ready for Pickup Items] e [!UICONTROL Canceled Items] tabelas. </li>
<li>O status do pedido é READY FOR PICKUP. </li>
<li>Histórico de pedidos atualizado: <code>We refunded $X offline.</code>
<li>Histórico de pedidos atualizado: <code>Order notified as partly canceled at: Date and hour</code>
<li>E-mail de reembolso recebido: <code>$x amount was refunded</code>
<li>O aviso de crédito é criado. (Aguarde até que o cron funcione.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Pronto para retirada - Cancelamento parcial</br></br>Alguns produtos são escolhidos e alguns são escolhidos com <code>0 qty</code>)</strong>
</td>
<td><ol>
<li>Coloque o pedido.</li>
<li>Aguarde até que a ordem seja sincronizada.</li>
<li>Verifique se a fatura foi criada (se autorizada e capturada) e se o email de fatura foi recebido.</li>
<li>Vá para a Postman e execute a solicitação Ready for Pickup com parte dos produtos definidos como escolhidos com 0 quantidade e o restante foi selecionado.</li>
</ol>
</td>
<td><ul>
<li><code>Your order is ready for pickup</code> com [!UICONTROL Ready for Pickup Items] e [!UICONTROL Canceled Items] tabelas. </li>
<li>O status do pedido é READY FOR PICKUP. </li>
<li>Histórico de pedidos atualizado: <code>We refunded $X offline.</code>
<li>Histórico de pedidos atualizado: <code>Order notified as partly canceled at: Date and hour</code>
<li>E-mail de reembolso recebido: <code>$x amount was refunded</code>
<li>O aviso de crédito é criado. (Aguarde até que o cron funcione.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Dispensado (durante a administração) </br></br>Cancelamento total (todos os produtos são definidos como rejeitados)</strong>
</td>
<td>
<ol>
<li>Coloque o pedido.</li>
<li>Aguarde até que a ordem seja sincronizada.</li>
<li>Verifique se a fatura foi criada (se autorizada e capturada) e se o email de fatura foi recebido.</li>
<li>Vá para a Postman e execute a solicitação Ready for Pickup com todos os produtos definidos como selecionados.</li>
<li>Abra a caixa de correio e localize o e-mail Ready for Pickup (Pronto para retirada). Em seguida, clique em **[!UICONTROL Confirm Arrival]**.</li>
<li>Fazer check-in.</li>
<li>Vá para o Postman e execute a solicitação Dispensed com todos os produtos definidos como rejeitados.</li>
</ol>
<td><ul>
<li>Histórico de pedidos atualizado: <code>We refunded $X offline.</code></li>
<li>E-mail de reembolso recebido: <code>$x amount was refunded</code></li>
<li>Status definido como <code>CLOSED</code>.</li>
<li>Aviso de crédito criado. (Aguarde até que o cron funcione.)</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Dispensado (durante a administração)</br></br>Cancelamento parcial</br>(Alguns produtos são dispensados; alguns são rejeitados.)</strong>
</br></td>
<td>
<ol>
<li>Coloque o pedido.</li>
<li>Aguarde até que a ordem seja sincronizada.</li>
<li>Verifique se a fatura foi criada (se autorizada e capturada) e se o email de fatura foi recebido.</li>
<li>Vá para o Postman e execute a solicitação Ready for Pickup com todos os produtos definidos como selecionados.</li>
<li>Abra sua caixa de correio. Encontre o email Pronto para Seleção e selecione <code>Confirm Arrival</code>.</li>
<li>Fazer check-in.</li>
<li>Vá para a Postman e execute a solicitação Dispensed com alguns produtos definidos como dispensados e alguns definidos como rejeitados</li>
</ol>
</td>
<td>
<li>Histórico de pedidos atualizado: <code>We refunded $X offline</code></li>
<li><code>Order notified as partly canceled at: Date and Hour</code>
<li>E-mail de reembolso recebido: <code>$x amount was refunded</code>
<li>Status do pedido definido como <code>Ready for pickup Dispensed</code>
<li>Aviso de crédito criado. (Aguarde até que o cron funcione.)</li>
</td>
</tr>
<tr>
<td> <strong>Nova RMA após retorno (completa)</strong>
</td>
<td>
<ol>
<li>Coloque o pedido.</li>
<li>Aguarde até que a ordem seja sincronizada.</li>
<li>Verifique se a fatura foi criada (se autorizada e capturada) e se o email de fatura foi recebido.</li>
<li>Escolha todos os produtos com o Postman.</li>
<li>Fazer check-in.</li>
<li>Faça uma despesa.</li>
<li>Acesse a ordem e selecione<strong>[!UICONTROL Create returns]=
<li>Crie o RMA.</li>
</ol>
</td>
<td>
<ul>
<li>O RMA foi criado e é exibido abaixo do <strong>[!UICONTROL Returns]</b> na exibição Ordem.</li>
<li>O cliente recebeu o email de confirmação RMA.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Nova RMA após retorno — Parcial</strong>
</td>
<td>
<ol>
<li>Coloque o pedido.</li>
<li>Aguarde até que a ordem seja sincronizada.</li>
<li>Verifique se a fatura foi criada (se autorizada e capturada) e se o email de fatura foi recebido.</li>
<li>Escolha todos os produtos com o Postman.</li>
<li>Fazer check-in.</li>
<li>Faça uma despesa.</li>
<li>Acesse o pedido e selecione  <strong>[!UICONTROL Create returns]</strong></li>
<li>Crie o RMA com parte dos produtos solicitados.</li>
</ol>
<td>
<ul>
<li>RMA criada e exibida abaixo do <strong>[!UICONTROL Returns]</strong> na exibição Ordem.</li>
<li>O cliente recebeu o email de confirmação RMA.</li>
<li>Após criar o RMA, obtenha a autorização do RMA: Em Admin, acesse <strong>[!UICONTROL Sales > Returns]</strong>. Selecione o RMA que você criou e o autorize.</li>
<li>Verifique se o cliente recebeu o email de confirmação de autorização de RMA.</li>
<li>Verifique se o reembolso foi adicionado às transações e ao histórico do pedido.</li>
</ul>
</td>
</tr>
</table>


### Armazenar permissões do aplicativo de preenchimento

Esta seção do plano de teste cobre o gerenciamento de conta para usuários do aplicativo de preenchimento da loja.

- Confirme se um Associado de loja pode se autenticar com uma nova conta de usuário criada a partir do Administrador do Adobe Commerce.
- Confirme se as atualizações nas contas existentes foram aplicadas com êxito.

**Área funcional:** Administrador do Adobe Commerce</br>
**Função:** Administrador, Store Associate</br>
**Tipo de teste:** Todos positivos

<table style="table-layout:auto">
<tr>
<th>Função</th>
<th>Cenário</th>
<th>Resultados esperados</th>
</tr>
<tr>
<td><strong>Gerenciamento de conta de usuário - Criar conta</strong></br></br>
</td>
<td>
<ol>
<li><strong>Administrador</strong> — Faça logon no Administrador do Adobe Commerce</li>
<li>Ir para <strong>[!UICONTROL System] &gt; Armazenar Permissões do Aplicativo de Cumprimento &gt; Todos os Usuários do Aplicativo de Cumprimento da Loja</strong></li>
<li><strong>Adicionar novo usuário.</strong></li>
</ol>
<td>
<ul>
<li>Conta criada com êxito.</li>
<li>Nova conta de usuário é exibida na página [!UICONTROL Store Fulfillment Users] painel.</li>
<li><strong>Store Associate</strong> faça logon no aplicativo Store Assist com uma nova conta de usuário.</li>
</ul>
</td>
</tr>
<tr>
<td><strong>Gerenciamento de conta de usuário - Atualizar conta de usuário existente</strong>
</td>
<td>
<ol>
<li>Faça logon no Administrador do Adobe Commerce com a conta de usuário Admin.</li>
<li>Ir para <strong>[!UICONTROL System] &gt; Armazenar Permissões do Aplicativo de Cumprimento &gt; Todos os Usuários do Aplicativo de Cumprimento da Loja</strong>.</li>
<li>Na lista Conta de usuário, abra uma conta de usuário ativa existente selecionando <strong>[!UICONTROL Edit]</strong>.
<li>Desative a conta alterando <strong>[!UICONTROL Is Active]</strong> para <strong>Não</strong>.</li>
</ol>
</td>
<td>
<ul>
<li>No <strong>[!UICONTROL Store Fulfillment App Users]</strong> no painel, o status da conta atualizada foi alterado para <strong>[!UICONTROL Inactive]</strong>.</li>
<li>O Store Associate não pode fazer logon no aplicativo Store Assist com as credenciais de conta inativas.</li>
</ul>
</td>
</tr>
</table>

## Tipos de produtos Adobe Commerce

Os cenários de teste para os Tipos de produto do Adobe Commerce verificam se os clientes veem as informações corretas de produto, estoque e método de entrega para diferentes tipos de produto:

- [!UICONTROL Configurable]
- [!UICONTROL Grouped]
- [!UICONTROL Virtual]
- [!UICONTROL Bundle products] na loja da Adobe Commerce.

**Área funcional:** Adobe Commerce Frontend</br>
**Função:** Usuário do aplicativo de assistência de armazenamento (Associado da loja)</br>
**Tipo de teste:** Todos positivos

<table style="table-layout:auto">
<tr>
<th>Função</th>
<th>Cenário</th>
<th>Comentários</th>
</tr>
<tr>
<td><strong>Produtos configuráveis</strong>
</td>
<td>
<ul>
<li>Verifique se o usuário pode ver apenas as opções configuráveis, qual fonte está ativada, o estoque está atribuído e se há alguns itens em estoque — verifique os produtos secundários.</li>
<li>Verifique se, ao selecionar uma loja diferente, as opções que não estão disponíveis são exibidas como riscadas.</li>
<li>Verifique se, se o usuário selecionar uma loja diferente, as opções configuráveis serão desselecionadas.</li>
<li>Verifique se um produto configurável já está no carrinho e se um usuário seleciona uma loja diferente, o produto aparece como esgotado.</li>
</ul>
</td>
<td></td>
</td>
</tr>
<tr>
<td><strong>Produtos agrupados</strong>
</td>
<td>
<ul>
<li>Verifique se os métodos de Delivery e [!UICONTROL Add to cart] são desabilitados para o cliente quando todos os produtos filho tiverem
<code>qty</code> defina como <code>0</code>.</li>
<li>Verifique se os métodos de entrega estão habilitados para o cliente quando pelo menos um dos produtos filho tiver <code>qty</code> defina como <code>0.</code></li>
<li>Verifique se [!UICONTROL Store Pickup Delivery] é visível e ativa apenas para os produtos que têm [!UICONTROL Available for Store Pickup] habilitado. (Verificar produto secundário.)</li>
</ul>
</td>
<td></td>
</tr>
<tr>
<td><strong>Produtos virtuais</strong>
</td>
<td>
Verifique se os produtos virtuais não oferecem a variável  [!UICONTROL In-store Pickup] método de delivery.
<td></td>
</td>
</tr>
<tr>
<td><strong>Produtos do pacote</strong>
</td>
<td>
<ul>
<li>Verifique se pelo menos um produto filho tem [!UICONTROL Available for Store Pickup] desativado, a opção Store Pickup delivery não está disponível para o cliente.</li>
<li>Verifique se pelo menos um produto filho tem [!UICONTROL Available for Home Delivery] desativado, a opção Home Delivery não está disponível para o cliente.</li>
<li>Verifique se pelo menos um dos produtos filho em um pacote está indisponível, o pacote (produto pai) também é mostrado como [!UICONTROL Out of stock].</li>
</ul>
</td>
<td></td>
</tr>
<tbody>
</table>

## Experiência de Check-in

Esta seção do plano de teste cobre a experiência de check-in para pedidos de retirada de loja para os seguintes recursos:

- Contato de retirada alternativo — Verifique o fluxo de trabalho para adicionar um [!UICONTROL Alternate Pickup Contact] e selecionando um [!UICONTROL Preferred Contact] em Ordens de retirada da loja.

- Formulário de check-in - Verifique o fluxo de trabalho para enviar uma solicitação de check-in para pedidos de retirada da Loja.

**Áreas funcionais:** Check-out do carrinho, Formulário de check-in para pedidos de retirada de loja</br>
**Função:** Administrador, Cliente, Store Associate</br>
**Tipo de teste:** Todos positivos

### Contato de Selecionador Alternativo


**Área funcional:** Check-out do carrinho</br>
**Função:** Cliente</br>
**Tipo de teste:** Todos positivos

<table style="table-layout:auto">
<tr>
<th>Função</th>
<th>Cenário</th>
<th>Resultados esperados</th>
</tr>
<tr>
<td><strong>Contato de Selecionador Alternativo</br>
Check-in</br><strong>
</td>
<td>
Um cliente envia um pedido com a opção Retirada na loja.</td>
<td>Durante o processo de finalização, o cliente visualiza o [!UICONTROL Alternate Pickup Contact] a opção na etapa Entrega.
</td>
</tr>
<tr>
<td><strong>Contato Preferencial de Seleção Alternativo, Fazer Check-in</strong>
<td>
Um cliente envia um pedido com a opção Retirada na loja. Durante o check-out, o cliente adiciona um [!UICONTROL Alternate Pickup Contact].</td>
<td>Durante o processo de finalização, o cliente visualiza o [!UICONTROL Preferred Contact] na etapa de envio.</td>
</td>
</tr>
<tr>
<td><strong>Detalhes do Contato de Coleta Alternativo, Check-in</strong>
</td>
<td>
Um cliente envia um pedido com a opção Retirada na loja. Durante o check-out, o cliente seleciona [!UICONTROL Alternate Pickup Contact] na etapa de envio.
</td>
<td>O cliente vê opções de entrada para inserir detalhes de contato: [!UICONTROL First name], [!UICONTROL Last name], [!UICONTROL Phone]e [!UICONTROL Email].</td>
</tr>
<tr>
<td><strong>Seleção alternativa, Check in Email</strong>
</td>
<td>Um cliente envia um pedido com a opção Retirada na loja. Durante o check-out, o cliente seleciona [!UICONTROL Alternate Pickup Contact] na etapa de envio, adiciona os detalhes do contato e envia o pedido.</td>
<td>Tanto o cliente quanto o contato alternativo recebem um Email de Check-in para o pedido.</td>
</tr>
<td><strong>Seleção alternativa, Detalhes do pedido</strong></td>
<td>Um cliente envia um pedido com a opção Retirada na loja. Durante o check-out, o cliente seleciona [!UICONTROL Alternate Pickup Contact] na etapa de envio, adiciona os detalhes do contato e envia o pedido.</td>
<td>O administrador vê as informações de contato adicionais na ordem salva.</td>
</tr>
<tr>
<td><strong>Contato de Selecionador Alternativo, Exibição de Ordem Associada de Loja</strong>
</td>
<td>Um cliente envia um pedido com a opção Retirada na loja. Durante o check-out, o cliente seleciona [!UICONTROL Alternate Pickup Contact] na etapa de envio, adiciona os detalhes do contato e envia o pedido.</td>
<td>O Store Associate pode ver as informações de contato adicionais sobre o pedido no FaaS/ChaaS.</td>
</td>
</tr>
</tbody>
</table>

### Formulário de check-in


**Área funcional:** Formulário de check-in</br>
**Função:** Cliente</br>
**Tipo de teste:** Todos positivos

<table style="table-layout:auto">
<tr>
<th>Função</th>
<th>Cenário</th>
<th>Resultados esperados</th>
</tr>
<tr>
<td><strong>Ação de Check-in — Enviar solicitação</strong>
</td>
<td>No formulário de check-in, um cliente preenche todos os campos obrigatórios e envia a solicitação.</td>
<td>O cliente recebe uma resposta bem-sucedida.</td>
</tr>
<tr>
<td><strong>Verificar Ação — Exibir detalhes da solicitação</strong></td>
<td>Um cliente envia com êxito uma solicitação de check-in.</td>
<td>O status do pedido é atualizado no sistema FaaS, e o Store Associate pode ver os detalhes da solicitação de check-in nas FaaS.
</td>
</tr>
<tr>
<td><strong>Ação de Check-in — Enviar solicitação apenas uma vez</strong></td>
<td>Depois de enviar uma solicitação de check-in para um pedido, um cliente seleciona o link para fazer check-in uma segunda vez.</td>
<td>No formulário de check-in, o cliente não vê uma opção para editar ou reenviar o formulário.</td>
</tr>
<tr>
<td><strong>Verificar Ação — Confirmar Chegada</strong></td>
<td>Uma ordem de retirada na loja é marcada pronta para retirada no FaaS. O cliente recebe um email Pronto para Seleção e seleciona [!UICONTROL Confirm Arrival].</td>
<td>O cliente vê o formulário de check-in do pedido.</td>
</tr>
</tbody>
</table>

## Aplicativo de assistência da loja

Esta seção do plano de teste cobre cenários para workflows de ordem de teste, separação e manipulação no aplicativo de assistência de loja.

**Área funcional:** Aplicativo de assistência de loja</br>
**Função:** Store Associate</br>
**Tipo de teste:** Todos positivos

<table style="table-layout:auto">
<tr>
<th>Função</th>
<th>Cenário</th>
<th>Resultados esperados</th>
</tr>
<tr>
<td>
<strong>Caminho feliz de escolha de pedido único, retirada de lado da curva</strong></td>
<td>Escolha itens de quantidade única e múltipla. Sem nilpicks e coleta de lado da curva (com preparo).
</td>
<td>
</td>
</tr>
<tr>
<td><strong>Separação de várias ordens — caminho feliz, retirada de lado da curva</strong></td>
<td>Itens únicos e de várias quantidades. Sem nilpicks e coleta de lado da curva (com preparo)</td>
<td></td>
</tr>
<tr>
<td><strong>Escolha de pedido único — caminho feliz na loja</strong></td>
<td>Itens únicos e de várias quantidades. Sem links e coleta de instância (com armazenamento temporário)</td>
<td>
</td>
</tr>
<tr>
<td><strong>Separação de vários pedidos — caminho feliz, retirada na loja</strong></td>
<td>Escolha itens de quantidade única e múltipla. Sem nilpicks e coleta de lado da curva (com preparo).</td>
<td></td>
</tr>
<tr>
<td><strong>Escolha de pedido único — caminho não feliz, retirada na loja</strong></td>
<td>Escolha itens únicos e de várias quantidades com separação parcial e automática e coleta instantânea (com armazenamento temporário)</td>
</td>
<td></td>
</tr>
<td><strong>Separação de várias ordens — não a retirada de lado de caminho feliz</strong></td>
<td>Escolha itens únicos e de várias quantidades com separação parcial e automática e coleta instantânea (com armazenamento temporário)</td>
<td></td>
</tr>
<td><strong>Escolha de pedido único — caminho não feliz, escolha de lado a lado</strong></td>
<td>Escolha itens únicos e de várias quantidades com separação parcial e pontiaguda e curva (com armazenamento temporário)</strong></td>
</td>
<td></td>
</tr>
<tr><td><strong>Pedido feito - cancelado antes da separação</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>Pedido colocado - cancelado antes da apresentação</strong></td>
<td></td>
<td></td>
</tr>
<tr>
<td><strong>Pedido colocado - pesquisa no módulo de ordem</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>Pedido colocado - pesquisa e check-in manual para hashdoff</strong></td>
<td></td>
<td></td>
</tr>
<tr><td><strong>Pedido colocado - todos os itens escolhidos ou não disponíveis marcados pelo seletor</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Pedido colocado com itens do pacote - separação e handoff</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Pedido colocado - Mão livre com rejeição</strong></td>
<td></td>
<td></td></tr>
<tr><td><strong>Pedido colocado - Mão desligada com rejeição de todos os itens</strong></td>
<td></td>
<td></td></tr>
</tbody>
</table>



## Implantar

Após verificar que a solução foi configurada e testada de acordo com suas especificações, você estará pronto para implantar do armazenamento temporário à produção.

A implantação e o teste variam dependendo da infraestrutura e das capacidades.

>[!TIP]
>
>Para obter diretrizes de implantação, listas de verificação e práticas recomendadas do Adobe Commerce em projetos de infraestrutura em nuvem, consulte [Implantar a loja](https://devdocs.magento.com/cloud/live/stage-prod-live.html) na documentação do desenvolvedor do Adobe Commerce.




















