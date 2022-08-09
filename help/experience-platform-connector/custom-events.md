---
title: Criar eventos personalizados
description: Saiba como criar eventos personalizados para conectar seus dados do Adobe Commerce a outros produtos Adobe DX.
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
source-git-commit: 2b735c292920bb0e9052d86bf152748e7ce96079
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---

# Criar eventos personalizados

É possível estender o [plataforma de eventos](events.md) ao criar seus próprios eventos de loja para coletar dados exclusivos do seu setor. Ao criar e configurar um evento personalizado, ele é enviado para a [Coletor de eventos do Adobe Commerce](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-collectors).

## Gerenciar eventos personalizados

Os eventos personalizados são compatíveis somente com a Adobe Experience Platform. Os dados personalizados não são encaminhados para painéis e rastreadores de métricas do Adobe Commerce.

Para qualquer `custom` , o coletor adiciona um `personId` (`ecid`) a `customContext` e envolve uma `xdm` ao redor dele antes de encaminhar para o Edge.

Exemplo:

Evento personalizado publicado pelo SDK de Eventos do Adobe Commerce:

```javascript
mse.publish.custom({
    customContext: { customStrAttr: "cheetah", customNumAttr: 128 },
});
```

No Experience Platform Edge:

```javascript
{
    xdm: {
        personId: 'ecid1234',
        customStrAttr: 'cheetah',
        customNumAttr: 128
    }
}
```

>[!NOTE]
>
> O uso de eventos personalizados pode afetar os relatórios padrão do Adobe Analytics.

## Gerenciar substituições de evento (atributos personalizados)

Substituições de atributos para eventos padrão são suportadas somente no Experience Platform. Os dados personalizados não são encaminhados para painéis de Comércio e rastreadores de métricas.

Para qualquer evento com um conjunto `customContext`, o coletor substitui `personId` e contadores Adobe Analytics e encaminha todos os outros atributos definidos em `customContext`.

Exemplos:

Exibição de produto com substituições publicadas pelo SDK de Eventos do Adobe Commerce:

```javascript
mse.publish.productPageView({
    customContext: { customCode: "okapi" },
});
```

No Experience Platform Edge:

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        customCode: 'okapi',
        commerce: {
            productViews: {
                value : 1
            }
        }
    }
}
```

A exibição de produto com o Adobe Commerce substitui publicadas pelo SDK de Eventos do Adobe Commerce:

```javascript
mse.publish.productPageView({
    customContext: { commerce: { customCode: "mongoose" } },
});
```

No Experience Platform Edge:

```javascript
{
    xdm: {
        eventType: 'commerce.productViews',
        personId: 'ecid1234',
        commerce: {
            customCode: 'mongoose',
            productViews: {
                value : 1
            }
        }
    }
}
```

>[!NOTE]
>
> Substituir eventos por atributos personalizados pode afetar os relatórios padrão do Adobe Analytics.
