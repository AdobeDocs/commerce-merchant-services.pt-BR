---
title: "[!DNL Live Search] Indexação"
description: "Saiba como [!DNL Live Search] indexa propriedades de atributo de produto."
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: c77b2f9cb55d3eb339dcc900ce606b94c592f559
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---

# Indexação

A variável [!DNL Live Search] o processo de indexação lê o catálogo de atributos do produto e cria um índice para que os produtos possam ser pesquisados, filtrados e apresentados rapidamente.

As propriedades do atributo de produto (metadados) determinam:

* Como um atributo pode ser usado no catálogo
* Sua aparência e comportamento na loja
* Os dados incluídos nas operações de transferência de dados

O escopo dos metadados do atributo é `website/store/store view`.

A variável [!DNL Live Search] A API permite que um cliente classifique por qualquer atributo de produto que tenha a [propriedade storefront](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` definir como `Yes` no Administrador do Adobe Commerce. Quando ativado, `Search Weight` e `Visible in Advanced Search` pode ser definido para o atributo.

[!DNL Live Search] não indexa produtos excluídos ou aqueles definidos como `Not Visible Individually`.

>[!NOTE]
>
> Clientes do Commerce com [!DNL Live Search] podem aproveitar as atualizações de alterações de preço e o tempo de sincronização mais rápidos em seus sites com o [Indexador de preços SaaS](../price-index/index.md).

## Pipeline de indexação

O cliente chama o serviço de pesquisa da loja para recuperar (filtrável, classificável) os metadados do índice. Somente atributos de produto pesquisáveis com o *Usar na navegação em camadas* propriedade definida como `Filterable (with results)` e *Usar para classificar na lista de produtos* definir como `Yes` pode ser chamado pelo serviço de pesquisa.
Para construir uma consulta dinâmica, o serviço de pesquisa precisa saber quais atributos podem ser pesquisados e quais deles [peso](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-results.html#weighted-search). [!DNL Live Search] respeita os pesos de pesquisa do Adobe Commerce (1-10, onde 10 é a prioridade mais alta). A lista de dados sincronizados e compartilhados com o serviço de catálogo pode ser encontrada no schema, que é definido em:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] diagrama de pesquisa do cliente de indexação](assets/indexing-pipeline.svg)

1. Verificar comerciante para [!DNL Live Search] direito.
1. Obtenha exibições da loja com alterações nos metadados do atributo.
1. Armazenar atributos de indexação.
1. Reindexar índice de pesquisa.

### Índice completo

Quando [!DNL Live Search] estiver configurado e sincronizado durante a integração, pode levar até 30 minutos para criar o índice inicial. Catálogos grandes podem levar mais tempo para serem indexados. O processo começa após `cron` O envia o feed e termina a execução.

Os seguintes eventos acionam uma criação de índice e sincronização completa:

* Integração [sincronização de dados do catálogo](install.md#synchronize-catalog-data)
* Alterações nos metadados do atributo

Por exemplo, alterar a variável `Use in Search` propriedade do `color` atributo de `No` para `Yes` altera os metadados do atributo para `searchable=true`, e aciona uma sincronização completa e reindexação. Os metadados de atributo a seguir acionam uma sincronização completa e reindexação quando alterados:

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### Streaming de atualizações de produto

Depois que o índice inicial for criado durante [integração](install.md#synchronize-catalog-data), as seguintes atualizações de produtos incrementais são continuamente sincronizadas e reindexadas:

* Novos produtos adicionados ao catálogo
* Alterações nos valores de atributo de produto

Por exemplo, adicionar um novo valor de amostra à variável `color` o atributo é manipulado como uma atualização de produto de transmissão.
Fluxo de trabalho de atualização de transmissão:

1. Os produtos atualizados são sincronizados da instância do Adobe Commerce para o serviço de catálogo.
1. O serviço de indexação procura continuamente atualizações de produtos no serviço de catálogo. Os produtos atualizados são indexados à medida que chegam ao serviço de catálogo.
1. Pode levar até 15 minutos para que uma atualização de produto seja disponibilizada no [!DNL Live Search].

## Pesquisa de cliente

A variável [!DNL Live Search] A API permite que um cliente classifique por qualquer atributo de produto classificável definindo o [propriedade storefront](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html), *Usado para classificar em listagens de produtos* para `Yes`. Dependendo do tema, essa configuração faz com que o atributo seja incluído como uma opção no [Classificar por](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) controle de paginação em páginas de catálogo. Até 200 atributos de produto podem ser indexados por [!DNL Live Search], com [propriedades da loja](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) que podem ser pesquisadas e filtradas.
Os metadados do índice são armazenados no pipeline de indexação e podem ser acessados pelo serviço de pesquisa.

![[!DNL Live Search] diagrama da API de metadados de índice](assets/index-metadata-api.svg)

### Fluxo de trabalho de atributo classificável

1. O cliente chama o Serviço de pesquisa.
1. O Serviço de pesquisa chama o Serviço de administração de pesquisa.
1. O serviço de pesquisa chama o pipeline de indexação.

## Indexado para todos os produtos

A ordem dos campos nesta lista reflete a ordem típica das colunas nos dados do produto exportados.

* `environment_id`
* `website_code`
* `store_code`
* `store_view_code`
* `product_id`
* `sku`
* `name`
* `type`
* `displayable`
* `deleted`
* `url`
* `currency`
* `meta_description`
* `meta_keyword`
* `meta_title`
* `description`
* `short_description`
* `weight`
* `image`
* `small_image`
* `thumbnail_image`
* `prices`
* `in_stock`
* `low_stock`

O campo a seguir é indexado para todos os produtos configuráveis:

* `childrenSkus`
