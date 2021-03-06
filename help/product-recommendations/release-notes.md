---
title: Notas de versão
description: As últimas informações da versão para [!DNL Product Recommendations] do Adobe Commerce.
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
source-git-commit: 78f469dda853a6f46394d5969f879100cf22f8bb
workflow-type: tm+mt
source-wordcount: '945'
ht-degree: 0%

---

# Notas de versão

As notas de versão contêm atualizações para o seguinte [!DNL Product Recommendations] módulos:

* A partir de março de 2021, [!DNL Product Recommendations] agora são compatíveis com o [PWA Studio](https://developer.adobe.com/commerce/pwa-studio/integrations/product-recommendations/) vitrines.
* [!DNL Product Recommendations] metapackage: `magento/product-recommendations`
* Suporte ao Page Builder no [!DNL Product Recommendations] (opcional) módulo: `magento/module-page-builder-product-recommendations`
* Suporte do tipo de recomendação de semelhança visual para [!DNL Product Recommendations] (opcional) módulo: `magento/module-visual-product-recommendations`

As notas de versão incluem:

* ![Novo](../assets/new.svg) - Novos recursos
* ![Correção](../assets/fix.svg) - Correções e melhorias

Consulte a documentação do desenvolvedor para [saiba mais sobre compatibilidade de produtos](https://devdocs.magento.com/release/availability.html).

## Adobe Commerce 2.3.x e 2.4.x

## 4.0.0 da magento/recomendações de produto

* ![Novo](../assets/new.svg) - Adicionado [indicadores de disponibilidade](create.md) para ajudá-lo a visualizar o progresso de treinamento de cada tipo de recomendação.
* ![Novo](../assets/new.svg) - Esta é uma versão principal. Você deve [editar](install-configure.md#update) a raiz `composer.json` para o seu projeto. Esta versão também requer que você forneça duas chaves de API ao instalar e configurar o Product Recommendations: [uma chave de produção e uma chave de sandbox](../landing/saas.md).

## 3.3.7 da magento/recomendações de produto

* ![Novo](../assets/new.svg) - Adição do suporte a PHP 8.1
* ![Novo](../assets/new.svg) - Redimensionamento de imagem aprimorado para que imagens de tamanhos diferentes sejam tratadas de forma mais consistente no modelo de exibição de referência

## 3.3.6 da magento/recomendações de produto

* ![Novo](../assets/new.svg) - Otimizado [!DNL Product Recommendations] metapackage ao listar explicitamente as dependências

### 3.3.5 da magento/recomendações de produto

* ![Novo](../assets/new.svg) - Adicionado [Suporte a B2B](onboarding.md#b2bsupport) no Product Recommendations
* ![Novo](../assets/new.svg) - Novos feeds adicionados a [sincronizar dados do catálogo](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-catalog-sync.html) para o Commerce Services através da linha de comando

### 3.3.3 da magento/recomendações de produto

* ![Novo](../assets/new.svg) - Adição de novo [tipos de recomendação](type.md): Conversão (exibir no carrinho), Conversão (exibir na compra) e Visualização recente. Esses novos tipos de recomendação estão disponíveis no `magento/product-recommendations` módulo 3.2.2 e posterior.
* ![Correção](../assets/fix.svg) - Correção de um problema em que o Fastly&#39;s Web Application Firewall (WAF) estava bloqueando incorretamente um cookie
* ![Correção](../assets/fix.svg) - Correção de um problema em que os produtos atribuídos à Exibição de armazenamento não padrão não eram exibidos no _Visualização de produto do Recommendations_ painel ao criar uma recomendação para a Exibição de loja específica
* ![Correção](../assets/fix.svg) - Correção de um problema em que determinados nomes de unidade de recomendação no Construtor de página impedia que a unidade de recomendação fosse exibida na loja

### 3.3.2 da magento/recomendações de produto

* ![Correção](../assets/fix.svg) - Correção da dependência ausente do suporte B2B

### 3.3.1 da magento/recomendações de produto

* ![Novo](../assets/new.svg) - Suporte adicionado para preços de grupos de clientes B2B. Ao definir um [filtro de preço](filters.md) em uma unidade de recomendação, os clientes B2B que estiverem conectados verão o conjunto de preços do grupo de clientes para os produtos exibidos.

### 3.3.0 da magento/recomendações de produto

* ![Novo](../assets/new.svg) - Adição de suporte à Camada de dados do cliente do Adobe para padronizar a coleta de dados comportamentais entre os recursos e serviços do Adobe Commerce. Consulte a [readme](https://github.com/adobe/magento-storefront-event-collector/blob/main/README.md) para saber mais.

### 3.2.6 da magento/recomendações de produto

* ![Correção](../assets/fix.svg) - Correção de um erro modal de JavaScript
* ![Correção](../assets/fix.svg) - Correção de um problema em que o Fastly&#39;s Web Application Firewall (WAF) estava bloqueando incorretamente um cookie

### 3.2.5 da magento/recomendações de produto

* ![Novo](../assets/new.svg) - Serviços do Magento renomeados para [Commerce Services](https://docs.magento.com/user-guide/system/saas.html) e melhor utilização no Administrador

### 3.2.4 da magento/recomendações de produto

* ![Correção](../assets/fix.svg) - Correção do erro &quot;Não é possível recuperar dados de opções de produto configuráveis&quot; ao indexar atributos de produto

### 3.2.3 da magento/recomendações de produto

* ![Correção](../assets/fix.svg) - Corrigido o erro &quot;Não é possível recuperar dados de opções de produto configuráveis&quot; durante a Sincronização de Catálogo
* ![Correção](../assets/fix.svg) - Correção de um problema em que o código de armazenamento não estava sendo definido corretamente ao ativar a configuração &quot;Adicionar código de armazenamento ao URL&quot;
* ![Correção](../assets/fix.svg) - Melhoria na detecção de alterações na configuração do Painel de administração para garantir que essas alterações sejam refletidas nos dados de Sincronização do catálogo

### 3.2.2 da magento/recomendações de produto

* ![Novo](../assets/new.svg) - Adicionada a capacidade de [visualizar resultados da recomendação](create.md) no momento da criação. Isso pode exigir que você atualize seu módulo para a versão mais recente.
* ![Novo](../assets/new.svg) - Adicionada a capacidade de [monitorar e gerenciar](https://docs.magento.com/user-guide/system/catalog-sync.html) o processo de sincronização de catálogo do Administrador.
* ![Novo](../assets/new.svg) - Adicionado [filtros](filters.md) para controlar quais produtos são exibidos nas recomendações.
* ![Novo](../assets/new.svg) - Adicionado o [Similaridade visual](type.md#visualsim) tipo de recomendação.

### 1.2.1 de magento/module-page-builder-product-recommendations para o Page Builder

* ![Novo](../assets/new.svg) - Suporte adicionado para a versão 3.2.0+ do `magento/product-recommendations` módulo

### 3.1.0 da magento/recomendações de produto

* ![Novo](../assets/new.svg) - Adicionada a capacidade de [resync](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-catalog-sync.html) seu catálogo para os serviços SaaS por meio da linha de comando.
* ![Novo](../assets/new.svg) - Suporte adicionado para prefixos de tabela do banco de dados
* ![Correção](../assets/fix.svg) - Remoção do suporte para PHP 7.1

### 3.0.8 de magento/recomendações de produto

* ![Correção](../assets/fix.svg) - Correção de um problema em que os eventos eram enviados para a coleta de dados antes da configuração do módulo, causando tráfego inválido

### 3.0.6 de magento/recomendações de produto

* ![Novo](../assets/new.svg) - **(Beta)** Inclui suporte para novos [Similaridade visual](type.md#visualsim) tipo de recomendação.

### 1.0.0 de magento/módulo-visual-product-recommendations

* ![Novo](../assets/new.svg) - **(Beta)** [Similaridade visual](type.md#visualsim). Com o _Similaridade visual_ tipo de recomendação, você pode implantar uma unidade de recomendação na página de detalhes do produto, que exibe produtos visualmente semelhantes ao produto que está sendo visualizado.

### 3.0.5 de magento/recomendações de produto

* ![Correção](../assets/fix.svg) - Correção do erro &quot;Não é possível recuperar dados de opções do produto&quot; que poderia ocorrer durante a exportação do catálogo.
* ![Correção](../assets/fix.svg) - O símbolo da moeda na _Receita_ na coluna _Recommendations do produto_ agora, o painel reflete corretamente a moeda base configurada.

### 3.0.4 de magento/recomendações de produto

* ![Correção](../assets/fix.svg) - Adição de suporte para Adobe Commerce 2.4.0

### 3.0.3 de magento/recomendações de produto

* ![Correção](../assets/fix.svg) - Implementação de símbolo aprimorada no modelo de loja

### 1.0.4 de magento/module-page-builder-product-recommendations para o Page Builder

* ![Novo](../assets/new.svg) - Adição do nome de Recomendação de produto ao editar o tipo de conteúdo do Construtor de páginas

### 3.0.2 magento/recomendações de produto

* ![Novo](../assets/new.svg) - Adição de uma coluna de status na grade ao selecionar unidades de recomendação no Construtor de páginas
* ![Correção](../assets/fix.svg) - Correção de um problema com protocolos http/https incorretos em URLs de produto e imagem

### 3.0.1 de magento/recomendações de produto

Esta é uma versão principal. Você deve [editar](install-configure.md#update) o arquivo composer.json raiz do seu projeto.

* ![Novo](../assets/new.svg) - Busca [!DNL Product Recommendations] em Espaços de dados SaaS alternativos. Isso permite usar as recomendações de produto calculadas no ambiente do produto em outros ambientes que não sejam de produção. [Alternando Espaços de Dados SaaS](settings.md) descreve mais detalhadamente esse recurso.

* ![Correção](../assets/fix.svg) - Correção de um problema em que o check-out era inibido para compradores que usavam a origem uBlock
* ![Correção](../assets/fix.svg) - Correção de um problema no envio de eventos adicionais irrelevantes para o carrinho

### 1.0.3 de magento/module-page-builder-product-recommendations para o Page Builder

* ![Novo](../assets/new.svg) - Suporte ao Page Builder. Com a integração do Page Builder, você pode colocar unidades de recomendação de maneira precisa e granular em qualquer local arbitrário no conteúdo criado pelo Page Builder. Você também pode criar um estilo para os próprios cabeçalhos e unidades de recomendação. Ir para [Page Builder](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html) para obter mais informações.

### 2.0.0 da magento/recomendações de produto

* ![Novo](../assets/new.svg) - Versão de disponibilidade geral!

## Documentação

Para saber mais sobre [!DNL Product Recommendations] e [!DNL Product Recommendations] desenvolvimento:

* [Guia do usuário](overview.md)
* [Documentação do desenvolvedor](https://devdocs.magento.com/recommendations/product-recs.html)
