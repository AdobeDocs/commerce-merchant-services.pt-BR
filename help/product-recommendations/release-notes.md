---
title: '[!DNL Product Recommendations] Notas de versão'
description: As informações mais recentes da versão do [!DNL Product Recommendations] do Adobe Commerce.
exl-id: 1758e688-d26f-45e7-818c-d4726338a6c3
feature: Services, Recommendations, Release Notes
source-git-commit: 316059288ace6ebaf3748a294d8fe7351fc63bbd
workflow-type: tm+mt
source-wordcount: '1315'
ht-degree: 0%

---

# [!DNL Product Recommendations] Notas de versão

As notas de versão contêm atualizações para o seguinte [!DNL Product Recommendations] módulos:

* [!DNL Product Recommendations] metapackage: `magento/product-recommendations`
* Suporte ao Page Builder no [!DNL Product Recommendations] (opcional) módulo: `magento/module-page-builder-product-recommendations`
* Suporte a tipo de recomendação de similaridade visual para [!DNL Product Recommendations] (opcional) módulo: `magento/module-visual-product-recommendations`

O suporte é fornecido para a versão principal atual lançada. As notas de versão para versões mais antigas são fornecidas para referência.
As notas de versão incluem:

![Novo](../assets/new.svg) Novos recursos
![Correção](../assets/fix.svg) Correções e aprimoramentos
![Bug](../assets/bug.svg) Problemas conhecidos

Consulte a documentação do desenvolvedor para [saiba mais sobre o suporte ao produto](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability).

## Atualizações do serviço hospedado

Essas notas descrevem atualizações que foram publicadas fora de uma versão com controle de versão ou melhorias no serviço hospedado.

+++Atualizações do serviço hospedado

_18 de julho de 2023_

![Novo](../assets/new.svg) [!DNL Product Recommendations] agora tem um GraphQL [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) consulta.

_25 de abril de 2023_

![Novo](../assets/new.svg) [!DNL Product Recommendations] os clientes agora podem aproveitar [Indexação de preços SaaS](../price-index/price-indexing.md).

+++

## Versão principal atual

### 6.0.2 do magento/product-recommendations

_9 de maio de 2024_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg) Correção de um problema em que clicar no botão **[!DNL Add to Cart]** em um produto simples em uma unidade Recommendations de produto redirecionava o comprador para a página inicial em vez de permanecer na página atual.

### Versões anteriores

### 6.0.1 do magento/product-recommendations

_19 de março de 2024_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Suporte ao PHP 8.3 adicionado.

### 6.0.0 do magento/product-recommendations

_22 de fevereiro de 2024_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) A variável [!DNL Catalog Sync Dashboard] agora é o [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard). Esse painel renovado fornece insights sobre fluxos de dados para [!DNL Product Recommendations], [!DNL Live Search], e [!DNL Catalog Service].
![Correção](../assets/fix.svg) Correção de um problema que causava erros de check-out do [!DNL Product Recommendations].

+++5.0.0 e anteriores

### 5.0.1 do magento/product-recommendations

_15 de setembro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Adição de novos módulos para oferecer suporte ao [Indexador de preços Saas](../price-index/price-indexing.md).
![Novo](../assets/new.svg) Foram adicionados novos módulos de exportação de dados para oferecer suporte à exportação de mais tipos de produtos, incluindo produtos empacotados e cartões-presente.
![Correção](../assets/fix.svg) O tamanho da tabela dos feeds Produtos e Preço foi bastante reduzido. Tabelas `catalog_data_exporter_products` e `catalog_data_exporter_product_prices` redução substancial do tamanho.

#### Limitações conhecidas

* A variável `websiteCode` o valor é retornado incorretamente se contiver um sublinhado (_).

### 5.0.0 do magento/product-recommendations

_20 de março de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Atualizado [!DNL Product Recommendations] para oferecer suporte ao Adobe Commerce 2.4.6.
![Novo](../assets/new.svg) Esta é uma versão principal. [Editar](install-configure.md#update) a raiz `composer.json` para o seu projeto.
![Novo](../assets/new.svg) [!DNL Product Recommendations] O agora oferece suporte completo [Inventory management](https://experienceleague.adobe.com/en/docs/commerce-admin/inventory/introduction) no Commerce (antes conhecido como Inventário de várias origens, ou MSI). Para habilitar o suporte completo, você deve [atualizar](install-configure.md#update) o módulo de dependência `commerce-data-export` para a versão 102.2.0+.

### 4.0.1 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg) Anteriormente, [!DNL Product Recommendations] mostraria um erro quando a moeda de exibição fosse alternada para uma moeda não padrão. A troca de moedas agora funciona corretamente.

### 4.0.0 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Adicionado [indicadores de disponibilidade](create.md) para ajudá-lo a visualizar o progresso do treinamento de cada tipo de recomendação.
![Novo](../assets/new.svg) Esta é uma versão principal. [Editar](install-configure.md#update) a raiz `composer.json` para o seu projeto. Esta versão também requer que você forneça duas chaves de API ao instalar e configurar [!DNL Product Recommendations]: [uma chave de produção e uma chave de sandbox](../landing/saas.md).

#### Limitações conhecidas

* A variável `websiteCode` o valor é retornado incorretamente se contiver um sublinhado (_).

### 3.3.7 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Suporte ao PHP 8.1 adicionado
![Novo](../assets/new.svg) Redimensionamento de imagem aprimorado para que o dimensionamento de imagens seja manipulado de forma mais consistente no modelo de exibição de referência

### 3.3.6 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Otimizado [!DNL Product Recommendations] metappackage listando explicitamente as dependências

### 3.3.5 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Adicionado [Suporte B2B](onboarding.md#b2bsupport) in [!DNL Product Recommendations]
![Novo](../assets/new.svg) Adição de novos feeds ao [sincronizar dados do catálogo](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) para os Serviços da Commerce por meio da linha de comando

### 3.3.3 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Adição de novo [tipos de recomendação](type.md): Conversão (exibição para carrinho), Conversão (exibição para compra) e Visualizado recentemente. Esses novos tipos de recomendações estão disponíveis no `magento/product-recommendations` módulos 3.2.2 e posteriores.
![Correção](../assets/fix.svg) Correção de um problema em que o WAF (Web Application Firewall) do Fastly bloqueava incorretamente um cookie
![Correção](../assets/fix.svg) Correção de um problema em que os produtos atribuídos ao Modo de exibição de loja não padrão não eram exibidos no _Visualização do produto Recommendations_ ao criar uma recomendação para essa Exibição de armazenamento específica
![Correção](../assets/fix.svg) Correção de um problema em que determinados nomes de unidade de recomendação no Page Builder impediam que a unidade de recomendação fosse exibida na loja

### 3.3.2 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg) Correção de uma dependência ausente para suporte B2B

### 3.3.1 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Adição de suporte para preços de grupo de clientes B2B. Ao definir um [filtro de preço](filters.md) em uma unidade de recomendação, os clientes B2B que estão conectados veem o conjunto de preços do grupo de clientes para os produtos exibidos.

### 3.3.0 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Adição de suporte para a Camada de dados de clientes Adobe para padronizar a coleta de dados comportamentais entre os recursos e serviços da Adobe Commerce. Consulte a [readme](https://github.com/adobe/commerce-events/blob/main/packages/storefront-events-collector/README.md) para saber mais.

### 3.2.6 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg) Correção de um erro modal de JavaScript
![Correção](../assets/fix.svg) Correção de um problema em que o WAF (Web Application Firewall) do Fastly bloqueava incorretamente um cookie

### 3.2.5 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Serviços de Magento renomeados para [Commerce Services](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) e melhor usabilidade no Administrador

### 3.2.4 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg) Correção do erro &quot;Não é possível recuperar dados de opções do produto configuráveis&quot; ao indexar atributos do produto

### 3.2.3 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg) Correção do erro &quot;Não é possível recuperar dados de opções do produto configuráveis&quot; durante a Sincronização do catálogo
![Correção](../assets/fix.svg) Correção de um problema em que o código da loja não estava sendo definido corretamente quando você ativou a configuração &quot;Adicionar código da loja à URL&quot;
![Correção](../assets/fix.svg) Detecção aprimorada de alterações na configuração do Painel de administração para garantir que essas alterações sejam refletidas nos dados de sincronização do catálogo

### 3.2.2 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Adicionada a capacidade de [visualizar resultados da recomendação](create.md) no momento da criação. Isso pode exigir que você atualize seu módulo para a versão mais recente.
![Novo](../assets/new.svg) Adicionada a capacidade de [monitorar e gerenciar](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) o processo de sincronização do catálogo do Administrador.
![Novo](../assets/new.svg) Adicionado [filtros](filters.md) para controlar quais produtos são exibidos nas recomendações.
![Novo](../assets/new.svg) Adição de [Semelhança visual](type.md#visualsim) tipo de recomendação.

### 1.2.1 do magento/module-page-builder-product-recommendations para o Page Builder

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Adição de suporte para a versão 3.2.0+ do `magento/product-recommendations` módulo

### 3.1.0 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Adicionada a capacidade de [ressincronizar](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/data-services/catalog-sync) seu catálogo para serviços SaaS por meio da linha de comando.
![Novo](../assets/new.svg) Suporte adicionado para prefixos de tabela de banco de dados
![Correção](../assets/fix.svg) Remoção do suporte ao PHP 7.1

### 3.0.8 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg) Correção de um problema em que os eventos eram enviados para coleta de dados antes do módulo ser configurado, causando tráfego inválido

### 3.0.6 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) **(Beta)** Inclui suporte para novos [Semelhança visual](type.md#visualsim) tipo de recomendação.

### 1.0.0 do magento/module-visual-product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) **(Beta)** [Semelhança visual](type.md#visualsim). Com o _Semelhança visual_ tipo de recomendação, é possível implantar uma unidade de recomendação na página de detalhes do produto que exibe produtos visualmente semelhantes ao produto que está sendo visualizado.

### 3.0.5 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg) Correção do erro &quot;Não é possível recuperar dados de opções do produto&quot; que poderia ocorrer durante a exportação do catálogo.
![Correção](../assets/fix.svg) O símbolo da moeda na variável _Receita_ coluna na _[!DNL Product Recommendations]_O painel agora reflete corretamente a moeda base configurada.

### 3.0.4 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg) Adição de suporte para o Adobe Commerce 2.4.0

### 3.0.3 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg) Implementação de símbolo aprimorada no modelo de loja

### 1.0.4 do magento/module-page-builder-product-recommendations para o Page Builder

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Adição do nome da Recomendação do produto ao editar o tipo de conteúdo do Page Builder

### 3.0.2 magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Adição de uma coluna de status na grade ao selecionar unidades de recomendação no Page Builder
![Correção](../assets/fix.svg) Correção de um problema com protocolos http/https incorretos em URLs de produtos e imagens

### 3.0.1 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

Esta é uma versão principal. [Editar](install-configure.md#update) arquivo composer.json raiz do seu projeto.

![Novo](../assets/new.svg) Buscar [!DNL Product Recommendations] em Espaços de dados SaaS alternativos. Isso permite usar [!DNL Product Recommendations] computados no ambiente do produto em outros ambientes que não sejam de produção. [Alternar espaços de dados SaaS](settings.md) descreve esse recurso.

![Correção](../assets/fix.svg) Correção de um problema em que o check-out era inibido para compradores que usavam o uBlock Origin
![Correção](../assets/fix.svg) Correção de um problema ao enviar eventos irrelevantes de adição ao carrinho

### 1.0.3 do magento/module-page-builder-product-recommendations para o Page Builder

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Suporte ao Page Builder. Com a integração do Page Builder, você pode colocar unidades de recomendação de maneira precisa e granular em qualquer local arbitrário no conteúdo criado pelo Page Builder. Também é possível estilizar os cabeçalhos e as próprias unidades de recomendação. Ir para [Page Builder](https://experienceleague.adobe.com/en/docs/commerce-admin/page-builder/add-content/recommendations) para obter mais informações.

### 2.0.0 do magento/product-recommendations

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Lançamento de disponibilidade geral!

+++

## Documentação

Para saber mais sobre [!DNL Product Recommendations] e [!DNL Product Recommendations] desenvolvimento:

* [Guia do usuário](overview.md)
* [Documentação do desenvolvedor](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/developer/development-overview)
