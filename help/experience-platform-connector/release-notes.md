---
title: Notas de versão
description: As informações mais recentes da versão do Adobe Experience Platform Connector da Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: 24494546d6d21cf46e3cb9f0fdd503ec8007daf8
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 1%

---

# Notas de versão

Essas notas de versão contêm atualizações para o conector Experience Platform e incluem:

![Novo](../assets/new.svg) - Novos recursos
![Correção](../assets/fix.svg) - Correções e aprimoramentos
![Bug](../assets/bug.svg) - Problemas conhecidos

Para obter alterações e correções de recursos relacionados a extensões usadas pelo conector do Experience Platform, consulte **Atualizações de serviço compatíveis**.

Consulte [Versões futuras](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) para saber mais sobre as programações de lançamento e o suporte.

Consulte a documentação do desenvolvedor para [saiba quais versões do Commerce oferecem suporte a este módulo](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Atualizações de serviço compatíveis

Essas notas de versão descrevem alterações de recursos e correções relacionadas a extensões usadas pelo conector Experience Platform.

+++Atualizações de serviço com suporte

_10 de outubro de 2023_

![Novo](../assets/new.svg) - Adição de novos eventos de status de pedido: [Pedido Faturado](events.md#orderinvoiced), [Devolução do Item da Ordem Iniciada](events.md#orderitemsreturninitiated), e [Devolução do Item da Ordem Concluída](events.md#orderitemreturncompleted).
![Correção](../assets/fix.svg) - Correção de um problema em que as alterações na configuração de moeda não eram refletidas nos eventos após a atualização do cache.
![Correção](../assets/fix.svg) - Corrigido o erro quando a mensagem de confirmação de pedido não era exibida se o posicionamento assíncrono de pedido estivesse ativado.
![Novo](../assets/new.svg) - Adição de dados a [addToRequisitionList](events.md#addtorequisitionlist) evento para produtos simples na página de exibição Categoria.
![Correção](../assets/fix.svg) - Correção de um problema no `selectedOptions` dados no [addToRequisitionList](events.md#addtorequisitionlist) evento quando os produtos são adicionados na página Confirmação de pedido.
![Novo](../assets/new.svg) - Adição de dados do produto ao [addToRequisitionList](events.md#addtorequisitionlist) evento quando produtos são adicionados à lista de requisições a partir da página de exibição Categoria.
![Novo](../assets/new.svg) - Adicionado [addToRequisitionList](events.md#addtorequisitionlist) evento quando produtos configuráveis são adicionados à lista de requisições a partir da página Exibição do produto.
![Novo](../assets/new.svg) - Adicionado [addToRequisitionList](events.md#addtorequisitionlist) e [removeFromRequisitionList](events.md#removefromrequisitionlist) eventos quando a quantidade do produto é aumentada e/ou diminuída de uma lista de requisições.

_10 de junho de 2023_

![Correção](../assets/fix.svg) - Correção de um problema ao `orderId` não foi transmitido no contexto devido a prefixos no identificador de pedido do Commerce.
![Correção](../assets/fix.svg) - Configurações atualizadas da Política de segurança de conteúdo.

_30 de março de 2023_

![Novo](../assets/new.svg) - Uma nova extensão foi adicionada, chamada `data-services-b2b` que inclui [eventos da lista de requisições](events.md#b2b-events) para os comerciantes B2B.
![Novo](../assets/new.svg) - Adição da variável `uniqueIdentifier` campo para [pesquisa](events.md#search-events) eventos. Esse novo campo permite que os comerciantes façam referência cruzada de solicitações de pesquisa e respostas de pesquisa.

_12 de outubro de 2022_

![Novo](../assets/new.svg) - Adição de dois [eventos da loja](events.md), `openCart` e `removeFromCart`, para o SDK de eventos e o coletor da Adobe Commerce Storefront.
![Novo](../assets/new.svg) - Adição de suporte para um [Loja AEM](overview.md#aem-support).

+++

## 3.0.0

_10 de outubro de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

Esta é uma versão principal. [Editar](install.md#update-the-experience-platform-connector) arquivo composer.json raiz do seu projeto.

![Novo](../assets/new.svg) - Disponibilidade geral para [enviar ordem histórica](connect-data.md#send-historical-order-data) dados e status para o Experience Platform.
![Novo](../assets/new.svg) - Adição de suporte para OAuth 2.0 ao [configurar](connect-data.md#connect-commerce-data-to-adobe-experience-platform) o conector Experience Platform.
![Novo](../assets/new.svg) - Encerramento do suporte para Adobe Commerce 2.4.3.

## 2.3.0

_27 de junho de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) - Adição da capacidade de [desativar envio de eventos da loja](connect-data.md#data-collection) ao Experience Platform.
![Correção](../assets/fix.svg) - Configurações atualizadas da Política de segurança de conteúdo.
![Correção](../assets/fix.svg) - Correção do suporte para eventos de back office na versão 2.4.7 do Commerce.
![Novo](../assets/new.svg) - Adição de uma mensagem de notificação sobre a invalidação de cache ao salvar alterações no formulário Conector de Experience Platform.


## 3.0.0-beta1 (somente interno)

_13 de junho de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) - (Beta) Adição da capacidade de [enviar ordem histórica](connect-data.md#beta-send-historical-order-data) dados e status para o Experience Platform. Esse recurso está disponível somente para usuários beta. Você pode participar do beta enviando um email para o seguinte endereço: `dataconnection@adobe.com`.

## 2.2.0

_30 de março de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) - Empacotado o `commerce-data-export` e `saas-export` dependências com o `experience-platform-connector` extensão. Anteriormente, você tinha que instalar essas dependências separadamente. Essas dependências, juntamente com a configuração de comerciante, permitem o processamento do lado do servidor de [eventos de back office](events.md#back-office-events).
![Novo](../assets/new.svg) - Adição de um novo evento de back office chamado [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_28 de fevereiro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) - Adição de suporte ao PHP 8.2 para todas as extensões do conector Experience Platform.

## 2.1.0

_17 de janeiro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) - Atualização do [Administrador do conector Experience Platform](connect-data.md) para especificar seu próprio SDK da Web da AEP (liga).
![Correção](../assets/fix.svg) Alterado para uso `identityMap` em vez de `personID` ao definir a identidade principal para qualquer dado enviado para a borda.

## 2.0.1

_10 de novembro de 2022_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg) - Agora o contexto do Adobe Experience Platform é definido somente após o Coletor de eventos da loja e o SDK de eventos da loja serem carregados com êxito.

## 2.0.0

_12 de outubro de 2022_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) - Adição da capacidade de especificar seu próprio AEP Web SDK quando [conectando](connect-data.md) sua instância do Adobe Commerce para o Experience Platform.
![Correção](../assets/fix.svg) - Atualização do requisito de escopo de sequência de dados para que as IDs de sequência de dados devam ser enviadas ao site em vez de armazenadas.

## 1.0.0

_9 de agosto de 2022_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) - Versão de disponibilidade geral.
