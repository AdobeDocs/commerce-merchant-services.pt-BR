---
title: Criar eventos personalizados
description: Saiba como criar eventos personalizados para conectar seus dados do Adobe Commerce a outros produtos Adobe DX.
exl-id: 5a754106-c66a-4280-9896-6d065df8a841
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 1d8609a607e0bcb74fdef47fb8e4e582085836e2
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Criar eventos personalizados

É possível estender a variável [plataforma de evento](events.md) criando seus próprios eventos de vitrine eletrônica para coletar dados exclusivos de seu setor. Ao criar e configurar um evento personalizado, ele é enviado para o [Coletor de eventos do Adobe Commerce](https://github.com/adobe/commerce-events/tree/main/packages/commerce-events-collectors).

## Lidar com eventos personalizados

Eventos personalizados são compatíveis somente com o Adobe Experience Platform. Os dados personalizados não são encaminhados para painéis e rastreadores de métricas do Adobe Commerce.

Para qualquer `custom` evento, o coletor adiciona um `personId` (`ecid`) para `customContext` e envolve um `xdm` antes de encaminhar para o Edge.

Exemplo:

Evento personalizado publicado pelo SDK de eventos da Adobe Commerce:

```javascript
mse.publish.custom({
    customContext: { customStrAttr: "cheetah", customNumAttr: 128 },
});
```

Na borda do Experience Platform:

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

## Lidar com substituições de eventos (atributos personalizados)

As substituições de atributo para eventos padrão são compatíveis somente com o Experience Platform. Os dados personalizados não são encaminhados para painéis e rastreadores de métricas do Commerce.

Para qualquer evento com um conjunto `customContext`, o coletor substitui `personId` e Adobe Analytics e encaminha todos os outros atributos definidos no `customContext`.

Exemplos:

Exibição de produto com substituições publicadas pelo SDK de eventos do Adobe Commerce:

```javascript
mse.publish.productPageView({
    customContext: { customCode: "okapi" },
});
```

Na borda do Experience Platform:

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

Exibição de produto com substituições do Adobe Commerce publicadas pelo SDK de eventos do Adobe Commerce:

```javascript
mse.publish.productPageView({
    customContext: { commerce: { customCode: "mongoose" } },
});
```

Na borda do Experience Platform:

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
