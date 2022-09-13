---
title: Dados disponíveis
description: Use dados de relatórios financeiros para reconciliar relatórios com sistemas não comerciais.
role: User
level: Intermediate
source-git-commit: ed471f363546f1d337e85568dc5079cae4507840
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Dados disponíveis

Alguns dados de pedidos e pagamentos estão disponíveis para você coordenar os relatórios financeiros do Adobe Commerce em sistemas externos.

## Reconciliar com o sistema ERP

Você pode reconciliar o relatório financeiro do Adobe Commerce com seu sistema ERP (Enterprise Resource Planning, planejamento de recursos corporativos) que não seja do Adobe usando a ID de incremento associada a uma ordem específica.

Quando os Serviços de Pagamento enviam a ordem de Comércio para o PayPal, a ID de incremento é incluída como a `custom_id` _e_ no `invoice_id` (que também contém uma string aleatória após a variável `increment_id`).

As IDs são facilmente acessíveis nos detalhes de atividade do comerciante para um pagamento e no webhook PayPal.

O `invoice_id` e `custom_id` são exibidos perto da parte inferior dos detalhes da atividade do comerciante para um pagamento:

![`custom_id` em detalhes de atividade comercial](assets/merchant-activity-ids.png)

`custom_id` e `invoice_id` nos detalhes do webhook do PayPal:

```json
   ...
   {
    "id": "4E855005GK253170H",
    "intent": "AUTHORIZE",
    "status": "COMPLETED",
    "payment_source": {
        ...
    },
    "purchase_units": [
        {
            ...
            "custom_id": "000001322",
            "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
            ...
            "payments": {
                "authorizations": [
                    {
                       ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ],
                "captures": [
                    {
                        ...
                        "invoice_id": "000001322-c01bd7c3-920f-4542-a900-738082177e92",
                        "custom_id": "000001322",
                        ...
                    }
                ]
            }
        }
    ],
    "payer": {
        ...
    },
    "create_time": "2022-09-12T14:59:01Z",
    "update_time": "2022-09-12T14:59:45Z",
    "links": [
        ...
    ]
}
   ...
```

Consulte a documentação das REST APIs do PayPal para obter mais informações:

* [`purchase_unit`em que `custom_id` e `invoice_id` residir](https://developer.paypal.com/docs/api/orders/v2/#definition-purchase_unit:~:text=Read%20only.-,purchase_unit, - Recolher)
* [Mostrar detalhes do pedido](https://developer.paypal.com/docs/api/orders/v2/#orders_get)