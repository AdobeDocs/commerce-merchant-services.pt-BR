---
title: Duração da sessão do usuário
description: O Administrador fornece a capacidade de configurar a duração do cookie do usuário do Adobe Commerce para a variável [!DNL Quick Checkout] extensão.
exl-id: 32cf5d70-9a50-49ca-8b40-5f04bc1e24b7
source-git-commit: b89427124cf76e7f36076454949191ee1d88f52c
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# Duração da sessão do usuário

A duração de uma sessão do comprador é determinada por vários fatores, que podem ser configurados no Administrador do Adobe Commerce. Consulte [Configurar a duração do cookie](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/configure/customer-online-options.html){target=_blank} para obter mais informações.

A vida útil dos cookies configurados pode afetar o [!DNL Quick Checkout] se:

1. Devido à inatividade, o comprador é desconectado do Adobe Commerce.
1. O [!DNL Bolt] sessão expira.

Se um comprador fizer um pedido quando seu [!DNL Bolt] expira, o pedido é feito com êxito, mas o usuário é desconectado de ambas as redes.

Se o usuário ainda estiver ativo após um check-out bem-sucedido, ele não será desconectado da Adobe Commerce e [!DNL Bolt].
