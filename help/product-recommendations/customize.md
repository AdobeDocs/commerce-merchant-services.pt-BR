---
title: Personalizar
description: Saiba como personalizar as recomendações de produto.
exl-id: b1b8e770-45ec-4403-b79b-4f0a9f7bd959
source-git-commit: acfaa1d72265e42b973677a7e014ba4b350ec56b
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Personalizar

Quando você instala o módulo Product Recommendations, o Adobe Commerce cria a variável `ProductRecommendationsLayout` diretório. Esse diretório contém arquivos de modelo que podem ser personalizados para alterar a forma como as recomendações são exibidas na loja. Especificamente, você pode modificar ou substituir o seguinte modelo:

`<your theme>/Magento_ProductRecommendationsLayout/web/template/recommendations.html`

Para obter mais informações sobre a modificação de arquivos de modelo, consulte [Personalização de modelo](https://developer.adobe.com/commerce/frontend-core/guide/templates/walkthrough/) no Guia do desenvolvedor de front-end.

Se você modificar a variável `recommendations.html` , você deve preservar as seguintes tags no arquivo para garantir que o Adobe Commerce possa coletar métricas de recomendação da sua loja:

| Tag | Uso |
|---|---|
| `<div data-bind="attr : {'data-unit-id' : unitId }"...</div>` | Coleta eventos de exibição. |
| `<a data-bind="attr : {'data-sku' : sku, 'data-unit-id'}"...</a>` | Coleta eventos de clique. <br/>**Nota:** Se você adicionar tags de âncora, será necessário incluir esses atributos. |

Além do `recommendations.html` arquivo, o `ProductRecommendationsLayout` O diretório contém os seguintes subdiretórios:

| Diretório | Finalidade |
|---|---|
| `layout` | Contém `*.xml` arquivos para cada tipo de página |
| `templates` | Contém arquivos que chamam os scripts de busca e renderização |
| `web/js` | Contém os arquivos JavaScript que buscam e renderizam recomendações para sua loja |
| `web/template` | Contém o modelo para o `magento/product-recommendations` módulo |

## Posicionamento da unidade de recomendação

Quando você [criar](create.md) uma recomendação, você especifica a [localização](placement.md) onde ele aparece na página. Uma unidade de recomendação pode ser colocada na parte superior ou inferior do container de conteúdo principal. No entanto, é possível personalizar essa disposição. Se você criar um tipo de conteúdo de recomendação do Page Builder, use as ferramentas do Page Builder para posicionar a unidade de recomendação na página. Para todos os outros tipos de página, edite o `*.xml` arquivos gerados quando a recomendação é criada.

1. Altere para a variável `layout` diretório:

   ```bash
   cd `<your theme>/Magento_ProductRecommendationsLayout/layout`
   ```

   A tabela a seguir lista os arquivos XML presentes nesse diretório:

   | Nome do arquivo | Página |
   |---|---|
   | `catalog_category_view.xml` | Categoria |
   | `catalog_product_view.xml` | Detalhes do produto |
   | `checkout_cart_index.xml` | Carrinho |
   | `checkout_onepage_success.xml` | Check-out |
   | `cms_index_index.xml` | Início |

   >[!NOTE]
   >
   >Os nomes de arquivo no `layout` o diretório pode ser diferente se a loja usar extensões de terceiros.

1. Modifique o `catalog_product_view.xml` para que a unidade de recomendação apareça após a imagem do produto na página de detalhes do produto. Antes de personalizar esse arquivo XML, examine-o e entenda as seções que você precisará modificar:

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="main.content">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   No trecho acima, a variável `main.content` O bloco de referência indica que a unidade de recomendação será colocada em algum lugar em relação a esse elemento. Seus `block` o elemento contém o `after="-"` atributo, que especifica que a unidade de recomendação será exibida na página após o bloco de conteúdo principal.

1. Vamos modificar esse arquivo especificando um bloco de conteúdo diferente.

   Alterar o bloco de referência `name` de `main.content` para `product.info.media`.

   ```xml
   <?xml version="1.0"?>
   <page xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:View/Layout/etc/page_configuration.xsd">
       <referenceBlock name="page.wrapper">
           <block class="Magento\Framework\View\Element\Template" before="-" name="product_recommendations_fetcher" template="Magento_ProductRecommendationsStorefront::fetcher.phtml" />
       </referenceBlock>
       <body>
           <referenceBlock name="product.info.media">
               <block class="Magento\ProductRecommendationsStorefront\Block\Renderer" after="-" name="product_recommendations_product_below_content" template="Magento_ProductRecommendationsStorefront::renderer.phtml">
                   <arguments>
                       <argument name="pagePlacement" xsi:type="string">below-main-content</argument>
                   </arguments>
               </block>
           </referenceBlock>
       </body>
   </page>
   ```

   Essa alteração faz com que sua unidade de recomendação apareça depois da imagem do produto na página Detalhes do produto. Se desejar que a unidade de recomendação apareça antes da variável `product.info.media`, altere o `after="-"` atributo para `before="-"`. A variável `pagePlacement` argumento é um argumento interno que não deve ser modificado.

Consulte [visão geral do layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/) para obter mais informações sobre os tipos de blocos na página.

## Atributos de produto personalizados

Os desenvolvedores geralmente precisam acessar valores de atributos de produto personalizados em unidades de recomendações em vitrines para que possam adicionar tratamentos visuais aos produtos com base nesses atributos.

Por exemplo, se sua loja vende alguns produtos orgânicos, você pode ter um atributo personalizado nesses produtos que os designa como `Organic = Yes`. Talvez seja necessário acessar esse valor de atributo na loja para que você possa dar a esses produtos um tratamento visual especial quando eles aparecerem no Recommendations. Da mesma forma, o acesso a esses valores de atributos de produto personalizados permite marcar os produtos ou direcionar a lógica personalizada na camada de apresentação do site.

![Adicionar medalha](assets/unit-custom.png)

Para garantir que um atributo de produto personalizado esteja disponível ao renderizar a unidade de recomendação na página, defina o `Used in Product Listing` propriedade para `Yes` no [Atributos do produto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-product-create.html) na página Admin.

Quando essa propriedade é definida, a carga JSON inclui um `attributes` objeto que contém uma matriz de códigos e valores de atributo. É possível aplicar o estilo personalizado da loja com base nesses valores de atributo, como adicionar tratamentos visuais especiais ou selos, conforme mencionado anteriormente.

>[!NOTE]
>
>As alterações no atributo do produto podem levar até uma hora para serem exibidas na carga JSON.
