---
title: Fluxo de trabalho de implementação
description: Saiba mais sobre as etapas para implementar com êxito [!DNL Product Recommendations] na sua loja.
exl-id: 766e1191-0330-4515-9331-e45318539dc9
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# Fluxo de trabalho de implementação

[!DNL Product Recommendations] O usa dados comportamentais e de catálogo:

- Comportamento - Dados do envolvimento de um comprador no site, como exibições de produtos, itens adicionados a um carrinho e compras. O Adobe Commerce e o Adobe Sensei não coletam informações de identificação pessoal.

- Catálogo - Metadados do produto, como nome, preço e disponibilidade.

Ao instalar o `magento/product-recommendations module`, o Adobe Sensei agrega os dados comportamentais e de catálogo e cria [!DNL Product Recommendations] para cada tipo de recomendação. O [!DNL Product Recommendations] em seguida, implanta essas recomendações na loja. Para ajudar você a implementar recomendações de produto na loja, use o seguinte fluxo de trabalho:

>[!NOTE]
>
> Se a loja estiver implementada usando o PWA Studio, consulte a [Documentação do PWA](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/). Se você usar uma tecnologia de primeiro plano personalizada, como React ou Vue JS, saiba como [integrar](headless.md) [!DNL Product Recommendations] em sua vitrine sem cabeça.

## Fluxo de trabalho

1. **Implantar coleta de dados para produção**

   Implantação [!DNL Product Recommendations] requer dois [fontes de dados](type.md): catálogo e comportamento. Como a produção é o único ambiente em que as ações dos compradores são capturadas e analisadas, é de seu interesse iniciar a coleta de dados na produção o mais rápido possível. [Saiba mais](behavioral-data.md) como a Adobe Sensei treina modelos de aprendizado de máquina que resultam em recomendações de maior qualidade. Como um benefício adicional, ao começar a coletar dados comportamentais sobre a produção, você pode [buscar recomendações](verify.md) com base nesses dados de produção ao operar em ambientes não relacionados à produção. Em seguida, você pode testar e testar diferentes recomendações que são calculadas com base em dados reais do comprador coletados na produção.

   Para implantar a coleta de dados na produção, é necessário [instalar e configurar](install-configure.md) o [!DNL Product Recommendations] , fornecendo um [Chave da API](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html).

   >[!TIP]
   >
   > Implantar a coleta de dados não altera a aparência da loja ou a experiência dos compradores. Somente a criação e implantação de unidades de recomendação altera a experiência do cliente em sua loja. Certifique-se de testar seu ambiente de não produção antes de implantar na produção. Além disso, não crie unidades de recomendação até personalizar seu modelo. Veja a próxima etapa.

1. **Personalizar o modelo para corresponder ao seu estilo**

   Sua loja representa sua marca, portanto, certifique-se de modificar o modelo de recomendações de produto para corresponder ao tema do site.

   >[!TIP]
   >
   > Ao personalizar o modelo, você pode especificar sua folha de estilos, substituir onde uma unidade de recomendação aparece em uma página e assim por diante.

   Consulte [Personalizar](https://experienceleague.adobe.com/docs/commerce-merchant-services/product-recommendations/developer/customize.html) na documentação do desenvolvedor para saber como concluir esta etapa.

1. **Testar recomendações em seu ambiente de não produção**

   É sempre uma prática recomendada testar uma nova tecnologia em seu ambiente de não produção antes de implantar na produção. Testar recomendações em seu ambiente de não produção permite reproduzir com diferentes tipos de unidades de recomendação, posicionamento e páginas. Você pode extrair recomendações com base em dados comportamentais já coletados na produção enquanto teste em seu ambiente de não produção, de modo que os resultados da recomendação sejam baseados no comportamento de compras dos clientes reais.

   >[!TIP]
   >
   > Certifique-se de que o catálogo de ambiente de não produção seja basicamente o mesmo que o catálogo de ambiente de produção. O uso de catálogos similares garante que os produtos retornados nas unidades de recomendação imitem os produtos na produção.

   Consulte [Buscar](staging-environment.md) dados comportamentais do ambiente de produção para saber como concluir essa etapa.

1. **Criar e implantar recomendações na loja de produção**

   Agora que você implantou a coleta de dados comportamentais na produção, modificou o modelo de recomendações do produto e testou as recomendações usando o comportamento real do comprador, você está pronto para promover todo o código para produção e [criar](create.md) recomendações de produto ao vivo.
