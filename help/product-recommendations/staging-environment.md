---
title: Teste no ambiente de preparo
description: Saiba como usar o [!DNL Product Recommendations] do ambiente de produção no ambiente de preparo para fins de teste.
exl-id: 178ff2aa-7821-45f7-85f1-d490d8182817
feature: Services, Recommendations, Staging
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# Teste no ambiente de preparo

Antes de implantar recomendações para o ambiente de produção, você deve testar em um ambiente de não produção para garantir que tudo esteja funcionando como o esperado.

[!DNL Product Recommendations] devolução de produtos com base em [dados comportamentais do comprador](behavioral-data.md) coletado em sua loja. No entanto, em um ambiente de não produção, é provável que você não tenha dados comportamentais de compradores. O único tipo de recomendação que você pode testar sem dados comportamentais é `More like this`. Esse tipo de recomendação não requer dados de entrada, pois usa uma correspondência direta de similaridade de conteúdo.

Os seguintes tipos de recomendações exigem dados comportamentais:

- Mais visualizados
- Visualizou isto, visualizou aquilo
- Comprei isto, comprei aquilo

Como você pode testar suas recomendações em um ambiente de não produção usando dados comportamentais? Há algumas opções.

## Buscar recomendações do ambiente de produção (recomendado)

O Adobe Commerce permite que você busque recomendações de seu ambiente de produção e as visualize em seu ambiente de não produção ao [alternância](settings.md) o espaço de dados SaaS.

Para buscar recomendações do seu ambiente de produção, você deve se certificar de que:

- A coleta de dados da vitrine eletrônica é [configurado e habilitado](install-configure.md) na produção.
- Seu catálogo de ambientes de não produção é basicamente o mesmo que você tem na produção. Usar catálogos semelhantes garante que os produtos retornados nas unidades de recomendação mimetizem os da produção.

## Gerar dados comportamentais em ambiente de não produção

1. Implante o `magento/product-recommendations` para um ambiente de não produção em que os dados do catálogo são semelhantes ao catálogo de produção.

1. Use uma das IDs de espaço de dados de não produção para [configuração](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) em Admin.

1. Gere os dados sozinho clicando em torno da loja para imitar o comportamento de compradores reais (ou criar um script de automação). Por meio de testes, você gera eventos comportamentais no ambiente de não produção. Esses eventos são usados para produzir as afinidades de produto que potencializam as recomendações. Para testes, [!DNL Commerce] A sugere que você interaja com os seguintes tipos de recomendações:

   - Mais visualizados - Requer o mínimo de dados de entrada. Os usuários devem visualizar os produtos.
   - Exibido isto, exibido aquilo - Requer que vários usuários visualizem vários produtos.
   - Comprei isto, comprei aquilo - Requer que vários usuários comprem vários produtos.

### Avisos

- Os dados comportamentais e de catálogo do espaço de dados SaaS de não produção identificam um ambiente isolado em que as recomendações do produto resultantes se baseiam inteiramente nos dados comportamentais gerados na loja associada.

- Como você não tem grandes quantidades de dados comportamentais, os dados de entrada para associações de produto de computação são escassos. No entanto, esses dados ainda são enviados para o Sensei para calcular os modelos de aprendizado de máquina e fornecer recomendações com base nos dados gerados nesse ambiente.
