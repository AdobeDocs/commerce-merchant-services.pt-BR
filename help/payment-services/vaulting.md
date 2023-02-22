---
title: Vazamento do cartão de crédito
description: Os compradores podem guardar (salvar) os detalhes do cartão de crédito para compras futuras.
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
source-git-commit: 817a01e98876bddf5f41a253501984539b3351cd
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Vazamento do cartão de crédito

Converta clientes únicos em compradores fiéis com compartimentalização de cartão de crédito. Os compradores podem salvar — ou &quot;cofre&quot; — suas credenciais de cartão de crédito durante o check-out para uso em uma compra posterior para o mesmo ou outro, armazenar na mesma conta comercial.

![Comparar o cartão de crédito para uso posterior](assets/save-card-for-later.png)

Os compradores usam o token armazenado para concluir um check-out futuro com suas informações de cartão de crédito salvas.

![Usar credenciais armazenadas para compra futura](assets/use-stored-card.png)

Também podem facilmente excluir os seus cartões de crédito válidos de [Métodos de pagamento armazenados](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) em Minha conta.

![Métodos de pagamento armazenados em minha conta](assets/stored-payment-methods.png)

## Ativar compartimentalização

Você pode ativar a compartimentalização do cartão de crédito — para clientes _e_ comerciantes no Administrador — para suas lojas no [!DNL Payment Services] [Configurações](settings.md#card-vaulting).

## Use compartimentalização no Administrador

Se um cliente tiver um cartão de crédito previamente validado, um comerciante pode criar uma ordem subsequente para esse cliente no Administrador usando seus métodos de pagamento válidos.

Você só poderá usar cartões com valor no Administrador se o cliente tiver uma conta existente e um token válido armazenado no sistema a partir de um pagamento concluído anteriormente.

Para criar um pedido no Administrador para um cliente usando seu cartão de crédito válido:

1. [Criar um pedido e adicionar produtos](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html).
1. Em _[!UICONTROL Payment & Shipping Information]_, selecione **[!UICONTROL Stored Cards]**como método de pagamento.
1. Selecione o método de pagamento de cartão de crédito válido desejado.
1. Depois de concluir quaisquer outras etapas necessárias para o pedido, [apresentar](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![Usar cartão de crédito válido em Admin para cliente](assets/admin-vaultedcard.png)

## Segurança

As informações mínimas relativas ao cartão de crédito são partilhadas com o comprador; eles só veem os últimos quatro dígitos, data de expiração e marca de seu cartão de crédito válido. As informações relativas ao cartão de crédito são armazenadas junto do prestador de pagamento para satisfazer [PCI](security.md#PCI-compliance) normas de conformidade.
