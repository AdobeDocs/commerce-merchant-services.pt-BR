---
title: Estender e personalizar dados do feed de exportação de dados SaaS
description: Saiba como estender e personalizar os dados do feed  [!DNL SaaS Data Export] .
role: Admin, Developer
exl-id: 69300242-d317-4ec8-86d0-0cd5d0c9c958
source-git-commit: b80bc2867f44e6123adb104eb148ac5e8f80b63d
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Estender e personalizar dados do feed de exportação de dados SaaS

A extensão [!DNL Commerce Data Export] fornece uma maneira de exportar dados do aplicativo [!DNL Commerce] para serviços da Commerce, como o Live Search, o Serviço de Catálogo e o Product Recommendations. Se necessário, você pode estender e personalizar os dados do feed para incluir dados adicionais ou modificar os dados coletados atualizando o módulo `Magento\CatalogDataExporter`.

>[!NOTE]
>
>Adicionar novos dados ao feed ou modificar dados existentes pode afetar o desempenho da coleção de feed e causar problemas na lógica de processamento no lado do Adobe Commerce. Teste o código personalizado antes de mesclar com um ambiente de produção.

## Estender dados de atributos no feed de produtos

O feed de produtos inclui atributos padrão que são necessários para o processamento do produto ou geralmente usados pelos consumidores. Você pode incluir atributos de sistema adicionais no feed de produtos adicionando-os ao feed.

Para concluir esta tarefa, atualize o módulo `magento/catalog-data-exporter` para adicionar os atributos de sistema adicionais ao [arquivo de configuração de injeção de dependência](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/) (`di.xml`). Adicione os atributos à consulta de Atributo de Produto (`Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery`).

**Exemplo**

```xml
    <type name="Magento\CatalogDataExporter\Model\Query\ProductAttributeQuery">
        <arguments>
            <argument name="systemAttributes" xsi:type="array">
                <item name="news_from_date" xsi:type="string">news_from_date</item>
                ...
                <item name="some_system_attribute_code">some_system_attribute_code</item>
            </argument>
        </arguments>
    </type>
```
