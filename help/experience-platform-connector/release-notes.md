---
title: Notas de versão
description: As informações mais recentes do Adobe Experience Platform Connector da Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
source-git-commit: 735fd14fad22826b04320644e120d296de19a211
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 1%

---

# Notas de versão

Essas notas de versão contêm atualizações para o conector de Experience Platform e incluem:

* ![Novo](../assets/new.svg) - Novos recursos
* ![Correção](../assets/fix.svg) - Correções e melhorias
* ![Bug](../assets/bug.svg) - Problemas conhecidos

Para obter alterações de recursos e correções relacionadas às extensões usadas pelo conector de Experience Platform, consulte **Atualizações de serviço suportadas**.

Consulte [Próximas versões](https://experienceleague.adobe.com/docs/commerce-operations/release/schedule.html) para saber mais sobre os cronogramas de lançamento e suporte.

Consulte a documentação do desenvolvedor para [saiba mais sobre compatibilidade de produtos](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Atualizações de serviço suportadas

Essas notas de versão descrevem alterações de recursos e correções relacionadas às extensões usadas pelo conector do Experience Platform.

+++Atualizações de serviço suportadas

_30 de março de 2023_

* ![Novo](../assets/new.svg) - Adição de uma nova extensão chamada `data-services-b2b` que inclui [eventos da lista de requisições](events.md#b2b-events) para comerciantes B2B
* ![Novo](../assets/new.svg) - Adicionado o `uniqueIdentifier` campo para [pesquisa](events.md#search-events) eventos. Esse novo campo permite que os comerciantes façam referência cruzada de quais solicitações de pesquisa correspondem a quais respostas de pesquisa.

_12 de outubro de 2022_

* ![Novo](../assets/new.svg) - Adicionado dois [eventos storefront](events.md): `openCart` e `removeFromCart` para o SDK e o coletor de eventos de loja da Adobe Commerce
* ![Novo](../assets/new.svg) - Suporte adicionado para um [Loja AEM](overview.md#aem-support)

+++

## 2.2.0

_30 de março de 2023_

* ![Novo](../assets/new.svg) - Pacote do `commerce-data-export` e `saas-export` dependências com o `experience-platform-connector` extensão. Anteriormente, você tinha que instalar essas dependências separadamente. Essas dependências, juntamente com a configuração do comerciante, permitem o processamento no servidor de [eventos de back-office](events.md#back-office-events).
* ![Novo](../assets/new.svg) - Adição de um novo evento de back-office chamado [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_28 de fevereiro de 2023_

* ![Novo](../assets/new.svg) - Suporte adicionado para PHP 8.2 para todos os módulos de conector Experience Platform

## 2.1.0

_17 de janeiro de 2023_

* ![Novo](../assets/new.svg) - Atualização do [Admin do conector de Experience Platform](connect-data.md) assim, você pode especificar seu próprio SDK da Web da AEP (liga). Além disso, foi adicionada uma opção para comerciantes inscritos em nosso programa beta do back office para enviar [dados de evento de back-office](connect-data.md#data-collection) para a borda. Esses eventos contêm [informações do status do pedido](events.md#beta-order-status-events) sobre um pedido, como se um pedido fosse feito, cancelado, reembolsado ou enviado.
* ![Correção](../assets/fix.svg) Alterado para uso `identityMap` em vez de `personID` ao definir a identidade primária para quaisquer dados enviados para a borda.

## 2.0.1

_10 de novembro de 2022_

* ![Problema corrigido](../assets/fix.svg) - Agora, o contexto do Adobe Experience Platform é definido somente após o Coletor de eventos de vitrine e o SDK do evento de vitrine serem carregados com êxito.

## 2.0.0

_12 de outubro de 2022_

* ![Novo](../assets/new.svg) - Adição da capacidade de especificar seu próprio SDK da Web da AEP ao [conexão](connect-data.md) sua instância do Adobe Commerce para o Experience Platform
* ![Correção](../assets/fix.svg) - Requisito de escopo do conjunto de dados atualizado para que as IDs do conjunto de dados precisem ser escoadas para o site em vez de visualização de armazenamento

## 1.0.0

_9 de agosto de 2022_

* ![Novo](../assets/new.svg) - Versão de disponibilidade geral

## Documentação

Para saber mais:

* [Documentação do desenvolvedor do Adobe Commerce](https://devdocs.magento.com/)
* [Guia do usuário do Adobe Commerce](https://docs.magento.com/user-guide/)
