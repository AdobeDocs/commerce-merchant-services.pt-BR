---
title: Duração da sessão do usuário
description: O Administrador fornece a capacidade de configurar a duração do cookie do usuário do Adobe Commerce para a variável [!DNL Quick Checkout] extensão.
source-git-commit: a95d2ed92c69feba03d1b84d44abf08c1d1b4029
workflow-type: tm+mt
source-wordcount: '127'
ht-degree: 0%

---


# Duração da sessão do usuário

A duração de uma sessão do comprador é determinada por vários fatores, que podem ser configurados no Administrador do Adobe Commerce. Consulte [Configurar a duração do cookie](https://docs.magento.com/user-guide/customers/customer-online-options.html){target=_blank} para obter mais informações.

A vida útil dos cookies configurados pode afetar o [!DNL Quick Checkout] se:

1. Devido à inatividade, o comprador é desconectado do Adobe Commerce.
1. O [!DNL Bolt] sessão expira.

Se um comprador fizer um pedido quando seu [!DNL Bolt] expira, o pedido é feito com êxito, mas o usuário é desconectado de ambas as redes.

Se o usuário ainda estiver ativo após um check-out bem-sucedido, ele não será desconectado da Adobe Commerce e [!DNL Bolt].
