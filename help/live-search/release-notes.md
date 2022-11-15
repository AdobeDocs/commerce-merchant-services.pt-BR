---
title: "[!DNL Live Search] Notas de versão"
description: "As informações mais recentes da versão para [!DNL Live Search] do Adobe Commerce."
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: 87b60e28e45466bf4271953c6704a53e6d43d73a
workflow-type: tm+mt
source-wordcount: '1166'
ht-degree: 1%

---

# [!DNL Live Search] Notas de versão

Essas notas de versão descrevem as versões mais recentes da [!DNL Live Search] e incluem:

* ![Novo](../assets/new.svg) - Novos recursos
* ![Correção](../assets/fix.svg) - Correções e melhorias
* ![Bug](../assets/bug.svg) - Problemas conhecidos

## [!DNL Live Search] 2.0.5

* Compatível com Adobe Commerce (EE): 2.4.x
* Compatível com Adobe Commerce for Cloud (ECE): 2.4.x
* Estabilidade: Estável

* ![Correção](../assets/fix.svg) - O Live Search geraria um erro quando os recursos do SDK não estavam disponíveis devido a problemas de rede. Esse erro foi corrigido.

Os comerciantes devem atualizar a versão da extensão do Live Search >= 2.0.5 para acessar esses recursos.

É recomendável atualizar e testar antes de levar para a produção. Considere atualizar o ambiente de produção durante horários fora de pico após verificar os resultados do ambiente de teste.

## [!DNL Live Search] 2.0.4

* Compatível com Adobe Commerce (EE): 2.4.x
* Compatível com Adobe Commerce for Cloud (ECE): 2.4.x
* Estabilidade: Estável

* ![Novo](../assets/new.svg) - O Live Search agora oferece suporte à filtragem pela configuração &quot;Exibir produtos esgotados&quot; no administrador. Se &quot;Exibir Produtos Fora de Estoque&quot; estiver definido como falso, `inStock = true` é adicionado ao filtro.
* ![Correção](../assets/fix.svg) - Para melhorar o desempenho, o bloco &quot;Sugestões&quot; foi removido do pop-up do Live Search. Os dados ainda são transmitidos por GraphQL, caso deseje substituir o recurso.
* ![Correção](../assets/fix.svg) - `categories` e `categoryPath` substituídos `categoryIds` para filtragem de categoria. Leia mais na [productSearch](https://devdocs.magento.com/live-search/product-search.html#filter) tópico.
* ![Correção](../assets/fix.svg) - Anteriormente, um usuário vinculado a uma empresa B2B recebia um Código incorreto do grupo de clientes ao fazer pesquisas. O Live Search agora retorna o valor correto.
* ![Correção](../assets/fix.svg) - Anteriormente, ao procurar por um termo que não existe, o Live Search retornaria um erro. Esse erro foi corrigido.

Os comerciantes devem atualizar a versão da extensão do Live Search >= 2.0.4 para acessar esses recursos.

## [!DNL Live Search] 2.0.3

* Compatível com Adobe Commerce (EE): 2.4.x
* Compatível com Adobe Commerce for Cloud (ECE): 2.4.x
* Estabilidade: Estável

* ![Novo](../assets/new.svg) - O Live Search agora oferece suporte a recursos B2B respeitando permissões de categoria, catálogos compartilhados e preços específicos do grupo de clientes.

Os comerciantes devem atualizar a versão da extensão do Live Search >= 2.0.3 para acessar esses recursos.

Recomendamos que os usuários atualizem e testem antes de enviar para a produção. Considere atualizar o ambiente de produção durante horários fora de pico após verificar os resultados do ambiente de teste.

>[!NOTE]
>
>O suporte B2B será adicionado em fases a partir de 9 de agosto nos serviços de back-end, com uma migração esperada a ser concluída até o final de agosto. Se a extensão Live Search não for atualizada, sua loja continuará a funcionar normalmente, mas sem recursos B2B.

### Limitações/bugs conhecidos:

* ![Bug](../assets/bug.svg) - As sugestões são fornecidas a partir de produtos que não podem ser exibidos para o grupo de clientes.
* ![Bug](../assets/bug.svg) - Os produtos não são exibidos se não forem adicionados ao &quot;Catálogo compartilhado padrão&quot;.
* ![Bug](../assets/bug.svg) - O Adaptador de pesquisa não renderiza o bucket &quot;Não&quot; para atributos de produtos booleanos, mesmo que os produtos estejam configurados com o atributo e o bucket &quot;Não&quot; seja retornado na resposta.
* Embora alguns produtos e consultas possam retornar resultados que não sejam em inglês, no momento as consultas em vários idiomas não são compatíveis.
* O B2B com Live Search for PWA Studio não estará disponível até que o PWA Studio adicione suporte para ele.
* Substituições de produto e atributos de produto no feed podem ter problemas de sincronização que exigem a execução de administradores `bin/magento indexer:reset` e `bin/magento indexer:reindex` para sincronizar novamente corretamente.
* Se você ativar ou desativar os recursos Permissões do catálogo/Catálogo compartilhado/B2B, a variável `catalog_data_exporter_product_overrides` indexer não é atualizado e marcado incorretamente como `valid`. Use `bin/magento saas:resync --feed=productOverrides` para corrigir o problema.

## [!DNL Live Search] 2,0

* Compatível com Adobe Commerce (EE): 2.4.x
* Compatível com Adobe Commerce for Cloud (ECE): 2.4.x
* Estabilidade: Estável

Existente [!DNL Live Search] As instalações devem ser atualizadas para [!DNL Live Search] 2.0.0 para aproveitar os novos recursos, correções e aprimoramentos a seguir:

* ![Novo](../assets/new.svg) - [!DNL Live Search] O agora é compatível com o PHP 8.1 para instalações que executam o Adobe Commerce 2.4.4.
* ![Novo](../assets/new.svg) - O `Magento_ElasticsearchCatalogPermissionsGraphQl` é adicionado à lista de módulos que são desativados durante a instalação.
* ![Novo](../assets/new.svg) - O número de linhas disponíveis no [[!DNL storefront popover]](quick-tour.md) pode ser configurado no *Administrador*.
* ![Novo](../assets/new.svg) - Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) compatibilidade para [!DNL Live Search].
* ![Novo](../assets/new.svg) - O [!DNL Live Search] o processo de instalação é atualizado com alterações avançadas do processo.
* ![Correção](../assets/fix.svg) - [Pesquisa avançada](https://docs.magento.com/user-guide/catalog/search-advanced.html) link removido do rodapé da loja.
* ![Bug](../assets/bug.svg) - Os seguintes atributos de produto não são compatíveis com [API Magento GraphQL](https://devdocs.magento.com/guides/v2.4/graphql) quando utilizado em relação à versão beta do PWA: `description`, `name`, `short_description`
* ![Bug](../assets/bug.svg) - A versão beta do PWA para [!DNL Live Search] não suporta [tratamento de evento](https://devdocs.magento.com/shared-services/storefront-events-sdk.html).

## [!DNL Live Search] 1.3.1.

* Compatível com Adobe Commerce (EE): 2.4.x
* Compatível com Adobe Commerce for Cloud (ECE): 2.4.x
* Estabilidade: Estável

* ![Correção](../assets/fix.svg) - [Atributo de preço personalizado](https://docs.magento.com/user-guide/stores/attributes-input-types.html) não retorna mais um erro quando configurado como um [faceta]({% link live-search/facets-add.md %}).
* ![Correção](../assets/fix.svg) - Correção de um problema que causava um erro quando não havia [símbolo de moeda](https://docs.magento.com/user-guide/stores/currency-symbols.html) (`data-currency-symbol`) está disponível.
* ![Correção](../assets/fix.svg) - [[!DNL Storefront popover]](storefront-popover.md) agora mostra o [Preço Especial](https://docs.magento.com/user-guide/catalog/product-price-special.html) (preço final mínimo), quando disponível.

## [!DNL Live Search] 1.3.0

* Compatível com Adobe Commerce (EE): 2.4.x
* Compatível com Adobe Commerce for Cloud (ECE): 2.4.x
* Estabilidade: Estável

* ![Novo](../assets/new.svg) - [Desempenho](performance.md) o painel de relatórios fornece informações sobre os termos de pesquisa que os compradores usam.
* ![Novo](../assets/new.svg) - [!DNL Live Search] [SDK de eventos de vitrine](https://devdocs.magento.com/shared-services/storefront-events-sdk.html) O fornece acesso a uma camada de dados comum com serviços de publicação de eventos e assinatura, além de métricas.
* ![Correção](../assets/fix.svg) - O [[!DNL Storefront Popover]](https://devdocs.magento.com/live-search/storefront-popover.html) tem um novo `active` classe para `.search-autocomplete` contêiner que controla a visibilidade.
* ![Correção](../assets/fix.svg) - Na loja, a [Pesquisar termos](https://docs.magento.com/user-guide/marketing/search-terms-popular.html) link de rodapé removido e seu cache desativado para [!DNL Live Search] instalações.
* ![Bug](../assets/bug.svg) - Patch for Search adapter trata de produtos duplicados.
* ![Bug](../assets/bug.svg) - [!DNL Live Search] suporta [fonte única](https://docs.magento.com/user-guide/catalog/inventory-sources.html) locais de inventário (físicos) com vários (virtuais) [stocks](https://docs.magento.com/user-guide/catalog/inventory-stock.html). No momento, não há suporte para várias fontes de inventário.

## [!DNL Live Search] 1.2.0

* Compatível com Adobe Commerce (EE): 2.4.x
* Compatível com Adobe Commerce for Cloud (ECE): 2.4.x
* Estabilidade: Estável

* ![Novo](../assets/new.svg) - [[!DNL Storefront popover]](storefront-popover.md) O exibe os produtos sugeridos e imagens em miniatura dos principais resultados da pesquisa, enquanto os compradores digitam consultas na caixa Pesquisar.
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
