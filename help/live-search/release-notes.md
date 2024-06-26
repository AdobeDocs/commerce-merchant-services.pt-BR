---
title: "[!DNL Live Search] Notas de versão"
description: "As informações mais recentes da versão do [!DNL Live Search] da Adobe Commerce."
exl-id: 2a581e43-35f5-48ce-9752-844430ccdebf
feature: Services, Search, Release Notes
source-git-commit: fe261bfaf5a64c9501bc5523d29f9b6a9fc1a6a2
workflow-type: tm+mt
source-wordcount: '1966'
ht-degree: 0%

---

# [!DNL Live Search] Notas de versão

Estas notas de versão descrevem as versões mais recentes da [!DNL Live Search].
O suporte é fornecido para a versão principal atual lançada. As notas de versão para versões mais antigas são fornecidas para referência.
As atualizações incluem:

![Novo](../assets/new.svg) Novos recursos
![Correção](../assets/fix.svg) Correções e aprimoramentos
![Bug](../assets/bug.svg) Problemas conhecidos

## Atualizações do serviço hospedado

Essas notas descrevem atualizações que foram publicadas fora de uma versão com controle de versão ou melhorias no serviço hospedado.

_13 de fevereiro de 2024_

![Novo](../assets/new.svg) [!DNL Live Search] agora oferece suporte à configuração de uma regra padrão para [Pesquisar merchandising](rules.md).

_12 de outubro de 2023_

![Novo](../assets/new.svg) Agora, os administradores do Commerce podem especificar o idioma do índice para [!DNL Live Search]. Consulte [Configurações](settings.md).
![Correção](../assets/fix.svg) A guia &quot;Regras de pesquisa&quot; foi renomeada para &quot;Pesquisar merchandising&quot;.

_13 de junho de 2023_

![Correção](../assets/fix.svg) Correção de um problema em que alguns caracteres, como aspas ou apóstrofos, causavam problemas de classificação. A reindexação resolve esses problemas.

_25 de abril de 2023_

![Novo](../assets/new.svg) [!DNL Live Search] agora, os clientes podem aproveitar o novo [Indexador de preços SaaS](../price-index/price-indexing.md).

### Widget do PLP

_31 de maio de 2024_

![Novo](../assets/new.svg) Lançada a versão 2.0.0 do widget PLP, que adiciona suporte para os seguintes recursos:

- Botões Adicionar ao carrinho - Disponível somente para produtos simples.
- Várias imagens por produto — a imagem pode mudar quando uma cor diferente é escolhida para um produto configurável.

_27 de outubro de 2023_

![Novo](../assets/new.svg) A variável [!DNL Live Search] O widget PLP agora é compatível com amostras de cores.


## [!DNL Live Search] 4.2.0 {#420}

_31 de maio de 2024_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Atualização da extensão do Live Search para usar widgets PLP versão 2.0.0.

## [!DNL Live Search] 4.1.2 {#412}

_16 de maio de 2024_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

### Atualizações

![Correção](../assets/fix.svg) Corrigido o [`productSearch`](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#filtering-by-categories) Consulta do GraphQL para filtrar corretamente com base na variável `categoryPath` e `categoryList` para categorias.

## [!DNL Live Search] 4.1.1 {#411}

_19 de março de 2024_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

### Novos recursos

![Novo](../assets/new.svg) Adição de suporte de idioma para polonês.
![Novo](../assets/new.svg) [!DNL Live Search] O agora suporta o PHP 8.3 para instalações que executam o Adobe Commerce 2.4.4.

## [!DNL Live Search] 4.1.0 {#410}

_22 de fevereiro de 2024_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

### Novos recursos

![Novo](../assets/new.svg) A variável [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard) O agora está disponível. Esse painel renovado fornece insights sobre fluxos de dados para [!DNL Product Recommendations], [!DNL Live Search], e [!DNL Catalog Service].

### Atualizações

![Correção](../assets/fix.svg) Correção de um problema que causava um erro quando usuários convidados adicionavam produtos a um carrinho em exibições de loja não padrão.
![Correção](../assets/fix.svg) Correção de um problema que fazia com que o popover de pesquisa sempre exibisse o símbolo de moeda na frente do valor do preço, independentemente das configurações de local.
![Correção](../assets/fix.svg) Remoção de definições de tipo desnecessárias para plug-ins principais desativados para corrigir problemas de compatibilidade na instalação.

## [!DNL Live Search] 4.0.0 {#400}

_13 de novembro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

### Novos recursos

![Novo](../assets/new.svg) [!DNL Live Search] O agora é compatível com amostras de cores no widget PLP.
![Novo](../assets/new.svg) [!DNL Live Search] O agora exibe o nome da categoria em vez da ID da categoria.
![Novo](../assets/new.svg) [!DNL Live Search] O agora suporta preços tachados no widget PLP.
![Novo](../assets/new.svg) Foi introduzido o botão &quot;Ocultar filtros&quot; para ocultar o painel de filtros.


### Atualizações

![Correção](../assets/fix.svg) A variável [!DNL Live Search] O widget PLP agora está habilitado por padrão para novas instalações.
![Correção](../assets/fix.svg) Estilos CSS reconfigurados para melhor isolar classes de widget.
![Correção](../assets/fix.svg) Correções de erros secundários

Após instalar a versão 3.1.1 ou superior, ative os novos indexadores:

- Feed de preços do produto
- Feed de dados do site de escopos
- Feed de dados dos grupos de clientes dos escopos

Depois da atualização, teste a configuração atualizada no controle de qualidade ou preparo antes de enviar as alterações para a produção.

## Versões anteriores

+++3.1.1 e anteriores

## [!DNL Live Search] 3.1.1 {#311}

_15 de setembro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) A guia Nova categoria de merchandising foi adicionada. Agora, os usuários podem adicionar Classificações inteligentes e Classificações manuais (fixar, impulsionar, enterrar, ocultar) por categoria
![Novo](../assets/new.svg) Os usuários podem adicionar uma única regra de categoria com classificação inteligente ou manual
![Novo](../assets/new.svg) Agora, os usuários podem adicionar regras de Classificação inteligente a subcategorias
![Novo](../assets/new.svg) Informações detalhadas são fornecidas ao excluir subcategorias com classificação inteligente
![Novo](../assets/new.svg) Adição da capacidade de excluir regras para estratégias de classificação herdadas
![Novo](../assets/new.svg) Adição da capacidade de excluir regras para uma única categoria
![Novo](../assets/new.svg) Agora os usuários podem pesquisar por nome de categoria ao adicionar uma regra
![Novo](../assets/new.svg) Com a Visualização em árvore de categorias, os usuários podem visualizar qual categoria tem regras aplicadas.
![Novo](../assets/new.svg) Visualização de categoria mostra apenas a categoria selecionada.
![Novo](../assets/new.svg) AEM CIF [Widget do Popover](https://github.com/adobe/aem-cif-guides-venia/pull/319) e [Widget do PLP](https://github.com/adobe/aem-cif-guides-venia/pull/320) Os componentes do permitem que os sites AEM aproveitem as [!DNL Live Search].

### Atualizações

![Correção](../assets/fix.svg) O tamanho da tabela dos feeds Produtos e Preço foi bastante reduzido. Tabelas `catalog_data_exporter_products` e `catalog_data_exporter_product_prices` redução substancial do tamanho.
![Correção](../assets/fix.svg) A guia &quot;Regras&quot; foi renomeada para &quot;Regras de pesquisa&quot;
![Correção](../assets/fix.svg) Ao classificar por &quot;tendência&quot;, agora é possível escolher entre: - 3 dias (padrão) - 14 dias - 30 dias
![Correção](../assets/fix.svg) &quot;Eventos&quot; (Aumentar/Fixar/Enterrar/Ocultar) foi renomeado para &quot;Classificação manual&quot;
![Correção](../assets/fix.svg) O &quot;Tipo de classificação&quot; foi renomeado para &quot;Classificação inteligente&quot;
![Correção](../assets/fix.svg) Correções de erros secundários

## [!DNL Live Search] 3.1.0 {#310}

_1 de setembro de 2023_

[!BADGE Compatível]{type="Informativo" tooltip="Compatível"}

### Atualizações

![Correção](../assets/fix.svg) O widget Lista de produtos foi atualizado para usar o [API do serviço de catálogo](https://developer.adobe.com/commerce/services/graphql/catalog-service/product-search/).

## [!DNL Live Search] 3.0.2 {#302}

_7 de agosto de 2023_

[!BADGE Compatível]{type="Informativo" tooltip="Compatível"}

### Novos recursos

![Novo](../assets/new.svg) Os seguintes valores foram adicionados ao `storeDetails` objeto:

- &quot;Permitir todos os produtos por página&quot;
- Taxa de câmbio
- &quot;Produtos por página em valores permitidos da grade&quot;
- &quot;Produtos por página no valor padrão da grade&quot;
- Idioma da loja

### Atualizações

![Correção](../assets/fix.svg) Os módulos do Serviço de catálogo foram adicionados ao metapackage para oferecer suporte à recuperação avançada de dados.
![Correção](../assets/fix.svg) A variável **Minha conta** a navegação da página não desaparece mais ao usar o widget Página de listagem de produtos.

Os comerciantes devem atualizar o [!DNL Live Search] versão da extensão do >= 3.0.2 para acessar esses recursos.

É recomendável atualizar e testar antes de enviar para a produção. Considere atualizar o ambiente de produção fora do horário de pico após verificar os resultados do ambiente de teste.

### Limitação

Usar o widget Página de listagem de produtos do Live Search causa falha no Google Tag Manager. Use o adaptador de pesquisa padrão se o Google Tag Manager for necessário.

## [!DNL Live Search] 3.0.1 {#301}

_14 de março de 2023_

[!BADGE Compatível]{type="Informativo" tooltip="Compatível"}

### Novos recursos

![Novo](../assets/new.svg) Cartão de item de produto na visualização de Regras
![Novo](../assets/new.svg) [Widget de página de listagem de produtos](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-storefront/plp-styling)
![Novo](../assets/new.svg) [Opções de filtragem de categoria](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/#facets)
![Novo](../assets/new.svg) Adição da capacidade de arrastar e soltar para criar eventos de Fixação
![Novo](../assets/new.svg) Novas ações de fixação: - Fixar no ponto - Botão Fixar para criar um evento Fixar com um clique - Fixar no início - Coloca o produto na primeira posição - Fixar no final - Coloca o produto na parte inferior dos resultados - Desafixar um evento com um clique
![Novo](../assets/new.svg) [Classificação inteligente para regras](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/live-search-admin/rules/rules-add)
![Novo](../assets/new.svg) [!DNL Live Search] O agora oferece suporte completo [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) no Commerce (antes conhecido como Inventário de várias origens, ou MSI). Para habilitar o suporte completo, você deve [atualizar](install.md#update) o módulo de dependência `commerce-data-export` para a versão 102.2.0+.

### Atualizações

![Correção](../assets/fix.svg) Configurar regras agora classifica automaticamente as posições de forma exclusiva
![Correção](../assets/fix.svg) A exclusão de um evento existente agora atualiza a visualização
![Correção](../assets/fix.svg) Regras sem eventos podem ser salvas
![Correção](../assets/fix.svg) Remover o seletor de facetas &quot;Selecionar tipo&quot;
![Correção](../assets/fix.svg) Adição de um novo status de &quot;Edição&quot; para regras não salvas

### Correções

![Correção](../assets/fix.svg) Correção de um erro de servidor quando há um evento não concluído durante o salvamento
![Correção](../assets/fix.svg) Correção da exclusão correta de um evento específico quando havia vários eventos
![Correção](../assets/fix.svg) Corrigido o evento de regra existente não atualizado quando um novo evento era adicionado
![Correção](../assets/fix.svg) Corrigido no segundo clique &quot;Editar&quot; nos detalhes, [!DNL Live Search] página que precisa ser recarregada
![Correção](../assets/fix.svg) Sinônimos: correção de um problema quando um usuário clicava fora da entrada, ele não podia retornar o foco para o campo
![Correção](../assets/fix.svg) Outras correções de pequenos erros e atualizações de desempenho


![Bug](../assets/bug.svg) - A classificação por &quot;Recomendado para você&quot; só é compatível com os widgets do Live Search. Não é compatível com a funcionalidade padrão de pesquisa Luma e PWA.
![Bug](../assets/bug.svg) - As facetas de atributos de preço personalizados não são renderizadas corretamente no Luma, mas a API as filtra corretamente.

Os comerciantes devem atualizar o [!DNL Live Search] versão da extensão do >= 3.0.1 para acessar esses recursos.

É recomendável atualizar e testar antes de enviar para a produção. Considere atualizar o ambiente de produção fora do horário de pico após verificar os resultados do ambiente de teste.

## [!DNL Live Search] 2.0.5 {#205}

[!BADGE Compatível]{type="Informativo" tooltip="Compatível"}

![Correção](../assets/fix.svg) - O Live Search geraria um erro quando os recursos do SDK não estivessem disponíveis devido a problemas de rede. Esse erro foi corrigido.

Os comerciantes devem atualizar a versão da extensão do Live Search >= 2.0.5 para acessar esses recursos.

É recomendável atualizar e testar antes de enviar para a produção. Considere atualizar o ambiente de produção fora do horário de pico após verificar os resultados do ambiente de teste.

### [!DNL Live Search] 2.0.4 {#204}

[!BADGE Compatível]{type="Informativo" tooltip="Compatível"}

![Novo](../assets/new.svg) O Live Search agora oferece suporte à filtragem pela configuração &quot;Exibir produtos sem estoque&quot; no administrador. Se &#39;Exibir produtos esgotados&#39; estiver definido como falso, `inStock = true` é adicionado ao filtro.
![Correção](../assets/fix.svg) Para melhorar o desempenho, o bloco &quot;Sugestões&quot; foi removido do pop-up do Live Search. Os dados ainda são transmitidos pelo GraphQL, caso você queira substituir o recurso.
![Correção](../assets/fix.svg) `categories` e `categoryPath` substituíram `categoryIds` para filtragem de categorias. Leia mais na seção [productSearch](https://developer.adobe.com/commerce/services/graphql/live-search/product-search/) tópico.
![Correção](../assets/fix.svg) Anteriormente, um usuário vinculado a uma empresa B2B recebia um código incorreto do grupo do cliente ao fazer pesquisas. O Live Search agora retorna o valor correto.
![Correção](../assets/fix.svg) Anteriormente, ao pesquisar um termo que não existe, o Live Search retornava um erro. Esse erro foi corrigido.

Os comerciantes devem atualizar o [!DNL Live Search] versão da extensão >= 2.0.4 para acessar esses recursos.

Os usuários são aconselhados a atualizar e testar antes de enviar para a produção. Considere atualizar o ambiente de produção fora do horário de pico após verificar os resultados do ambiente de teste.

### [!DNL Live Search] 2.0.3 {#203}

[!BADGE Compatível]{type="Informativo" tooltip="Compatível"}

![Novo](../assets/new.svg) O Live Search agora oferece suporte a recursos B2B, respeitando permissões de categoria, catálogos compartilhados e preços específicos do grupo de clientes.

Os comerciantes devem atualizar o [!DNL Live Search] versão da extensão >= 2.0.3 para acessar esses recursos.

Os usuários são aconselhados a atualizar e testar antes de enviar para a produção. Considere atualizar o ambiente de produção fora do horário de pico após verificar os resultados do ambiente de teste.

### [!DNL Live Search] 2.0 {#20}

[!BADGE Compatível]{type="Informativo" tooltip="Compatível"}

Existente [!DNL Live Search] as instalações devem ser atualizadas para [!DNL Live Search] 2.0.0 para aproveitar os seguintes novos recursos, correções e melhorias:

![Novo](../assets/new.svg) [!DNL Live Search] O agora suporta o PHP 8.1 para instalações que executam o Adobe Commerce 2.4.4.
![Novo](../assets/new.svg) A variável `Magento_ElasticsearchCatalogPermissionsGraphQl` O módulo é adicionado à lista de módulos que são desativados durante a instalação.
![Novo](../assets/new.svg) O número de linhas disponíveis na [[!DNL storefront popover]](overview.md) pode ser configurado no *Admin*.
![Novo](../assets/new.svg) Beta [PWA](https://developer.adobe.com/commerce/pwa-studio/) compatível com [!DNL Live Search].
![Novo](../assets/new.svg) A variável [!DNL Live Search] o processo de instalação é atualizado com alterações avançadas do processo.
![Correção](../assets/fix.svg) [Pesquisa avançada](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search) link removido do rodapé da loja.
![Bug](../assets/bug.svg) Os seguintes atributos de produto não são compatíveis com o [API do Commerce GraphQL](https://developer.adobe.com/commerce/services/graphql/live-search/) quando usado em relação à versão beta do PWA: `description`, `name`, `short_description`
![Bug](../assets/bug.svg) A versão beta do PWA para [!DNL Live Search] não suporta [manipulação de eventos](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/).

### [!DNL Live Search] 1.3.1 {#131}

[!BADGE Compatível]{type="Informativo" tooltip="Compatível"}

![Correção](../assets/fix.svg) [Atributo de preço personalizado](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/product-attributes/attributes-input-types) O não retorna mais um erro quando configurado como [faceta]({% link live-search/facets-add.md %}).
![Correção](../assets/fix.svg) Correção de um problema que causava a ocorrência de um erro quando não [símbolo de moeda](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration(optional)) (`data-currency-symbol`) está disponível.
![Correção](../assets/fix.svg) [[!DNL Storefront popover]](storefront-popover.md) O agora mostra o [Preço especial](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/products/pricing/product-price-special) (preço final mínimo) quando disponível.

### [!DNL Live Search] 1.3.0 {#130}

[!BADGE Compatível]{type="Informativo" tooltip="Compatível"}

![Novo](../assets/new.svg) [Desempenho](performance.md) o painel de relatórios fornece informações sobre os termos de pesquisa que os compradores usam.
![Novo](../assets/new.svg) [!DNL Live Search] [SDK de eventos da loja](https://developer.adobe.com/commerce/services/shared-services/storefront-events/sdk/) O fornece acesso a uma camada de dados comum com serviços e métricas de publicação e assinatura de eventos.
![Correção](../assets/fix.svg) A variável [[!DNL Storefront popover]](storefront-popover.md) tem um novo `active` classe para a `.search-autocomplete` container que controla a visibilidade.
![Correção](../assets/fix.svg) Na vitrine, o [Pesquisar termos](https://experienceleague.adobe.com/en/docs/commerce-admin/catalog/catalog/search/search-terms) o link do rodapé é removido e seu cache é desativado por [!DNL Live Search] instalações.
![Bug](../assets/bug.svg) O patch para o adaptador de Pesquisa manipula produtos duplicados.
![Bug](../assets/bug.svg) [!DNL Live Search] suporta [de uma única fonte](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/sources/sources-manage) locais de inventário (físico) com vários (virtuais) [estoques](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/stocks/stocks-manage). Agora, não há suporte para várias fontes de inventário.

### [!DNL Live Search] 1.2.0 {#120}

[!BADGE Compatível]{type="Informativo" tooltip="Compatível"}

![Novo](../assets/new.svg) [[!DNL Storefront popover]](storefront-popover.md) O exibe produtos sugeridos e imagens em miniatura dos principais resultados da pesquisa, à medida que os compradores digitam as consultas na caixa Pesquisar.
![Novo](../assets/new.svg) Commerce *Admin* a sessão permanece aberta durante longos períodos de inatividade do teclado
![Novo](../assets/new.svg) [!DNL Live Search] é ativado automaticamente após a integração
![Correção](../assets/fix.svg) O tempo de indexação inicial é inferior a uma hora
![Correção](../assets/fix.svg) Atualizações incrementais de produtos quase em tempo real (após a instalação e a configuração)
![Correção](../assets/fix.svg) Colunas classificáveis no editor de sinônimos
![Correção](../assets/fix.svg) [!DNL Live Search] O não gera mais um erro se os critérios de pesquisa contiverem valores vazios de ordem de classificação
![Correção](../assets/fix.svg) A filtragem de intervalo não é mais interrompida se os códigos de atributo contiverem cadeias de caracteres &quot;para&quot; ou &quot;de&quot;

### [!DNL Live Search] 1.1.0 {#110}

[!BADGE Compatível]{type="Informativo" tooltip="Compatível"}

![Bug](../assets/bug.svg) A variável [!DNL Live Search] o serviço oferece suporte somente ao [moeda de base](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/currency/currency-configuration) da instalação do Adobe Commerce.
![Bug](../assets/bug.svg) Ao adicionar uma faceta, o Feed de atributos do produto não é atualizado corretamente quando definido como `Update on Save`. Para evitar esse problema, acesse [Gerenciamento de índice](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) e definir o Feed de atributos do produto como `Update by Schedule`.
![Bug](../assets/bug.svg) [!DNL Live Search] os sinônimos são definidos por exibição de loja, mas atualmente são armazenados por site e identificados com uma combinação de `environmentId` e `storeViewCode`. Como resultado, todos os sites e exibições de armazenamento na instalação do Adobe Commerce compartilham sinônimos. O conjunto de sinônimos criado mais recentemente para a exibição de loja tem prioridade.
![Bug](../assets/bug.svg) Se um sinônimo contiver várias palavras, cada palavra será tratada como um sinônimo separado. Por exemplo, se você definir &quot;peça de tempo&quot; como um sinônimo de &quot;relógio&quot;, tanto &quot;tempo&quot; quanto &quot;peça&quot; serão tratados como sinônimos de relógio.

+++

## Documentação

Para saber mais:

- [Documentação do desenvolvedor do Adobe Commerce](https://developer.adobe.com/commerce/docs)
- [Guia do usuário do Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce)
- [[!DNL Live Search] no Marketplace](https://commercemarketplace.adobe.com/magento-live-search.html)
