---
title: '[!DNL Catalog Service] Notas de versão'
description: As informações mais recentes da versão do [!DNL Catalog Service] para Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
feature: Services, Catalog Service, Release Notes
source-git-commit: 8b0640064168303f48b34af7bb3f1ce1f43b2470
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---

# [!DNL Catalog Service] Notas de versão

Estas notas de versão descrevem as versões mais recentes da [!DNL Catalog Service].
O suporte é fornecido para a versão principal atual lançada. As notas de versão para versões mais antigas são fornecidas para referência.
As atualizações incluem:

![Novo](../assets/new.svg) Novos recursos
![Correção](../assets/fix.svg) Correções e aprimoramentos
![Bug](../assets/bug.svg) Problemas conhecidos

## Versão principal atual

### Versão V1.18

_11 de abril de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Adição de suporte para PHP 8.3.

![Novo](../assets/new.svg) A variável [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) e [`refineProduct`](https://developer.adobe.com/commerce/services/graphql/catalog-service/refine-product/) as consultas agora retornam dados de opções personalizáveis para produtos simples e complexos.<!--DATA-5538-->

### Versão V1.17

_22 de fevereiro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) A variável [[!DNL Data Management Dashboard]](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-dashboard.html) O agora está disponível. Esse painel renovado fornece insights sobre fluxos de dados para [!DNL Product Recommendations], [!DNL Live Search], e [!DNL Catalog Service]. O suporte para esse recurso foi introduzido na v3.1.0 do `catalog-service` metapackage.

## Versões anteriores

+++ Versões anteriores

### Versão V1.16

_13 de fevereiro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Os vídeos de produtos agora são compatíveis com a API de serviço de catálogo.
![Correção](../assets/fix.svg) Agora há suporte para pacotes de produtos com preços fixos.
![Correção](../assets/fix.svg) As opções indisponíveis agora são mostradas no widget PDP.

#### Limitações conhecidas

Estes recursos ainda não são compatíveis:

* O tamanho máximo para a carga de atributos dinâmicos é de 9 MB.
* Preço de produto de grupo. Esse valor pode ser calculado com preços simples do produto.
* Em uma matriz de imagens, somente a primeira imagem contém funções.

As seguintes limitações podem ser resolvidas usando a API Mesh e a Core GraphQL API:

* Preço Mínimo Anunciado
* [Nível de preços](mesh.md)

### Versão V1.13

_12 de outubro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) O Serviço de catálogo oferece suporte ao `inStock` sinalizador para grades de produtos.
![Novo](../assets/new.svg) A variável `urlKey` e `externalId` Os campos foram adicionados ao esquema do GraphQL.
![Novo](../assets/new.svg) Produtos e cartões-presente baixáveis agora são compatíveis.

### Versão V1.12

_19 de setembro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) O Serviço de catálogo agora usa [Indexação de preços SaaS](../price-index/price-indexing.md).
![Correção](../assets/fix.svg) Esta versão contém correções de erros e melhorias no lado do serviço.

### Versão V1.11

_18 de julho de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) O Serviço de catálogo agora é compatível com o [`recommendations`](https://developer.adobe.com/commerce/services/graphql/recommendations/recommendations/) Consulta do GraphQL para Recommendations do produto.

### Versão V1.10

_27 de junho de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) A API do Serviço de catálogo agora é compatível com `related products`.

### Versão V1.7

_12 de abril de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) O Serviço de catálogo agora limpa as variantes de produtos excluídas.
![Correção](../assets/fix.svg) Aprimoramentos de desempenho e escalabilidade da infraestrutura.

### Versão V1.6

_28 de março de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Adição de amostras à [`products`](https://developer.adobe.com/commerce/services/graphql/catalog-service/products/) consulta.
![Novo](../assets/new.svg) Adicionada a capacidade de obter `entityId` usar [API Mesh](mesh.md).

### Versão V1.5

_6 de março de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Adicionado [`categories`](https://developer.adobe.com/commerce/services/graphql/schema/catalog-service/categories/) funcionalidade do GraphQL.
![Correção](../assets/fix.svg) Melhor desempenho e escalabilidade da API.

### Versão V1.4

_7 de fevereiro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Metappackage do serviço de catálogo publicado para simplificar as etapas de instalação.
![Correção](../assets/fix.svg) Melhorias na escalabilidade e no desempenho da API.

### Versão V1.3

_17 de janeiro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Simplificação e melhoria da experiência de integração.
![Novo](../assets/new.svg) Novos pontos de extremidade de sandbox do cliente estão disponíveis para testes de pré-produção.
![Novo](../assets/new.svg) Suporte adicionado para produtos virtuais.
![Correção](../assets/fix.svg) Melhorias na escalabilidade e no desempenho da API.

### Versão V1.1

_18 de novembro de 2022_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) O Serviço de catálogo agora é compatível com o Adobe [API Mesh](https://developer.adobe.com/graphql-mesh-gateway/).
![Correção](../assets/fix.svg) Melhor escalabilidade da API e desempenho geral.

### Versão V1.0

_4 de outubro de 2022_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Agora oferecem suporte a produtos agrupados.
![Novo](../assets/new.svg) Adição de substituições de visibilidade B2B. Agora os produtos podem ser pesquisados e adicionados ao carrinho para grupos específicos de clientes.
![Correção](../assets/fix.svg) O serviço agora está mais estável e melhorou o desempenho.

### Versão 0.3 - Beta+

_12 de setembro de 2022_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) Suporte a imagens para variantes: as imagens do produto são retornadas com base nas opções selecionadas
![Novo](../assets/new.svg) Funções para suporte a preços: permite que somente membros de grupos de clientes específicos vejam o preço dos produtos
![Correção](../assets/fix.svg) Melhor estabilidade e desempenho do serviço
![Novo](../assets/new.svg) As atualizações são recebidas quando os produtos são excluídos do catálogo

### Versão Beta

_9 de agosto de 2022_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) A variável `products` e `refineProduct` queries retornam os seguintes dados:

* Atributos de produto predefinidos (sistema).
* Atributos dinâmicos do produto e filtrá-los por função (página de exibição do produto/página da lista de produtos).
* Opções de produto.
* Imagens de produto e filtrá-las por função (PDP/PLP).
* Um preço específico para produtos simples e faixas de preço para produtos configuráveis.
* Preços de grupo e faixas de preços do cliente. Eles retornam um preço padrão de fallback para os compradores sem um grupo de clientes.
* Tipos de produto que usam preços específicos do cliente B2B.
