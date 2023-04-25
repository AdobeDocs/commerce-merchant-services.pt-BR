---
title: "[!DNL Live Search] Indexando"
description: "Saiba como [!DNL Live Search] indexa as propriedades do atributo do produto."
exl-id: 04441e58-ffac-4335-aa26-893988a89720
source-git-commit: f310f840e286859070002ab0e23eda3787c89f36
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---

# Indexação

As propriedades do atributo do produto (metadados) determinam:

* Como um atributo pode ser usado no catálogo
* Sua aparência e comportamento na loja
* Os dados incluídos em operações de transferência de dados

O escopo dos metadados do atributo é `website/store/store view`.

O [!DNL Live Search] A API permite que um cliente classifique por qualquer atributo de produto que tenha a variável [propriedade storefront](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) `Use in Search` defina como `Yes` no Administrador do Adobe Commerce. Quando ativado, `Search Weight` e `Visible in Advanced Search` pode ser definido para o atributo .

[!DNL Live Search] não indexa produtos excluídos ou aqueles definidos como `Not Visible Individually`.

>[!NOTE]
>
> Clientes comerciais com [!DNL Live Search] pode aproveitar as vantagens de atualizações de preço e tempo de sincronização mais rápido em seus sites com a variável [Indexador de preço SaaS](../price-index/index.md).

## pipeline de indexação

O cliente chama o serviço de pesquisa da loja para recuperar metadados de índice (filtráveis, classificáveis). Somente atributos de produto pesquisáveis com a variável *Usar na navegação em camadas* propriedade definida como `Filterable (with results)` e *Usar para classificação na lista de produtos* defina como `Yes` pode ser chamado pelo serviço de pesquisa.
Para construir uma consulta dinâmica, o serviço de pesquisa precisa saber quais atributos podem ser pesquisados e seu peso. [!DNL Live Search] respeita os pesos de pesquisa do Adobe Commerce (1-10, onde 10 é a prioridade mais alta). A lista de dados sincronizados e compartilhados com o serviço de catálogo pode ser encontrada no schema , que é definido em:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

![[!DNL Live Search] indexando diagrama de pesquisa do cliente](assets/indexing-pipeline.svg)

1. Verificar comerciante para [!DNL Live Search] direito.
1. Obter visualizações de loja com alterações nos metadados do atributo.
1. Armazenar atributos de indexação.
1. Reindexe o índice de pesquisa.

### Índice completo

When [!DNL Live Search] estiver configurado e sincronizado durante a integração, pode levar até oito horas para criar o índice inicial. O processo começa após `cron` envia o feed e termina a execução.

Os seguintes eventos acionam uma sincronização completa e uma build de índice:

* Integração [sincronização de dados do catálogo](install.md#synchronize-catalog-data)
* Alterações nos metadados do atributo

Por exemplo, alterar a variável `Use in Search` da `color` atributo de `No` para `Yes` altera os metadados do atributo para `searchable=true`e aciona uma sincronização completa e uma reindexação. Os seguintes metadados de atributo acionam uma sincronização completa e reindexam quando alterados:

* `filterableInSearch`
* `searchable`
* `sortable`
* `visibleInSearch`

### Transmissão de atualizações de produtos

Depois que o índice inicial é criado durante [integração](install.md#synchronize-catalog-data), as seguintes atualizações de produtos incrementais são sincronizadas e reindexadas continuamente:

* Novos produtos adicionados ao catálogo
* Alterações nos valores do atributo do produto

Por exemplo, adicionar um novo valor de amostra ao `color` é tratado como uma atualização de produto de streaming.
Fluxo de trabalho de atualização de fluxo:

1. Os produtos atualizados são sincronizados da instância do Adobe Commerce para o serviço de catálogo.
1. O serviço de indexação procura continuamente atualizações de produtos do serviço de catálogo. Os produtos atualizados são indexados à medida que chegam ao serviço de catálogo.
1. Pode levar até 15 minutos para que uma atualização de produto fique disponível em [!DNL Live Search].

## Pesquisa de cliente

O [!DNL Live Search] A API permite que um cliente classifique por qualquer atributo de produto classificável definindo a variável [propriedade storefront](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html), *Usado para classificação em listas de produtos* para `Yes`. Dependendo do tema, essa configuração faz com que o atributo seja incluído como uma opção no [Classificar por](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html) controle de paginação em páginas de catálogo. Até 300 atributos de produto podem ser indexados por [!DNL Live Search], com [propriedades storefront](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html) que podem ser pesquisados e filtrados.
Os metadados de índice são armazenados no pipeline de indexação e são acessíveis pelo serviço de pesquisa.

![[!DNL Live Search] diagrama da API de metadados de índice](assets/index-metadata-api.svg)

### Fluxo de trabalho do atributo classificável

1. O cliente chama o Serviço de pesquisa.
1. O Serviço de Pesquisa chama o Serviço de Administração de Pesquisa.
1. O serviço de pesquisa chama o pipeline de indexação.

## Indexado para todos os produtos

A ordem dos campos nesta lista reflete a ordem típica das colunas em dados de produto exportados.

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
