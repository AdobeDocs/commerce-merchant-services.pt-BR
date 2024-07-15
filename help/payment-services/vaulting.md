---
title: Compartimentalização do cartão de crédito
description: Os compradores podem guardar (salvar) os detalhes do cartão de crédito para compras futuras.
exl-id: b4060307-ffcd-41cb-9b9d-a2fef02f23bd
feature: Payments, Checkout
source-git-commit: 6769e29a4ae07b8cf15aa2da3cac2fe8583497e0
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Compartimentalização do cartão de crédito

Converta clientes ocasionais em compradores fiéis com cofre de cartão de crédito. Os compradores podem salvar — ou &quot;guardar&quot; — suas credenciais de cartão de crédito durante o checkout para uso em uma compra posterior para a mesma, ou outra, loja na mesma conta de comerciante.

![Guarde seu cartão de crédito para uso posterior](assets/save-card-for-later.png){width="400" zoomable="yes"}

Os compradores usam o token armazenado para concluir um check-out futuro com as informações de cartão de crédito salvas.

![Usar credenciais armazenadas para compra futura](assets/use-stored-card.png){width="400" zoomable="yes"}

Eles também podem facilmente excluir seus cartões de crédito com cofre de [Métodos de Pagamento Armazenados](https://docs.magento.com/user-guide/customers/account-dashboard-stored-payment-methods.html) em sua Minha Conta.

![Métodos de pagamento armazenados em minha conta](assets/stored-payment-methods.png){width="400" zoomable="yes"}

>[!WARNING]
>
>Atualmente, o PayPal pode armazenar no máximo cinco cartões com cofre.

## Ativar compartimentação

Você pode habilitar a compartimentalização de cartão de crédito para clientes _e_ comerciantes no Administrador para suas lojas em [!DNL Payment Services] [Configurações](settings.md#card-vaulting).

## Usar a compartimentalização no Admin

Se um cliente tiver um cartão de crédito com cofre anterior, um comerciante poderá criar uma ordem subsequente para esse cliente no Administrador usando seus métodos de pagamento com cofre.

Você só poderá usar cartões com cofre no Administrador se o cliente tiver uma conta existente e um token válido armazenado no sistema a partir de um pagamento concluído anteriormente.

Para criar um pedido no Administrador para um cliente usando seu cartão de crédito com cofre:

1. [Criar um pedido e adicionar produtos](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html).
1. Em _[!UICONTROL Payment & Shipping Information]_, selecione **[!UICONTROL Stored Cards]**como método de pagamento.
1. Selecione o método de pagamento com cartão de crédito com cofre desejado.
1. Após concluir quaisquer outras etapas necessárias para o pedido, [envie-o](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/customer-account-create-order.html?lang=en#step-3%3A-submit-the-order).

   ![Usar cartão de crédito com cofre no Administrador para o cliente](assets/admin-vaultedcard.png){width="600" zoomable="yes"}

## Segurança

As informações mínimas do cartão de crédito são compartilhadas com o comprador; eles veem apenas os últimos quatro dígitos, a data de expiração e a marca do cartão de crédito com cofre. As informações de cartão de crédito são armazenadas com o provedor de pagamento para atender aos padrões de conformidade [PCI](security.md#PCI-compliance).
