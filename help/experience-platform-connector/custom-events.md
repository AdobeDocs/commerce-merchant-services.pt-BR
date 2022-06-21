---
title: Criar eventos personalizados
description: Saiba como criar eventos personalizados para conectar seus dados do Adobe Commerce a outros produtos Adobe DX.
source-git-commit: 1dd8f94e632bb98666ad252badf8420a014260fb
workflow-type: tm+mt
source-wordcount: '213'
ht-degree: 0%

---

# Criar eventos personalizados

É possível estender o [plataforma de eventos](events.md) ao criar seus próprios eventos de loja para coletar dados exclusivos do seu setor. Ao criar e configurar um evento personalizado, ele é enviado para a [Coletor de eventos de vitrine do Magento](https://www.npmjs.com/package/@adobe/magento-storefront-event-collector).

## Gerenciar eventos personalizados

Os eventos personalizados são compatíveis somente com a Adobe Experience Platform. Os dados personalizados não são encaminhados para painéis e rastreadores de métricas do Adobe Commerce.

Para qualquer `custom` , o coletor adiciona um `personId` (`ecid`) a `customContext` e envolve uma `xdm` ao redor dele antes de encaminhar para o Edge.

Exemplo:

Evento personalizado publicado por meio do SDK do MSE:

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

Exibição de produto com substituições publicadas pelo SDK do MSE:

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

A exibição de produto com Adobe Commerce substitui publicadas pelo SDK do MSE:

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
