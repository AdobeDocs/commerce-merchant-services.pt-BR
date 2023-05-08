---
title: Testar e validar
description: O teste e a validação ajudam a garantir que [!DNL Payment Services] As funções funcionam conforme o esperado e fornecem as melhores opções de pagamento para os clientes
exl-id: 95b4615e-73b0-41e8-83e2-e65a0b22f10f
source-git-commit: 0324c2d8e34fee0872d5f52ed3a246094b482aa2
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---

# Testar e validar

Antes de expor [!DNL Payment Services] para [!DNL Adobe Commerce] e [!DNL Magento Open Source] aos seus compradores, é uma boa ideia testar no seu ambiente sandbox _e_ em produção. O teste e a validação ajudam a garantir que [!DNL Payment Services] As funções funcionam conforme o esperado e fornecem as melhores opções de pagamento para sua loja e clientes.

## Testar no ambiente sandbox

Teste [!DNL Payment Services] em um ambiente sandbox é uma etapa importante de validação, mesmo sendo um ambiente simulado conectado apenas à sandbox PayPal, não a bancos e comerciantes reais.

1. Conclua um check-out bem-sucedido em sua loja com [Campos de cartão de crédito](payments-options.md#credit-card-fields) ou qualquer um dos [Botões inteligentes PayPal](payments-options.md#paypal-smart-buttons). Consulte [Testando credenciais](#testing-credentials) para obter mais informações sobre o uso de cartões de crédito falsos para teste.
1. Capturar (quando a ação de pagamento é [defina como `Authorize and Capture`](onboard.md#set-payment-services-as-payment-method)), [reembolso](refunds.md)ou [void](voids.md) o pedido concluído. Você também pode simplesmente [criar uma fatura](https://docs.magento.com/user-guide/sales/invoice-create.html){target="_blank"} para uma ordem, se a ação de pagamento estiver definida como `Authorize` em vez de `Authorize and Capture`.
1. Dentro de 24 a 48 horas, visualize a transação e outras informações na [Relatório de pagamentos](payouts.md).
1. Veja os detalhes do pedido na [Relatório de status do pagamento da ordem](order-payment-status.md).

### Testando credenciais

Ao testar e validar a sandbox, você deve usar números falsos de cartão de crédito para não criar encargos reais em uma conta de cartão de crédito existente.

Usar o Gerador de Cartão de Crédito do PayPal para [gerar informações aleatórias do cartão de crédito](https://www.paypal.com/us/smarthelp/article/where-can-i-find-test-credit-card-numbers-ts2157) para teste.

Para testar o Apple Pay no modo sandbox:

* Crie um [Conta de testador da sandbox do Apple](https://developer.apple.com/apple-pay/sandbox-testing/#create-a-sandbox-tester-account), completo com informações falsas sobre cartão de crédito e faturamento.
* [Registre os domínios da sandbox](https://developer.paypal.com/docs/checkout/apm/apple-pay/#link-registeryoursandboxdomains).

>[!NOTE]
>
>O processamento do pagamento da sandbox do PayPal às vezes é lento e o serviço pode, ocasionalmente, ficar inativo. Esta situação não é uma indicação da velocidade e eficiência do processamento de pagamentos de produtos vivos.

## Teste na produção

É altamente recomendável testar [!DNL Payment Services] em produção, com cartões de crédito reais e bancos, antes de expor esta funcionalidade aos compradores. Mesmo que testando [!DNL Payment Services] na sandbox é importante, testar na produção é o método mais infalível para garantir [!DNL Payment Services] funciona conforme o esperado.

Você pode testar [!DNL Payment Services] em produção de uma das duas formas seguintes:

* Escolha um horário em que você saiba que nenhum pedido será feito por compradores.
* Use um armazenamento da Web temporariamente inacessível aos compradores, mas que pode ser acessado para testes.

Conclua o teste de produção com cartões de crédito reais e contas PayPal, testando todo o ciclo de vida de um pagamento, incluindo captura e reembolso. Completar todo o check-out e o fluxo de pagamento durante o teste dá a você a imagem mais clara de como seu [!DNL Payment Services] funcionará quando os compradores em tempo real o estiverem usando.

Você também deve verificar se as informações que aparecem nos demonstrativos bancários para os métodos de pagamento que você usa no teste de produção estão corretas e esperadas (incluindo a descrição da sua empresa).

Para testar o Apple Pay no modo de produção, você deve [registre seus domínios de produção](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).
