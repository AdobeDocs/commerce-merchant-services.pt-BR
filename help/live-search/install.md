---
title: "Instalar [!DNL Live Search]"
description: "Saiba como instalar, atualizar e desinstalar [!DNL Live Search] do Adobe Commerce."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
source-git-commit: a17c9ef193394d86f5439f900ebba3dd68d33b45
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Instalar [!DNL Live Search]

O Live Search é instalado como uma extensão do Adobe Marketplace. Depois que a variável [!DNL Live Search] o módulo (com módulos de catálogo como dependências) é instalado e configurado, [!DNL Commerce] O começa a compartilhar dados de pesquisa e catálogo com os serviços SaaS. Neste ponto, *Administrador* os usuários do podem configurar, personalizar e gerenciar aspectos de pesquisa, sinônimos e regras de merchandising.

Este tópico fornece instruções para fazer o seguinte:

* Instalar [!DNL Live Search] (Métodos 1 e 2)
* [Atualizar [!DNL Live Search]](#update)
* [Desinstalar [!DNL Live Search]](#uninstall)

## Antes de começar {#before-you-begin}

Faça o seguinte:

1. Confirme que [trabalhos cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) e [indexadores](https://docs.magento.com/user-guide/system/index-management.html) estão em execução.

1. Escolha o método de integração que atenda aos seus requisitos e siga as instruções.

   * [Método 1](#method-1): Instalar sem [!DNL Elasticsearch]
   * [Método 2](#method-2): Instalar com [!DNL Elasticsearch] (Sem tempo de inatividade)

## Método 1: Instalar sem Elasticsearch {#method-1}

Esse método de integração é recomendado ao instalar [!DNL Live Search] a:

* Novo [!DNL Commerce] instalação
* Ambiente de preparo

Nesse cenário, as operações de vitrine são interrompidas enquanto o [!DNL Live Search] indexa todos os produtos no catálogo. Durante a instalação, [!DNL Live Search] estão habilitados e [!DNL Elasticsearch] os módulos estão desabilitados.

>[!TIP]
>
>Para evitar erros de digitação, passe o mouse sobre a caixa do código localizada na extremidade direita, clique no botão [!UICONTROL **Copiar**] e cole na linha de comando.

1. Instalar o Adobe Commerce 2.4.x sem [!DNL Live Search].

1. Para baixar o `live-search` , execute o seguinte na linha de comando:

   ```bash
   composer require magento/live-search
   ```

   Para obter mais informações, consulte a lista de [!DNL Live Search] [dependências](#dependencies) capturados por [!DNL Composer].

1. Execute os seguintes comandos para desativar [!DNL Elasticsearch] e módulos relacionados e instalação [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch 
   Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   >[!WARNING]
   >
   > Embora os dados sejam indexados e sincronizados, as operações de pesquisa e navegação de categoria não estão disponíveis na loja. Dependendo do tamanho do catálogo, o processo pode demorar pelo menos uma hora a partir do momento `cron` O é executado para sincronizar os dados com o [!DNL Live Search] serviços.

1. Verifique se o seguinte [indexadores](https://docs.magento.com/user-guide/system/index-management.html) estão definidas como `Update by Schedule`:

   * Feed do produto
   * Feed da variante do produto
   * Feed de atributos do catálogo

1. Configure seu [Chaves da API](#configure-api-keys) e verifique se os dados do catálogo são [sincronizado](#synchronize-catalog-data) com [!DNL Live Search] serviços.

1. Para disponibilizar facetas como filtros na loja, adicione o [facetas](facets-add.md) você precisa, de acordo com a [requisitos de lapidamento](facets.md).

   Você deve poder adicionar facetas depois de `cron` executa os feeds de atributo e exporta os metadados de atributo.

1. Aguarde pelo menos uma hora depois `cron` é executado para sincronizar dados. Então, [verify](#verify-export) que os dados foram exportados.

1. [Teste](#test-the-connection) a conexão da loja.

## Método 2: Instalar com o Elasticsearch {#method-2}

Esse método de integração é recomendado ao instalar [!DNL Live Search] para:

* Uma produção existente [!DNL Commerce] instalação

Nesse cenário, [!DNL Elasticsearch] gerencia temporariamente as solicitações de pesquisa da loja enquanto a [!DNL Live Search] O serviço indexa todos os produtos em segundo plano, sem interrupção das operações normais de vitrine. [!DNL Elasticsearch] está desativado e [!DNL Live Search] habilitado depois que todos os dados do catálogo forem indexados e sincronizados.

>[!TIP]
>
>Para evitar erros de digitação, passe o mouse sobre a caixa do código localizada na extremidade direita, clique no botão [!UICONTROL **Copiar**] e cole na linha de comando.

1. Para baixar o `live-search` , execute o seguinte na linha de comando:

   ```bash
   composer require magento/live-search
   ```

   Para obter mais informações, consulte a lista de [!DNL Live Search] [dependências](#live-search-dependencies) capturados por [!DNL Composer].

1. Execute o seguinte comando para desativar temporariamente o [!DNL Live Search] módulos que atendem aos resultados de pesquisa da loja.

   ```bash
   bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento setup:upgrade
   ```

   [!DNL Elasticsearch] O continua a gerenciar solicitações de pesquisa da loja enquanto o [!DNL Live Search] O serviço sincroniza dados do catálogo e indexa produtos em segundo plano.

1. Verifique se o seguinte [indexadores](https://docs.magento.com/user-guide/system/index-management.html) estão definidas como `Update by Schedule`:

   * Feed do produto
   * Feed da variante do produto
   * Feed de atributos do catálogo

1. Configure seu [Chaves da API](#configure-api-keys) e verifique se os dados do catálogo são [sincronizado](#synchronize-catalog-data) com [!DNL Live Search] serviços.

1. Para disponibilizar facetas como filtros na loja, adicione o [facetas](facets-add.md) você precisa, de acordo com a [requisitos de lapidamento](facets.md).

   Você deve poder adicionar facetas depois de `cron` O executa os feeds de produto e atributo e exporta os metadados do atributo para [!DNL Live Search] serviços.

1. Aguarde pelo menos uma hora para que os dados sejam indexados e sincronizados. Em seguida, use o [Reprodução GraphQL](https://devdocs.magento.com/live-search/graphql-support.html) com a consulta padrão para verificar o seguinte:

   * A contagem de produtos retornados está próxima do que você espera para a exibição de loja.
   * As facetas são retornadas.

1. Execute os seguintes comandos para habilitar [!DNL Live Search] módulos, desabilitar [!DNL Elasticsearch]e executar `setup`.

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
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

A chave da API do Adobe Commerce e sua chave privada associada são necessárias para se conectar [!DNL Live Search] para uma instalação do Adobe Commerce. A chave da API é gerada e mantida na conta do [!DNL Commerce] titular da licença, que pode compartilhá-la com o desenvolvedor ou com o SI. O desenvolvedor pode então criar e gerenciar os Espaços de dados do SaaS em nome do titular da licença.  Se você já tiver um conjunto de chaves de API, não precisará gerá-las novamente.

### Titular da licença da Adobe Commerce

Para gerar uma chave de API e chave privada, consulte [Conector do Commerce Services](../landing/saas.md).

### Desenvolvedor Adobe Commerce ou SI

O desenvolvedor ou o SI configura o espaço de dados SaaS, conforme descrito na *Commerce Services* da configuração. No *Administrador*, os Commerce Services serão disponibilizados na variável *Configuração* barra lateral quando um módulo SaaS é instalado.

## Sincronizar dados do catálogo {#synchronize-catalog-data}

[!DNL Live Search] O requer dados sincronizados do produto para operações de pesquisa e dados do atributo sincronizado para configurar aspectos. A sincronização inicial entre o catálogo de produtos e o serviço de catálogo começa quando [!DNL Live Search] é conectado pela primeira vez. Dependendo do método de instalação e do tamanho do catálogo, pode levar até oito horas para que os dados sejam exportados e indexados por [!DNL Live Search]. A lista de dados sincronizados e compartilhados com o serviço de catálogo pode ser encontrada no schema , que é definido em:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### Verificar exportação {#verify-export}

Para verificar se os dados do catálogo foram exportados da sua instância do Adobe Commerce e estão sincronizados para [!DNL Live Search], procure entradas nas seguintes tabelas:

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

Para obter ajuda adicional, consulte [[!DNL Live Search] catálogo não sincronizado](https://support.magento.com/hc/en-us/articles/4405637804301-Live-search-catalog-not-synchronized) na Base de conhecimento de suporte.

### Atualizações futuras de produtos

Após a sincronização inicial, pode levar até 15 minutos para que as atualizações de produtos incrementais se tornem disponíveis para a pesquisa de vitrine. Para saber mais, acesse [Indexação - Transmissão de atualizações de produtos](indexing.md).

## Testar a conexão {#test-connection}

Na loja, verifique o seguinte:

* O [!UICONTROL Search] a caixa retorna os resultados corretamente
* O navegador de categoria retorna os resultados corretamente
* As facetas estão disponíveis como filtros nas páginas de resultados da pesquisa

Se tudo der certo, parabéns! [!DNL Live Search] está instalado, conectado e pronto para uso.

Se encontrar problemas na loja, verifique o `var/log/system.log` arquivo para falhas ou erros de comunicação da API no lado dos serviços.

## Verificar a versão instalada

Antes de atualizar o Live Search, execute o seguinte na linha de comando para verificar a versão do Live Search que está instalada no momento:

```bash
composer show magento/module-live-search | grep version
```

## Atualização [!DNL Live Search] {#update}

Para atualizar [!DNL Live Search], execute o seguinte na linha de comando:

```bash
composer update magento/live-search --with-dependencies
```

Para atualizar para uma versão principal, como de 1.0.0 a 2.0.0, edite a raiz do projeto [!DNL Composer] `.json` como segue:

1. Se estiver instalado `magento/live-search` a versão é `1.3.1` ou inferior, e você está atualizando para a versão `2.0.0` ou superior, execute o seguinte comando antes da atualização:

   ```bash
   bin/magento module:enable Magento_AdvancedSearch
   ```

   Para obter informações sobre o `magento/live-search` , execute o seguinte comando:

   ```bash
   composer show magento/live-search
   ```

1. Abra a raiz `composer.json` arquivo e pesquisa por `magento/live-search`.

1. No `require` atualize o número da versão da seguinte maneira:

   ```json
   "require": {
      ...
      "magento/live-search": "^2.0",
      ...
    }
   ```

1. **Salvar** `composer.json`. Em seguida, execute o seguinte na linha de comando:

   ```bash
   composer update magento/live-search –-with-dependencies
   ```

## Desinstalação [!DNL Live Search] {#uninstall}

Para desinstalar [!DNL Live Search], consulte [Desinstalar módulos](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).

## [!DNL Live Search] pacotes {#packages}

| Embalagem | Descrição |
|--- |--- |
| `module-live-search` | Permite que os comerciantes definam suas configurações de pesquisa para lapidamento, sinônimos, regras de consulta etc., além de fornecer acesso a um playground GraphQL somente leitura para testar consultas da *Administrador*. |
| `module-live-search-adapter` | Envia solicitações de pesquisa da loja para a [!DNL Live Search] e renderiza os resultados na loja. <br />- Navegação por categoria - Roteia solicitações da loja [navegação superior](https://docs.magento.com/user-guide/catalog/navigation-top.html) ao serviço de pesquisa.<br />- Pesquisa global - Rota solicitações do [pesquisa rápida](https://docs.magento.com/user-guide/catalog/search-quick.html) na parte superior direita da loja até a [!DNL Live Search] serviço. |
| `module-live-search-storefront-popover` | Uma oferta de &quot;pesquisa ao digitar&quot; substitui a pesquisa rápida padrão e retorna sugestões dinâmicas de produtos e miniaturas dos principais resultados de pesquisa. |

## [!DNL Live Search] dependências {#dependencies}

O seguinte [!DNL Live Search] as dependências são capturadas por [!DNL Composer]:

| Dependência | Descrição |
|--- |--- |
| Exportar módulos | Os seguintes módulos coletam e sincronizam dados do catálogo:<br />`saas-export`<br />`module-bundle-product-exporter`<br />`module-catalog-data-exporter`<br />`module-catalog-inventory-data-exporter`<br />`module-catalog-url-rewrite-data-exporter`<br />`module-configurable-product-data-exporter`<br />`module-data-exporter`<br />`module-parent-product-data-exporter` |
| `services-connector` | Necessário para configurar sua conexão com o Commerce Services. |
| `module-services-id` | Necessário para configurar sua conexão com o Commerce Services. |
