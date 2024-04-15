---
title: '"Configurações do Commerce e [!DNL Live Search] '''
description: Descreve as configurações do Adobe Commerce que [!DNL Live Search] pode ler.
exl-id: a4e9e2dd-e912-4ced-a44a-091ac5334e50
features: Services, Search, Configuration
source-git-commit: d1cd70e66e616c052418c719f6da23b010a22241
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# [!DNL Live Search] e Configurações do Adobe Commerce

Há definições de configuração do Commerce que [!DNL Live Search] suporta. Este tópico lista esses valores de configuração.

## Valores de configuração compatíveis

| Definição da configuração do Commerce | Suportado pelo Popover | Suportado pelo adaptador |
|---|---|---|
| Lojas > Configuração > Catálogo > Catálogo > Pesquisa no catálogo > Permitir todos os produtos por duração da página | Sim. Máximo de 500 produtos | Sim. Máximo de 500 produtos |
| Lojas > Configuração > Catálogo > Catálogo > Pesquisa no catálogo > Duração mínima da consulta | Sim | Sim |
| Lojas > Configuração > Catálogo > Catálogo > Pesquisa no catálogo > Produtos por página em valores permitidos da grade | Sim | Sim |
| Lojas > Configuração > Catálogo > Catálogo > Pesquisa no catálogo > Produtos por página no valor padrão da grade | Sim. Máximo de 500 produtos | Sim. Máximo de 500 produtos |
| Lojas > Configuração > Catálogo > Inventário > Exibir Produtos Sem Estoque | Sim com v2.0.4+ | Sim com v2.0.4+ |
| Lojas > Configuração > Moeda > Moeda de Exibição Padrão | Sim com 3.1.0+ | Sim com 3.1.0+ |
| Lojas > Configuração > Geral > Configuração de Moeda > Opções de Moeda > Moeda Base | Sim | Sim |

Os preços na Página de listagem de produtos do widget e Popover agora são convertidos para a Moeda de exibição padrão usando as Taxas de moeda configuradas.

## Pesquisar termos

[!DNL Live Search] suporta [redirecionamentos de termo de pesquisa](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-terms.html) em implementações em que o Adobe Commerce lida com o roteamento: Luma e outros temas baseados em php.

## Valores de configuração não suportados

[!DNL Live Search] O não pode ler todos os valores de configuração. Esta tabela lista os valores que podem ser de maior interesse para os desenvolvedores.

| Definição da configuração do Commerce | Notas |
|---|---|
| Lojas > Configuração > Catálogo > Loja > Modo de lista | É renderizado corretamente, mas os eventos não são enviados para algumas interações de página |
| Lojas > Configuração > Catálogo > Catálogo > Pesquisa no catálogo > Duração máxima da consulta | Não implementado; os Serviços de Pesquisa aceitam até 255 caracteres |
| Configuração > Vendas > Imposto > Configurações De Exibição De Preço > Exibir Preços Do Produto No Catálogo |  |
| Lojas > Configuração > Catálogo > Loja > Lista de Produtos Classificar por | Não se aplica à [!DNL Live Search] [Widget da página de listagem de produtos](plp-styling.md) |
