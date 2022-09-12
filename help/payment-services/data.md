---
title: Dados disponíveis
description: Use dados de relatórios financeiros para reconciliar relatórios com sistemas não comerciais.
role: User
level: Intermediate
source-git-commit: 1186b4e52f1d613332a7862c58f482c2591e29a8
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Dados disponíveis

Alguns dados de pedidos e pagamentos estão disponíveis para você coordenar os relatórios financeiros do Adobe Commerce em sistemas externos.

## Reconciliar com o sistema ERP

Você pode reconciliar o relatório financeiro do Adobe Commerce com seu sistema ERP (Enterprise Resource Planning, planejamento de recursos corporativos) que não seja do Adobe usando a ID de incremento associada a uma ordem específica.

Quando os Serviços de Pagamento enviam a ordem de Comércio para o PayPal, a ID de incremento é incluída como a `custom_id`. O `custom_id` é visível nos detalhes da atividade do comerciante para um pagamento e no webhook PayPal.

`custom_id` na parte inferior dos detalhes da atividade do comerciante para um pagamento:

![`custom_id` em detalhes de atividade comercial](assets/merchant-activity.png)

`custom_id` nos detalhes do webhook do PayPal:

```json
   ...
   },
   "seller_protection": {
   "status": "NOT_ELIGIBLE"
   },
   "create_time": "2022-08-28T21:06:53Z",
   "custom_id": "000000829",
   "supplementary_data": {
   "related_ids":

   { "authorization_id": "6WW957787A749904A", "order_id": "3SV13726F9525791J" }
   },
   ...
```

Consulte a documentação das REST APIs do PayPal para obter mais informações:

* [`purchase_unit` em que `custom_id` residências](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit, - Recolher)
* [Mostrar detalhes do pedido](https://developer.paypal.com/docs/api/orders/v2/#orders_get)
