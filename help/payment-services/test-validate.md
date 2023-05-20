---
title: Testar e validar
description: O teste e a validação ajudam a garantir que [!DNL Payment Services] As funções funcionam conforme o esperado e fornecem as melhores opções de pagamento para seus clientes
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
source-git-commit: 0324c2d8e34fee0872d5f52ed3a246094b482aa2
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# Testar e validar

Antes de expor [!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source] para seus compradores, é uma boa ideia testar em seu ambiente de sandbox _e_ em produção. O teste e a validação ajudam a garantir que [!DNL Payment Services] As funções funcionam conforme o esperado e fornecem as melhores opções de pagamento para sua loja e clientes.

## Teste em ambiente de sandbox

Testes [!DNL Payment Services] em um ambiente de sandbox é uma etapa de validação importante, embora seja um ambiente simulado conectado somente à sandbox do PayPal, não aos bancos e comerciantes reais.

1. Conclua um check-out bem-sucedido de sua loja, com [Campos de cartão de crédito](payments-options.md#credit-card-fields) ou qualquer um dos [Botões Inteligentes do PayPal](payments-options.md#paypal-smart-buttons). Consulte [Testando credenciais](#testing-credentials) para obter mais informações sobre como usar cartões de crédito falsos para testes.
1. Capturar (quando sua ação de pagamento for [definir como `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method)), [reembolso](refunds.md)ou [void](voids.md) o pedido recém-concluído. Você também pode simplesmente [criar uma fatura](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"} para um pedido, se sua ação de pagamento estiver definida como `Authorize` em vez de `Authorize and Capture`.
1. Em 24-48 horas, visualize a transação e outras informações no [Relatório de pagamentos](payouts.md).
1. Veja detalhes do pedido no [Relatório de status do pagamento da ordem](order-payment-status.md).

### Testando credenciais

Ao testar e validar sua sandbox, você deve usar números de cartão de crédito falsos para não criar encargos reais para uma conta de cartão de crédito existente.

Use o Gerador de cartão de crédito do PayPal para [gerar informações de cartão de crédito aleatórias](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) para testes.

Para testar o Apple Pay no modo de sandbox:

* Criar um [Conta do testador de sandbox da Apple](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account), completo com informações falsas sobre cartões de crédito e cobrança.
* [Registrar seus domínios de sandbox](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains).

>[!NOTE]
>
>O processamento de pagamento de sandbox do PayPal às vezes é lento e o serviço pode ocasionalmente falhar. Essa situação não é uma indicação da velocidade e da eficiência do processamento de pagamento de produtos em tempo real.

## Teste em produção

É altamente recomendável que você teste [!DNL Payment Services] em produção, com cartões de crédito e bancos reais, antes de expor essa funcionalidade aos compradores. Embora os testes [!DNL Payment Services] na sandbox é importante, testar na produção é o método mais à prova de erros para garantir [!DNL Payment Services] funciona conforme o esperado.

Você pode testar [!DNL Payment Services] em produção de uma das duas formas seguintes:

* Escolha um horário em que você saiba que nenhum pedido será feito pelos compradores.
* Use uma loja na web que esteja temporariamente inacessível aos compradores, mas que esteja acessível a você para testes.

Conclua seus testes de produção com cartões de crédito reais e contas do PayPal, testando todo o ciclo de vida de um pagamento, incluindo captura e reembolso. Concluir todo o fluxo de pagamento e check-out durante os testes fornece uma imagem mais clara de como seus [!DNL Payment Services] A funcionalidade funcionará quando for usada por compradores em tempo real.

Você também deve verificar se as informações exibidas nos extratos bancários dos métodos de pagamento usados no teste de produção estão corretas e esperadas (incluindo a descrição da sua empresa).

Para testar o Apple Pay no modo de produção, você deve [registrar domínios de produção](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).
