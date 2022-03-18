---
title: Teste da [!DNL Express Checkout] para extensão do Adobe Commerce
description: O teste e a validação garantem que a variável [!DNL Express Checkout] A extensão funciona conforme o esperado.
exl-id: 308f39e1-e2f6-40d8-b876-0f9013effed3
source-git-commit: d8302d2d652b4e2380cc862183e58cbd2cca831b
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Teste da [!DNL Express Checkout] para extensão do Adobe Commerce

>[!IMPORTANT]
>
> Esse recurso destina-se somente aos usuários do EAP (Early Adobe Program) e ainda não está acessível para todos os clientes. Atualmente limitado a clientes dos EUA. Entre em contato com o Suporte da Adobe Commerce para obter assistência e perguntas.

Antes de expor o [!DNL Express Checkout] para a extensão do Adobe Commerce para seus compradores, é recomendável testar em um ambiente sandbox e em seu ambiente de produção. O teste e a validação ajudam a garantir que a variável [!DNL Express Checkout] O funciona conforme o esperado e fornece uma experiência de check-out contínua para sua loja e clientes.

Antes de configurar o [!DNL Express Checkout] no administrador do Adobe Commerce, é necessário criar um [produção](https://merchant.bolt.com/register){target=&quot;_blank&quot;} e [sandbox](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} conta comercial no Bolt.

## Teste na sandbox

Teste da [!DNL Express Checkout] em um ambiente de sandbox é uma etapa de validação muito importante, mesmo sendo um ambiente simulado conectado apenas à conta de sandbox Bolt, não a bancos ou comerciantes reais.

### Uso da conta sandbox

Ao testar e validar sua sandbox, você deve usar um número de cartão de crédito falso e um [sandbox](https://merchant-sandbox.bolt.com/register){target=&quot;_blank&quot;} conta comercial no Bolt, para que você não esteja criando encargos reais para uma conta de cartão de crédito existente.

## Testes na produção

>[!NOTE]
>
> É altamente recomendável testar a variável [!DNL Express Checkout] num ambiente de produção, com cartões de crédito reais e bancos, antes de expor a extensão aos compradores. Embora os testes em sandbox sejam importantes, testar na produção é o método mais infalível para garantir que funcione como esperado.

Recomendado para o ensaio em produção de uma das duas formas seguintes:

- Escolha um horário em que você saiba que nenhum pedido será feito por compradores.
- Use um armazenamento da Web temporariamente inacessível aos compradores, mas que pode ser acessado para testes.

Conclua o teste de produção com cartões de crédito reais e contas de produção Bolt, testando todo o ciclo de vida de um check-out. Quando você conclui todo o fluxo de finalização durante o teste, você obtém uma imagem clara de como sua funcionalidade funciona quando os compradores em tempo real a utilizam.

Você também deve verificar se as informações que aparecem nos demonstrativos bancários para os métodos de pagamento que você usa no teste de produção estão corretas e esperadas (incluindo a descrição da sua empresa).

## Como testar o [!DNL Express Checkout] extensão

Conclua um check-out bem-sucedido em sua loja seguindo estas etapas:

1. Vá para a loja e coloque os itens desejados no carrinho.
1. Prossiga para o check-out.
1. Digite um endereço de email associado a uma Conta Bolt quando solicitado.
1. Insira a Senha única (OTP) enviada ao endereço de email da conta.
1. Selecione o painel de ambiente:

   - Sandbox
   - Produção

1. Colocar pedido.

Depois que um pedido é feito, você pode visualizar os detalhes de seus pedidos na _Grade de pedidos_ exibir:

1. Navegar para _Vendas_ > _Pedidos_.
1. Consulte a lista de todos os pedidos feitos.

Consulte a [ordens](https://docs.magento.com/user-guide/sales/orders.html) tópico para obter mais informações sobre seu _Grade de pedidos_ exibir.
