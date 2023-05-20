---
title: "Testar o [!DNL Quick Checkout] para extensão do Adobe Commerce"
description: "Testar e validar garante que o [!DNL Quick Checkout] A extensão do funciona conforme esperado."
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: bd02a8083d3f4c9cb0422b27d61bd5462187ffc3
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---


# Teste o [!DNL Quick Checkout] extensão

Antes de expor a variável [!DNL Quick Checkout] para obter a extensão do Adobe Commerce para seus compradores, é recomendável testar em um ambiente de sandbox e em seu ambiente de produção. O teste e a validação ajudam a garantir que a [!DNL Quick Checkout] O funciona conforme o esperado e fornece uma experiência de finalização perfeita para sua loja e clientes.

Antes de configurar o [!DNL Quick Checkout] no Administrador do Adobe Commerce, é necessário criar  [produção](https://merchant.bolt.com/register){target="_blank"} and [sandbox](https://merchant-sandbox.bolt.com/register){target="_blank"} contas do comerciante em [!DNL Bolt].

## Teste em sandbox

Teste do [!DNL Quick Checkout] em um ambiente de sandbox é uma etapa de validação muito importante, embora seja um ambiente simulado conectado somente ao [!DNL Bolt] conta de sandbox, não para bancos ou comerciantes reais.

### Uso da conta de sandbox

Ao testar e validar sua sandbox, você deve usar um número de cartão de crédito falso e um [sandbox](https://merchant-sandbox.bolt.com/register){target="_blank"} conta de comerciante em [!DNL Bolt], para que você não crie encargos reais para uma conta de cartão de crédito existente.

## Testes em produção

>[!NOTE]
>
> É altamente recomendável que você teste o [!DNL Quick Checkout] em um ambiente de produção, com cartões de crédito e bancos reais, antes de expor a extensão aos compradores. Embora o teste em sandbox seja importante, o teste em produção é o método mais à prova de falhas para garantir que funcione conforme o esperado.

Teste seu ambiente de produção de uma destas duas formas recomendadas:

- Escolha um horário em que você saiba que nenhum pedido será feito pelos compradores.
- Use uma loja na web que esteja temporariamente inacessível aos compradores, mas que esteja acessível a você para testes.

Conclua seus testes de produção com cartões de crédito reais e [!DNL Bolt] contas de produção, testando todo o ciclo de vida de uma finalização. Quando você conclui todo o fluxo de check-out durante os testes, ele fornece uma imagem clara de como sua funcionalidade funciona quando compradores ao vivo a usam.

Você também deve verificar se as informações exibidas nos extratos bancários dos métodos de pagamento usados no teste de produção estão corretas e esperadas (incluindo a descrição da sua empresa).

## Como testar a [!DNL Quick Checkout] extensão

Conclua um check-out bem-sucedido de sua loja:

1. Vá para a loja e coloque os itens desejados no carrinho.
1. Prossiga para o check-out.
1. Insira um endereço de email associado a um [!DNL Bolt] quando solicitado.
1. Insira a OTP (senha ocasional) enviada para o endereço de email da conta.
1. Selecione o painel do ambiente:

   - Sandbox
   - Produção

1. Coloque o pedido.

Depois que um pedido é feito, você pode visualizar os detalhes dos seus pedidos em _Grade de pedidos_ exibir:

1. Navegue até _Vendas_ > _Pedidos_.
1. Consulte a lista de todos os pedidos feitos.

Consulte a [Pedidos](https://docs.magento.com/user-guide/sales/orders.html) para obter mais informações sobre o seu _Grade de pedidos_ exibição.
