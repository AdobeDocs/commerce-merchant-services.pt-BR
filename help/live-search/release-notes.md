---
title: Notas de versão do Live Search
description: As informações mais recentes da versão do Live Search da Adobe Commerce.
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: c70d08b90d7584559fd69cdeece0220015ae8523
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 1%

---

# [!DNL Live Search] Notas de versão

Essas notas de versão descrevem as versões mais recentes da [!DNL Live Search] e incluem:

* ![Novo](../assets/new.svg) - Novos recursos
* ![Correção](../assets/fix.svg) - Correções e melhorias
* ![Bug](../assets/bug.svg) - Problemas conhecidos

## [!DNL Live Search] 2,0

* Compatível com Adobe Commerce (EE): 2.4.x
* Compatível com Adobe Commerce for Cloud (ECE): 2.4.x
* Estabilidade: Estável

* ![Novo](../assets/new.svg) - O número de linhas disponíveis no [loja](quick-tour.md) pode ser configurado no *Administrador*.
* ![Novo](../assets/new.svg) - Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) compatibilidade para o Live Search.
* ![Novo](../assets/new.svg) - O processo de instalação do Live Search é atualizado com alterações avançadas no processo.
* ![Correção](../assets/fix.svg) - [Pesquisa avançada](https://docs.magento.com/user-guide/catalog/search-advanced.html) link removido do rodapé da loja.
* ![Bug](../assets/bug.svg) - Os seguintes atributos de produto não são compatíveis com [API Magento GraphQL](https://devdocs.magento.com/guides/v2.4/graphql) quando utilizado em relação à versão beta do PWA: `description`, `name`, `short_description`
* ![Bug](../assets/bug.svg) - A versão beta do PWA para Live Search não é compatível [tratamento de evento](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).

## [!DNL Live Search] 1.3.1.

* Compatível com Adobe Commerce (EE): 2.4.x
* Compatível com Adobe Commerce for Cloud (ECE): 2.4.x
* Estabilidade: Estável

* ![Correção](../assets/fix.svg) - [Atributo de preço personalizado](https://docs.magento.com/user-guide/stores/attributes-input-types.html) não retorna mais um erro quando configurado como um [faceta]({% link live-search/facets-add.md %}).
* ![Correção](../assets/fix.svg) - Correção de um problema que causava um erro quando não havia [símbolo de moeda](https://docs.magento.com/user-guide/stores/currency-symbols.html) (`data-currency-symbol`) está disponível.
* ![Correção](../assets/fix.svg) - [Potência de vitrine](storefront-popover.md) agora mostra o [Preço Especial](https://docs.magento.com/user-guide/catalog/product-price-special.html) (preço final mínimo), quando disponível.

## [!DNL Live Search] 1.3.0

* Compatível com Adobe Commerce (EE): 2.4.x
* Compatível com Adobe Commerce for Cloud (ECE): 2.4.x
* Estabilidade: Estável

* ![Novo](../assets/new.svg) - [Desempenho](performance.md) o painel de relatórios fornece informações sobre os termos de pesquisa que os compradores usam.
* ![Novo](../assets/new.svg) - [!DNL Live Search] [SDK de eventos de vitrine](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) O fornece acesso a uma camada de dados comum com serviços de publicação de eventos e assinatura, além de métricas.
* ![Correção](../assets/fix.svg) - O [Popover de frente de loja](https://devdocs.magento.com/live-search/storefront-popover.html) tem um novo `active` classe para `.search-autocomplete` contêiner que controla a visibilidade.
* ![Correção](../assets/fix.svg) - Na loja, a [Pesquisar termos](https://docs.magento.com/user-guide/marketing/search-terms-popular.html) link de rodapé removido e seu cache desativado para [!DNL Live Search] instalações.
* ![Bug](../assets/bug.svg) - Patch for Search adapter trata de produtos duplicados.
* ![Bug](../assets/bug.svg) - [!DNL Live Search] suporta [fonte única](https://docs.magento.com/user-guide/catalog/inventory-sources.html) locais de inventário (físicos) com vários (virtuais) [stocks](https://docs.magento.com/user-guide/catalog/inventory-stock.html). No momento, não há suporte para várias fontes de inventário.

## [!DNL Live Search] 1.2.0

* Compatível com Adobe Commerce (EE): 2.4.x
* Compatível com Adobe Commerce for Cloud (ECE): 2.4.x
* Estabilidade: Estável

* ![Novo](../assets/new.svg) - Loja [proveta](storefront-popover.md) O exibe os produtos sugeridos e imagens em miniatura dos principais resultados da pesquisa, enquanto os compradores digitam consultas na caixa Pesquisar.
* ![Novo](../assets/new.svg) - Comércio *Administrador* a sessão permanece aberta durante longos períodos de inatividade do teclado
* ![Novo](../assets/new.svg) - [!DNL Live Search] é ativado automaticamente após a integração
* ![Correção](../assets/fix.svg) - O tempo de indexação inicial é inferior a uma hora
* ![Correção](../assets/fix.svg) - Atualizações incrementais de produtos quase em tempo real (após a instalação e a configuração)
* ![Correção](../assets/fix.svg) - Colunas classificáveis no editor Sinônimo
* ![Correção](../assets/fix.svg) - [!DNL Live Search] não gera mais um erro se os critérios de pesquisa contiverem um valor de ordem de classificação vazio
* ![Correção](../assets/fix.svg) - A filtragem de intervalo não é mais interrompida se os códigos de atributo contiverem sequências de caracteres &quot;para&quot; ou &quot;de&quot;

## [!DNL Live Search] 1.1.0

* Compatível com Adobe Commerce (EE): 2.4.x
* Compatível com Adobe Commerce for Cloud (ECE): 2.4.x
* Estabilidade: Estável

* ![Bug](../assets/bug.svg) - O [!DNL Live Search] o serviço suporta somente o [moeda base](https://docs.magento.com/user-guide/stores/currency-configuration.html) da instalação do Adobe Commerce.
* ![Bug](../assets/bug.svg) - Ao adicionar uma faceta, o Feed de atributos do produto não é atualizado corretamente quando definido como `Update on Save`. Para evitar esse problema, acesse [Gerenciamento de índice](https://docs.magento.com/user-guide/system/index-management.html) e defina o Feed de atributos do produto como `Update by Schedule`.
* ![Bug](../assets/bug.svg) - [!DNL Live Search] os sinônimos são definidos por exibição de loja, mas são armazenados por site no momento e identificados com uma combinação de `environmentId` + `storeViewCode`. Como resultado, todos os sites e exibições de armazenamento na instalação do Adobe Commerce compartilham o mesmo conjunto de sinônimos. O conjunto de sinônimos criado mais recentemente para a exibição de loja tem prioridade.
* ![Bug](../assets/bug.svg) - Se um termo de sinônimo contiver várias palavras, cada palavra será tratada como um sinônimo separado. Por exemplo, se você definir &quot;peça-hora&quot; como sinônimo de &quot;relógio&quot;, tanto &quot;hora&quot; quanto &quot;peça&quot; são tratadas como sinônimos de relógio.

## Documentação

Para saber mais:

* [Documentação do desenvolvedor do Adobe Commerce](https://devdocs.magento.com/)
* [Guia do usuário do Adobe Commerce](https://docs.magento.com/user-guide/)
* [[!DNL Live Search] no Marketplace](https://marketplace.magento.com/magento-live-search.html)
