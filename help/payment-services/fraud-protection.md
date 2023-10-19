---
title: Proteção contra fraude Signifyd
description: Ativar proteção automatizada contra fraudes para [!DNL Payment Services] com Signifyd.
role: Admin, User
level: Intermediate
feature: Payments, Checkout, Configuration, Security
exl-id: 440296bb-a6ff-408b-8195-3027916e4f84
source-git-commit: 480b35fbc57b8528dbc305aa7db52483ba49d98c
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# Proteção contra fraude Signifyd

Você pode ativar a proteção automatizada contra fraudes para [!DNL Payment Services] com o [Extensão Signifyd](https://commercemarketplace.adobe.com/signifyd-module-connect.html).

O Adobe Commerce é compatível com o Signifyd versões 5.4.0 e mais recentes. [!DNL Payment Services] suporta fluxos Signifyd de pré-autenticação e pós-autenticação.

O Signifyd/[!DNL Payment Services] A integração do oferece cobertura para cartões de crédito, cartões de débito, cartões com cofre, checkout por meio do Admin e métodos de pagamento PayPal e Apple. Embora alguns detalhes das transações não sejam compartilhados entre os Serviços de Pagamento e a Signifyd, a Signifyd fornece uma cobertura de risco abrangente para todos os métodos de pagamento, garantindo o máximo de proteção.

Consulte [Documentação do Signifyd](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#downloadandinstallingmagento2extension) para saber mais sobre como instalar e configurar a extensão.

## Integração

Você deve se comunicar diretamente com o Signifyd para integrar a extensão para uso com o [!DNL Payment Services]— não há [!DNL Payment Services] configuração necessária. Depois de instalada, é possível configurar a extensão Signifyd no Admin. Qualquer suporte relacionado a esta extensão será gerenciado pela Signifyd.

Ao integrar com o Signifyd, você deve:

1. Contate Signifyd para configurar uma nova conta.
1. Por padrão, Signifyd é [incluir na lista de permissões µ](https://github.com/signifyd/magento2/blob/main/docs/RESTRICT-PAYMENTS.md) para garantir que o Signifyd não acione outras opções de pagamento não compatíveis no momento. Se quiser proibir um método de pagamento específico, faça alterações.
1. Confirme com a Signifyd que o PayPal não rejeitará pedidos, por meio da configuração de proteção contra fraude do comerciante no Paypal, que podem ser aprovados pela Signifyd.
1. Habilitar a extensão Signifyd para ser compatível com o [!DNL Payment Services]:
   * Ao usar [!DNL Payment Services] in _Ao vivo_ , Signifyd deve estar no modo Produção.
   * Ao usar [!DNL Payment Services] in _Sandbox_ , Signifyd deve estar no modo Test.

## Configuração

Como o Signifyd executa alguma ação em seus pedidos, é necessário configurar a extensão para que se comporte adequadamente com base na ação de pagamento definida para [!DNL Payment Services].

Estas opções de configuração não são compatíveis com os Serviços de pagamento e a integração com o Signifyd:

* Quando [!DNL Payment Services] está configurado com o `Authorize` ação de pagamento _e_ Signifyd está em `PostAuth` com o _[!UICONTROL Decline Guarantees]_opção definida como **Criar memorando de crédito**.

  Motivo: [!DNL Payment Services] cria uma transação de autorização que o Signify tenta reembolsar.


* [!DNL Payment Services] está configurado com o `Authorize and Capture` ação de pagamento _e_ Signifyd está em `PostAuth` com o _[!UICONTROL Decline Guarantees]_opção definida como **Cancelar pedido**.

  Motivo: [!DNL Payment Services] cria uma transação de captura que Signifyd tenta anular.


Consulte a documentação do Signifyd para obter informações sobre [configuração da extensão](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#configuringmagento2extension).

Consulte a documentação do Signifyd para [saiba mais sobre os workflows de pedido](https://community.signifyd.com/support/s/article/magento-2-extension-install-guide?language=en_US#howmagento2works).
