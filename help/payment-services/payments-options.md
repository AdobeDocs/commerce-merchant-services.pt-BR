---
title: Opções de pagamento
description: Defina as opções de pagamento para personalizar os métodos disponíveis para os clientes da loja.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
source-git-commit: bfb2b6632fe494d6e392c214f5e3f5a11930c0b2
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 0%

---

# Opções de pagamento

Com Adobe Commerce e Magento Open Source [!DNL Payment Services], você tem várias opções de pagamento disponíveis. Você pode configurar essas opções de pagamento por meio de:

* [Painel](configure-dashboard.md)
* [Configuração da loja](configure-admin.md) (recomendado para opções de pagamento herdadas ou uma configuração de várias lojas)

Há comportamentos diferentes para cada método de pagamento, dependendo de onde você está no processo de finalização:

* Página do produto — A página do produto de um item
* Minicarrinho—Disponível após clicar no ícone do carrinho quando um produto é adicionado ao carrinho
* Carrinho de compras—Disponível após o clique de _Exibir e editar carrinho_ do minicarrinho
* Exibição de finalização de compra — Disponível após clicar de _Prossiga para o check-out_ do minicarrinho ou carrinho de compras

>[!IMPORTANT]
>
>A integração dos serviços de pagamento deve ser concluída antes de os pagamentos poderem ser processados.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] fornecer uma verificação simples e segura dos métodos de pagamento com cartão de crédito ou cartão de débito. Quando um comprador faz o check-out usando campos de cartão de crédito, ele informa o nome, o endereço de cobrança e as informações do cartão de crédito ou de débito, para fazer o pedido. As informações do cliente são usadas com segurança durante a sessão de compra para orientá-las perfeitamente durante o fluxo de finalização.

Você pode configurar [!UICONTROL Credit Card Fields] na configuração da loja ou no painel Serviços de Pagamento. Consulte [Configuração [!DNL Payment Services]](configure-dashboard.md#configure-credit-card-fields) para obter mais informações.

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons], que usam o PayPal para concluir uma compra, armazena o endereço de envio do comprador, endereços de faturamento e detalhes de pagamento para uso posterior. Os compradores podem usar qualquer método de pagamento armazenado ou oferecido anteriormente pelo PayPal.

Você pode configurar [!DNL PayPal Smart Buttons] na configuração da loja ou no painel Serviços de Pagamento.  Consulte [Configuração [!DNL Payment Services]](configure-dashboard.md#configure-paypal-smart-buttons) para obter mais informações.

### Botão PagarPal

Os clientes podem fazer check-out com facilidade e confiança usando o botão PayPal .

O botão PayPal é visível da página do produto, do minicarrinho, do carrinho de compras e das visualizações de check-out.

### Botão Venmo

Os clientes podem fazer check-out usando o [Venmo](https://venmo.com/) botão.

O botão Venmo é visível da página do produto, do minicarrinho, do carrinho de compras e das visualizações de check-out.

### [!DNL Pay Later] botão

Ofereça a seus clientes pagamentos de curto prazo, sem juros e outras opções de financiamento para que possam comprar agora e pagar mais tarde com o [!DNL Pay Later] botão.

O [!DNL Pay Later] é visível da página do produto, do minicarrinho, do carrinho de compras e das visualizações de check-out.

Há duas opções de pagamento com a variável [!DNL Pay Later] botão:

* **Pagamento em 4**—Os clientes podem pagar o saldo da sua ordem em quatro pagamentos sem juros (de duas em duas semanas) após um pagamento inicial. Consulte a [Pagar na documentação 4](https://www.paypal.com/us/digital-wallet/ways-to-pay/buy-now-pay-later) para obter mais informações.
* **Crédito PayPal**—Os clientes podem pagar o saldo total do seu pedido ao longo de seis meses, sem juros. Consulte a [Documentação de crédito PayPal](https://www.paypal.com/us/webapps/mpp/paypal-credit) para obter mais informações.

### [!DNL Pay Now] botão

O [!DNL Pay Now] é visível na janela pop-up PayPal quando um cliente clica em um botão de pagamento na tela de pagamentos.

Se o valor final do pedido ainda não for conhecido (como quando você ainda não tem informações de endereço de envio) e o cliente estiver em processo de fazer check-out da página do produto, do minicarrinho ou do carrinho de compras, um _Continuar_ em vez disso, o botão está disponível. Quando um cliente clica em _Continuar_, depois de confirmar o método de pagamento, eles são direcionados a uma página de revisão do pedido para coletar os detalhes necessários antes de concluir o check-out.

## [!DNL Pay Later] mensagens

Para ajudar seu cliente a identificá-las como possíveis opções de pagamento, [!DNL Pay Later] as mensagens são visíveis na página do produto, no minicarrinho e carrinho de compras e durante o check-out.

* **Quando um cliente seleciona um produto entre US$ 30 e US$ 600**, mensagens no PayPal e [!DNL Pay Later] Esse botão fornece ao cliente mais informações sobre a opção de pagamento Pagamento em 4. Os clientes podem clicar em **Saiba mais** para saber mais sobre a opção &quot;Pagar em 4&quot; _ou_ clique no texto &quot;Ou veja o financiamento especial de 6 meses&quot; no pop-up para saber mais sobre a opção Crédito do PayPal e se candidatar a ela.
* **Quando um cliente seleciona um produto ou produtos acima de US$ 98,99**, mensagens no PayPal e [!DNL Pay Later] Os botões fornecem aos clientes mais informações sobre a opção de pagamento Crédito PayPal. Os clientes podem clicar em **Saiba mais** para saber mais sobre a opção Crédito do PayPal e se candidatar a ela _ou_ clique no texto &quot;Ou veja Pagamento em 4&quot; no pop-up para saber mais sobre a opção Pagamento em 4.

   >[!NOTE]
   >
   >Os montantes acima indicados estão sujeitos a alterações.

Consulte [Configurar [!DNL Payment Services]](configure-admin.md#configure-paypal-smart-buttons) para saber como desativar ou ativar o [!DNL Pay Later] mensagem.

## Recálculo de pedido

Quando um cliente entra no fluxo de finalização do minicarrinho, carrinho de compras ou página de produto, ele é direcionado para uma página de revisão do pedido, onde pode ver o endereço de envio selecionado em uma janela pop-up PayPal. Depois que o cliente seleciona o método de entrega, a quantia da ordem é recalculada adequadamente e o cliente pode ver os custos e impostos de entrega.

Quando um cliente entra no fluxo de finalização da página de finalização, o sistema já está ciente do endereço de envio e do valor calculado final, e os totais são devidamente representados.

Os feriados fiscais, os custos de envio e o imposto sobre vendas podem variar bastante de um local para outro. Depois [!DNL Payment Services] recebe o endereço e a taxa de frete, recalcula rapidamente todos os custos aplicáveis e os exibe adequadamente durante os últimos estágios do check-out.

## Check-out da página do produto

Quando um cliente faz o check-out diretamente da página do produto, usando o PayPal ou [!DNL Pay Later] botões, somente o item representado na página de produto atual é comprado. Os itens que já residem no carrinho do cliente não são adicionados ao fluxo de check-out e não são comprados.

Se o cliente cancelar o pedido, o item na página de produto atual será adicionado ao carrinho do cliente, unindo quaisquer outros itens presentes no carrinho. Essa função permite que o cliente compre rapidamente o item que está visualizando no momento, além de manter quaisquer outros itens que adicionou ao carrinho anteriormente ao navegar pelos produtos.

Quando um cliente entra no fluxo de finalização da página do produto, a página de finalização é simplificada. A visualização mostra apenas dados e opções relacionados ao pedido.

## Segurança

Consulte [Conformidade com a PCI](security.md#pci-compliance) para obter mais informações.
