---
title: Teste no ambiente de preparo
description: Saiba como usar [!DNL Product Recommendations] do ambiente de produção em seu ambiente de preparo para fins de teste.
exl-id: 178ff2aa-7821-45f7-85f1-d490d8182817
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# Teste no ambiente de preparo

Antes de implantar as recomendações no ambiente de produção, é necessário testar em um ambiente de não produção, para garantir que tudo funcione conforme o esperado.

[!DNL Product Recommendations] produtos de retorno com base em [dados comportamentais do comprador](behavioral-data.md) coletado da loja. Em um ambiente não relacionado à produção, no entanto, é provável que você não tenha dados comportamentais dos compradores. O único tipo de recomendação que você pode testar sem dados comportamentais é `More like this`. Esse tipo de recomendação não requer dados de entrada, pois usa uma correspondência de similaridade direta de conteúdo.

Os seguintes tipos de recomendação exigem dados comportamentais:

- Mais visualizados
- Visualizou isso, viu que
- Comprou isto, comprou aquilo

Como você pode testar suas recomendações em um ambiente de não produção usando dados comportamentais? Há algumas opções.

## Buscar recomendações do ambiente de produção (recomendado)

O Adobe Commerce permite buscar recomendações do ambiente de produção e visualizá-las no ambiente de não-produção por [switching](settings.md) o espaço de dados SaaS.

Para obter as recomendações do ambiente de produção, você deve garantir que:

- A coleta de dados da vitrine é [configurado e ativado](install-configure.md) em produção.
- Seu catálogo de ambiente de não produção é basicamente o mesmo que você tem em produção. O uso de catálogos similares garante que os produtos retornados nas unidades de recomendação imitem os de produção.

## Gerar dados comportamentais em um ambiente de não produção

1. Implante o `magento/product-recommendations` para um ambiente de não produção em que os dados do catálogo são semelhantes ao catálogo de produção.

1. Usar uma das IDs do espaço de dados de não produção para [configuração](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) em Admin.

1. Gere os dados por conta própria clicando em sua loja para imitar o comportamento dos compradores reais (ou crie um script de automação). Por meio dos testes, você gera eventos comportamentais em seu ambiente de não produção. Esses eventos são usados para produzir afinidades de produto que alimentam as recomendações. Para testes, [!DNL Commerce] O sugere que você interaja com os seguintes tipos de recomendação:

   - Mais visualizados - Requer dados de entrada mínimos. Os usuários devem visualizar os produtos.
   - Revisado isso, visualizado que - Requer que vários usuários visualizem vários produtos.
   - Comprado isso, comprado - Requer que vários usuários comprem vários produtos.

### Avisos

- Os dados comportamentais e de catálogo do Espaço de dados SaaS de não produção identificam um ambiente isolado no qual as recomendações de produto resultantes são baseadas inteiramente nos dados comportamentais gerados na loja associada.

- Como você não tem grandes quantidades de dados comportamentais, os dados de entrada para computar associações de produtos são escassos. No entanto, esses dados ainda são enviados ao Sensei para calcular os modelos de aprendizado de máquina e fornecer recomendações com base nos dados gerados nesse ambiente.
