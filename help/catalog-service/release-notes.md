---
title: '[!DNL Catalog Service] Notas de versão'
description: As informações mais recentes da versão do [!DNL Catalog Service] para Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: 2767de477e274c1855d21d6e678cc6139ff4faa4
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%

---

# [!DNL Catalog Service] Notas de versão

Estas notas de versão descrevem as versões mais recentes da [!DNL Catalog Service] e incluem:

![Novo](../assets/new.svg) Novos recursos
![Correção](../assets/fix.svg) Correções e aprimoramentos
![Bug](../assets/bug.svg) Problemas conhecidos

## Versão principal atual

### Versão V1.5

Data de lançamento: 2023-3-6 Compatível com o Adobe Commerce (EE): 2.4.4+ Compatível com o Adobe Commerce para nuvem (ECE): 2.4.4+ Estabilidade: disponibilidade geral

![Novo](../assets/new.svg) Adicionado [`categories`](https://developer.adobe.com/commerce/webapi/graphql/schema/catalog-service/queries/categories/) funcionalidade do GraphQL.
![Correção](../assets/fix.svg) Melhor desempenho e escalabilidade da API.

### Versão V1.4

Data de lançamento: 2023-2-7 Compatível com o Adobe Commerce (EE): 2.4.x Compatível com o Adobe Commerce para nuvem (ECE): 2.4.x Estabilidade: disponibilidade geral

![Novo](../assets/new.svg) Metappackage do serviço de catálogo publicado para simplificar as etapas de instalação.
![Correção](../assets/fix.svg) Melhorias na escalabilidade e no desempenho da API.

#### Limitações conhecidas

Estes recursos ainda não são compatíveis:

* Pacote de produtos com preço fixo
* Nenhuma atualização é recebida quando as variantes são excluídas do catálogo.
* O tamanho máximo para a carga de atributos dinâmicos é de 9 MB.
* Preço de produto de grupo. Pode ser calculada com preços simples de produtos.
* Em uma matriz de imagens, somente a primeira imagem contém funções.
* Amostras de cores
* Carregamento da página de detalhes do produto por meio do URL do produto.

As seguintes limitações podem ser resolvidas usando a API Core GraphQL:

* Preço Mínimo Anunciado
* Nível de preços
* Produtos e cartões-presente baixáveis
* Categorias (`categories` e `categoryList`)

### Versão V1.3

Data de lançamento: 2023-1-17 Compatível com o Adobe Commerce (EE): 2.4.x Compatível com o Adobe Commerce para nuvem (ECE): 2.4.x Estabilidade: disponibilidade geral

![Novo](../assets/new.svg) Simplificação e melhoria da experiência de integração.
![Novo](../assets/new.svg) Novos pontos de extremidade de sandbox do cliente estão disponíveis para testes de pré-produção.
![Novo](../assets/new.svg) Suporte adicionado para produtos virtuais.
![Correção](../assets/fix.svg) Melhorias na escalabilidade e no desempenho da API.

### Versão V1.1

Data de lançamento: 2022-11-18 Compatível com o Adobe Commerce (EE): 2.4.x Compatível com o Adobe Commerce para Cloud (ECE): 2.4.x Estabilidade: disponibilidade geral

![Novo](../assets/new.svg) O Serviço de catálogo agora é compatível com o Adobe [API Mesh](https://developer.adobe.com/graphql-mesh-gateway/).
![Correção](../assets/fix.svg) Melhoramos a escalabilidade da API e o desempenho geral.

### Versão V1.0

Data de lançamento: 2022-10-04 Compatível com o Adobe Commerce (EE): 2.4.x Compatível com o Adobe Commerce para nuvem (ECE): 2.4.x Estabilidade: disponibilidade geral

![Novo](../assets/new.svg) Agora oferecem suporte a produtos agrupados.
![Novo](../assets/new.svg) Adição de substituições de visibilidade B2B. Agora os produtos podem ser pesquisados e adicionados ao carrinho para grupos específicos de clientes.
![Correção](../assets/fix.svg) O serviço agora está mais estável e melhorou o desempenho.

## Versões anteriores

+++Versões Beta

### Versão 0.3 - Beta+

Data de lançamento: 2022-09-12 Compatível com o Adobe Commerce (EE): 2.4.x Compatível com o Adobe Commerce para nuvem (ECE): 2.4.x Estabilidade: Beta

![Novo](../assets/new.svg) Suporte a imagens para variantes: as imagens do produto são retornadas com base nas opções selecionadas
![Novo](../assets/new.svg) Funções para suporte a preços: permite que somente membros de grupos de clientes específicos vejam o preço dos produtos
![Correção](../assets/fix.svg) Melhor estabilidade e desempenho do serviço
![Novo](../assets/new.svg) As atualizações são recebidas quando os produtos são excluídos do catálogo

### Versão Beta

Data de lançamento: 2022-08-09 Compatível com o Adobe Commerce (EE): 2.4.x Compatível com o Adobe Commerce para nuvem (ECE): 2.4.x Estabilidade: Beta

![Novo](../assets/new.svg) A variável `products` e `refineProduct` queries retornam os seguintes dados:

* Atributos de produto predefinidos (sistema).
* Atributos dinâmicos do produto e filtrá-los por função (página de exibição do produto/página da lista de produtos).
* Opções de produto.
* Imagens de produto e filtrá-las por função (PDP/PLP).
* Um preço específico para produtos simples e faixas de preço para produtos configuráveis.
* Preços de grupo e faixas de preços do cliente. Eles retornam um preço padrão de fallback para os compradores sem um grupo de clientes.
* Tipos de produto que usam preços específicos do cliente B2B.

+++