---
title: '"Testando o [!DNL Quick Checkout] para extensão do Adobe Commerce"'
description: '"Testar e validar garante que a função [!DNL Quick Checkout] A extensão funciona conforme o esperado."'
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---


# Teste a [!DNL Quick Checkout] extensão

Antes de expor o [!DNL Quick Checkout] para a extensão do Adobe Commerce para seus compradores, é recomendável testar em um ambiente sandbox e em seu ambiente de produção. O teste e a validação ajudam a garantir que a variável [!DNL Quick Checkout] O funciona conforme o esperado e fornece uma experiência de check-out contínua para sua loja e clientes.

Antes de configurar o [!DNL Quick Checkout] no administrador do Adobe Commerce é necessário criar  [produção](https://merchant.bolt.com/register){target=&quot;_blank&quot;} e [sandbox](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} contas comerciais em [!DNL Bolt].

## Teste na sandbox

Teste da [!DNL Quick Checkout] em um ambiente sandbox é uma etapa de validação muito importante, mesmo sendo um ambiente simulado conectado somente ao [!DNL Bolt] conta de sandbox, não para bancos reais ou comerciantes.

### Uso da conta sandbox

Ao testar e validar sua sandbox, você deve usar um número de cartão de crédito falso e um [sandbox](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} conta comercial no [!DNL Bolt], para que você não esteja criando encargos reais para uma conta de cartão de crédito existente.

## Testes na produção

>[!NOTE]
>
> É altamente recomendável testar a variável [!DNL Quick Checkout] num ambiente de produção, com cartões de crédito reais e bancos, antes de expor a extensão aos compradores. Embora os testes em sandbox sejam importantes, testar na produção é o método mais infalível para garantir que funcione como esperado.

Teste seu ambiente de produção de uma dessas duas maneiras recomendadas:

- Escolha um horário em que você saiba que nenhum pedido será feito por compradores.
- Use um armazenamento da Web temporariamente inacessível aos compradores, mas que pode ser acessado para testes.

Conclua o teste de produção com cartões de crédito reais e [!DNL Bolt] contas de produção, testando todo o ciclo de vida de uma finalização. Quando você conclui todo o fluxo de checkout durante o teste, ele fornece uma imagem clara de como sua funcionalidade funciona quando os compradores em tempo real a usam.

Você também deve verificar se as informações que aparecem nos demonstrativos bancários para os métodos de pagamento que você usa no teste de produção estão corretas e esperadas (incluindo a descrição da sua empresa).

## Como testar o [!DNL Quick Checkout] extensão

Conclua um check-out bem-sucedido em sua loja:

1. Vá para a loja e coloque os itens desejados no carrinho.
2. Prossiga para o check-out.
3. Insira um endereço de email associado a um [!DNL Bolt] quando solicitado.
4. Insira a Senha única (OTP) enviada ao endereço de email da conta.
5. Selecione o painel de ambiente:

   - Sandbox
   - Produção

6. Coloque o pedido.

Depois que um pedido é feito, você pode visualizar os detalhes de seus pedidos na _Grade de pedidos_ exibir:

1. Navegar para _Vendas_ > _Pedidos_.
1. Consulte a lista de todos os pedidos feitos.

Consulte a [Pedidos](https://docs.magento.com/user-guide/sales/orders.html) tópico para obter mais informações sobre seu _Grade de pedidos_ exibir.
