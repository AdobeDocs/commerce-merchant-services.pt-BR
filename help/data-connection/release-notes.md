---
title: Notas de versão
description: As informações mais recentes da versão do [!DNL Data Connection] extensão do Adobe Commerce.
exl-id: 7636664b-488a-46f7-8d19-a9faac126aec
feature: Personalization, Integration, Release Notes
source-git-commit: a2d5e695b3f6491d051da77bfc0fb596f5411c92
workflow-type: tm+mt
source-wordcount: '877'
ht-degree: 0%

---

# Notas de versão

>[!IMPORTANT]
>
>O conector Experience Platform foi renomeado para [!DNL Data Connection].

Essas notas de versão contêm atualizações para o [!DNL Data Connection] e inclui:

![Novo](../assets/new.svg) - Novos recursos
![Correção](../assets/fix.svg) - Correções e aprimoramentos
![Bug](../assets/bug.svg) - Problemas conhecidos

Para obter alterações e correções de recursos relacionados a extensões usadas pelo [!DNL Data Connection] consulte **Atualizações de serviço compatíveis**.

Consulte [Versões futuras](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) para saber mais sobre as programações de lançamento e o suporte.

Consulte a documentação do desenvolvedor para [saiba quais versões do Commerce oferecem suporte a este módulo](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).

## Atualizações de serviço compatíveis

Essas notas de versão descrevem alterações de recursos e correções relacionadas a extensões usadas pelo [!DNL Data Connection] extensão.

+++Atualizações de serviço com suporte

_24 de janeiro de 2024_

![Novo](../assets/new.svg) - Atualização do `data-services-b2b` extensão para incluir um novo evento de requisição chamado [deleteRequisitionList](events.md#deleterequisitionlist) para os comerciantes B2B.

_16 de novembro de 2023_

![Correção](../assets/fix.svg) - Correção de um problema em que uma mensagem de erro era exibida incorretamente ao fazer um pedido com vários endereços de envio.
![Correção](../assets/fix.svg) - Correção de um problema no [productPageView](events.md#productpageview) evento em que a variável `productListItems.priceTotal` o campo event não convertia o preço após alternar a moeda na exibição da loja.
![Correção](../assets/fix.svg) - Correção de um problema no `productListItems` campo de evento em que o código de moeda não era atualizado quando o comerciante trocou a exibição da loja.

_10 de outubro de 2023_

![Novo](../assets/new.svg) - Adição de novos eventos de status de pedido: [Pedido Faturado](events-backoffice.md#orderinvoiced), [Devolução do Item da Ordem Iniciada](events-backoffice.md#orderitemsreturninitiated), e [Devolução do Item da Ordem Concluída](events-backoffice.md#orderitemreturncompleted).
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

![Novo](../assets/new.svg) - Uma extensão chamada `data-services-b2b` que inclui [eventos da lista de requisições](events.md#b2b-events) para os comerciantes B2B.
![Novo](../assets/new.svg) - Adição da variável `uniqueIdentifier` campo para [pesquisa](events.md#search-events) eventos. Esse novo campo permite que os comerciantes façam referência cruzada de solicitações de pesquisa e respostas de pesquisa.

_12 de outubro de 2022_

![Novo](../assets/new.svg) - Adição de dois [eventos da loja](events.md), `openCart` e `removeFromCart`, para o SDK de eventos e o coletor da Adobe Commerce Storefront.
![Novo](../assets/new.svg) - Adição de suporte para um [Loja AEM](overview.md#aem-support).

+++

## 3.1.2

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

_5 de junho de 2024_

![Correção](../assets/new.svg) - Correção de um problema em que o formato de data incorreto estava sendo usado ao iniciar um [sincronização histórica](connect-data.md#specify-order-history-date-range).
![Correção](../assets/new.svg) - Corrigiu um problema onde a variável [startCheckout](events.md#startcheckout) O evento não estava sendo enviado no Adobe Commerce 2.4.7.

## 3.1.1

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

_4 de abril de 2024_

![Novo](../assets/new.svg) - Adição de suporte para PHP 8.3 para todos [!DNL Data Connection] extensões.
![Novo](../assets/new.svg) - Adição de um artigo sobre como [integrar](mobile-sdk-epc.md) o SDK do Adobe Experience Platform Mobile com Commerce.

## 3.2.0-beta2

_4 de março de 2024_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) - Se você estiver participando do beta, verifique se `composer.json` O arquivo tem o seguinte no nível raiz: ` "minimum-stability": "beta"`. Além disso, adicione `composer require "magento/customers-connector: ^1.2.0"` para enviar perfis de clientes da sua instância do Commerce para o SaaS.
![Novo](../assets/new.svg) - Adição da capacidade de [adicionar atributos personalizados](update-xdm.md#update-schema-with-time-series-behavioral-and-back-office-event-data).
![Novo](../assets/new.svg) - Adição da capacidade de [coletar e enviar registros de perfil](connect-data.md#send-customer-profile-data) e dados para o Experience Platform.

## 3.1.0

_16 de novembro de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg) - O conector Experience Platform foi renomeado para [!DNL Data Connection].
![Correção](../assets/new.svg) - Adição da capacidade de registrar resposta de erro se o Adobe IMS não puder gerar o token de acesso.
![Correção](../assets/new.svg) - Adição de uma mensagem de notificação se você tentar sincronizar Pedidos históricos, mas não tiver especificado as credenciais da conta.

## 3.0.0

_10 de outubro de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

Esta é uma versão principal. [Editar](install.md#update-the-data-connection) arquivo composer.json raiz do seu projeto.

![Novo](../assets/new.svg) - Disponibilidade geral para [enviar ordem histórica](connect-data.md#send-historical-order-data) dados e status para o Experience Platform.
![Novo](../assets/new.svg) - Adição de suporte para OAuth 2.0 ao [configurar](connect-data.md#connect-commerce-data-to-adobe-experience-platform) o [!DNL Data Connection] extensão.
![Novo](../assets/new.svg) - Encerramento do suporte para Adobe Commerce 2.4.3.

## 2.3.0

_27 de junho de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) - Adição da capacidade de [desativar envio de eventos da loja](connect-data.md#data-collection) ao Experience Platform.
![Correção](../assets/fix.svg) - Configurações atualizadas da Política de segurança de conteúdo.
![Correção](../assets/fix.svg) - Correção do suporte para eventos de back office na versão 2.4.7 do Commerce.
![Novo](../assets/new.svg) - Adição de uma mensagem de notificação sobre a invalidação do cache ao salvar as alterações na [!DNL Data Connection] formulário de extensão.


## 3.0.0-beta1 (somente interno)

_13 de junho de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) - (Beta) Adição da capacidade de [enviar ordem histórica](connect-data.md#beta-send-historical-order-data) dados e status para o Experience Platform.

## 2.2.0

_30 de março de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) - Empacotado o `commerce-data-export` e `saas-export` dependências com o `experience-platform-connector` extensão. Anteriormente, você tinha que instalar essas dependências separadamente. Essas dependências, juntamente com a configuração de comerciante, permitem o processamento do lado do servidor de [eventos de back office](events-backoffice.md).
![Novo](../assets/new.svg) - Adição de um novo evento de back office chamado [`orderShipmentCompleted`](events-backoffice.md#ordershipmentcompleted).

## 2.1.1

_28 de fevereiro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) - Adição de suporte para PHP 8.2 para todos [!DNL Data Connection] extensões.

## 2.1.0

_17 de janeiro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg) - Atualização do [[!DNL Data Connection] administrador da extensão](connect-data.md) para especificar seu próprio SDK da Web da AEP (liga).
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
