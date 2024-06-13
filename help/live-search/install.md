---
title: "Introdução ao [!DNL Live Search]"
description: "Conheça os requisitos de sistema e as etapas de instalação para [!DNL Live Search] da Adobe Commerce."
exl-id: aa251bb0-d52c-4cff-bccb-76a08ae2a3b2
role: Admin, Developer
source-git-commit: 099a4b9ce3ab71bc3c7ae181be242863a55d0ca9
workflow-type: tm+mt
source-wordcount: '2266'
ht-degree: 0%

---

# Configurar para ser bem-sucedido com [!DNL Live Search]

Adobe Commerce [!DNL Live Search] e [[!DNL Catalog Service]](../catalog-service/guide-overview.md) trabalhe em conjunto para fornecer uma solução de pesquisa intuitiva, relevante e eficiente, permitindo que seus clientes encontrem exatamente o que precisam com rapidez. Especificamente, [!DNL Catalog Service] exibe seus dados de catálogo para serviços SaaS, como [!DNL Live Search] para usar.

Este artigo fornece instruções passo a passo para implementar o [!DNL Live Search] com [!DNL Catalog Service].

>[!IMPORTANT]
>
>Quando se trata de pesquisa no site, o Adobe Commerce oferece opções. Certifique-se de ler [Limites e limites](boundaries-limits.md) antes da implementação, assegurar [!DNL Live Search] O é adequado às necessidades da sua empresa.

## Público-alvo

Este artigo destina-se ao desenvolvedor ou ao integrador de sistemas de sua equipe responsável pela instalação e configuração da instância do Adobe Commerce.

## Requisitos

- [Adobe Commerce](https://business.adobe.com/products/magento/magento-commerce.html) 2.4.4+
- PHP 8.1 / 8.2 / 8.3
- [!DNL Composer]

## Plataformas compatíveis

- Adobe Commerce na nuvem (ECE): 2.4.4+
- Adobe Commerce no local (EE) : 2.4.4+

## Visão geral do fluxo de trabalho

Em um alto nível, a integração [!DNL Live Search] exige que você:

![Fluxo de trabalho do Live Search](assets/livesearch-workflow.png)

## 1. Instale o [!DNL Live Search] extensão

[!DNL Live Search] O é instalado como uma extensão do [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html) até [Compositor](https://getcomposer.org/). Depois de instalar e configurar [!DNL Live Search], ADOBE [!DNL Commerce] O começa a compartilhar dados de pesquisa e catálogo com serviços SaaS. Neste ponto, *Admin* os usuários podem configurar, personalizar e gerenciar aspectos de pesquisa, sinônimos e regras de merchandising.

>[!NOTE]
>
>Em [!DNL Live Search] 3.0.2, o [!DNL Catalog Service] a extensão é fornecida com o [!DNL Live Search] instalação.

1. Confirme que [trabalhos cron](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs) e [indexadores](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) estão em execução.

   >[!IMPORTANT]
   >
   >Devido ao anúncio do fim de suporte do Elasticsearch 7 para agosto de 2023, é recomendável que todos os clientes do Adobe Commerce migrem para o mecanismo de pesquisa OpenSearch 2.x. Para obter informações sobre como migrar o mecanismo de pesquisa durante uma atualização de produto, consulte [Migração para o OpenSearch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/prepare/opensearch-migration) no _Guia de atualização_.

1. Baixe o `live-search` pacote do [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html).

1. Execute o seguinte a partir da linha de comando:

   ```bash
   composer require magento/live-search
   ```

   Se você estiver adicionando a variável [!DNL Live Search] extensão para um **novo** Instalação do Adobe Commerce, execute o seguinte para desativar [!DNL OpenSearch] e módulos relacionados, e instalar [!DNL Live Search]. Em seguida, siga para a etapa 4.

   ```bash
      bin/magento module:disable Magento_Elasticsearch Magento_Elasticsearch7 Magento_OpenSearch Magento_ElasticsearchCatalogPermissions Magento_InventoryElasticsearch Magento_ElasticsearchCatalogPermissionsGraphQl
   ```

   Se você estiver adicionando a variável [!DNL Live Search] extensão para um **existente** Instalação do Adobe Commerce, execute o seguinte para desativar temporariamente o [!DNL Live Search] módulos que apresentam resultados de pesquisa da loja. Em seguida, siga para a etapa 4:

   ```bash
      bin/magento module:disable Magento_LiveSearchAdapter Magento_LiveSearchStorefrontPopover Magento_LiveSearchProductListing 
   ```

   [!DNL Elasticsearch] continua a gerenciar solicitações de pesquisa da loja enquanto a [!DNL Live Search] o serviço sincroniza dados de catálogo e indexa produtos em segundo plano.

1. Execute o seguinte:

   ```bash
   bin/magento setup:upgrade
   ```

1. Verifique se o seguinte [indexadores](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) são definidos como &quot;Atualizar por programação&quot;:

   - Feed do produto
   - Feed de variante de produto
   - Feed de atributos do catálogo
   - Feed de preços do produto
   - Feed de dados do site de escopos
   - Feed de dados dos grupos de clientes dos escopos
   - Feed de categorias
   - Feed de permissões de categoria

1. Se estiver instalando o [!DNL Live Search] em uma nova instância do Commerce, você está pronto e pode pular para a [2. Configurar chaves de API](#2-configure-api-keys) seção. Se estiver instalando o Live Search em uma instância existente do Commerce, continue para a próxima etapa.

1. Execute os seguintes comandos para habilitar o [!DNL Live Search] extensão, desativar [!DNL OpenSearch], e execute `setup`.

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

## 2. Configurar chaves de API

A chave de API do Adobe Commerce e sua chave privada associada são necessárias para se conectar [!DNL Live Search] para uma instalação do Adobe Commerce. A chave de API é gerada e mantida na conta da [!DNL Commerce] o titular da licença, que pode compartilhá-la com o desenvolvedor ou com o integrador de sistemas. Em seguida, o desenvolvedor poderá criar e gerenciar os Espaços de dados SaaS em nome do detentor da licença. Se você já tiver um conjunto de chaves de API, não será necessário gerá-las novamente.

Saiba como configurar as chaves de API no [Conector dos Commerce Services](../landing/saas.md) artigo.

## 3. Sincronizar os dados do catálogo {#synchronize-catalog-data}

[!DNL Live Search] O move dados do catálogo para a infraestrutura SaaS do Adobe. Os dados são indexados e os resultados da pesquisa são enviados desse índice diretamente para a loja. Dependendo do tamanho e da complexidade, a indexação pode levar de 30 minutos a algumas horas.

Para iniciar a sincronização inicial dos dados do catálogo com os serviços SaaS, execute os seguintes comandos nesta ordem:

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

Quando você executa esses comandos, a sincronização inicial dos dados do catálogo com os serviços SaaS é iniciada.

>[!WARNING]
>
> Embora os dados sejam indexados e sincronizados, as operações de pesquisa e navegação de categoria não estão disponíveis na loja. Dependendo do tamanho do catálogo, o processo pode levar pelo menos uma hora a partir do momento `cron` O é executado para sincronizar os dados com os serviços SaaS.

### Monitorar progresso da sincronização

É possível exibir os dados sincronizados e compartilhados usando o [Painel de gerenciamento de dados](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Esse painel fornece informações valiosas sobre a disponibilidade de dados de produtos para sua loja, garantindo que eles possam ser exibidos imediatamente para seus compradores.

![Painel de gerenciamento de dados](assets/data-management-dashboard.png)

#### Futuras atualizações do produto

Após a sincronização inicial, pode levar até 15 minutos para que atualizações de produtos incrementais sejam disponibilizadas para pesquisa na loja. Para saber mais, consulte [Indexação - Streaming de atualizações de produto](indexing.md).

## 4. Verifique se os dados foram exportados {#verify-export}

Para verificar se os dados do catálogo foram exportados da instância do Adobe Commerce e estão sincronizados para [!DNL Live Search], você tem algumas opções:

- Procure entradas nas seguintes tabelas:

   - `catalog_data_exporter_products`
   - `catalog_data_exporter_product_attributes`

- Use o [Playground de GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/) com a query padrão para verificar o seguinte:

   - A contagem de produtos retornada está próxima do que você espera da exibição da loja.
   - Os aspectos são retornados.

Para obter ajuda adicional, consulte [[!DNL Live Search] catálogo não sincronizado](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/live-search-catalog-data-sync) na Base de conhecimento de suporte.

## 5. Configurar os dados

A configuração correta dos dados do produto garante bons resultados de pesquisa para os clientes. Nesta seção, você ativa os widgets da lista de produtos e atribui categorias.

### Ativar widgets de listagem de produtos

Quando você instala [!DNL Live Search] 4.0.0+, os Dispositivos de listagem de produtos são ativados por padrão. Quando os widgets são ativados, um componente de interface do usuário diferente é usado para a página de resultados da pesquisa e para a navegação de categorias na Página de listagem de produtos. Esse componente da interface do usuário faz chamadas diretas para o [API do serviço de catálogo](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/), o que resulta em tempos de resposta mais rápidos.

Se você tiver uma [!DNL Live Search] versão anterior à 4.0.0+, é necessário ativar manualmente o Widget de listagem de produtos.

1. No *Admin*, vá para **[!UICONTROL Stores]** > _[!UICONTROL Settings]_>**[!UICONTROL Configuration]**.
1. Em **[!UICONTROL Live Search]**, selecione **[!UICONTROL Storefront Features]**.
1. Definir **[!UICONTROL Enable Product Listing Widgets]** para `Yes`.

   ![Ativar widgets de listagem de produtos](assets/ls-admin-enable-widget.png)

Ao alterar essa configuração, a mensagem `Page cache is invalidated` é exibida. É necessário liberar o cache de Magento para salvar a alteração.

1. Acesse o [Gerenciamento de cache](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management) ao executar uma das ações a seguir:

   - Clique em **[!UICONTROL Cache Management]** na mensagem acima do espaço de trabalho.
   - No _Admin_ barra lateral, vá para **[!UICONTROL System]** > _[!UICONTROL Tools]_>**[!UICONTROL Cache Management]**.

1. Selecione o **Configuração** [!UICONTROL Cache Type] e clique em **[!UICONTROL Flush Magento Cache]**.

   As alterações na loja são imediatas depois de liberar o cache.

### Atribuir categorias

Produtos devolvidos em [!DNL Live Search] deve ser atribuído a um [categoria](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/categories/categories). Na Luma, por exemplo, os produtos são colocados em categorias como &quot;Homens&quot;, &quot;Mulheres&quot; e &quot;Engrenagens&quot;. As subcategorias também são configuradas para &quot;Topos&quot;, &quot;Partes inferiores&quot; e &quot;Inspeções&quot;. Isso permite uma melhor granularidade ao filtrar.

## 6. Testar a conexão {#test-connection}

Com seus dados de catálogo agora em SaaS, teste para garantir que os dados do produto sejam retornados nas seguintes situações:

- A variável [!UICONTROL Search] a caixa retorna os resultados corretamente
- A pesquisa de categoria retorna os resultados corretamente
- Os aspectos estão disponíveis como filtros nas páginas de resultados da pesquisa

Se tudo funcionar corretamente, [!DNL Live Search] O está instalado, conectado e pronto para uso.

Se encontrar problemas na loja, verifique a `var/log/system.log` arquivo para falhas de comunicação da API ou erros no lado dos serviços.

Para permitir [!DNL Live Search] por meio de um firewall, adicione `commerce.adobe.io` para o incluo na lista de permissões ➡.

## 7. Personalizar para sua loja

Você instalou o [!DNL Live Search] extensão, sincronizado, validado e configurado seus dados. Agora, você deverá garantir que o [!DNL Live Search] os widgets estão em conformidade com a aparência da sua loja.

Você pode estilizar os widgets popover e PLP definindo regras CSS personalizadas, conforme necessário. Consulte [Elementos Popover de estilo](storefront-popover-styling.md) e [Widget da página de listagem de produtos](plp-styling.md).

Se você quiser estender a funcionalidade dos widgets, o código-fonte de cada um deles estará disponível em um repositório público.
Nesse cenário, você pode personalizar o JavaScript de acordo com suas necessidades e, em seguida, hospedar seu código personalizado no CDN. Este script personalizado se comunica com a variável [!DNL Live Search] e retorna os resultados normalmente, permitindo que você controle a funcionalidade do widget.

- [repositório de widgets PLP](https://github.com/adobe/storefront-product-listing-page)
- [Pesquisar repositório de barras](https://github.com/adobe/storefront-search-as-you-type)

## Atualizando [!DNL Live Search] {#update}

Antes de atualizar o Live Search, execute o seguinte na linha de comando para verificar a versão do Live Search instalada:

```bash
composer show magento/module-live-search | grep version
```

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

1. Salvar `composer.json`. Em seguida, execute o seguinte a partir da linha de comando:

   ```bash
   composer update magento/live-search --with-dependencies
   ```

## Desinstalando [!DNL Live Search] {#uninstall}

Para desinstalar o [!DNL Live Search], consulte [Desinstalar módulos](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/tutorials/uninstall-modules).

## [!DNL Live Search] pacotes {#packages}

A variável [!DNL Live Search] A extensão do consiste nos seguintes pacotes:

| Pacote | Descrição |
|--- |--- |
| `module-live-search` | Permite que os comerciantes definam suas configurações de pesquisa para facetas, sinônimos, regras de consulta e assim por diante, e fornece acesso a um playground do GraphQL somente leitura para testar consultas do *Admin*. |
| `module-live-search-adapter` | Direciona as solicitações de pesquisa da loja para a [!DNL Live Search] e renderiza os resultados na loja. <br />- Navegação de categoria - Encaminha solicitações da loja [navegação superior](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/navigation/navigation-top) ao serviço de pesquisa.<br />- Pesquisa global - Encaminha solicitações do [pesquisa rápida](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) na parte superior direita da loja, à [!DNL Live Search] serviço. |
| `module-live-search-storefront-popover` | Um popover &quot;pesquisar ao digitar&quot; substitui a pesquisa rápida padrão e retorna dados e miniaturas dos principais resultados da pesquisa. |

## [!DNL Live Search] dependências {#dependencies}

As seguintes [!DNL Live Search] as dependências são capturadas pelo [!DNL Composer].

- `magento/module-saas-catalog`
- `magento/module-saas-category`
- `magento/module-saas-category-permissions`
- `magento/module-saas-product-override`
- `magento/module-saas-product-variant`
- `magento/module-saas-price`
- `magento/module-saas-scopes`
- `magento/module-bundle-product-data-exporter`
- `magento/module-catalog-inventory-data-exporter`
- `magento/module-catalog-url-rewrite-data-exporter`
- `magento/module-configurable-product-data-exporter`
- `magento/module-parent-product-data-exporter`
- `magento/module-gift-card-product-data-exporter`
- `magento/module-bundle-product-override-data-exporter`
- `data-services`
- `services-id`

## Conceitos avançados

As seções a seguir fornecem tópicos mais avançados ao usar o [!DNL Live Search] e [!DNL Catalog Service].

### Endpoint

[!DNL Live Search] se comunica por meio do endpoint em `https://catalog-service.adobe.io/graphql`.

Como [!DNL Live Search] não tem acesso à base de dados completa do produto, [!DNL Live Search] O GraphQL e o Commerce Core GraphQL não terão paridade completa.

É recomendável chamar as APIs SaaS diretamente, especificamente o endpoint do Serviço de catálogo.

- Obter desempenho e reduzir a carga do processador, ignorando o processo de banco de dados/Graphql do Commerce
- Aproveite o [!DNL Catalog Service] federação a ser chamada [!DNL Live Search], [!DNL Catalog Service], e [!DNL Product Recommendations] de um único endpoint.

Para alguns casos de uso, talvez seja melhor chamar [!DNL Catalog Service] para obter detalhes sobre o produto e casos semelhantes. Consulte [refineProduct](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) para obter mais informações.

Se você tiver uma implementação personalizada do headless, verifique a [!DNL Live Search] implementações de referência:

- [Widget do PLP](https://github.com/adobe/storefront-product-listing-page)
- [Campo do Live Search](https://github.com/adobe/storefront-search-as-you-type)

Se você não usar os componentes padrão, como o Adaptador de pesquisa ou widgets do Luma, ou AEM CIF Widgets, o evento (dados de sequência de cliques que alimentam o Adobe Sensei para Merchandising inteligente e métricas de desempenho) não funcionará imediatamente e exigirá desenvolvimento personalizado para implementar eventos headless.

A versão mais recente de [!DNL Live Search] já usa [!DNL Catalog Service].

### Suporte de idioma

[!DNL Live Search] os widgets suportam os seguintes idiomas:

|  |  |  |  |
|--- |--- |--- |--- |
| Idioma | Região | Código do idioma | Localidade do Magento |
| Búlgaro | Bulgária | bg_BG | bg_BG |
| Catalão | Espanha | ca_ES | ca_ES |
| Tcheco | República Checa | cs_CZ | cs_CZ |
| Dinamarquês | Dinamarca | da_DK | da_DK |
| Alemão | Alemanha | de_DE | de_DE |
| Grego | Grécia | el_GR | el_GR |
| Inglês | Reino Unido | en_GB | en_GB |
| Inglês | Estados Unidos | pt_BR | pt_BR |
| Espanhol | Espanha | es_ES | es_ES |
| Estoniano | Estônia | et_EE | et_EE |
| Basco | Espanha | eu_ES | eu_ES |
| Persa | Irã | fa_IR | fa_IR |
| Finlandês | Finlândia | fi_FI | fi_FI |
| Francês | França | fr_FR | fr_FR |
| Galego | Espanha | gl_ES | gl_ES |
| Hindi | Índia | hi_IN | hi_IN |
| Húngaro | Hungria | hu_HU | hu_HU |
| Indonésio | Indonésia | id_ID | id_ID |
| Italiano | Itália | it_IT | it_IT |
| Coreano | Coreia do Sul | ko_KR | ko_KR |
| Lituano | Lituânia | lt_LT | lt_LT |
| Letão | Letônia | lv_LV | lv_LV |
| Norueguês | Noruega - Bokmal | nb_NO | nb_NO |
| Holandês | Holanda | nl_NL | nl_NL |
| Polonês | Polônia | pl_PL | pl_PL |
| Português | Brasil | pt_BR | pt_BR |
| Português | Portugal | pt_PT | pt_PT |
| Romeno | Romênia | ro_RO | ro_RO |
| Russo | Rússia | ru_RU | ru_RU |
| Sueco | Suécia | sv_SE | sv_SE |
| Tailandês | Tailândia | th_TH | th_TH |
| Turco | Turquia | tr_TR | tr_TR |
| Chinês | China | zh_CN | zh_Hans_CN |
| Chinês | Taiwan | zh_TW | zh_Hant_TW |

Se o widget detectar que a configuração de idioma do administrador do Commerce (_Lojas_ > Configurações > _Configuração_ > _Geral_ > Opções de país) corresponde a um idioma suportado, o padrão é esse idioma. Caso contrário, os widgets padrão serão em inglês.

Os administradores também podem definir o idioma do [índice de pesquisa](settings.md#language), para ajudar a garantir melhores resultados de pesquisa.

### Repositório de código do widget

O widget Página de listagem de produtos e o widget de campo do Live Search estão disponíveis para download no repositório do github.

Isso permite que os desenvolvedores personalizem totalmente a funcionalidade e o estilo. Esses usuários hospedam o código enquanto ainda aproveitam o [!DNL Live Search] serviço.

- [Widget do PLP](https://github.com/adobe/storefront-product-listing-page)
- [Barra de pesquisa](https://github.com/adobe/storefront-search-as-you-type)

### Inventory management

[!DNL Live Search] suporta [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) no Commerce (antes conhecido como Inventário de várias origens, ou MSI). Para habilitar o suporte completo, você deve [atualizar](install.md#update) o módulo de dependência `commerce-data-export` para a versão 102.2.0+.

[!DNL Live Search] retorna um valor booleano observando se um produto está disponível no Inventory management, mas não contém informações sobre qual origem tem o estoque.

### Indexador de preços

Os clientes do Live Search podem usar o novo [Indexador de preços SaaS](../price-index/price-indexing.md), que oferece atualizações de alteração de preço e tempo de sincronização mais rápidos.

### Suporte de preço

Os widgets do Live Search são compatíveis com a maioria, mas não com todos os tipos de preço compatíveis com o Adobe Commerce.

Atualmente, os preços básicos são suportados. Os preços avançados que não são compatíveis são:

- Custo
- Preço Mínimo Anunciado

Examinar [API Mesh](../catalog-service/mesh.md) para cálculos de preços mais complexos.

O formato de preço oferece suporte à definição da configuração local na instância do Commerce: *Lojas* > Configurações > *Configuração* > Geral > *Geral* > Opções locais > Local.

### Suporte a vitrine headless

Como opção, talvez seja necessário instalar o `module-data-services-graphql` módulo que expande a cobertura existente do GraphQL do aplicativo para incluir campos necessários para a coleção de dados comportamentais da loja.

```bash
composer require magento/module-data-services-graphql
```

Esse módulo adiciona contextos adicionais às consultas do GraphQL:

- `dataServicesStorefrontInstanceContext`
- `dataServicesMagentoExtensionContext`
- `dataServicesStoreConfigurationContext`

### Suporte B2B

[!DNL Live Search] suporta [Funcionalidade B2B](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/guide-overview) com adicional [limitações](boundaries-limits.md#b2b-and-category-permissions).

### suporte para PWA

[!DNL Live Search] funciona com o PWA Studio, mas os usuários podem ver pequenas diferenças em comparação a outras implementações do Commerce. Funcionalidades básicas, como pesquisa e listagem de produtos, funcionam em Venia, mas algumas permutas de Graphql podem não funcionar corretamente. Também pode haver diferenças de desempenho.

- A atual implementação do PWA de [!DNL Live Search] requer mais tempo de processamento para retornar resultados de pesquisa do que [!DNL Live Search] com a loja Commerce nativa.
- [!DNL Live Search] O no PWA não suporta [manipulação de eventos](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/). Como resultado, os relatórios de pesquisa e o merchandising inteligente funcionarão.
- Filtrar diretamente em `description`, `name`, `short_description` não é compatível com o GraphQL quando usado com [PWA](https://developer.adobe.com/commerce/pwa-studio/), mas são retornados com um filtro mais geral.

Para usar [!DNL Live Search] com o PWA Studio, os integradores também devem:

1. Instalar [livesearch-storefront-utils](https://www.npmjs.com/package/@magento/ds-livesearch-storefront-utils).
1. Defina o `environmentId` no `storeDetails` objeto.

   ```javascript
   const storeDetails: StoreDetailsProps = {
       environmentId: <Storefront_ID>,
       websiteCode: "base",
       storeCode: "main_website_store",
       storeViewCode: "default",
       searchUnitId: searchUnitId,
       config: {
           minQueryLength: 5,
           pageSize: 8,
           currencySymbol: "$",
           },
       };
   ```

### Cookies

[!DNL Live Search] O coleta dados de interação do usuário como parte de sua funcionalidade básica, e os cookies são usados para armazenar esses dados. Ao coletar qualquer informação do usuário, ele deve concordar em armazenar cookies. [!DNL Live Search] e [!DNL Product Recommendations] compartilhar o fluxo de dados e, portanto, o mesmo mecanismo de cookie. Leia mais sobre isso em [Lidar com restrições de cookies](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/setting-cookie).
