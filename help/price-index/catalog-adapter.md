---
title: Extensão do Adaptador de Catálogo
description: Utilização do Adaptador de catálogo para renderizar preços dos Serviços Commerce
seo-title: Catalog Adapter Extension
seo-description: Using Catalog Adapter to render prices from Commerce Services
exl-id: 2c9120eb-aa51-48e9-b6a4-fffe25fc31f2
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 0%

---

# Adaptador do catálogo

A variável `[!DNL Catalog Adapter]` A extensão desativa o indexador de preço de produto padrão incluído no aplicativo do Commerce e usa os preços fornecidos pelo [Serviço de catálogo](../catalog-service/overview.md) em vez disso.

O adaptador foi projetado para funcionar com [Exportação de dados SaaS](../data-export/overview.md) e o Serviço Adobe Commerce. A exportação de dados SaaS é responsável pela apresentação dos [!DNL Catalog Adapter] recupera todos os preços do Adobe Commerce Service.

Quando você habilita o [!DNL Catalog Adapter], a indexação de preços e as operações são afetadas das seguintes formas:

- O indexador de preços incluído no aplicativo Adobe Commerce está desativado.
- Os preços são gerenciados usando a exportação de dados SaaS e o [Indexador de preços SaaS](price-indexing.md).
- Quando um cliente abre um produto, categoria ou outra página que mostra os preços do produto, os preços são recuperados do Serviço da Adobe Commerce.
- Os preços são enviados para o Adobe Commerce Service sincronizando os dados do [Exportação de dados SaaS](../data-export/overview.md).
- O check-out recalcula os preços dinamicamente.

Você pode reativar a indexação de preços no aplicativo do Commerce removendo ou desabilitando a extensão Adaptador de Catálogo.

## Requisitos

- Adobe Commerce 2.4.4+
- Tenha um dos seguintes serviços da Commerce instalado:

   - [Live Search](../live-search/install.md)
   - [Recommendations do produto](../product-recommendations/install-configure.md)
   - [Serviço de catálogo](../catalog-service/installation.md)

## Instalação

A extensão Adaptador do catálogo é um metapackage do Composer que instala os seguintes módulos:

- **Desativador do Indexador de Preços**-Este módulo desativa o índice de preços no aplicativo Commerce para que os preços sejam fornecidos por meio do índice de preços SaaS. O indexador de preços do produto no aplicativo Commerce não pode ser ativado quando a extensão de indexação de preços SaaS estiver instalada.
- **Provedor de preços**-Este módulo fornece os preços dos produtos do Serviço Adobe Commerce. Ele forma o query de pesquisa e obtém os preços dos produtos no front-end.
- **Adaptador de Pesquisa do Serviço de Catálogo**-Este módulo transfere preços do aplicativo Adobe Commerce para um serviço Adobe Commerce em resposta a uma solicitação de pesquisa de produto.

## Etapas de instalação

>[!BEGINTABS]

>[!TAB Infraestrutura em nuvem]

Use este método para instalar o [!DNL Catalog Adapter] para uma instância Commerce Cloud.

1. Na estação de trabalho local, altere para o diretório do projeto do Adobe Commerce na infraestrutura em nuvem.

   >[!NOTE]
   >
   >Para obter informações sobre como gerenciar os ambientes de projeto do Commerce localmente, consulte [Gerenciamento de ramificações com a CLI](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) no _Guia do usuário do Adobe Commerce na infraestrutura em nuvem_.

1. Confira a ramificação do ambiente para atualizar usando a CLI do Adobe Commerce Cloud.

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. Adicione o módulo Adaptador do Catálogo.

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. Atualizar dependências de pacote.

   ```bash
   composer update "magento/catalog-adapter"
   ```

1. Confirmar e enviar alterações de código para a `composer.json` e `composer.lock` arquivos.

1. Adicionar, confirmar e enviar as alterações de código para o `composer.json` e `composer.lock` para o ambiente de nuvem.

   ```shell
   git add -A
   git commit -m "Add catalog adapter module"
   git push origin <branch-name>
   ```

   Enviar as atualizações para o ambiente de nuvem inicia o [Processo de implantação da nuvem do Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) para aplicar as alterações. Verifique o status da implantação no [implantar log](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB No local]

Use este método para instalar o [!DNL Catalog Adapter] para uma instância local.

1. Adicione o Adaptador de catálogo ao seu projeto usando o Composer:

   ```bash
   composer require magento/catalog-adapter --no-update
   ```

1. Atualize as dependências e instale a extensão:

   ```bash
   composer update  "magento/catalog-adapter"
   ```

1. Atualizar o Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >Em alguns casos, especialmente ao implantar na produção, você pode evitar a limpeza do código compilado, pois pode levar algum tempo. Certifique-se de fazer backup do sistema antes de fazer qualquer alteração.

>[!ENDTABS]


## Reativar o indexador de preço do produto Adobe Commerce

Se você tiver aplicativos de terceiros que dependem do indexador de preço de produto padrão do Adobe Commerce, será possível reativá-lo com os seguintes comandos:

```bash
# re-enable Product Price indexer
bin/magento module:disable Magento_PriceIndexerDisabler
# re-index Product Price indexer
bin/magento index:reindex catalog_product_price
```

## Desabilitar indexador de preços de produto para o cenário de frente de loja headless

Se você tiver uma instância do Commerce headless, talvez seja necessário desativar a indexação de preço do produto do Adobe Commerce para reduzir a carga na instância do Adobe Commerce. Você pode concluir essa tarefa instalando o `magento/module-price-indexer-disabler` módulo:

```bash
composer require magento/module-price-indexer-disabler
```

## Cenários de uso

A seguir estão alguns comuns `[!DNL Catalog Adapter]` cenários.

### Nenhuma dependência no indexador de preço de produto do Adobe Commerce

- Você é um comerciante do Luma ou do Adobe Commerce Core GraphQL que tem um serviço necessário instalado (Live Search, Product Recommendations, Catalog Service)
- Nenhuma integração com extensões de terceiros que dependem do indexador de preço do produto da Adobe Commerce

1. Instale o [!DNL Catalog Adapter].

### Com dependências no indexador de preço de produto do Adobe Commerce

- Você é um comerciante do Luma ou do Adobe Commerce Core GraphQL que tem um serviço compatível instalado (Live Search, Product Recommendations, Catalog Service)
- Use uma extensão de terceiros que depende do indexador de preço do produto do Adobe Commerce

1. Instale o [!DNL Catalog Adapter].
1. Reative a indexação padrão de preço do produto Adobe Commerce.

### Instâncias headless do Commerce

- Um comerciante com uma instância do Commerce headless com os serviços necessários instalados (Live Search, Recommendations de produtos, Serviço de catálogo)
- Nenhuma dependência do indexador de preço de produto padrão do Adobe Commerce

1. Instale o `magento/module-price-indexer-disabler` módulo do [!DNL Catalog Adapter] pacote.

