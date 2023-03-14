---
title: "Configurações de comércio e [!DNL Live Search] "
description: "Descreve as configurações do Adobe Commerce que [!DNL Live Search] posso ler."
source-git-commit: 10edbb6127405d45c06d4c8ffc89d92a6ca061c3
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# [!DNL Live Search] e Configurações do Adobe Commerce

Há definições de configuração do Commerce que [!DNL Live Search] suporta. Este tópico lista esses valores de configuração.

## Valores de configuração compatíveis

| Definição da configuração de comércio | Suportado pelo Popover | Suportado pelo adaptador |
|---|---|---|
| Lojas -> Configuração -> Catálogo -> Catálogo -> Pesquisa no catálogo -> Duração mínima da consulta | Sim | Sim |
| Lojas -> Configuração -> Catálogo -> Inventário -> Exibir produtos esgotados | Sim com v2.0.4+ | Sim com v2.0.4+ |
| Lojas -> Configuração -> Geral -> Configuração de Moeda -> Opções de Moeda -> Moeda Base | Sim | Sim |

## Valores de configuração não suportados

[!DNL Live Search] O não pode ler todos os valores de configuração. Esta tabela lista os valores que podem ser de maior interesse para os desenvolvedores.

| Definição da configuração de Magento | Notas |
|---|---|
| Lojas -> Configuração -> Catálogo -> Vitrine -> Modo de lista | É renderizado corretamente, mas os eventos não são enviados para algumas interações de página |
| Lojas -> Configuração -> Catálogo -> Loja -> Permitir todos os produtos por página | Não implementado; envia solicitação para o serviço de pesquisa sem tamanho de página e [!DNL Live Search] retorna um tamanho de página padrão de 20 |
| Lojas -> Configuração -> Catálogo -> Catálogo -> Pesquisa no catálogo -> Duração máxima da consulta | Não implementado; os Serviços de Pesquisa aceitam até 255 caracteres |
| Lojas -> Configuração -> Geral -> Configuração de Moeda -> Opções de Moeda -> Moeda de Exibição Padrão | Não implementado; [!DNL Live Search] tem acesso somente à moeda base |
| Configuração -> Vendas -> Imposto -> Configurações De Exibição De Preço -> Exibir Preços Do Produto No Catálogo |  |
