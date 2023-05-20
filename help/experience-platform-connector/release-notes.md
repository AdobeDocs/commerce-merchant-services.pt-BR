---
title: Notas de versão
description: As informações mais recentes da versão do Adobe Experience Platform Connector da Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
source-git-commit: 22823b662eefa953fcca6ae78f6c37ee8abff3d1
workflow-type: tm+mt
source-wordcount: '345'
ht-degree: 1%

---

# Notas de versão

Essas notas de versão contêm atualizações para o conector Experience Platform e incluem:

* ![Novo](../assets/new.svg) - Novos recursos
* ![Correção](../assets/fix.svg) - Correções e aprimoramentos
* ![Bug](../assets/bug.svg) - Problemas conhecidos

Para obter alterações e correções de recursos relacionados a extensões usadas pelo conector do Experience Platform, consulte **Atualizações de serviço compatíveis**.

Consulte [Versões futuras](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) para saber mais sobre as programações de lançamento e o suporte.

Consulte a documentação do desenvolvedor para [saiba mais sobre a compatibilidade do produto](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Atualizações de serviço compatíveis

Essas notas de versão descrevem alterações de recursos e correções relacionadas a extensões usadas pelo conector Experience Platform.

+++Atualizações de serviço com suporte

_30 de março de 2023_

* ![Novo](../assets/new.svg) - Uma nova extensão foi adicionada, chamada `data-services-b2b` que inclui [eventos da lista de requisições](events.md#b2b-events) para comerciantes B2B
* ![Novo](../assets/new.svg) - Adição da variável `uniqueIdentifier` campo para [pesquisa](events.md#search-events) eventos. Esse novo campo permite que os comerciantes façam referência cruzada de quais solicitações de pesquisa correspondem a quais respostas de pesquisa.

_12 de outubro de 2022_

* ![Novo](../assets/new.svg) - Adição de dois [eventos da loja](events.md): `openCart` e `removeFromCart` ao SDK de eventos e ao coletor da Adobe Commerce Storefront
* ![Novo](../assets/new.svg) - Adição de suporte para um [Loja AEM](overview.md#aem-support)

+++

## 2.2.0

_30 de março de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

* ![Novo](../assets/new.svg) - Empacotado o `commerce-data-export` e `saas-export` dependências com o `experience-platform-connector` extensão. Anteriormente, você tinha que instalar essas dependências separadamente. Essas dependências, juntamente com a configuração de comerciante, permitem o processamento do lado do servidor de [eventos de back office](events.md#back-office-events).
* ![Novo](../assets/new.svg) - Adição de um novo evento de back office chamado [`orderShipmentCompleted`](events.md#ordershipmentcompleted).

## 2.1.1

_28 de fevereiro de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

* ![Novo](../assets/new.svg) - Adição de suporte ao PHP 8.2 para todos os módulos de conector de Experience Platform

## 2.1.0

_17 de janeiro de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

* ![Novo](../assets/new.svg) - Atualização do [Administrador do conector Experience Platform](connect-data.md) para especificar seu próprio SDK da Web da AEP (liga).
* ![Correção](../assets/fix.svg) Alterado para uso `identityMap` em vez de `personID` ao definir a identidade principal para qualquer dado enviado para a borda.

## 2.0.1

_10 de novembro de 2022_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

* ![Problema corrigido](../assets/fix.svg) - Agora o contexto do Adobe Experience Platform é definido somente após o Coletor de eventos da loja e o SDK de eventos da loja serem carregados com êxito.

## 2.0.0

_12 de outubro de 2022_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

* ![Novo](../assets/new.svg) - Adição da capacidade de especificar seu próprio AEP Web SDK quando [conectando](connect-data.md) sua instância do Adobe Commerce para o Experience Platform
* ![Correção](../assets/fix.svg) - Atualização do requisito de escopo de sequência de dados para que as IDs de sequência de dados devam ser enviadas ao site em vez de armazenadas

## 1.0.0

_9 de agosto de 2022_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

* ![Novo](../assets/new.svg) - Versão de disponibilidade geral
