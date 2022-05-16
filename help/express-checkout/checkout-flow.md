---
title: Fluxo de finalização
description: Visão geral da [!DNL Express Checkout] no Adobe Commerce.
exl-id: 82761627-a0d4-4cb0-aad1-9865fcb550d4
source-git-commit: bd9541c5e4810085ab85206b2ecca21e66800a2f
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# [!DNL Express Checkout] fluxo

>[!IMPORTANT]
>
> Esse recurso destina-se somente aos usuários do EAP (Early Adobe Program) e ainda não está acessível para todos os clientes. Atualmente limitado a clientes dos EUA. Entre em contato com o Suporte da Adobe Commerce para obter assistência e perguntas.

Esta seção fornece uma visão geral da experiência típica de check-out usando o [!DNL Express Checkout] para extensão do Adobe Commerce.

Um sucesso [!DNL Express Checkout] O fluxo consiste nas seguintes etapas:

1. Abra a loja e adicione itens ao carrinho.
1. Prossiga para o check-out.

![Check-out](assets/proceed-checkout.png)

1. Quando solicitado, insira um endereço de email associado a um [!DNL Bolt] conta.
1. Insira a Senha única (OTP) enviada para isso [!DNL Bolt] endereço de email ou número de telefone da conta.
1. Depois de fazer logon com o [!DNL Bolt] Os detalhes de check-out são automaticamente preenchidos:

   - Informações sobre envio
   - Método de pagamento

   >[!NOTE]
   >
   > Você pode usar suas informações de carteira existentes (endereço ou informações do cartão de crédito) mesmo se os detalhes de check-out forem preenchidos automaticamente.

1. Colocar pedido.

O [!DNL Express Checkout] é compatível com as opções padrão adicionais de check-out do Adobe Commerce, como [cartões-presente](https://docs.magento.com/user-guide/catalog/product-gift-card.html) ou [códigos de desconto](https://docs.magento.com/user-guide/marketing/price-rules-cart-coupon.html).

## [!DNL Express Checkout] casos de uso

O [!DNL Express Checkout] O permite vários casos de uso durante um fluxo de finalização:

- Usuário convidado com um registro [!DNL Bolt] conta.
- Usuário convidado com um novo [!DNL Bolt] conta.
- Um usuário existente do Adobe Commerce com/sem um registro [!DNL Bolt] conta.

## Check-out do usuário convidado: Como funciona

A experiência de check-out de convidado é diferente da experiência de logon. Quando um comprador insere um endereço de email no check-out, a variável [!DNL Express Checkout] O valida para localizar um [!DNL Bolt] conta.

### Registrado [!DNL Bolt] account

Se uma [!DNL Bolt] for encontrada, os compradores continuarão com suas [!DNL Express Checkout] experiência de finalização contínua:

1. Insira a Senha única (OTP) enviada para isso [!DNL Bolt] endereço de email da conta ou dispositivo móvel, dependendo das preferências do usuário no [!DNL Bolt] conta.
1. Depois de fazer logon com o [!DNL Bolt] preenche os detalhes de check-out automaticamente:

   - Informações sobre envio
   - Método de pagamento

1. Colocar pedido.

>[!TIP]
>
> O usuário convidado coloca o pedido e pode se registrar no Adobe Commerce.

### Novo [!DNL Bolt] account

Se não [!DNL Bolt] for encontrada, os compradores continuarão com a verificação predefinida do Adobe Commerce e o comprador fornecerá todos os detalhes necessários para fazer o pedido:

- Informações sobre remessa e faturamento
- Método de remessa
- Revisar método de pagamento
- Uma caixa de seleção aparece para se registrar no [!DNL Bolt] para finalizações mais rápidas antes de fazer o pedido. Eles podem concordar com os termos e condições para criar seus [!DNL Bolt] conta.

   ![Lembrar [!DNL Bolt]](assets/checked-bolt.png)

- O usuário convidado coloca o pedido e pode se registrar no Adobe Commerce.

## Um usuário existente do Adobe Commerce: Como funciona

Um usuário existente pode selecionar detalhes existentes quando o usuário colocar um pedido com a variável [!DNL Express Checkout] para obter uma experiência de finalização mais rápida.

Quando um comprador insere um endereço de email no check-out, a variável [!DNL Express Checkout] O valida para localizar um [!DNL Bolt] conta.

### Registrado [!DNL Bolt] conta com um usuário do Adobe Commerce

Se uma [!DNL Bolt] for encontrada, os compradores continuarão com a verificação predefinida do Adobe Commerce e o comprador fornecerá todos os detalhes necessários e colocará o pedido:

- Informações sobre remessa e faturamento
- Método de remessa
- Revisar método de pagamento

Consulte a [solução de problemas](../express-checkout/troubleshooting.md) para obter mais informações se encontrar problemas ao colocar um pedido como um usuário existente do Adobe Commerce.

>[!NOTE]
>
> Se o usuário tiver uma [!DNL Bolt] A conta e o email não aparecem como registrados no Adobe Commerce, ele aciona o logon OTP (One-Time Password, Senha única). Consulte a [registrado [!DNL Bolt] account](#registered-bolt-account) fluxo.

### Novo [!DNL Bolt] account

Se não [!DNL Bolt] for encontrada, os compradores continuarão com o check-out padrão do Adobe Commerce e o comprador selecionará todos os detalhes necessários de suas informações salvas para colocar o pedido:

- Informações sobre remessa e faturamento
- Método de remessa
- Revisar método de pagamento
- Uma caixa de seleção aparece para se registrar no [!DNL Bolt] para finalizações mais rápidas antes de fazer o pedido. Eles podem concordar com os termos e condições para criar seus [!DNL Bolt] conta.

   ![Lembrar [!DNL Bolt]](assets/checked-bolt.png)

## Obter ajuda

Contato [!DNL Adobe Commerce] equipe de engenharia por meio do Slack atribuído [Canal de programas Adobe Beta](http://adobe-beta-programs.slack.com/) para qualquer assistência.
