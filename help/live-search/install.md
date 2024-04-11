---
title: "Instalar [!DNL Live Search]"
description: "Saiba como instalar, atualizar e desinstalar [!DNL Live Search] da Adobe Commerce."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: 8a98e069cd9ec3d2c4fec33485e5c8186d94518f
workflow-type: tm+mt
source-wordcount: '1240'
ht-degree: 0%

---

# Instalar [!DNL Live Search]

[!DNL Live Search] O é instalado como uma extensão do Adobe Marketplace. Depois que a variável [!DNL Live Search] o módulo (com módulos de catálogo como dependências) é instalado e configurado, [!DNL Commerce] O começa a compartilhar dados de pesquisa e catálogo com serviços SaaS. Neste ponto, *Admin* os usuários podem configurar, personalizar e gerenciar aspectos de pesquisa, sinônimos e regras de merchandising.

Este tópico fornece instruções para fazer o seguinte:

* Instalar [!DNL Live Search] (Métodos 1 e 2)
* [Atualizar [!DNL Live Search]](#update)
* [Desinstalar [!DNL Live Search]](#uninstall)

## Antes de começar {#before-you-begin}

Faça o seguinte:

1. Confirme que [trabalhos cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) e [indexadores](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) estão em execução.

1. Escolha o método de integração que atenda aos seus requisitos e siga as instruções.

   * [Método 1](#method-1): Instalar sem [!DNL OpenSearch]
   * [Método 2](#method-2): Instalar com [!DNL OpenSearch] (Sem tempo de inatividade)

>[!IMPORTANT]
>
>Devido ao anúncio do fim de suporte do Elasticsearch 7 para agosto de 2023, é recomendável que todos os clientes do Adobe Commerce migrem para o mecanismo de pesquisa OpenSearch 2.x. Para obter informações sobre como migrar o mecanismo de pesquisa durante a atualização do produto, consulte [Migração para o OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) no _Guia de atualização_.

## Método 1: instalação sem OpenSearch {#method-1}

Esse método de integração é recomendado ao instalar o [!DNL Live Search] para um:

* Novo [!DNL Commerce] instalação
* Ambiente de preparo

Neste cenário, as operações de vitrine são interrompidas enquanto a [!DNL Live Search] serviço indexa todos os produtos no catálogo. Durante a instalação, [!DNL Live Search] Os módulos do estão ativados e [!DNL OpenSearch] Os módulos do estão desativados.

1. Instalar o Adobe Commerce 2.4.4+ sem [!DNL Live Search].

1. Para baixar o `live-search` execute o seguinte a partir da linha de comando:

   ```bash
   composer require magento/live-search
   ```

1. Execute os seguintes comandos para desativar o [!DNL OpenSearch] e módulos relacionados, e instalar [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > Embora os dados sejam indexados e sincronizados, as operações de pesquisa e navegação de categoria não estão disponíveis na loja. Dependendo do tamanho do catálogo, o processo pode levar pelo menos uma hora a partir do momento `cron` O é executado para sincronizar os dados com o [!DNL Live Search] serviços.

1. Verifique se o seguinte [indexadores](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) são definidos como &quot;Atualizar por programação&quot;:

   * Feed do produto
   * Feed de variante de produto
   * Feed de atributos do catálogo
   * Feed de preços do produto
   * Feed de dados do site de escopos
   * Feed de dados dos grupos de clientes dos escopos
   * Feed de categorias
   * Feed de permissões de categoria

1. Configurar o [Chaves de API](#configure-api-keys) e verifique se os dados do catálogo estão [sincronizado](#synchronize-catalog-data) com [!DNL Live Search] serviços.

1. Para disponibilizar facetas como filtros na loja, adicione o [facetas](facets-add.md) você precisa, de acordo com a [requisitos de facetagem](facets.md).

   Você poderá adicionar facetas depois de `cron` O executa os feeds de atributo e exporta metadados de atributo.

1. Execute o seguinte comando nesta ordem:

   ```bash
   bin/magento saas:resync --feed productattributes
   bin/magento saas:resync --feed products
   bin/magento saas:resync --feed scopesCustomerGroup
   bin/magento saas:resync --feed scopesWebsite
   bin/magento saas:resync --feed prices
   bin/magento saas:resync --feed productoverrides
   bin/magento saas:resync --feed variants
   bin/magento saas:resync --feed categories
   bin/magento saas:resync --feed categoryPermissions
   ```

1. [Verificar](#verify-export) que os dados foram exportados.

1. [Teste](#test-the-connection) a conexão da loja.

## Método 2: instalar com OpenSearch {#method-2}

Esse método de integração é recomendado ao instalar o [!DNL Live Search] para:

* Uma produção existente [!DNL Commerce] instalação

Nesse cenário, [!DNL OpenSearch] gerencia temporariamente solicitações de pesquisa da loja enquanto a [!DNL Live Search] o serviço indexa todos os produtos em segundo plano, sem interrupção das operações normais da loja. [!DNL OpenSearch] está desativado e [!DNL Live Search] habilitado depois que todos os dados do catálogo são indexados e sincronizados.

1. Para baixar o `live-search` execute o seguinte a partir da linha de comando:

   ```bash
   composer require magento/live-search
   ```

1. Execute o seguinte comando para desabilitar temporariamente o [!DNL Live Search] módulos que apresentam resultados de pesquisa da loja.

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] continua a gerenciar solicitações de pesquisa da loja enquanto a [!DNL Live Search] o serviço sincroniza dados de catálogo e indexa produtos em segundo plano.

1. Verifique se o seguinte [indexadores](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) são definidos como &quot;Atualizar por programação&quot;:

   * Feed do produto
   * Feed de variante de produto
   * Feed de atributos do catálogo
   * Feed de preços do produto
   * Feed de dados do site de escopos
   * Feed de dados dos grupos de clientes dos escopos

1. Configurar o [Chaves de API](#configure-api-keys) e verifique se os dados do catálogo estão [sincronizado](#synchronize-catalog-data) com [!DNL Live Search] serviços.

1. Para disponibilizar facetas como filtros na loja, adicione o [facetas](facets-add.md) você precisa, de acordo com a [requisitos de facetagem](facets.md).

   Você poderá adicionar facetas depois de `cron` O executa o produto e os feeds de atributo e exporta os metadados de atributo para o [!DNL Live Search] serviços.

1. Execute o seguinte comando nesta ordem:

   ```bash
   bin/magento saas:resync --feed productattributes
   bin/magento saas:resync --feed products
   bin/magento saas:resync --feed scopesCustomerGroup
   bin/magento saas:resync --feed scopesWebsite
   bin/magento saas:resync --feed prices
   bin/magento saas:resync --feed productoverrides
   bin/magento saas:resync --feed variants
   bin/magento saas:resync --feed categories
   bin/magento saas:resync --feed categoryPermissions
   ```

1. Após a conclusão da sincronização, use o [Playground de GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/) com a query padrão para verificar o seguinte:

   * A contagem de produtos retornada está próxima do que você espera da exibição da loja.
   * Facetas são retornadas.

1. Execute os seguintes comandos para habilitar [!DNL Live Search] módulos, desativar [!DNL OpenSearch], e execute `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover  Magento_LiveSearchProductListing 
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

1. [Teste](#test-the-connection) a conexão da loja.

## Configurar chaves de API {#configure-api-keys}

A chave de API do Adobe Commerce e sua chave privada associada são necessárias para se conectar [!DNL Live Search] para uma instalação do Adobe Commerce. A chave de API é gerada e mantida na conta da [!DNL Commerce] titular da licença, que pode compartilhá-la com o desenvolvedor ou com a SI. Em seguida, o desenvolvedor poderá criar e gerenciar os Espaços de dados SaaS em nome do detentor da licença.  Se você já tiver um conjunto de chaves de API, não será necessário gerá-las novamente.

### Titular da licença da Adobe Commerce

Para gerar uma chave de API e uma chave privada, consulte [Conector dos Commerce Services](../landing/saas.md).

### Desenvolvedor do Adobe Commerce ou SI

O desenvolvedor ou SI configura o espaço de dados SaaS conforme descrito na seção *Commerce Services* seção da configuração. No *Admin*, os Serviços da Commerce ficam disponíveis no *Configuração* barra lateral quando um módulo SaaS está instalado.

## Sincronizar dados do catálogo {#synchronize-catalog-data}

[!DNL Live Search] O requer dados de produto sincronizados para operações de pesquisa e dados de atributo sincronizados para configurar facetas. A sincronização inicial entre o catálogo de produtos e o serviço de catálogo começa quando [!DNL Live Search] é conectado pela primeira vez. Dependendo do método de instalação e do tamanho do catálogo, pode levar até 30 minutos para que os dados sejam exportados e indexados pelo [!DNL Live Search]. A lista de dados sincronizados e compartilhados com o serviço de catálogo pode ser encontrada no schema, que é definido em:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

Use o [Painel de gerenciamento de dados](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) para monitorar o status de sincronização dos dados do produto transferidos do banco de dados do Commerce para os serviços SaaS da Commerce.

### Verificar exportação {#verify-export}

Para verificar se os dados do catálogo foram exportados da instância do Adobe Commerce e estão sincronizados para [!DNL Live Search], procure entradas nas seguintes tabelas:

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

Para obter ajuda adicional, consulte [[!DNL Live Search] catálogo não sincronizado](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) na Base de conhecimento de suporte.

### Futuras atualizações do produto

Após a sincronização inicial, pode levar até 15 minutos para que atualizações de produtos incrementais sejam disponibilizadas para pesquisa na loja. Para saber mais, acesse [Indexação - Streaming de atualizações de produto](indexing.md).

## Testar a conexão {#test-connection}

Na loja, verifique o seguinte:

* A variável [!UICONTROL Search] a caixa retorna os resultados corretamente
* A pesquisa de categoria retorna os resultados corretamente
* Facetas estão disponíveis como filtros nas páginas de resultados da pesquisa

Se tudo funcionar corretamente, parabéns! [!DNL Live Search] O está instalado, conectado e pronto para uso.

Se encontrar problemas na loja, verifique a `var/log/system.log` arquivo para falhas de comunicação da API ou erros no lado dos serviços.

Para permitir o Live Search por meio de um firewall, adicione `commerce.adobe.io` à lista de permissões.

## Verificando a versão instalada

Antes de atualizar o Live Search, execute o seguinte na linha de comando para verificar a versão do Live Search instalada:

```bash
composer show magento/module-live-search | grep version
```

## Atualizando [!DNL Live Search] {#update}

Para atualizar [!DNL Live Search], execute o seguinte a partir da linha de comando:

```bash
composer update magento/live-search --with-dependencies
```

Para atualizar para uma versão principal, como 3.1.1 para 4.0.0, edite a raiz do projeto [!DNL Composer] `.json` do seguinte modo:

1. Se o estiver instalado atualmente `magento/live-search` a versão é `3.1.1` ou abaixo, e você está atualizando para a versão `4.0.0` ou superior, execute o seguinte comando antes da atualização:

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   Para obter mais informações sobre a versão instalada no momento `magento/live-search` execute o seguinte comando:

   ```bash
   composer show magento/live-search
   ```

1. Abra a raiz `composer.json` arquivo e pesquisa `magento/live-search`.

1. No `require` , atualize o número da versão da seguinte maneira:

   ```json
   "require": {
      ...
      "magento/live-search": "^4.0",
      ...
    }
   ```

1. **Salvar** `composer.json`. Em seguida, execute o seguinte a partir da linha de comando:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## Desinstalando [!DNL Live Search] {#uninstall}

Para desinstalar o [!DNL Live Search], consulte [Desinstalar módulos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] pacotes {#packages}

| Pacote | Descrição |
|--- |--- |
| `module-live-search` | Permite que os comerciantes definam suas configurações de pesquisa para facetas, sinônimos, regras de consulta e assim por diante, e fornece acesso a um playground do GraphQL somente leitura para testar consultas do *Admin*. |
| `module-live-search-adapter` | Direciona as solicitações de pesquisa da loja para a [!DNL Live Search] e renderiza os resultados na loja. <br />- Navegação de categoria - Encaminha solicitações da loja [navegação superior](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) ao serviço de pesquisa.<br />- Pesquisa global - Encaminha solicitações do [pesquisa rápida](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) na parte superior direita da loja, à [!DNL Live Search] serviço. |
| `module-live-search-storefront-popover` | Um popover &quot;pesquisar ao digitar&quot; substitui a pesquisa rápida padrão e retorna dados e miniaturas dos principais resultados da pesquisa. |

## [!DNL Live Search] dependências {#dependencies}

As seguintes [!DNL Live Search] as dependências são capturadas pelo [!DNL Composer].

* `magento/module-saas-catalog`
* `magento/module-saas-category`
* `magento/module-saas-category-permissions`
* `magento/module-saas-product-override`
* `magento/module-saas-product-variant`
* `magento/module-saas-price`
* `magento/module-saas-scopes`
* `magento/module-bundle-product-data-exporter`
* `magento/module-catalog-inventory-data-exporter`
* `magento/module-catalog-url-rewrite-data-exporter`
* `magento/module-configurable-product-data-exporter`
* `magento/module-parent-product-data-exporter`
* `magento/module-gift-card-product-data-exporter`
* `magento/module-bundle-product-override-data-exporter`
* `data-services`
* `services-id`
