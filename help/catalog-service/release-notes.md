---
title: '[!DNL Catalog Service] Notas de versão'
description: As últimas informações da versão para [!DNL Catalog Service] para Adobe Commerce.
exl-id: 9bf8e3f7-5b74-4755-867e-ac1c5000ff33
source-git-commit: cfa0b505b0fb793bbc072f9f837551b7e67e9721
workflow-type: tm+mt
source-wordcount: '658'
ht-degree: 0%

---

# [!DNL Catalog Service] Notas de versão

Essas notas de versão descrevem as versões mais recentes da [!DNL Catalog Service] e incluem:

* ![Novo](../assets/new.svg) Novos recursos
* ![Correção](../assets/fix.svg) Correções e melhorias
* ![Bug](../assets/bug.svg) Problemas conhecidos

## Versão V1.3

Data de lançamento: 2023-1-17 Compatível com Adobe Commerce (EE): Compatível com 2.4.x com Adobe Commerce for Cloud (ECE): 2.4.x Estabilidade: Disponibilidade geral

![Novo](../assets/new.svg) A experiência de integração foi simplificada e aprimorada.
![Novo](../assets/new.svg) Os novos endpoints de sandbox do cliente estão disponíveis para testes de pré-produção.
![Novo](../assets/new.svg) Suporte adicionado para produtos virtuais.
![Correção](../assets/fix.svg) Melhorias na escalabilidade e no desempenho da API.

### Limitações conhecidas

Esses recursos ainda não são compatíveis:

* Pacotes de produtos com preço fixo
* Nenhuma atualização é recebida quando as variantes são excluídas do catálogo.
* O tamanho máximo para a carga de atributos dinâmicos é de 9 MB.
* Preço do produto do grupo. Pode ser calculado com preços simples do produto.
* Em uma matriz de imagens, somente a primeira imagem contém funções.
* Amostras de cores
* Carregando a Página de detalhes do produto pelo URL do produto.

As seguintes limitações podem ser solucionadas com o uso da API do GraphQL:

* Preço Mínimo Anunciado
* Preços de camada
* Produtos para download e cartões-presente
* Categorias (`categories` e `categoryList`)

## Versão V1.1

Data de lançamento: 2022-11-18 Compatível com Adobe Commerce (EE): Compatível com 2.4.x com Adobe Commerce for Cloud (ECE): 2.4.x Estabilidade: Disponibilidade geral

![Novo](../assets/new.svg) O Serviço de Catálogo agora oferece suporte ao Adobe [Malha da API](https://developer.adobe.com/graphql-mesh-gateway/).
![Correção](../assets/fix.svg) Melhoramos a escalabilidade da API e o desempenho geral.

### Limitações conhecidas

Esses recursos ainda não são compatíveis:

* Pacotes de produtos com preço fixo
* Nenhuma atualização é recebida quando as variantes são excluídas do catálogo.
* O tamanho máximo para a carga de atributos dinâmicos é de 9 MB.
* Preço do produto do grupo. Pode ser calculado com preços simples do produto.
* Em uma matriz de imagens, somente a primeira imagem contém funções.
* Amostras de cores
* Carregando a Página de detalhes do produto pelo URL do produto.

As seguintes limitações podem ser solucionadas com o uso da API do GraphQL:

* Preço Mínimo Anunciado
* Preços de camada
* Produtos para download e cartões-presente
* Categorias (`categories` e `categoryList`)

## Versão V1.0

Data de lançamento: 2022-10-04 Compatível com Adobe Commerce (EE): Compatível com 2.4.x com Adobe Commerce for Cloud (ECE): 2.4.x Estabilidade: Disponibilidade geral

![Novo](../assets/new.svg) Agora oferece suporte para produtos agrupados e agrupados.
![Novo](../assets/new.svg) Foram adicionadas substituições de visibilidade B2B. Os produtos agora podem ser pesquisados e adicionados ao carrinho para grupos específicos de clientes.
![Correção](../assets/fix.svg) O serviço agora é mais estável e tem desempenho aprimorado.

### Limitações conhecidas

Esses recursos ainda não são compatíveis:

* Preços de camada
* As atualizações não são recebidas quando as variantes são excluídas do catálogo
* O tamanho máximo para a carga dos atributos dinâmicos é &lt;9MB
* Preço fixo para produtos de pacote
* Preço total dos produtos agrupados
* Suporte para tipos de produtos virtuais, de download e de cartão-presente
* Preço Mínimo Anunciado (MAPA)

## Versão 0.3 - Beta+

Data de lançamento: 2022-09-12 Compatível com Adobe Commerce (EE): Compatível com 2.4.x com Adobe Commerce for Cloud (ECE): 2.4.x Estabilidade: Beta

![Novo](../assets/new.svg) As imagens para variantes são compatíveis: as imagens do produto são retornadas com base nas opções selecionadas
![Novo](../assets/new.svg) Funções para suporte de preços: permitir que somente membros de grupos específicos de clientes vejam o preço dos produtos
![Correção](../assets/fix.svg) Melhor estabilidade e desempenho do serviço
![Novo](../assets/new.svg) As atualizações são recebidas quando os produtos são excluídos do catálogo

### Limitações conhecidas

Esses recursos ainda não são compatíveis:

* Preços de camada
* Pacote e produtos agrupados
* Nenhuma atualização é recebida quando as variantes são excluídas do catálogo
* Substituições de visibilidade B2B: os produtos podem ser pesquisáveis ou adicionados ao carrinho para grupos específicos de clientes

## Versão beta

Data de lançamento: 2022-08-09 Compatível com Adobe Commerce (EE): Compatível com 2.4.x com Adobe Commerce for Cloud (ECE): 2.4.x Estabilidade: Beta

![Novo](../assets/new.svg) O `products` e `refineProduct` as consultas retornam os seguintes dados:

* Atributos de produto predefinidos (do sistema).
* Atributos dinâmicos do produto e os filtre por função (página de exibição do produto/página de lista de produtos).
* Opções de produto.
* Imagens do produto e filtrá-las por função (PDP/PLP).
* Um preço específico para produtos simples e intervalos de preço para produtos configuráveis.
* Preços e intervalos de preços do grupo de clientes. Eles retornam um preço padrão de fallback para compradores sem um grupo de clientes.
* Tipos de produto que usam preços específicos de clientes B2B.

### Limitações conhecidas

* Não há suporte para pacotes e produtos agrupados.
* Os preços de camada não são suportados.
* Em uma matriz de imagens, somente a primeira imagem contém funções.
* As imagens para variantes não são recuperadas.
* As atualizações não são recebidas quando os produtos ou variantes são excluídos do catálogo.
