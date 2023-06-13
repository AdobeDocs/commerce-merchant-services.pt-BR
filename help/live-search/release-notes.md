---
title: '[!DNL Live Search] Notas de versão'
description: "As informações mais recentes da versão do [!DNL Live Search] da Adobe Commerce."
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: d4f22cdae9b4b0a19691465ae87e344847672698
workflow-type: tm+mt
source-wordcount: '1277'
ht-degree: 0%

---

# [!DNL Live Search] Notas de versão

Estas notas de versão descrevem as versões mais recentes da [!DNL Live Search].
O suporte é fornecido para a versão principal atual lançada. As notas de versão para versões mais antigas são fornecidas para referência.
As atualizações incluem:

![Novo](../assets/new.svg) Novos recursos
![Correção](../assets/fix.svg) Correções e aprimoramentos
![Bug](../assets/bug.svg) Problemas conhecidos


_13 de junho de 2023_

![Novo](../assets/new.svg) O Live Search agora oferece suporte a mais 5 [valores de configuração](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/configuration.html).
![Correção](../assets/fix.svg) Correção de um problema em que alguns caracteres, como aspas ou apóstrofos, causavam problemas de classificação. A reindexação resolverá esses problemas.

_25 de abril de 2023_

![Novo](../assets/new.svg) Os clientes do Live Search agora podem aproveitar o novo [Indexador de preços SaaS](../price-index/index.md).

## [!DNL Live Search] 3.0.1 {#301}

_14 de março de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

### Novos recursos

* Cartão de item de produto na visualização de Regras
* [Widget de página de listagem de produtos](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling.html)
* [Opções de filtragem de categoria](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#facets)
* Adição da capacidade de arrastar e soltar para criar eventos de Fixação
* Novas ações de Fixação:
   * Fixar no ponto - O botão Fixar para criar o evento Fixar com um clique
   * Fixar na parte superior - Coloca o produto na primeira posição
   * Fixar na parte inferior - Coloca o produto na parte inferior dos resultados
   * Desafixar um evento com um clique
* [Classificação inteligente para regras](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add.html#ranking-type)

### Atualizações

* Configurar regras agora classifica automaticamente as posições de forma exclusiva
* A exclusão de um evento existente agora atualiza a visualização
* Regras sem eventos podem ser salvas
* Remover o seletor de facetas &quot;Selecionar tipo&quot;
* Adição de um novo status de &quot;Edição&quot; para regras não salvas

### Correções

* Correção de um erro de servidor quando há um evento não concluído durante o salvamento
* Correção da exclusão correta de um evento específico quando havia vários eventos
* Corrigido o evento de regra existente não atualizado quando um novo evento era adicionado
* Corrigido no segundo clique &quot;Editar&quot; nos detalhes, [!DNL Live Search] página que precisa ser recarregada
* Sinônimos: correção de um problema quando um usuário clicava fora da entrada, ele não podia retornar o foco para o campo
* Outras correções de pequenos erros e atualizações de desempenho


* ![Bug](../assets/bug.svg) - A classificação por &quot;Recomendado para você&quot; só é compatível com os widgets do Live Search. Não é compatível com a funcionalidade padrão de pesquisa Luma e PWA.
* ![Bug](../assets/bug.svg) - As facetas de atributos de preço personalizados não são renderizadas corretamente no Luma, mas a API as filtra corretamente.

Os comerciantes devem atualizar o [!DNL Live Search] versão da extensão do >= 3.0.1 para acessar esses recursos.

É recomendável atualizar e testar antes de enviar para a produção. Considere atualizar o ambiente de produção fora do horário de pico após verificar os resultados do ambiente de teste.

## Versões anteriores

+++2.0.5 e anteriores

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

* ![Correção](../assets/fix.svg) - O Live Search geraria um erro quando os recursos do SDK não estivessem disponíveis devido a problemas de rede. Esse erro foi corrigido.

Os comerciantes devem atualizar a versão da extensão do Live Search >= 2.0.5 para acessar esses recursos.

É recomendável atualizar e testar antes de enviar para a produção. Considere atualizar o ambiente de produção fora do horário de pico após verificar os resultados do ambiente de teste.

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) O Live Search agora oferece suporte à filtragem pela configuração &quot;Exibir produtos sem estoque&quot; no administrador. Se &#39;Exibir produtos esgotados&#39; estiver definido como falso, `inStock = true` é adicionado ao filtro.
![Correção](../assets/fix.svg) Para melhorar o desempenho, o bloco &quot;Sugestões&quot; foi removido do pop-up do Live Search. Os dados ainda são transmitidos pelo GraphQL, caso você queira substituir o recurso.
![Correção](../assets/fix.svg) `categories` e `categoryPath` substituíram `categoryIds` para filtragem de categorias. Leia mais na seção [productSearch](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) tópico.
![Correção](../assets/fix.svg) Anteriormente, um usuário vinculado a uma empresa B2B recebia um código incorreto do grupo do cliente ao fazer pesquisas. O Live Search agora retorna o valor correto.
![Correção](../assets/fix.svg) Anteriormente, ao pesquisar um termo que não existe, o Live Search retornava um erro. Esse erro foi corrigido.

Os comerciantes devem atualizar o [!DNL Live Search] versão da extensão >= 2.0.4 para acessar esses recursos.

Os usuários são aconselhados a atualizar e testar antes de enviar para a produção. Considere atualizar o ambiente de produção fora do horário de pico após verificar os resultados do ambiente de teste.

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) O Live Search agora oferece suporte a recursos B2B, respeitando permissões de categoria, catálogos compartilhados e preços específicos do grupo de clientes.

Os comerciantes devem atualizar o [!DNL Live Search] versão da extensão >= 2.0.3 para acessar esses recursos.

Os usuários são aconselhados a atualizar e testar antes de enviar para a produção. Considere atualizar o ambiente de produção fora do horário de pico após verificar os resultados do ambiente de teste.

### [!DNL Live Search] 2.0 {#20}

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

Existente [!DNL Live Search] as instalações devem ser atualizadas para [!DNL Live Search] 2.0.0 para aproveitar os seguintes novos recursos, correções e melhorias:

![Novo](../assets/new.svg) [!DNL Live Search] O agora suporta o PHP 8.1 para instalações que executam o Adobe Commerce 2.4.4.
![Novo](../assets/new.svg) A variável `Magento_ElasticsearchCatalogPermissionsGraphQl` O módulo é adicionado à lista de módulos que são desativados durante a instalação.
![Novo](../assets/new.svg) O número de linhas disponíveis na [[!DNL storefront popover]](quick-tour.md) pode ser configurado no *Admin*.
![Novo](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) compatibilidade para [!DNL Live Search].
![Novo](../assets/new.svg) A variável [!DNL Live Search] o processo de instalação é atualizado com alterações avançadas do processo.
![Correção](../assets/fix.svg) [Pesquisa avançada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) link removido do rodapé da loja.
![Bug](../assets/bug.svg) Os seguintes atributos de produto não são compatíveis com o [API do GraphQL para comércio](https://developer.adobe.com/commerce/webapi/graphql/) quando usado em relação à versão beta do PWA: `description`, `name`, `short_description`
![Bug](../assets/bug.svg) A versão beta do PWA para [!DNL Live Search] não suporta [manipulação de eventos](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Correção](../assets/fix.svg) [Atributo de preço personalizado](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) O não retorna mais um erro quando configurado como [faceta]({% link live-search/facets-add.md %}).
![Correção](../assets/fix.svg) Correção de um problema que causava a ocorrência de um erro quando não [símbolo de moeda](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`) está disponível.
![Correção](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) O agora mostra o [Preço especial](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) (preço final mínimo) quando disponível.

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) [Desempenho](performance.md) o painel de relatórios fornece informações sobre os termos de pesquisa que os compradores usam.
![Novo](../assets/new.svg) [!DNL Live Search] [SDK de eventos da loja](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) O fornece acesso a uma camada de dados comum com serviços e métricas de publicação e assinatura de eventos.
![Correção](../assets/fix.svg) A variável [[!DNL Storefront popover]](storefront-popover.md) tem um novo `active` classe para a `.search-autocomplete` container que controla a visibilidade.
![Correção](../assets/fix.svg) Na vitrine, o [Pesquisar termos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) o link do rodapé é removido e seu cache é desativado por [!DNL Live Search] instalações.
![Bug](../assets/bug.svg) O patch para o adaptador de Pesquisa manipula produtos duplicados.
![Bug](../assets/bug.svg) [!DNL Live Search] suporta [de uma única fonte](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) locais de inventário (físico) com vários (virtuais) [estoques](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). Agora, não há suporte para várias fontes de inventário.

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) O exibe produtos sugeridos e imagens em miniatura dos principais resultados da pesquisa, à medida que os compradores digitam as consultas na caixa Pesquisar.
![Novo](../assets/new.svg) Commerce *Admin* a sessão permanece aberta durante longos períodos de inatividade do teclado
![Novo](../assets/new.svg) [!DNL Live Search] é ativado automaticamente após a integração
![Correção](../assets/fix.svg) O tempo de indexação inicial é inferior a uma hora
![Correção](../assets/fix.svg) Atualizações incrementais de produtos quase em tempo real (após a instalação e a configuração)
![Correção](../assets/fix.svg) Colunas classificáveis no editor de sinônimos
![Correção](../assets/fix.svg) [!DNL Live Search] O não gera mais um erro se os critérios de pesquisa contiverem valores vazios de ordem de classificação
![Correção](../assets/fix.svg) A filtragem de intervalo não é mais interrompida se os códigos de atributo contiverem cadeias de caracteres &quot;para&quot; ou &quot;de&quot;

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Bug](../assets/bug.svg) A variável [!DNL Live Search] o serviço oferece suporte somente ao [moeda de base](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) da instalação do Adobe Commerce.
![Bug](../assets/bug.svg) Ao adicionar uma faceta, o Feed de atributos do produto não é atualizado corretamente quando definido como `Update on Save`. Para evitar esse problema, acesse [Gerenciamento de índice](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) e definir o Feed de atributos do produto como `Update by Schedule`.
![Bug](../assets/bug.svg) [!DNL Live Search] os sinônimos são definidos por exibição de loja, mas atualmente são armazenados por site e identificados com uma combinação de `environmentId` e `storeViewCode`. Como resultado, todos os sites e exibições de armazenamento na instalação do Adobe Commerce compartilham sinônimos. O conjunto de sinônimos criado mais recentemente para a exibição de loja tem prioridade.
![Bug](../assets/bug.svg) Se um sinônimo contiver várias palavras, cada palavra será tratada como um sinônimo separado. Por exemplo, se você definir &quot;peça de tempo&quot; como um sinônimo de &quot;relógio&quot;, tanto &quot;tempo&quot; quanto &quot;peça&quot; serão tratados como sinônimos de relógio.

+++

## Documentação

Para saber mais:

* [Documentação do desenvolvedor do Adobe Commerce](https://developer.adobe.com/commerce/docs)
* [Guia do usuário do Adobe Commerce](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] no Marketplace](https://marketplace.magento.com/magento-live-search.html)
