---
title: Fluxo de trabalho de implementação
description: Saiba mais sobre as etapas para implementar com êxito o [!DNL Product Recommendations] na sua loja.
exl-id: 766e1191-0330-4515-9331-e45318539dc9
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# Fluxo de trabalho de implementação

[!DNL Product Recommendations] O usa dados comportamentais e de catálogo:

- Comportamental - Dados do envolvimento de um comprador no site, como exibições de produtos, itens adicionados a um carrinho e compras. A Adobe Commerce e a Adobe Sensei não coletam informações de identificação pessoal.

- Catálogo - Metadados do produto, como nome, preço e disponibilidade.

Ao instalar o `magento/product-recommendations module`, o Adobe Sensei agrega os dados comportamentais e de catálogo e cria [!DNL Product Recommendations] para cada tipo de recomendação. A variável [!DNL Product Recommendations] em seguida, implanta essas recomendações na loja. Para ajudar você a implementar as recomendações de produtos em sua loja, use o seguinte fluxo de trabalho:

>[!NOTE]
>
> Se sua loja for implementada usando o PWA Studio, consulte a [Documentação do PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Se você usar uma tecnologia de front-end personalizada, como React ou Vue JS, saiba como [integrar](headless.md) [!DNL Product Recommendations] em sua loja headless.

## Fluxo de trabalho

1. **Implantar coleção de dados para produção**

   Implantação [!DNL Product Recommendations] requer dois [fontes de dados](type.md): catálogo e comportamental. Como a produção é o único ambiente em que as ações dos compradores são capturadas e analisadas, é do seu interesse iniciar a coleta de dados sobre a produção o mais rápido possível. [Saiba mais](behavioral-data.md) como o Adobe Sensei treina modelos de aprendizado de máquina que resultam em recomendações de maior qualidade. Como um benefício adicional, ao começar a coletar dados comportamentais sobre a produção, você pode [buscar recomendações](verify.md) com base nesses dados de produção enquanto opera em ambientes não relacionados à produção. Em seguida, você pode testar e experimentar com diferentes recomendações que são computadas com base nos dados reais do comprador coletados na produção.

   Para implantar a coleta de dados na produção, você deve [instalar e configurar](install-configure.md) o [!DNL Product Recommendations] módulo fornecendo uma [Chave de API](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html).

   >[!TIP]
   >
   > A implantação da coleção de dados não altera a aparência da loja nem a experiência dos compradores. Somente criar e implantar unidades de recomendação altera a experiência do cliente em sua loja. Certifique-se de testar seu ambiente de não produção antes de implantar na produção. Além disso, não crie unidades de recomendação até personalizar o modelo. Consulte a próxima etapa.

1. **Personalizar o modelo para corresponder ao seu estilo**

   Sua loja representa sua marca, portanto, modifique o modelo de recomendações de produto para corresponder ao tema do site.

   >[!TIP]
   >
   > Personalizando o modelo, você pode especificar sua folha de estilos, substituir onde uma unidade de recomendação aparece em uma página e assim por diante.

   Consulte [Personalizar](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/customize.html) na documentação do desenvolvedor para saber como concluir esta etapa.

1. **Testar recomendações em seu ambiente de não produção**

   É sempre uma prática recomendada testar uma nova tecnologia em seu ambiente de não produção antes de implantar na produção. O teste de recomendações em seu ambiente de não produção permite que você jogue com diferentes tipos de unidade de recomendação, posicionamento e páginas. Você pode extrair recomendações com base em dados comportamentais já coletados na produção enquanto testa em seu ambiente de não produção, de modo que os resultados da recomendação se baseiem no comportamento de compra dos clientes reais.

   >[!TIP]
   >
   > Certifique-se de que o catálogo de ambientes de não produção seja basicamente o mesmo que o que você tem em produção. Usar catálogos semelhantes garante que os produtos retornados nas unidades de recomendação mimetizem os produtos na produção.

   Consulte [Buscar](staging-environment.md) dados comportamentais do ambiente de produção para saber como concluir esta etapa.

1. **Criar e implantar recomendações em sua loja de produção**

   Agora que você implantou a coleção de dados comportamentais na produção, modificou o modelo de recomendações de produto e testou as recomendações usando o comportamento real do comprador, você está pronto para promover todos os códigos para produção e [criar](create.md) recomendações de produto em tempo real.
