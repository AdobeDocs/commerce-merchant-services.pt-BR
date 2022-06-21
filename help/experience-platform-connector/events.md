---
title: Eventos
description: Saiba quais eventos capturam dados e veja a definição completa do esquema.
source-git-commit: 566abe09b8c1b0837a833b2f8fcfe1e81bb6963d
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Eventos de beacon do projeto

A seguir, é exibida a lista [!DNL Commerce] eventos disponíveis ao instalar a extensão do conector Experience Platform. Os dados que esses eventos coletam são enviados para a borda do Adobe Experience Platform. Você também pode criar [eventos personalizados](custom-events.md) para coletar dados adicionais não fornecidos imediatamente.

Clique no nome do evento para ver a definição completa do schema.

| Evento | Tipo |
|---|---|
| [Adicionar ao carrinho](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts) | Loja |
| [Exibir carrinho de compras](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts) | Loja |
| [Exibir página](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts) | Loja |
| [Exibir produto](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts) | Loja |
| [Iniciar Check-out](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts) | Loja |
| [Check-out completo](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/checkout/placeOrderAEP.ts) | Loja |
| [Fazer logon](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts) | Perfil |
| [Fazer logoff](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts) | Perfil |
| [Criar conta](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts) | Perfil |
| [Editar Conta](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts) | Perfil |

>[!NOTE]
>
> O `Sign In`, `Sign Out`, `Create Account`e `Update Account` são acionados quando a ação específica é tentada. Não indica que a ação foi bem sucedida.
