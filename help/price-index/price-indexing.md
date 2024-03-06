---
title: Indexação de preços SaaS
description: Usando a indexação de preços SaaS para melhorar o desempenho
seo-title: Adobe SaaS Price Indexing
seo-description: Price indexing give performance improvements using SaaS infrastructure
exl-id: 5b92d6ea-cfd6-4976-a430-1a3aeaed51fd
source-git-commit: a90fcd8401b7745a65715f68efccdb3ce7c77ccb
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Indexação de preços SaaS

A indexação de preços SaaS acelera o tempo necessário para que as alterações de preço sejam refletidas no [Commerce Services](../landing/saas.md) após terem sido apresentadas. Isso permite que os comerciantes com catálogos grandes e complexos, ou com vários sites ou grupos de clientes, processem continuamente as alterações de preço.
Se você tiver uma loja headless ou usar o [catálogo-adaptador](./catalog-adapter.md) , os clientes podem desativar o indexador de preço principal do Adobe Commerce.

Processos computacionais pesados, como indexação e cálculo de preços, foram movidos do núcleo do Commerce para a infraestrutura da Adobe Cloud. Isso permite que os comerciantes aumentem rapidamente os recursos para aumentar os tempos de indexação de preços e refletir essas alterações mais rapidamente.

O fluxo de dados de indexação principal para serviços SaaS é semelhante a:

![Fluxo de dados padrão](assets/old_way.png)

Com a indexação de preços SaaS, o fluxo é:

![Fluxo de dados de indexação de preço SaaS](assets/new_way.png)

Todos os comerciantes podem se beneficiar dessas melhorias, mas os que verão os maiores ganhos são os clientes com:

* Alterações constantes de preço: comerciantes que exigem alterações repetidas em seus preços para atender a objetivos estratégicos, como promoções frequentes, descontos sazonais ou markdowns de inventário.
* Vários sites e/ou grupos de clientes: comerciantes com catálogos de produtos compartilhados em vários sites (domínios/marcas) e/ou grupos de clientes.
* Grande número de preços únicos em sites ou grupos de clientes: comerciantes com catálogos de produtos compartilhados extensos que contêm preços únicos em sites ou grupos de clientes, como comerciantes B2B com preços pré-negociados, marcas com estratégias de preços diferentes.

A indexação de preço do SaaS está disponível gratuitamente para clientes que usam os serviços da Adobe Commerce e oferece suporte ao cálculo de preço para todos os tipos de produto Adobe Commerce incorporados.

Este guia descreve como a indexação de preços do SaaS funciona e como ativá-la.

## Requisitos

* Adobe Commerce 2.4.4+
* Pelo menos um dos seguintes Commerce Services com a versão mais recente da extensão do Adobe Commerce:

   * [Serviço de catálogo](../catalog-service/overview.md)
   * [Live Search](../live-search/guide-overview.md)
   * [Recommendations do produto](../product-recommendations/guide-overview.md)

Os usuários do Luma e do Adobe Commerce Core GraphQL podem instalar o [`catalog-adapter`](catalog-adapter.md) Extensão que fornece compatibilidade com o Luma e o Core GraphQl e desativa o indexador de Preço de produto do Adobe Commerce.

## Uso

Depois de atualizar sua instância do Adobe Commerce com suporte à indexação de preços do SaaS, sincronize os novos feeds:

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

## Preços para tipos de produtos personalizados

Os cálculos de preço são compatíveis com tipos de produtos personalizados, como preço base, preço especial, preço de grupo, preço de regra de catálogo etc.

Se você tiver um tipo de produto personalizado que usa uma fórmula específica para calcular o preço final, será possível estender o comportamento do feed de preço do produto.

1. Crie um plug-in no `Magento\ProductPriceDataExporter\Model\Provider\ProductPrice` classe.

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
       <type name="Magento\ProductPriceDataExporter\Model\Provider\ProductPrice">
           <plugin name="custom_type_price_feed" type="YourModule\CustomProductType\Plugin\UpdatePriceFromFeed" />
       </type>
   </config>
   ```

1. Crie um método com a fórmula personalizada:

   ```php
   class UpdatePriceFromFeed
   {
       /**
       * @param ProductPrice $subject
       * @param array $result
       * @param array $values
       *
       * @return array
       */
       public function afterGet(ProductPrice $subject, array $result, array $values) : array
       {
           // Override the output $result with your data for the corresponding products (see original method for details) 
           return $result;
       }
   }
   ```
