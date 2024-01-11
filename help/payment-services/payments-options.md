---
title: Opções de pagamento
description: Defina as opções de pagamento para personalizar os métodos disponíveis para seus clientes de loja.
exl-id: 95e648e6-6cb8-4226-b5ea-e1857212f20a
feature: Payments, Checkout, Configuration
source-git-commit: 3276cdac48461cb61c8669e2019b567c70d6f493
workflow-type: tm+mt
source-wordcount: '944'
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

![Campos de cartão de crédito no check-out](assets/credit-card-fields.png){width="500" zoomable="yes"}

Ativar [compartimentalização de cartão de crédito](#vaulting) para que suas lojas permitam que os compradores guardem (salvem) suas informações de cartão de crédito para um check-out rápido posteriormente.

Você pode configurar [!UICONTROL Credit Card Fields] na configuração da loja ou na Página Inicial dos Serviços de Pagamento. Consulte [Configurações](settings.md#credit-card-fields) para obter mais informações.

Também é possível alterar o layout, a largura, a altura e o estilo externo dos campos de cartão de crédito. Consulte [Documentação do PayPal](https://developer.paypal.com/docs/checkout/advanced/customize/card-field-style/) para obter mais informações.

## [!DNL Apple Pay] botão

Os clientes podem usar [[!DNL Apple Pay]](https://www.apple.com/apple-pay/), que utilizam credenciais de pagamento de cartão de crédito e débito armazenadas em um dispositivo iOS ou macOS, para fazer compras.

[!DNL Apple Pay] O só está disponível no navegador Safari.

![Botão Pagamento do Apple no minicart](assets/apple-pay-button.png){width="500" zoomable="yes"}

A variável [!DNL Apple Pay] O botão é visível nas exibições página do produto, minicarrinho, carrinho de compras e check-out.

>[!NOTE]
>
> Para usar [!DNL Apple Pay] para suas lojas, conclua [autorregistro com [!DNL Apple Pay]](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain) (_Registre seu domínio ativo_ (somente na seção ) e [configure-o para suas lojas no [!DNL Payment Services]](settings.md#payment-buttons).

Você pode configurar [!UICONTROL Apple Pay] na configuração da loja ou na Página Inicial dos Serviços de Pagamento. Consulte [Configurações](settings.md#apple-pay) para obter mais informações.

## [!DNL PayPal Smart Buttons]

[!DNL PayPal Smart Buttons], que usam o PayPal para concluir uma compra, armazena o endereço de entrega, os endereços de cobrança e os detalhes de pagamento do comprador para uso posterior. Os compradores podem usar qualquer método de pagamento armazenado ou oferecido anteriormente pelo PayPal.

![Botão PayPal](assets/paypal-button.png){width="350" zoomable="yes"}

Você pode configurar [!UICONTROL PayPal Smart Buttons] na configuração da loja ou na Página Inicial dos Serviços de Pagamento.  Consulte [Configurações](settings.md#payment-buttons) para obter mais informações.

Consulte PayPal&#39;s [Documentação de métodos de pagamento](https://developer.paypal.com/docs/checkout/payment-methods/) para saber em quais países cada método de pagamento está disponível atualmente.

### [!DNL PayPal] botão

Os clientes podem fazer check-out com facilidade e confiança usando o botão PayPal.

A variável [!DNL PayPal] O botão é visível nas exibições página do produto, minicarrinho, carrinho de compras e check-out.

### [!DNL Venmo] botão

Os clientes podem fazer check-out usando o [Venmo](https://venmo.com/) botão.

A variável [!DNL Venmo] O botão é visível nas exibições página do produto, minicarrinho, carrinho de compras e check-out.

### Botão Cartão de crédito ou débito do PayPal

Os clientes podem fazer check-out usando o botão PayPal Débito ou Cartão de crédito.

O botão PayPal Debit or Credit card (Cartão de crédito ou débito do PayPal) está visível na página de check-out.

Esta opção pode ser usada para apresentar uma opção de pagamento com cartão de crédito ou débito aos seus compradores com um botão hospedado no PayPal, como alternativa à integração com cartão de crédito.

### [!DNL Pay Later] botão

Ofereça aos clientes pagamentos de curto prazo, sem juros e outras opções de financiamento para que eles possam comprar agora e pagar posteriormente com o [!DNL Pay Later] botão.

A variável [!DNL Pay Later] O botão é visível nas exibições página do produto, minicarrinho, carrinho de compras e check-out.

Consulte informações sobre as ofertas de Pagar mais tarde em [PayPal&#39;s Pay Later oferece documentação](https://developer.paypal.com/docs/checkout/pay-later/us/). Use o **País ou região** para selecionar uma região de interesse.

Consulte [Configurações](settings.md#payment-buttons) para saber como desativar/ativar o [!DNL Pay Later] mensagens.

## Usar somente botões de pagamento do PayPal

Para colocar rapidamente sua loja no modo de produção, você pode configurar _somente_ Botões de pagamento do PayPal (Venmo, PayPal etc.)—em vez de também usar a opção de pagamento com cartão de crédito PayPal.

Isso permite:

* Forneça uma variedade de opções de pagamento para seus clientes, incluindo os botões de pagamento Venmo e PayPal, com a opção de desativar os campos de cartão hospedados no PayPal e usar um provedor de cartão de crédito existente.
* Use seu fornecedor de cartão de crédito existente para pagamentos de cartão de crédito, ao mesmo tempo que utiliza outras opções de pagamento do PayPal.
* Use os botões de pagamento do PayPal em uma região na qual o PayPal não oferece suporte a cartões de crédito como uma opção de pagamento.

Para **capturar pagamentos com _somente_ Botões de pagamento do PayPal (_não_ a opção de pagamento com cartão de crédito do PayPal)**:

1. Verifique se o armazenamento está [no modo de produção](settings.md#enable-payment-services).
1. [Configurar os botões de pagamento do PayPal desejados](settings.md#payment-buttons) em Configurações.
1. Girar _Desligado_ o **[[!UICONTROL Show PayPal Credit and Debit card button]](settings.md#payment-buttons)** opção no _[!UICONTROL Payment buttons]_seção.

Para **capture pagamentos com seu provedor de cartão de crédito atual _e_ Botões de pagamento do PayPal**:

1. Verifique se o armazenamento está [no modo de produção](settings.md#enable-payment-services).
1. [Configurar os botões de pagamento do PayPal desejados](settings.md#payment-buttons).
1. Girar _Desligado_ o **[[!UICONTROL PayPal Show Credit and Debit card button]](settings.md#payment-buttons)** opção no _[!UICONTROL Payment buttons]_seção.
1. Girar _Desligado_ o **[[!UICONTROL Show on checkout page]](settings.md#credit-card-fields)** opção no _[!UICONTROL Credit card fields]_e use sua [conta do provedor de cartão de crédito existente](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/payments.html#payments).

## Recálculo de pedido

Quando um cliente entra no fluxo de finalização do minicarrinho, carrinho de compras ou página do produto, ele é direcionado a uma página de revisão do pedido, onde pode ver o endereço de envio selecionado em uma janela pop-up do PayPal. Depois que o cliente selecionar o método de entrega, a quantia da ordem será recalculada apropriadamente e o cliente poderá ver os custos e impostos de entrega.

Quando um cliente entra no fluxo de finalização da página de finalização da compra, o sistema já sabe o endereço de entrega e o valor final calculado, e os totais são devidamente representados.

Feriados fiscais, custos de envio e imposto sobre vendas podem variar amplamente de local para local. Depois [!DNL Payment Services] recebe o endereço e a taxa de entrega, ele recalcula rapidamente todos os custos aplicáveis e os exibe adequadamente durante os últimos estágios da finalização.

## Compartimentalização de cartão de crédito

Os compradores podem arquivar (ou &quot;salvar&quot;) suas informações de cartão de crédito para compras futuras no nível do site (qualquer loja na conta do mesmo comerciante).

Consulte [Compartimentalização de cartão de crédito](vaulting.md) para obter mais informações.

## Segurança

Consulte [Conformidade com o PCI](security.md#pci-compliance) para obter mais informações.
