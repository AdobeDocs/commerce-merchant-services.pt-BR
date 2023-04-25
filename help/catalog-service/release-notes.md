---
title: '[!DNL Catalog Service] Notas de versão'
description: As últimas informações da versão para [!DNL Catalog Service] para Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: f310f840e286859070002ab0e23eda3787c89f36
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# [!DNL Catalog Service] Notas de versão

Essas notas de versão descrevem as versões mais recentes da [!DNL Catalog Service] e incluem:

![Novo](../assets/new.svg) Novos recursos
![Correção](../assets/fix.svg) Correções e melhorias
![Bug](../assets/bug.svg) Problemas conhecidos

## Versão principal atual

_25 de abril de 2023_

![Novo](../assets/new.svg) Os clientes do Serviço de catálogo agora podem aproveitar as vantagens do novo [Indexador de preço SaaS](../price-index/index.md).

### Versão V1.7

_12 de abril de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) O Serviço de catálogo agora limpa as variantes de produto excluídas.
![Correção](../assets/fix.svg) Escalabilidade da infraestrutura e melhorias de desempenho.

#### Limitações conhecidas

Esses recursos ainda não são compatíveis:

* Pacotes de produtos com preço fixo
* O tamanho máximo para a carga de atributos dinâmicos é de 9 MB.
* Preço do produto do grupo. Pode ser calculado com preços simples do produto.
* Em uma matriz de imagens, somente a primeira imagem contém funções.

As seguintes limitações podem ser solucionadas com o uso da malha da API e da API do GraphQL principal:

* Preço Mínimo Anunciado
* [Preços de camada](mesh.md)
* Produtos para download e cartões-presente

### Versão V1.6

_28 de março de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) Adição de amostras ao [`products`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/products/) query.
![Novo](../assets/new.svg) Adição da capacidade de obter `entityId` usar [Malha da API](mesh.md).

### Versão V1.5

_6 de março de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) Adicionado [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) Funcionalidade do GraphQL.
![Correção](../assets/fix.svg) Melhor desempenho e escalabilidade da API.

### Versão V1.4

_7 de fevereiro de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) Metapackage de serviço de catálogo publicado para simplificar as etapas de instalação.
![Correção](../assets/fix.svg) Melhorias na escalabilidade e no desempenho da API.

### Versão V1.3

_17 de janeiro de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) A experiência de integração foi simplificada e aprimorada.
![Novo](../assets/new.svg) Os novos endpoints de sandbox do cliente estão disponíveis para testes de pré-produção.
![Novo](../assets/new.svg) Suporte adicionado para produtos virtuais.
![Correção](../assets/fix.svg) Melhorias na escalabilidade e no desempenho da API.

### Versão V1.1

_18 de novembro de 2022_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) O Serviço de Catálogo agora oferece suporte ao Adobe [Malha da API](https://developer.adobe.com/graphql-mesh-gateway/).
![Correção](../assets/fix.svg) Melhoria na escalabilidade da API e no desempenho geral.

### Versão V1.0

_4 de outubro de 2022_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) Agora oferece suporte para produtos agrupados e agrupados.
![Novo](../assets/new.svg) Foram adicionadas substituições de visibilidade B2B. Os produtos agora podem ser pesquisados e adicionados ao carrinho para grupos específicos de clientes.
![Correção](../assets/fix.svg) O serviço agora é mais estável e tem desempenho aprimorado.

## Versões anteriores

+++Versões beta

### Versão 0.3 - Beta+

_12 de setembro de 2022_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) As imagens para variantes são compatíveis: as imagens do produto são retornadas com base nas opções selecionadas
![Novo](../assets/new.svg) Funções para suporte de preços: permitir que somente membros de grupos específicos de clientes vejam o preço dos produtos
![Correção](../assets/fix.svg) Melhor estabilidade e desempenho do serviço
![Novo](../assets/new.svg) As atualizações são recebidas quando os produtos são excluídos do catálogo

### Versão beta

_9 de agosto de 2022_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) O `products` e `refineProduct` as consultas retornam os seguintes dados:

* Atributos de produto predefinidos (do sistema).
* Atributos dinâmicos do produto e os filtre por função (página de exibição do produto/página de lista de produtos).
* Opções de produto.
* Imagens do produto e filtrá-las por função (PDP/PLP).
* Um preço específico para produtos simples e intervalos de preço para produtos configuráveis.
* Preços e intervalos de preços do grupo de clientes. Eles retornam um preço padrão de fallback para compradores sem um grupo de clientes.
* Tipos de produto que usam preços específicos de clientes B2B.

+++
