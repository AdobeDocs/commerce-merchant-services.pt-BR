---
title: Tempo de vida da sessão do usuário
description: O Administrador fornece a capacidade de configurar a duração do cookie do seu usuário do Adobe Commerce para o [!DNL Quick Checkout] extensão.
exl-id: 32cf5d70-9a50-49ca-8b40-5f04bc1e24b7
feature: Checkout, Services
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---

# Duração da sessão do usuário

A duração de uma sessão do comprador é determinada por vários fatores, que podem ser configurados no administrador do Adobe Commerce. Consulte [Configurar o tempo de vida do cookie](https://experienceleague.adobe.com/docs/commerce-admin/customers/customer-accounts/configure/customer-online-options.html){target=_blank} para obter mais informações.

A duração configurada dos cookies pode afetar o [!DNL Quick Checkout] se:

1. Devido à inatividade, o comprador foi desconectado do Adobe Commerce.
1. A variável [!DNL Bolt] sessão expira.

Se um comprador fizer um pedido quando seu [!DNL Bolt] expirar a sessão, o pedido será feito com êxito, mas o usuário será desconectado das duas redes.

Se o usuário ainda estiver ativo após um check-out bem-sucedido, ele não será desconectado do Adobe Commerce e [!DNL Bolt].
