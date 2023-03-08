---
title: Opções de pagamento
description: Defina as opções de pagamento para personalizar os métodos disponíveis para seus clientes de loja.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
source-git-commit: 31665f90909ce2364579fc7f9c97087e2376c0a6
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 0%

---

# Opções de pagamento

Com [!DNL Adobe Commerce] e [!DNL Magento Open Source] [!DNL Payment Services], você tem várias opções de pagamento disponíveis. É possível configurar essas opções de pagamento por meio de:

* [Configurações da página inicial](payments-home.md)
* [Armazenar configuração](configure-admin.md) (recomendado para opções de pagamento herdadas ou configuração de várias lojas)

Há comportamentos diferentes para cada método de pagamento, dependendo de onde você está no processo de finalização:

* Página do produto — A página de produto de um item
* Minicarrinho — Disponível após clicar no ícone do carrinho quando um produto foi adicionado ao carrinho
* Carrinho de compras — Disponível após clicar em _Exibir e editar carrinho_ do minicarrinho
* Exibição de check-out — disponível ao clicar em _Prosseguir para o check-out_ do minicarrinho ou carrinho de compras

>[!IMPORTANT]
>
>A integração dos Serviços de pagamento deve ser concluída para que os pagamentos possam ser processados.

## [!UICONTROL Credit Card Fields]

[!UICONTROL Credit Card Fields] forneça um checkout simples e seguro para métodos de pagamento com cartão de crédito ou débito. Quando um comprador faz o check-out usando campos de cartão de crédito, ele insere seu nome, endereço de cobrança e informações de cartão de crédito ou débito para fazer seu pedido. As informações de seus clientes são usadas com segurança durante a sessão de compra para orientá-los perfeitamente pelo fluxo de finalização.

Ativar [compartimentalização de cartão de crédito](#vaulting) para que suas lojas permitam que os compradores guardem (salvem) suas informações de cartão de crédito para um check-out rápido posteriormente.

Você pode configurar [!UICONTROL Credit Card Fields] na configuração da loja ou na Página Inicial dos Serviços de Pagamento. Consulte [Configurações](settings.md#credit-card-fields) para obter mais informações.

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons], que usam o PayPal para concluir uma compra, armazena o endereço de entrega, os endereços de cobrança e os detalhes de pagamento do comprador para uso posterior. Os compradores podem usar qualquer método de pagamento armazenado ou oferecido anteriormente pelo PayPal.

![[!DNL PayPal Smart Buttons] opções](assets/buttons-md.png)

Você pode configurar [!UICONTROL PayPal Smart Buttons] na configuração da loja ou na Página Inicial dos Serviços de Pagamento.  Consulte [Configurações](settings.md#payment-buttons) para obter mais informações.

### [!DNL PayPal] botão

Os clientes podem fazer check-out com facilidade e confiança usando o botão PayPal.

A variável [!DNL PayPal] O botão é visível nas exibições página do produto, minicarrinho, carrinho de compras e check-out.

### [!DNL Venmo] botão

Os clientes podem fazer check-out usando o [Venmo](https://venmo.com/) botão.

A variável [!DNL Venmo] O botão é visível nas exibições página do produto, minicarrinho, carrinho de compras e check-out.

### [!DNL Apple Pay] botão

Os clientes podem usar a Touch ID em seus dispositivos para usar [[!DNL Apple Pay]](https://www.apple.com/apple-pay/), que utilizam credenciais de pagamento de cartão de crédito e débito armazenadas em seus dispositivos iOS ou macOS.

A variável [!DNL Apple Pay] O botão é visível nas exibições página do produto, minicarrinho, carrinho de compras e check-out.

>[!NOTE]
>
> Para usar o Apple Pay, entre em contato com seu representante de vendas ou com a Equipe de conta do Adobe para ativá-lo para suas lojas ao vivo.

### [!DNL Pay Later] botão

Ofereça aos clientes pagamentos de curto prazo, sem juros e outras opções de financiamento para que eles possam comprar agora e pagar posteriormente com o [!DNL Pay Later] botão.

A variável [!DNL Pay Later] O botão é visível nas exibições da página do produto, minicarrinho, carrinho de compras e check-out:

* **Quando um cliente seleciona um produto entre US$ 30 e US$ 600**, mensagens no PayPal e [!DNL Pay Later] fornece ao cliente mais informações sobre a [!DNL Pay in 4] opção de pagamento. Os clientes podem clicar em **Saiba mais** para saber mais sobre o &quot;[!DNL Pay in 4]opção &quot; _ou_ clique no texto &quot;Or see 6 months special financing&quot; no pop-up para saber mais e solicitar a opção PayPal Credit.
* **Quando um cliente seleciona um ou mais produtos acima de US$ 98,99**, mensagens no PayPal e [!DNL Pay Later] oferece aos clientes mais informações sobre a opção de pagamento PayPal Credit. Os clientes podem clicar em **Saiba mais** para conhecer e solicitar a opção PayPal Credit, _ou_ clique no texto &quot;Ou veja Pagar em 4&quot; no pop-up para saber mais sobre a [!DNL Pay in 4] opção.

   >[!NOTE]
   >
   >Os valores listados acima estão sujeitos a alterações.

Consulte [Configurações](settings.md#payment-buttons) para saber como desativar/ativar o [!DNL Pay Later] mensagens.

Há duas opções de pagamento com a variável [!DNL Pay Later] botão:

* **Pagamento em 4**—Os clientes podem pagar o saldo do pedido em quatro pagamentos sem juros (a cada duas semanas) após uma entrada inicial. Consulte a [Documentação do Pay in 4](https://www.paypal.com/us/digital-wallet/ways-to-pay/buy-now-pay-later) para obter mais informações.
* **Crédito do PayPal**— os clientes podem pagar o saldo total do pedido em seis meses, sem juros. Consulte a [Documentação de crédito do PayPal](https://www.paypal.com/us/webapps/mpp/paypal-credit) para obter mais informações.

### [!DNL Pay Now] botão

A variável [!DNL Pay Now] O botão está visível na janela pop-up do PayPal quando um cliente clica em um botão de pagamento na tela de pagamentos.

Se o valor final do pedido ainda não for conhecido (como quando você ainda não tem informações sobre o endereço de entrega) e o cliente estiver no processo de finalização da página do produto, do minicarrinho ou do carrinho de compras, uma _Continuar_ botão está disponível. Quando um cliente clica em _Continuar_ Depois de confirmar o método de pagamento, ele é direcionado a uma página de revisão do pedido para coletar os detalhes necessários antes de concluir a finalização da compra.

## Recálculo de pedido

Quando um cliente entra no fluxo de finalização do minicarrinho, carrinho de compras ou página do produto, ele é direcionado a uma página de revisão do pedido, onde pode ver o endereço de envio selecionado em uma janela pop-up do PayPal. Depois que o cliente selecionar o método de entrega, a quantia da ordem será recalculada apropriadamente e o cliente poderá ver os custos e impostos de entrega.

Quando um cliente entra no fluxo de finalização da página de finalização da compra, o sistema já sabe o endereço de entrega e o valor final calculado, e os totais são devidamente representados.

Feriados fiscais, custos de envio e imposto sobre vendas podem variar amplamente de local para local. Depois [!DNL Payment Services] recebe o endereço e a taxa de entrega, ele recalcula rapidamente todos os custos aplicáveis e os exibe adequadamente durante os últimos estágios da finalização.

## Check-out da página do produto

Quando um cliente faz o check-out diretamente da página do produto, usando o PayPal ou [!DNL Pay Later] , somente o item representado na página atual do produto é comprado. Os itens que já residem no carrinho do cliente não são adicionados ao fluxo de check-out e não são comprados.

Se o cliente cancelar o pedido, o item na página do produto atual será adicionado ao carrinho do cliente, juntando todos os outros itens presentes no carrinho. Essa função permite que o cliente compre rapidamente o item que está visualizando no momento, além de reter quaisquer outros itens adicionados ao carrinho anteriormente ao navegar pelos produtos.

Quando um cliente entra no fluxo de check-out da página do produto, a página de check-out é simplificada — a visualização mostra apenas os dados e as opções relacionados ao pedido.

## Compartimentalização de cartão de crédito

Os compradores podem arquivar (ou &quot;salvar&quot;) suas informações de cartão de crédito para compras futuras no nível do site (qualquer loja na conta do mesmo comerciante).

Consulte [Compartimentalização de cartão de crédito](vaulting.md) para obter mais informações.

## Segurança

Consulte [Conformidade com o PCI](security.md#pci-compliance) para obter mais informações.
