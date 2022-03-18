---
title: Instalar o Live Search
description: Saiba como instalar, atualizar e desinstalar o Live Search do Adobe Commerce.
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
source-git-commit: 19f0c987ab6b43b6fac1cad266b5fd47a7168e73
workflow-type: tm+mt
source-wordcount: '1490'
ht-degree: 0%

---

# Instalar [!DNL Live Search]

[!DNL Live Search] é um conjunto independente [pacotes](#live-search-packages) que substitui os recursos de pesquisa padrão do Magento Open Source e Adobe Commerce. O [!DNL Live Search] O módulo é instalado a partir da linha de comando do servidor e se conecta à instalação do Adobe Commerce como um [service](https://docs.magento.com/user-guide/system/saas.html). Quando o processo estiver concluído, [!DNL Live Search] aparece no *Marketing* menu em *SEO &amp; Pesquisar* no [!DNL Commerce] Administrador

O lado do Adobe Commerce inclui hospedar o Administrador de pesquisa, sincronizar dados de catálogo e executar o serviço de query.

![Diagrama de arquitetura do Live Search](assets/architecture-diagram.svg)

Depois que a variável [!DNL Live Search] o módulo (com módulos de catálogo como dependências) é instalado e configurado, [!DNL Commerce] O começa a compartilhar dados de pesquisa e catálogo com os serviços SaaS. Neste ponto, os usuários administradores podem configurar, personalizar e gerenciar aspectos de pesquisa, sinônimos e regras de comercialização.

Este tópico fornece instruções para fazer o seguinte:

* [Instalar [!DNL Live Search]](#before-you-begin) (Métodos 1 e 2)
* [Atualizar [!DNL Live Search]](#update)
* [Desinstalar [!DNL Live Search]](#uninstall)

## Requisitos {#requirements}

* [Adobe Commerce](https://magento.com/products/magento-commerce) 2.4.x
* PHP 7.3 / 7.4
* [!DNL Composer]

### Plataformas compatíveis

* Adobe Commerce no local (EE) : 2.4.x
* Adobe Commerce on Cloud (ECE) : 2.4.x

## Limites e limites

No momento, a API da categoria de pesquisa/categoria do Live Search tem os seguintes limites compatíveis e limites estáticos:

### Indexação

* Índices até 300 atributos de produto por visualização de loja
* Indexa somente produtos do banco de dados do Adobe Commerce
* Não indexa páginas CMS

### Funcionalidade

* Loja [Pesquisa avançada (formulário)](https://docs.magento.com/user-guide/catalog/search-advanced.html) módulo
* [Grupos de clientes](https://docs.magento.com/user-guide/customers/customer-groups.html)
* [Grupos de preços personalizados](https://docs.magento.com/user-guide/catalog/product-price-group.html)
* Várias localizações de inventário, conforme usado por [MCOM](https://docs.magento.com/user-guide/mcom.html) ou outras extensões OMS
* [Recursos B2B integrados](https://business.adobe.com/products/magento/b2b-ecommerce.html)

### Queries

* O Live Search não tem acesso à taxonomia completa da árvore de categorias, o que faz com que alguns cenários de pesquisa de navegação em camadas estejam além de seu alcance.
* O Live Search usa um endpoint GraphQL exclusivo para consultas para oferecer suporte a recursos como lapidamento inteligente e pesquisa por tipo. Embora semelhantes ao [API Magento GraphQL](https://devdocs.magento.com/guides/v2.4/graphql), há algumas diferenças e alguns campos podem não ser totalmente compatíveis no momento.

### Progressive Web Application (PWA)

* O Live Search não é compatível [PWA](https://developer.adobe.com/commerce/pwa-studio/) neste momento.

## Antes de começar {#before-you-begin}

Faça o seguinte:

1. Confirme que [trabalhos cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) e [indexadores](https://docs.magento.com/user-guide/system/index-management.html) estão em execução.

1. Escolha o método de integração que atenda aos seus requisitos e siga as instruções.

   * [Método 1](#method-1): Instalar sem [!DNL Elasticsearch]
   * [Método 2](#method-2): Instalar com [!DNL Elasticsearch] (Sem tempo de inatividade)

   >[!TIP]
   >
   >Para inserir instruções na linha de comando, passe o mouse sobre a extremidade direita da caixa de código e clique no botão [!UICONTROL **Copiar**] link . Em seguida, cole-o na linha de comando. Se você não tiver experiência em trabalhar na linha de comando, peça ajuda ao integrador de sistema ou desenvolvedor.

## Método 1: Instalar sem Elasticsearch {#method-1}

Esse método de integração é recomendado ao instalar [!DNL Live Search] a:

* Novo [!DNL Commerce] instalação
* Ambiente de preparo

Nesse cenário, as operações de vitrine são interrompidas enquanto o [!DNL Live Search] indexa todos os produtos no catálogo. Durante a instalação, [!DNL Live Search] estão habilitados e [!DNL Elasticsearch] os módulos estão desabilitados.

1. Instalar o Adobe Commerce 2.4.x sem [!DNL Live Search].

1. Para baixar o `live-search` , execute o seguinte na linha de comando:

   ```bash
   composer require magento/DNL live-search
   ```

   Para obter mais informações, consulte a lista de [!DNL Live Search] [dependências](#dependencies) capturados por [!DNL Composer].

1. Execute os seguintes comandos para desativar [!DNL Elasticsearch] e módulos relacionados e instalação [!DNL Live Search]:

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_AdvancedSearch  Magento_InventoryElasticsearch
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

1. Configure seu [Chaves da API](#configure-api-keys) para [sincronizar](#synchronize-catalog-data) seus dados de catálogo para [!DNL Live Search] serviços.

1. Para disponibilizar facetas como filtros na loja, adicione o [facetas](https://docs.magento.com/user-guide/live-search/facets-add.html) você precisa, de acordo com a [requisitos de lapidamento](https://docs.magento.com/user-guide/live-search/facets.html).

   Você deve poder adicionar facetas depois de `cron` executa os feeds de atributo e exporta os metadados de atributo.

1. Aguarde pelo menos uma hora depois `cron` é executado para sincronizar dados. Então, [verify](#verify-export) que os dados foram exportados.

1. [Teste](#test-the-connection) a conexão da loja.

## Método 2: Instalar com o Elasticsearch {#method-2}

Esse método de integração é recomendado ao instalar [!DNL Live Search] para:

* Uma produção existente [!DNL Commerce] instalação

Nesse cenário, [!DNL Elasticsearch] gerencia temporariamente as solicitações de pesquisa da loja enquanto a [!DNL Live Search] O serviço indexa todos os produtos em segundo plano, sem interrupção das operações normais de vitrine. [!DNL Elasticsearch] está desativado e [!DNL Live Search] habilitado depois que todos os dados do catálogo forem indexados e sincronizados.

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

1. Configure seu [Chaves da API](#configure-api-keys) para [sincronizar](#synchronize-catalog-data) seus dados de catálogo para [!DNL Live Search] serviços.

1. Para disponibilizar facetas como filtros na loja, adicione o [facetas](https://docs.magento.com/user-guide/live-search/facets-add.html) você precisa, de acordo com a [requisitos de lapidamento](https://docs.magento.com/user-guide/live-search/facets.html).

   Você deve poder adicionar facetas depois de `cron` O executa os feeds de produto e atributo e exporta os metadados do atributo para [!DNL Live Search] serviços.

1. Aguarde pelo menos uma hora para que os dados sejam indexados e sincronizados. Em seguida, use o [Reprodução GraphQL](https://devdocs.magento.com/live-search/graphql-support.html) com a consulta padrão para verificar o seguinte:

   * A contagem de produtos retornada está próxima do que você espera para a exibição de loja
   * As facetas são retornadas

1. Execute os seguintes comandos para desativar [!DNL Elasticsearch] módulos, habilitar [!DNL Live Search] módulos e executar `setup`:

   ```bash
   bin/magento module:enable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover
   ```

   ```bash
   bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch6 Magento_Elasticsearch7 Magento_ElasticsearchCatalogPermissions Magento_AdvancedSearch Magento_InventoryElasticsearch
   ```

   ```bash
   bin/magento setup:upgrade
   ```

1. [Teste](#test-the-connection) a conexão da loja.

## Configurar chaves de API {#configure-api-keys}

A chave da API do Adobe Commerce e sua chave privada associada são necessárias para se conectar [!DNL Live Search] para uma instalação do Adobe Commerce. A chave da API é gerada e mantida na conta do [!DNL Commerce] titular da licença, que pode compartilhá-la com o desenvolvedor ou com o SI. O desenvolvedor pode então criar e gerenciar os Espaços de dados do SaaS em nome do titular da licença.

### Titular da licença da Adobe Commerce

Para gerar uma chave de API e chave privada, consulte [Conector do Commerce Services](https://docs.magento.com/user-guide/system/saas.html).

### Desenvolvedor Adobe Commerce ou SI

O desenvolvedor ou o SI configura o Espaço de dados SaaS conforme descrito na seção Serviços do Commerce da configuração. Os Commerce Services ficam disponíveis na barra lateral de configuração de administração quando um módulo SaaS é instalado.

## Sincronizar dados do catálogo {#synchronize-catalog-data}

[!DNL Live Search] O requer dados sincronizados do produto para operações de pesquisa e dados do atributo sincronizado para configurar aspectos. A sincronização inicial entre o catálogo de produtos e o serviço de catálogo começa quando [!DNL Live Search] é conectado pela primeira vez. Dependendo do método de instalação e do tamanho do catálogo, pode levar até oito horas para que os dados sejam exportados e indexados por [!DNL Live Search]. A lista de dados sincronizados e compartilhados com o serviço de catálogo pode ser encontrada no schema , que é definido em:

`vendor/magento/module-catalog-data-exporter/etc/et_schema.xml`

### Verificar exportação {#verify-export}

Para verificar se os dados do catálogo foram exportados da sua instância do Adobe Commerce e estão sincronizados para [!DNL Live Search], procure entradas nas seguintes tabelas:

* `catalog_data_exporter_products`
* `catalog_data_exporter_product_attributes`

Para obter ajuda adicional, consulte [[!DNL Live Search] catálogo não sincronizado](https://support.magento.com/hc/en-us/articles/4405637804301-Live-search-catalog-not-synchronized) na Base de conhecimento de suporte.

### Atualizações futuras de produtos

Após a sincronização inicial, pode levar até quinze minutos para que as atualizações de produtos incrementais se tornem disponíveis para a pesquisa de vitrine. Para saber mais, acesse [Atualizações de produto de streaming](https://devdocs.magento.com/live-search/indexing.html).

## Testar a conexão {#test-connection}

Na loja, verifique o seguinte:

* O [!UICONTROL Search] a caixa retorna os resultados corretamente
* O navegador de categoria retorna os resultados corretamente
* As facetas estão disponíveis como filtros nas páginas de resultados da pesquisa

Se tudo der certo, parabéns! [!DNL Live Search] está instalado, conectado e pronto para uso.

Se encontrar problemas na loja, verifique o `var/log/system.log` arquivo para falhas ou erros de comunicação da API no lado dos serviços.

## Atualização [!DNL Live Search] {#update}

Para atualizar [!DNL Live Search], execute o seguinte na linha de comando:

```bash
composer update magento/live-search --with-dependencies
```

Para atualizar para uma versão principal, como de 1.0 a 2.0, edite a raiz do projeto [!DNL Composer] `.json` como segue:

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
| `module-live-search` | Permite que os comerciantes definam suas configurações de pesquisa para lapidamento, sinônimos, regras de consulta etc., além de fornecer acesso a um playground GraphQL somente leitura para testar consultas do Administrador. |
| `module-live-search-adapter` | Envia solicitações de pesquisa da loja para a [!DNL Live Search] e renderiza os resultados na loja. <br />- Navegação por categoria - Roteia solicitações da loja [navegação superior](https://docs.magento.com/user-guide/catalog/navigation-top.html) ao serviço de pesquisa.<br />- Pesquisa global - Rota solicitações do [pesquisa rápida](https://docs.magento.com/user-guide/catalog/search-quick.html) na parte superior direita da loja até a [!DNL Live Search] serviço. |
| `module-live-search-storefront-popover` | Uma oferta de &quot;pesquisa ao digitar&quot; substitui a pesquisa rápida padrão e retorna sugestões dinâmicas de produtos e miniaturas dos principais resultados de pesquisa. |

## [!DNL Live Search] dependências {#dependencies}

O seguinte [!DNL Live Search] as dependências são capturadas por [!DNL Composer]:

| Dependência | Descrição |
|--- |--- |
| Exportar módulos | Os seguintes módulos coletam e sincronizam dados do catálogo:<br />`saas-export`<br />`module-bundle-product-exporter`<br />`module-catalog-data-exporter`<br />`module-catalog-inventory-data-exporter`<br />`module-catalog-url-rewrite-data-exporter`<br />`module-configurable-product-data-exporter`<br />`module-data-exporter`<br />`module-parent-product-data-exporter` |
| `services-connector` | Necessário para configurar sua conexão com o Commerce Services. |
| `module-services-id` | Necessário para configurar sua conexão com o Commerce Services. |
