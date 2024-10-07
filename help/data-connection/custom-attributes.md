---
title: Adicionar atributos de ordem personalizados
description: Saiba como adicionar atributos de pedido personalizados aos dados de back office e enviar esses atributos ao Experience Platform.
role: Admin, Developer
feature: Personalization, Integration
source-git-commit: 14d190726324e2f42d66c2270f2e27be5a74132f
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 2%

---

# Adicionar atributos de ordem personalizados

Neste artigo, você aprenderá a adicionar atributos personalizados a eventos de back office. Com atributos personalizados, você pode capturar insights de dados avançados para aprimorar as análises e criar experiências personalizadas para seus compradores.

Os atributos personalizados são aceitos em dois níveis:

- Nível do pedido
- Nível do item da ordem

>[!NOTE]
>
>O Adobe [!DNL Commerce] oferece suporte a atributos personalizados que têm um tipo de dados de cadeia de caracteres, Booleano ou data.

Adicionar atributos personalizados aos eventos de back office requer que você:

1. Crie um projeto na instalação do [!DNL Commerce].
1. Atualize seu esquema para que os novos atributos personalizados possam ser assimilados corretamente no Experience Platform.
1. Em Admin, confirme se os atributos personalizados estão sendo capturados e enviados para o Experience Platform.

>[!IMPORTANT]
>
>A estrutura de diretório e os exemplos de código abaixo ilustram como você pode implementar atributos personalizados. A estrutura de diretório e o código real necessários dependem da configuração e do ambiente da loja.

## Etapa 1: criar a estrutura de diretório

1. Navegue até o diretório `app/code` em sua instalação do [!DNL Commerce] e crie um diretório de módulo. Por exemplo: `Magento/AepCustomAttributes`. Esse diretório contém os arquivos necessários para seus atributos personalizados.
1. No diretório do módulo, crie um subdiretório chamado `etc`. O diretório `etc` contém os arquivos `module.xml`, `query.xml`, `di.xml` e `et_schema.xml`.

## Etapa 2: definir as dependências e a versão de configuração

Crie um arquivo `module.xml` que defina as dependências e a versão da instalação. Por exemplo:

```xml
<?xml version="1.0"?>
<!--
/**
* Copyright (c) [year], [name]. All rights reserved.
*/
-->
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
    <module name="Magento_SalesRuleStaging" setup_version="2.0.0">
        <sequence>
            <module name="Magento_Staging"/>
            <module name="Magento_SalesRule"/>
        </sequence>
    </module>
</config>
```

## Etapa 3: Recuperar dados da ordem de venda

Criar um arquivo `query.xml` que recupere dados de ordem de venda. Por exemplo:

```xml
<query>
    <source name="sales_order" type="sales">
        <attribute name="increment_id" operator="eq" alias="order_increment_id"/>
        <link source="inventory_source_item" condition_type="by_sku"/>
    </source>
</query>
```

## Etapa 4: configurar a injeção de dependência

Crie um arquivo `di.xml` que configure a injeção de dependência. Por exemplo:

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
          package="com.example.instrumentedtest"
          android:versionCode="1"
          android:versionName="1.0">
    <uses-sdk android:minSdkVersion="8" android:targetSdkVersion="15"/>
    
    <instrumentation
        android:name=".MyInstrumentationTestRunner"
        android:targetPackage="com.example.instrumentedtest"/>
    
    <!-- More instrumentation elements might be here -->
</manifest>
```

## Etapa 5: definir os serviços usados para a injeção de dependência

Crie um arquivo `et_schema.xml` que defina os serviços usados para a injeção de dependência. Por exemplo:

```xml
<services>
    <service id="App\Controller\MainController" class="App\Controller\MainController">
        <argument type="service" id="doctrine.orm.default_entity_manager"/>
        <argument type="service" id="form.factory"/>
        <argument type="service" id="security.authorization_checker"/>
    </service>

    <!-- ... -->

    <service id="App\Controller\SecurityController" class="App\Controller\SecurityController">
        <argument type="service" id="security.authentication_utils"/>
        <tag name="controller.service_arguments"/>
    </service>

    <!-- ... -->
</services>
```

## Etapa 6: criar um diretório para os arquivos PHP

No mesmo nível que o diretório `etc`, crie um diretório chamado `Module/Provider`. Este diretório contém os arquivos PHP `OrderCustomAttributes` e `OrderItemCustomAttributes`.

## Etapa 7: definir OrderCustomAttributes

Crie um arquivo `OrderCustomAttributes.php` que defina a ordem dos atributos personalizados. Por exemplo:

```php
namespace App\Transformers;

use League\Fractal\TransformerAbstract;
use Illuminate\Support\Collection;

class CustomAttributeTransformer extends TransformerAbstract
{
    protected $availableIncludes = [];
    protected $defaultIncludes = [];

    public function __construct($signsField, $jsonSignsField = null)
    {
        $this->signsField = $signsField;
        $this->jsonSignsField = $jsonSignsField;
    }

    public function transform(Collection $collection)
    {
        // Initialize array for additional information.
        $additionalInformation = [];

        // Source - this comes from values sent to this transformer.
        foreach ($collection->{$this->signsField} ?: [] as $value) {
            if (is_array($value)) {
                // If value is an array, serialize it.
                foreach ($value as &$item) {
                    if (isset($item['custom_attr'])) {
                        // Serialize custom attribute data.
                        ...
                    }
                }
            } else {
                // Add non-array values directly.
                ...
            }
        }

        ...

        return [
            'current' => ...,
            'additional_information' => ...,
            'source' => ...,
        ];
    }

    private function flatten(array $values)
    {
      return Arr::flatten($values);
  }
}
```

## Etapa 8: definir OrderItemCustomAttributes

Criar um arquivo `OrderItemCustomAttributes.php` que defina os atributos personalizados do item de pedido. Por exemplo:

```php
namespace Magento\AepCustomAttributes\Model\Provider;

use Magento\Framework\Serialize\Serializer\Json;

class OrderItemCustomAttribute
{
    private Json $jsonSerializer;
    private string $usingField;

    public function __construct(Json $jsonSerializer, string $usingField)
    {
        $this->jsonSerializer = $jsonSerializer;
        $this->usingField = $usingField;
    }

    public function get(array $values): array
    {
        $output = [];
        $values = $this->flatten($values);

        foreach ($values as $row) {
            $info = \is_string($row['additionalInformation']) ? $row['additionalInformation'] : '{}';
            $unserializedData = $this->jsonSerializer->unserialize($info) ?? [];

            $attrLabel = implode(',', ['label1', 'label2']);
            $unserializedData['custom_attr1'] = $attrLabel;

            $additionalInformation = [];
            foreach ($unserializedData as $name => $value) {
                $additionalInformation[] = [
                    'name' => $name,
                    'value' => \is_string($value) ? $value : $this->jsonSerializer->serialize($value),
                ];
            }

            foreach ($additionalInformation as $information) {
                $output[] = [
                    'additionalInformation' => $information,
                    $this->usingField => $row[$this->usingField],
                ];
            }
        }

        return $output;
    }

    private function flatten(array $values): array
    {
        return array_merge([], ...array_values($values));
    }
}
```

## Etapa 9: criar um diretório para o arquivo productContext

No mesmo nível que o diretório `etc`, crie um diretório chamado `Plugin/Module`. Este diretório contém o arquivo `ProductContext.php`.

## Etapa 10: definir a classe ProductContext

Crie um arquivo chamado `ProductContext.php` que defina a classe `ProductContext`. Por exemplo:

```php
namespace Magento\Catalog\Model\Product;

use Magento\Framework\App\ResourceConnection;
use Magento\Quote\Api\Data\CartInterface;

class ProductContext
{
    private $brandCache = [];
    private $resourceConnection;

    public function __construct(
        ResourceConnection $resourceConnection
    ) {
        $this->resourceConnection = $resourceConnection;
    }

    public function afterGetProductData($subject, array $result)
    {
        if (isset($result['brand_id'])) {
            if (!isset($this->brandCache[$result['brand_id']])) {
                // @todo load brand label by brand id.
                $this->brandCache[$result['brand_id']] = 'Brand Label ' . $result['brand_id'];
            }
            $result['brands'] = ['label' => $this->brandCache[$result['brand_id']]];
        }

        return $result;
    }
}
```

## Etapa 11: Registrar o módulo

No mesmo nível que o diretório `etc`, crie um arquivo `registration.php` que registre o módulo. Por exemplo:

```php
use \Magento\Framework\Component\ComponentRegistrar;

ComponentRegistrar::register(
    ComponentRegistrar::MODULE,
    'Dfe_Stripe',
    __DIR__
);
```

## Etapa 12: estender o esquema XDM existente

Para garantir que os novos atributos de pedido personalizados possam ser assimilados pelo esquema [!DNL Commerce] no Experience Platform, é necessário estender o esquema para incluir esses campos personalizados.

Para saber como estender um esquema XDM existente para incluir esses campos personalizados, consulte o artigo [Criar e editar esquemas na interface](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/resources/schemas#custom-fields-for-standard-groups) na documentação do Experience Platform. O campo ID do locatário é gerado dinamicamente; no entanto, a estrutura do campo deve se parecer com o exemplo fornecido na documentação do Experience Platform.

>[!IMPORTANT]
>
>Os atributos personalizados XDM devem corresponder aos atributos enviados de [!DNL Commerce].

Para `commerce.order`, adicione um campo para o nível Ordem:

![Nível do pedido](assets/order-level.png)

Para `productListItems`, adicione campos para o nível de item Ordem:

![Nível do Item da Ordem](assets/order-item-level.png)

## Etapa 12: Confirmar se os dados estão sendo capturados

Visualize a guia [Personalização de dados](connect-data.md#data-customization) no Administrador para confirmar se os dados do atributo personalizado estão sendo capturados e enviados para o Experience Platform.

### Solução de problemas

Se você vir a mensagem `No custom order attributes found.` na guia **[!UICONTROL Data Customization]**, confirme o seguinte:

1. Você concluiu os pré-requisitos para habilitar a [extensão do Conector de Dados](overview.md#prerequisites).
1. Você configurou [atributos de pedido personalizados](#add-custom-order-attributes).
1. Pelo menos um evento de pedido foi gerado.
