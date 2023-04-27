---
title: '[!DNL Live Search] Notas de versão'
description: "As informações mais recentes da versão para [!DNL Live Search] do Adobe Commerce."
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
source-git-commit: f955cfc918c19a3c32126d8c9ef8a59b0e0dce0a
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 0%

---

# [!DNL Live Search] Notas de versão

Essas notas de versão descrevem as versões mais recentes da [!DNL Live Search].
É fornecido suporte para a versão principal mais recente. As notas de versão para versões mais antigas são fornecidas para referência.
As atualizações incluem:

![Novo](../assets/new.svg) Novos recursos
![Correção](../assets/fix.svg) Correções e melhorias
![Bug](../assets/bug.svg) Problemas conhecidos


_25 de abril de 2023_

![Novo](../assets/new.svg) Os clientes do Live Search agora podem aproveitar as vantagens do novo [Indexador de preço SaaS](../price-index/index.md).

## [!DNL Live Search] 3.0.1 {#301}

_14 de março de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

### Novos recursos

* Cartão de item de produto na visualização de Regras
* [Widget Página de listagem do produto](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling.html)
* [Opções de filtragem de categorias](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/#facets)
* Adição da capacidade de arrastar e soltar para criar eventos de Pin
* Novas ações de pino:
   * Fixar no ponto - Botão Fixar para criar um evento de Fixar com um clique
   * Fixar no topo - Posiciona o produto na primeira posição
   * Fixar na parte inferior - Posiciona o produto na parte inferior dos resultados
   * Desfixar um evento com um clique
* [Classificação inteligente para regras](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add.html#ranking-type)

### Atualizações

* Configurar regras agora classifica as posições automaticamente de forma exclusiva
* Excluir um evento existente agora atualiza a visualização
* Regras sem eventos podem ser salvas
* Remova o seletor de lapidamento &quot;Selecionar tipo&quot;
* Novo status &quot;Edição&quot; adicionado para regras não salvas

### Correções

* Correção de um erro de servidor quando há um evento inacabado durante o salvamento
* Correção da exclusão correta de um evento específico quando há vários eventos
* Correção de um evento de regra existente que não era atualizado quando um novo evento era adicionado
* Corrigido no segundo clique &quot;Editar&quot; nos detalhes, [!DNL Live Search] página que requer recarregamento
* Sinônimos: Correção de um problema quando um usuário clicava fora da entrada, ele não podia retornar o foco para o campo
* Outras pequenas correções de erros e atualizações de desempenho


* ![Bug](../assets/bug.svg) - A classificação por &quot;Recomendado para você&quot; só é suportada nos widgets do Live Search. Não é compatível com a funcionalidade de pesquisa Luma e PWA padrão.
* ![Bug](../assets/bug.svg) - Os aspectos de atributos de preço personalizados não são renderizados corretamente no Luma, mas a API filtra-os corretamente neles.

Os comerciantes devem atualizar a [!DNL Live Search] versão de extensão >= 3.0.1 para acessar esses recursos.

É recomendável atualizar e testar antes de levar para a produção. Considere atualizar o ambiente de produção durante horários fora de pico após verificar os resultados do ambiente de teste.

## Versões anteriores

+++2.0.5 e anterior

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

* ![Correção](../assets/fix.svg) - O Live Search geraria um erro quando os recursos do SDK não estavam disponíveis devido a problemas de rede. Este erro foi corrigido.

Os comerciantes devem atualizar a versão da extensão do Live Search >= 2.0.5 para acessar esses recursos.

É recomendável atualizar e testar antes de levar para a produção. Considere atualizar o ambiente de produção durante horários fora de pico após verificar os resultados do ambiente de teste.

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) O Live Search agora oferece suporte à filtragem pela configuração &quot;Exibir produtos esgotados&quot; no administrador. Se &quot;Exibir Produtos Fora de Estoque&quot; estiver definido como falso, `inStock = true` é adicionado ao filtro.
![Correção](../assets/fix.svg) Para melhorar o desempenho, o bloco &quot;Sugestões&quot; foi removido do pop-up do Live Search. Os dados ainda são transmitidos pelo GraphQL, caso você queira substituir o recurso.
![Correção](../assets/fix.svg) `categories` e `categoryPath` substituídos `categoryIds` para filtragem de categoria. Leia mais na [productSearch](https://developer.adobe.com/commerce/webapi/graphql/schema/live-search/queries/product-search/) tópico.
![Correção](../assets/fix.svg) Anteriormente, um usuário vinculado a uma empresa B2B recebia um Código de grupo do cliente incorreto ao fazer pesquisas. O Live Search agora retorna o valor correto.
![Correção](../assets/fix.svg) Anteriormente, ao pesquisar por um termo que não existe, o Live Search retornaria um erro. Esse erro foi corrigido.

Os comerciantes devem atualizar a [!DNL Live Search] versão de extensão >= 2.0.4 para acessar esses recursos.

Os usuários são aconselhados a atualizar e testar antes de enviar para a produção. Considere atualizar o ambiente de produção durante horários fora de pico após verificar os resultados do ambiente de teste.

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) O Live Search agora oferece suporte a recursos B2B respeitando permissões de categoria, catálogos compartilhados e preços específicos do grupo de clientes.

Os comerciantes devem atualizar a [!DNL Live Search] versão de extensão >= 2.0.3 para acessar esses recursos.

Os usuários são aconselhados a atualizar e testar antes de enviar para a produção. Considere atualizar o ambiente de produção durante horários fora de pico após verificar os resultados do ambiente de teste.

### [!DNL Live Search] 2.0 {#20}

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

Existente [!DNL Live Search] As instalações devem ser atualizadas para [!DNL Live Search] 2.0.0 para aproveitar os novos recursos, correções e aprimoramentos a seguir:

![Novo](../assets/new.svg) [!DNL Live Search] O agora é compatível com o PHP 8.1 para instalações que executam o Adobe Commerce 2.4.4.
![Novo](../assets/new.svg) O `Magento_ElasticsearchCatalogPermissionsGraphQl` é adicionado à lista de módulos que são desativados durante a instalação.
![Novo](../assets/new.svg) O número de linhas disponíveis no [[!DNL storefront popover]](quick-tour.md) pode ser configurado no *Administrador*.
![Novo](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) compatibilidade para [!DNL Live Search].
![Novo](../assets/new.svg) O [!DNL Live Search] o processo de instalação é atualizado com alterações avançadas do processo.
![Correção](../assets/fix.svg) [Pesquisa avançada](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search.html#advanced-search) link removido do rodapé da loja.
![Bug](../assets/bug.svg) Os seguintes atributos de produto não são compatíveis com o [API do Commerce GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) quando utilizado em relação à versão beta do PWA: `description`, `name`, `short_description`
![Bug](../assets/bug.svg) A versão beta do PWA para [!DNL Live Search] não suporta [tratamento de evento](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Correção](../assets/fix.svg) [Atributo de preço personalizado](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/attributes-input-types.html) não retorna mais um erro quando configurado como um [faceta]({% link live-search/facets-add.md %}).
![Correção](../assets/fix.svg) Correção de um problema que causava um erro quando não havia [símbolo de moeda](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html#step-5%3A-customize-currency-symbols-(optional)) (`data-currency-symbol`) está disponível.
![Correção](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) agora mostra o [Preço Especial](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/product-price-special.html) (preço final mínimo), quando disponível.

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) [Desempenho](performance.md) o painel de relatórios fornece informações sobre os termos de pesquisa que os compradores usam.
![Novo](../assets/new.svg) [!DNL Live Search] [SDK de eventos de vitrine](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) O fornece acesso a uma camada de dados comum com serviços de publicação de eventos e assinatura, além de métricas.
![Correção](../assets/fix.svg) O [[!DNL Storefront popover]](storefront-popover.md) tem um novo `active` classe para `.search-autocomplete` contêiner que controla a visibilidade.
![Correção](../assets/fix.svg) Na loja, a [Pesquisar termos](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html#popular-search-terms) link de rodapé removido e seu cache desativado para [!DNL Live Search] instalações.
![Bug](../assets/bug.svg) Patch para o adaptador de pesquisa trata de produtos duplicados.
![Bug](../assets/bug.svg) [!DNL Live Search] suporta [fonte única](https://experienceleague.adobe.com/docs/commerce-admin/inventory/sources/sources-manage.html) locais de inventário (físicos) com vários (virtuais) [stocks](https://experienceleague.adobe.com/docs/commerce-admin/inventory/stocks/stocks-manage.html). Agora, não há suporte para várias fontes de inventário.

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) O exibe os produtos sugeridos e imagens em miniatura dos principais resultados da pesquisa, enquanto os compradores digitam consultas na caixa Pesquisar.
![Novo](../assets/new.svg) Comércio *Administrador* a sessão permanece aberta durante longos períodos de inatividade do teclado
![Novo](../assets/new.svg) [!DNL Live Search] é ativado automaticamente após a integração
![Correção](../assets/fix.svg) O tempo de indexação inicial é menor que uma hora
![Correção](../assets/fix.svg) Atualizações incrementais de produtos quase em tempo real (após a instalação e a configuração)
![Correção](../assets/fix.svg) Colunas classificáveis no editor Sinônimo
![Correção](../assets/fix.svg) [!DNL Live Search] não gera mais um erro se os critérios de pesquisa contiverem um valor de ordem de classificação vazio
![Correção](../assets/fix.svg) A filtragem de intervalo não é mais interrompida se os códigos de atributo contiverem sequências de caracteres &quot;para&quot; ou &quot;de&quot;

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Bug](../assets/bug.svg) O [!DNL Live Search] o serviço suporta somente o [moeda base](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration.html) da instalação do Adobe Commerce.
![Bug](../assets/bug.svg) Ao adicionar uma faceta, o Feed de atributos do produto não é atualizado corretamente quando definido como `Update on Save`. Para evitar esse problema, acesse [Gerenciamento de índice](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html) e defina o Feed de atributos do produto como `Update by Schedule`.
![Bug](../assets/bug.svg) [!DNL Live Search] os sinônimos são definidos por exibição de loja, mas são armazenados por site no momento e identificados com uma combinação de `environmentId` e `storeViewCode`. Como resultado, todos os sites e exibições de armazenamento na instalação do Adobe Commerce compartilham sinônimos. O conjunto de sinônimos criado mais recentemente para a exibição de loja tem prioridade.
![Bug](../assets/bug.svg) Se um termo de sinônimo contiver várias palavras, cada palavra será tratada como um sinônimo separado. Por exemplo, se você definir &quot;peça-hora&quot; como sinônimo de &quot;relógio&quot;, tanto &quot;hora&quot; quanto &quot;peça&quot; são tratadas como sinônimos de relógio.

+++

## Documentação

Para saber mais:

* [Documentação do desenvolvedor do Adobe Commerce](https://developer.adobe.com/commerce/docs)
* [Guia do usuário do Adobe Commerce](https://experienceleague.adobe.com/docs/commerce.html)
* [[!DNL Live Search] no Marketplace](https://marketplace.magento.com/magento-live-search.html)
