---
title: Adicionar sinônimos
description: Adicione sinônimos do Live Search para melhorar a resposta às solicitações de pesquisa.
exl-id: 6c277d88-cb22-4174-abda-6d6bb65fe3be
source-git-commit: 87e0500c623f9492d1722c21a2b47bf43d104829
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Adicionar sinônimos

Aumente a participação do cliente adicionando sua própria lista com curadoria de sinônimos do Live Search. [!DNL Live Search] O pode gerenciar até 200 sinônimos por `Data Space ID`.

![[!DNL Live Search] sinônimos](assets/synonym-workspace.png)

## Etapa 1: Adicionar um sinônimo

1. Em Admin, acesse **Marketing** > SEO &amp; Pesquisar > **[!DNL Live Search]**.
1. Para várias lojas, defina **Escopo** para [exibição de loja](https://docs.magento.com/user-guide/configuration/scope.html) onde as configurações de sinônimo se aplicam.
1. Clique no botão **Sinônimos** guia .
1. Clique no botão **Adicionar sinônimos** botão.

## Etapa 2: Definir o sinônimo por tipo

Siga as instruções para [tipo de sinônimo](synonyms-type.md) que você deseja criar.

### Sinônimo bidirecional

1. Aceite o padrão **Dois sentidos** opção.

   ![Adicionar sinônimo bidirecional](assets/synonym-add-two-way.png)


1. Insira o **Palavra-chave** termo ou frase a ser correspondida.
1. Insira o **Expansão** termo(s) que você deseja adicionar como sinônimos para a palavra-chave. Separe vários termos com uma vírgula.
Neste exemplo, a palavra-chave para correspondência é &quot;calças&quot; e o conjunto de termos de expansão é &quot;calças compridas, calças, fendas&quot;.

   ![Exemplo de sinônimo bidirecional](assets/synonym-add-two-way-example.png)

1. Ao concluir, clique em **Salvar**.
O conjunto de sinônimos aparece na lista com uma seta bidirecional entre cada termo que significa que os termos são intercambiáveis.

   ![Sinônimo bidirecional](assets/synonym-two-way.png)

### Sinônimo unidirecional

1. Clique no botão **Unidirecional** tipo de sinônimo.

   ![Adicionar sinônimo unidirecional](assets/synonym-add-one-way.png)

1. Insira o **Palavra-chave** e **Expansão** termo(s). Separe vários termos com uma vírgula.

   ![Exemplo de sinônimo unidirecional](assets/synonym-add-one-way-example.png)

   Neste exemplo, a palavra-chave é &quot;calças&quot; e os termos de expansão unidirecional &quot;capris, calças de comprimento de vitelo, empurradores de pedalar&quot; são cada um um um subconjunto de &quot;calças&quot;, mas com um significado específico.

1. Ao concluir, clique em **Salvar**.
O conjunto de sinônimos aparece na lista com uma seta unidirecional apontando dos termos de expansão para a palavra-chave para indicar que os termos são subconjuntos da palavra-chave. Um sinal de mais separa cada termo de expansão.

   ![Sinônimo unidirecional](assets/synonym-one-way.png)

## Etapa 3: Publicar alterações

1. Quando o(s) sinônimo(s) estiver(em) concluído(s), clique em **Publicar alterações**.
1. Aguarde até duas horas para que suas atualizações estejam disponíveis na loja.

![Publicar alterações](assets/synonym-publish.png)

## Descrições do campo

| Campo | Descrição |
|--- |--- |
| [Tipo](synonyms.md) | Determina se os sinônimos têm o mesmo significado da palavra-chave ou se são um subconjunto da palavra-chave. Opções:<br />Dois sentidos (padrão) - Termos que têm o mesmo significado que a palavra-chave e retornam os mesmos resultados de pesquisa<br />Unidirecional - Termos que são um subconjunto da palavra-chave. Os sinônimos unidirecionais retornam uma lista mais restrita de produtos específicos. |
| Palavra-chave | Uma palavra que geralmente é associada a uma seleção de produtos em seu catálogo. |
| Expansão | Termos adicionais que têm o mesmo significado ou o mesmo que a palavra-chave. |
