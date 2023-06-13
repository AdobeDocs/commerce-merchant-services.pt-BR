---
title: '"Configurações do Commerce e [!DNL Live Search] '''
description: Descreve as configurações do Adobe Commerce que [!DNL Live Search] pode ler.
exl-id: a4e9e2dd-e912-4ced-a44a-091ac5334e50
source-git-commit: c8303b11c7a274a3956a7336203aa34bd9d6a67f
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# [!DNL Live Search] e Configurações do Adobe Commerce

Há definições de configuração do Commerce que [!DNL Live Search] suporta. Este tópico lista esses valores de configuração.

## Valores de configuração compatíveis

| Definição da configuração de comércio | Suportado pelo Popover | Suportado pelo adaptador |
|---|---|---|
| Lojas > Configuração > Catálogo > Catálogo > Pesquisa no catálogo > Permitir todos os produtos por comprimento de página | Sim. Máximo de 500 produtos | Sim. Máximo de 500 produtos |
| Lojas > Configuração > Catálogo > Catálogo > Pesquisa no catálogo > Duração mínima da consulta | Sim | Sim |
| Lojas > Configuração > Catálogo > Catálogo > Pesquisa no catálogo > Produtos por página em valores permitidos da grade | Sim | Sim |
| Lojas > Configuração > Catálogo > Catálogo > Pesquisa no catálogo > Produtos por página no valor padrão da grade | Sim | Sim |
| Lojas > Configuração > Catálogo > Inventário > Exibir Produtos Sem Estoque | Sim com v2.0.4+ | Sim com v2.0.4+ |
| Lojas > Configuração > Moeda > Moeda de Exibição Padrão | Sim com 3.1.0+ | Sim com 3/1/0+ |
| Lojas > Configuração > Geral > Configuração de Moeda > Opções de Moeda > Moeda Base | Sim | Sim |

Os preços na Página de listagem de produtos do widget e Popover agora são convertidos para a Moeda de exibição padrão usando as Taxas de moeda configuradas

## Valores de configuração não suportados

[!DNL Live Search] O não pode ler todos os valores de configuração. Esta tabela lista os valores que podem ser de maior interesse para os desenvolvedores.

| Definição da configuração de comércio | Notas |
|---|---|
| Lojas > Configuração > Catálogo > Loja > Modo de lista | É renderizado corretamente, mas os eventos não são enviados para algumas interações de página |
| Lojas > Configuração > Catálogo > Catálogo > Pesquisa no catálogo > Duração máxima da consulta | Não implementado; os Serviços de Pesquisa aceitam até 255 caracteres |
| Configuração > Vendas > Imposto > Configurações De Exibição De Preço > Exibir Preços Do Produto No Catálogo |  |
