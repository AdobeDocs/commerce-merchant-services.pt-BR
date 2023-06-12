---
title: Eventos
description: Saiba quais dados cada evento captura.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 7b34b66d5fb199e75b321a7d7ff0f98a3a0dcf8b
workflow-type: tm+mt
source-wordcount: '4605'
ht-degree: 0%

---

# Eventos do conector Experience Platform

A tabela a seguir lista os eventos do Commerce disponíveis ao instalar a extensão do conector do Experience Platform. Os dados que esses eventos coletam são enviados para a borda do Adobe Experience Platform. Você também pode criar [eventos personalizados](custom-events.md) para coletar dados adicionais não fornecidos imediatamente.

Além dos dados coletados pelos eventos a seguir, você também obtém [outros dados](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) fornecido pelo Adobe Experience Platform Web SDK.

## Eventos da loja

Os eventos da loja coletam dados comportamentais anônimos dos compradores enquanto eles navegam pelo site. Você pode usar os dados que esses eventos coletam para criar promoções e campanhas direcionadas a um conjunto específico de compradores. Os dados de eventos da loja incluem apenas produtos simples e configuráveis.

>[!NOTE]
>
>Todos os eventos da loja incluem a variável [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) que inclui o endereço de email do comprador, quando disponível, e a ECID. Ao incluir esses dados de perfil em cada evento, não é necessário importar uma conta de usuário separada do Adobe Commerce.

### addToCart

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando um produto é adicionado ao carrinho ou quando a quantidade de um produto no carrinho é incrementada. | `commerce.productListAdds` |

#### Dados coletados de addToCart

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `productListAdds` | Indica se um produto foi adicionado a um carrinho de compras. Um valor de `1` indica que um produto foi adicionado. |
| `productListItems` | Uma variedade de produtos adicionados ao carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O preço total do item de linha do produto |
| `quantity` | O número de unidades de produto adicionadas ao carrinho |
| `discountAmount` | Indica o valor do desconto aplicado |
| `currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moeda do produto |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |
| `cartID` | A ID exclusiva que identifica o carrinho do cliente |

### openCart

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um novo carrinho é criado, ou seja, quando um produto é adicionado a um carrinho vazio. | `commerce.productListOpens` |

#### Dados coletados do openCart

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `productListOpens` | Indica se um carrinho foi criado. Um valor de `1` indica que um carrinho foi criado. |
| `productListItems` | Uma variedade de produtos adicionados ao carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O preço total do item de linha do produto |
| `quantity` | O número de unidades de produto adicionadas ao carrinho |
| `discountAmount` | Indica o valor do desconto aplicado |
| `currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moeda do produto |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |
| `cartID` | A ID exclusiva que identifica o carrinho do cliente |

### removeFromCart

| Descrição | Nome do evento XDM |
|---|---|
| Acionado sempre que um produto é removido ou sempre que a quantidade de um produto no carrinho é reduzida. | `commerce.productListRemovals` |

#### Dados coletados de removeFromCart

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `productListRemovals` | Indica se um produto foi removido do carrinho. Um valor de `1` indica que um produto foi removido do carrinho. |
| `productListItems` | Uma variedade de produtos removidos do carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O preço total do item de linha do produto |
| `quantity` | O número de unidades de produto removidas do carrinho |
| `discountAmount` | Indica o valor do desconto aplicado |
| `currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moeda do produto |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |
| `cartID` | A ID exclusiva que identifica o carrinho do cliente |

### shoppingCartView

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando qualquer página do carrinho é carregada. | `commerce.productListViews` |

#### Dados coletados de shoppingCartView

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `productListViews` | Indica se uma lista de produtos foi exibida |
| `productListItems` | Uma variedade de produtos no carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O preço total do item de linha do produto |
| `quantity` | O número de unidades de produto no carrinho |
| `discountAmount` | Indica o valor do desconto aplicado |
| `currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moeda do produto |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |
| `cartID` | A ID exclusiva que identifica o carrinho do cliente |

### pageView

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando qualquer página é carregada. | `web.webpagedetails.pageViews` |

#### Dados coletados de pageView

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `pageViews` | Indica se uma página foi carregada. A `value` de `1` indica que a página foi carregada. |

### productPageView

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando qualquer página de produto é carregada. | `commerce.productViews` |

#### Dados coletados de productPageView

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `productViews` | Indica se o produto foi visualizado |
| `productListItems` | Uma variedade de produtos no carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O preço total do item de linha do produto |
| `discountAmount` | Indica o valor do desconto aplicado |
| `currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moeda do produto |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |

### startCheckout

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando o comprador clica em um botão de check-out. | `commerce.checkouts` |

#### Dados coletados de startCheckout

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `checkouts` | Indica se uma ação ocorreu durante o processo de check-out |
| `productListItems` | Uma variedade de produtos no carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O preço total do item de linha do produto |
| `quantity` | O número de unidades de produto no carrinho |
| `discountAmount` | Indica o valor do desconto aplicado |
| `currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moeda do produto |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |
| `cartID` | A ID exclusiva que identifica o carrinho do cliente |

### completeCheckout

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando o comprador faz um pedido. | `commerce.order` |

#### Dados coletados de completeCheckout

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `purchases` | Indica se um pedido foi aceito |
| `order` | Contém informações sobre o pedido feito de um ou mais produtos |
| `purchaseID` | Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva. |
| `orderType` | Indica o tipo de pedido feito, como Check-out ou Compra instantânea |
| `payments` | A lista de pagamentos deste pedido |
| `currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado para este item de pagamento. Por exemplo, `USD` ou `EUR`. |
| `paymentAmount` | O valor do pagamento |
| `paymentType` | O método de pagamento deste pedido. As opções são: `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other` |
| `transactionID` | O identificador de transação exclusivo para este item de pagamento |
| `shipping` | Detalhes de remessa de um ou mais produtos. |
| `shippingMethod` | O método de entrega escolhido pelo cliente, como entrega padrão, entrega expressa, retirada na loja etc. |
| `shippingAmount` | O custo total de envio dos itens no carrinho |
| `promotionID` | Identificador exclusivo da promoção, se houver |
| `personalEmail` | Especifica o endereço de email pessoal |
| `address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes |
| `productListItems` | Uma variedade de produtos no carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O preço total do item de linha do produto |
| `quantity` | O número de unidades de produto no carrinho |
| `discountAmount` | Indica o valor do desconto aplicado |
| `currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado para os totais do pedido. |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |

## Eventos de perfil

Os eventos de perfil incluem informações de conta, como `signIn`, `signOut`, `createAccount`, e `editAccount`. Esses dados são usados para ajudar a preencher os principais detalhes do cliente necessários para definir melhor os segmentos ou executar campanhas de marketing, como se você deseja direcionar os compradores que vivem em Nova York.

### signIn

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando um comprador tenta entrar. | `userAccount.login` |

>[!NOTE]
>
> Esse evento é acionado quando uma ação específica é tentada. Não indica que a ação tenha sido julgada procedente.

#### Dados coletados do logon

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `person` | Um ator, contato ou proprietário individual |
| `accountID` | Registra a ID da conta do usuário |
| `accountType` | Registra o tipo de conta do usuário, como `Personal` ou `Company`, se aplicável |
| `personalEmailID` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes |
| `personalEmail` | Captura detalhes de contato - um email e informações associadas |
| `address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes |
| `userAccount` | Indica detalhes de fidelidade, preferências, processos de logon e outras preferências de conta |
| `login` | Indica se um visitante tentou fazer logon |

### signOut

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando um comprador tenta sair. | `userAccount.logout` |

>[!NOTE]
>
> Esse evento é acionado quando uma ação específica é tentada. Não indica que a ação tenha sido julgada procedente.

#### Dados coletados da saída

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `userAccount` | Indica detalhes de fidelidade, preferências, processos de logon e outras preferências de conta |
| `logout` | Indica se um visitante tentou fazer logoff |

### createAccount

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um comprador tenta criar uma conta. | `userAccount.createProfile` |

>[!NOTE]
>
> Esse evento é acionado quando uma ação específica é tentada. Não indica que a ação tenha sido julgada procedente.

#### Dados coletados de createAccount

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `person` | Um ator, contato ou proprietário individual |
| `accountID` | Registra a ID da conta do usuário |
| `accountType` | Registra o tipo de conta do usuário, como `Personal` ou `Company`, se aplicável |
| `personalEmailID` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes |
| `personalEmail` | Captura detalhes de contato - um email e informações associadas |
| `address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes |
| `userAccount` | Indica detalhes de fidelidade, preferências, processos de logon e outras preferências de conta |
| `createProfile` | Indica se um usuário criou um perfil de conta |

### editAccount

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um comprador tenta editar uma conta. | `userAccount.updateProfile` |

>[!NOTE]
>
> Esse evento é acionado quando uma ação específica é tentada. Não indica que a ação tenha sido julgada procedente.

#### Dados coletados de editAccount

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `person` | Um ator, contato ou proprietário individual |
| `accountID` | Registra a ID da conta do usuário |
| `accountType` | Registra o tipo de conta do usuário, como `Personal` ou `Company`, se aplicável |
| `personalEmailID` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes |
| `personalEmail` | Captura detalhes de contato - um email e informações associadas |
| `address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes |
| `userAccount` | Indica detalhes de fidelidade, preferências, processos de logon e outras preferências de conta |
| `updateProfile` | Indica se um usuário atualizou seu perfil de conta |

## Pesquisar eventos

Os eventos de pesquisa fornecem dados relevantes para a intenção do comprador. O insight sobre a intenção do comprador ajuda os comerciantes a ver como eles estão procurando por itens, em que clicam e, em última análise, compram ou abandonam os produtos. Um exemplo de como você pode usar esses dados é se quiser direcionar os compradores existentes que pesquisam pelo seu produto principal, mas nunca compram o produto.

Use o `uniqueIdentifier` campo encontrado em ambos os `searchRequestSent` e `searchResponseReceived` eventos para fazer referência cruzada de uma solicitação de pesquisa com a resposta de pesquisa correspondente.

### searchRequestSent

| Descrição | Nome do evento XDM |
|---|---|
| Acionado pelos seguintes eventos no popover &quot;pesquisar ao digitar&quot;:<br><br>Pressione Enter E Clique _Exibir todos_<br><br> Acionado pelos seguintes eventos nas páginas de resultados da pesquisa:<br><br>Selecione um filtro e Altere a ordem de classificação (_Classificar por_), Alterar a direção da classificação (crescente ou decrescente), Alterar o número de resultados por página (_Mostrar # por página_), Navegar até a próxima página, Navegar até a página anterior, Navegar até uma página diferente | `searchRequest` |

>[!NOTE]
>
>Os eventos de pesquisa não são compatíveis em um Adobe Commerce Enterprise Edition com o módulo B2B instalado.

#### Dados coletados de searchRequestSent

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `searchRequest` | Indica se uma solicitação de pesquisa foi enviada |
| `id` | O identificador exclusivo para esta solicitação de pesquisa específica |
| `filter` | Indica se algum filtro foi aplicado para limitar os resultados da pesquisa |
| `attribute` (filtro) | A faceta de um item usada para determinar se ele deve ser incluído nos resultados da pesquisa |
| `value` | Valores de atributo usados para determinar quais itens são incluídos nos resultados da pesquisa |
| `isRange` | Quando verdadeiro, os valores indicam pontos de extremidade de um intervalo aceitável de valores |
| `sort` | Indica como os resultados da pesquisa devem ser classificados |
| `attribute` (classificar) | Um atributo usado para classificar itens nos resultados da pesquisa |
| `order` | A ordem na qual retornar os resultados da pesquisa |
| `query` | Os termos procurados |

### searchResponseReceived

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando o Live Search retorna resultados para o pop-over &quot;pesquisar ao digitar&quot; ou para a página de resultados da pesquisa. | `searchResponse` |

>[!NOTE]
>
>Os eventos de pesquisa não são compatíveis em um Adobe Commerce Enterprise Edition com o módulo B2B instalado.

#### Dados coletados de searchResponseReceived

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `searchResponse` | Indica se uma resposta de pesquisa foi recebida |
| `id` | O identificador exclusivo para esta resposta de pesquisa específica |
| `suggestions` | Uma matriz de strings que inclui os nomes de produtos e categorias existentes no catálogo semelhantes à consulta de pesquisa |
| `numberOfResults` | O número de produtos devolvidos |
| `productListItems` | Uma variedade de produtos no carrinho de compras. |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `productImageUrl` | URL da imagem principal do produto |

## Eventos B2B

![B2B para Adobe Commerce](../assets/b2b.svg) Para comerciantes B2B, você deve [instalar](install.md#install-the-b2b-extension) o `experience-platform-connector-b2b` para habilitar esses eventos.

Os eventos B2B contêm [lista de requisições](https://experienceleague.adobe.com/docs/commerce-admin/b2b/requisition-lists/requisition-lists.html) informações, como se uma lista de requisições tivesse sido criada, adicionada ou deletada. Ao rastrear eventos específicos para listas de requisição, você pode ver quais produtos seus clientes compram frequentemente e criar campanhas com base nesses dados.

### createRequisitionList

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um comprador cria uma nova lista de requisições. | `commerce.requisitionListOpens` |

#### Dados coletados de createRequisitionList

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `requisitionList` | As propriedades da lista de requisições criadas pelo cliente |
| `ID` | Identificador exclusivo da lista de requisições |
| `name` | Nome da lista de requisições especificada pelo cliente |
| `description` | Descrição da lista de requisições especificada pelo cliente |

### addToRequisitionList

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando um comprador adiciona um produto a uma lista de requisições existente ou ao criar uma nova lista. | `commerce.requisitionListAdds` |

>[!NOTE]
>
>`addToRequisitionList` O não é compatível com páginas de exibição de categoria ou produtos configuráveis. Ele é compatível com as páginas de exibição de produtos e para produtos simples.

#### Dados coletados de addToRequisitionList

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `requisitionList` | As propriedades da lista de requisições criadas pelo cliente |
| `ID` | Identificador exclusivo da lista de requisições |
| `name` | Nome da lista de requisições especificada pelo cliente |
| `description` | Descrição da lista de requisições especificada pelo cliente |
| `productListItems` | Uma matriz de produtos que foram adicionados à lista de requisições |
| `name` | O nome de exibição ou nome legível do produto |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `quantity` | O número de unidades de produto adicionadas |
| `priceTotal` | O preço total do item de linha do produto |
| `discountAmount` | Indica o valor do desconto aplicado |
| `currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado para este item de pagamento |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |

### removeFromRequisitionList

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um comprador remove um produto de uma lista de requisições. | `commerce.requisitionListRemovals` |

#### Dados coletados de removeFromRequisitionList

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `requisitionList` | As propriedades da lista de requisições criadas pelo cliente |
| `ID` | Identificador exclusivo da lista de requisições |
| `name` | Nome da lista de requisições especificada pelo cliente |
| `description` | Descrição da lista de requisições especificada pelo cliente |
| `productListItems` | Uma matriz de produtos que foram adicionados à lista de requisições |
| `name` | O nome de exibição ou nome legível do produto |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `quantity` | O número de unidades de produto adicionadas |
| `priceTotal` | O preço total do item de linha do produto |
| `discountAmount` | Indica o valor do desconto aplicado |
| `currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado para este item de pagamento |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |

## Eventos de back office

Os eventos de back office contêm informações sobre o status de um pedido, como se um pedido foi feito, cancelado, reembolsado, remetido ou concluído. Os dados coletados por esses eventos do lado do servidor mostram uma visualização 360 do pedido do comprador. Essa visualização ajuda os comerciantes a direcionar ou analisar melhor todo o status do pedido ao desenvolver campanhas de marketing. Por exemplo, você pode detectar tendências em determinadas categorias de produtos que apresentam um bom desempenho em diferentes épocas do ano. Tais como roupas de inverno que vendem melhor durante os meses mais frios ou certas cores do produto que os compradores estão interessados ao longo dos anos. Além disso, os dados de status do pedido podem ajudar você a calcular o valor vitalício do cliente, entendendo a propensão do comprador para converter com base em pedidos anteriores.

>[!NOTE]
>
>Todos os eventos de back office incluem o [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) que fornece o endereço de email do comprador. Ao incluir esses dados de perfil em cada evento, não é necessário importar uma conta de usuário separada do Adobe Commerce.

### orderPlaced

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando um comprador faz um pedido. | `commerce.backofficeOrderPlaced` |

#### Dados coletados de orderPlaced

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes |
| `productListItems` | Uma variedade de produtos no pedido |
| `id` | O identificador de item de linha para esta entrada de produto. O produto em si é identificado através da `product` campo. |
| `name` | O nome de exibição ou nome legível do produto |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `quantity` | O número de unidades de produto no carrinho |
| `priceTotal` | O preço total do item de linha do produto |
| `discountAmount` | Indica o valor do desconto aplicado |
| `order` | Contém informações sobre o pedido |
| `purchaseID` | Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva |
| `priceTotal` | O preço total deste pedido após a aplicação de todos os descontos e impostos |
| `currencyCode` | O código de moeda ISO 4217 usado para os totais do pedido |
| `purchaseOrderNumber` | Identificador exclusivo atribuído pelo comprador para esta compra ou contrato |
| `payments` | A lista de pagamentos deste pedido |
| `paymentType` | O método de pagamento deste pedido. Valores personalizados enumerados são permitidos. |
| `currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado para este item de pagamento |
| `paymentAmount` | O valor do pagamento |
| `taxAmount` | O valor do imposto pago pelo comprador como parte do pagamento final |
| `createdDate` | A hora e a data em que um novo pedido é criado no sistema de comércio. Por exemplo, `2022-10-15T20:20:39+00:00` |
| `shipping` | Detalhes de remessa de um ou mais produtos |
| `shippingMethod` | O método de entrega escolhido pelo cliente, como entrega padrão, entrega expressa, retirada na loja etc. |
| `shippingAmount` | O valor que o cliente teve de pagar pelo envio. |
| `address` | Endereço de entrega físico |
| `street1` | Informações no nível da rua principal, número do apartamento, número da rua e nome da rua |
| `street2` | Campo adicional para informações no nível da rua |
| `city` | O nome da cidade |
| `state` | O nome do estado. Este é um campo de forma livre. |
| `postalCode` | O código postal da localização. Os códigos postais não estão disponíveis para todos os países. Em alguns países, conterá apenas parte do código postal. |
| `country` | O nome do território administrado pelo governo. Exceto `xdm:countryCode`, este é um campo de formato livre que pode ter o nome do país em qualquer idioma. |
| `billingAddress` | Endereço postal de cobrança |
| `street1` | Informações no nível da rua principal, número do apartamento, número da rua e nome da rua |
| `street2` | Campo adicional para informações no nível da rua |
| `city` | O nome da cidade |
| `state` | O nome do estado. Este é um campo de forma livre. |
| `postalCode` | O código postal da localização. Os códigos postais não estão disponíveis para todos os países. Em alguns países, conterá apenas parte do código postal. |
| `country` | O nome do território administrado pelo governo. Exceto `xdm:countryCode`, este é um campo de formato livre que pode ter o nome do país em qualquer idioma. |
| `personalEmail` | Um endereço de email pessoal |
| `address` | O endereço técnico, por exemplo, &quot;name@domain.com&quot;, conforme geralmente definido em RFC2822 e padrões subsequentes |

### orderItemsShipped

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um pedido é enviado. | `commerce.backofficeOrderItemsShipped` |

#### Dados coletados de orderItemsShipped

A tabela a seguir descreve os dados coletados para esse evento.
|Campo|Descrição| |—|—| |`address`|O endereço técnico, por exemplo, `name@domain.com` conforme geralmente definido em RFC2822 e padrões subsequentes| |`productListItems`|Uma variedade de produtos na ordem| |`id`|O identificador de item de linha para esta entrada de produto. O produto em si é identificado através da `product` campo.| |`name`|O nome de exibição ou o nome legível do produto| |`SKU`|Unidade De Manutenção De Estoque. O identificador exclusivo do produto.| |`quantity`|O número de unidades de produto no carrinho| |`priceTotal`|O preço total do item de linha do produto| |`discountAmount`|Indica o valor do desconto aplicado| |`order`|Contém informações sobre o pedido| |`purchaseID`|Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva| |`priceTotal`|O preço total deste pedido após a aplicação de todos os descontos e impostos| |`currencyCode`|O código de moeda ISO 4217 usado para os totais do pedido| |`purchaseOrderNumber`|Identificador exclusivo atribuído pelo comprador para esta compra ou contrato| |`payments`|A lista de pagamentos deste pedido| |`paymentType`|O método de pagamento deste pedido. Valores personalizados enumerados são permitidos.| |`currencyCode`|A [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado para este item de pagamento| |`paymentAmount`|O valor do pagamento| |`lastUpdatedDate`|A hora em que um determinado registro de pedido foi atualizado pela última vez no sistema de comércio| |`shipping`|Detalhes de remessa de um ou mais produtos| |`shippingMethod`|O método de entrega escolhido pelo cliente, como entrega padrão, entrega expressa, retirada na loja e assim por diante| |`trackingNumber`|O número de rastreamento fornecido pela transportadora para uma remessa de item de pedido| |`trackingURL`|O URL para rastrear o status de envio de um item do pedido| |`shipDate`|A data em que um ou mais itens de uma ordem são remetidos| |`address`|Endereço físico de entrega| |`street1`|Informações no nível da rua principal, número do apartamento, número da rua e nome da rua| |`street2`|Campo adicional para informações no nível da rua| |`city`|O nome da cidade| |`state`|O nome do estado. Este é um campo de forma livre.| |`postalCode`|O código postal da localização. Os códigos postais não estão disponíveis para todos os países. Em alguns países, conterá apenas parte do código postal.| |`country`|O nome do território administrado pelo governo. Exceto `xdm:countryCode`, este é um campo de formato livre que pode ter o nome do país em qualquer idioma.| |`shippingAmount`|O valor que o cliente teve de pagar pelo envio.| |`billingAddress`|Endereço postal de cobrança| |`street1`|Informações no nível da rua principal, número do apartamento, número da rua e nome da rua| |`street2`|Campo adicional para informações no nível da rua| |`city`|O nome da cidade| |`state`|O nome do estado. Este é um campo de forma livre.| |`postalCode`|O código postal da localização. Os códigos postais não estão disponíveis para todos os países. Em alguns países, conterá apenas parte do código postal.| |`country`|O nome do território administrado pelo governo. Exceto `xdm:countryCode`, este é um campo de formato livre que pode ter o nome do país em qualquer idioma.| |`personalEmail`|Um endereço de email pessoal| |`address`|O endereço técnico, por exemplo, &#39;name@domain.com&#39;, conforme geralmente definido em RFC2822 e padrões subsequentes|

### orderCanceled

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando um comprador cancela um pedido. | `commerce.backofficeOrderCancelled` |

#### Dados coletados de orderCanceled

A tabela a seguir descreve os dados coletados para esse evento.
|Campo|Descrição| |—|—| |`address`|O endereço técnico, por exemplo, `name@domain.com` conforme geralmente definido em RFC2822 e padrões subsequentes| |`productListItems`|Uma variedade de produtos na ordem| |`id`|O identificador de item de linha para esta entrada de produto. O produto em si é identificado através da `product` campo.| |`name`|O nome de exibição ou o nome legível do produto| |`SKU`|Unidade De Manutenção De Estoque. O identificador exclusivo do produto.| |`quantity`|O número de unidades de produto no carrinho| |`priceTotal`|O preço total do item de linha do produto| |`discountAmount`|Indica o valor do desconto aplicado| |`order`|Contém informações sobre o pedido| |`purchaseID`|Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva| |`purchaseOrderNumber`|Identificador exclusivo atribuído pelo comprador para esta compra ou contrato| |`cancelDate`|A data e a hora em que um comprador cancela um pedido| |`lastUpdatedDate`|A hora em que um determinado registro de pedido foi atualizado pela última vez no sistema de comércio| |`personalEmail`|Um endereço de email pessoal| |`address`|O endereço técnico, por exemplo, &#39;name@domain.com&#39;, conforme geralmente definido em RFC2822 e padrões subsequentes|

### creditMemoIssued

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um comprador retorna um item em um pedido. | `commerce.backofficeCreditMemoIssued` |

#### Dados recolhidos de creditMemoIssued

A tabela a seguir descreve os dados coletados para esse evento.
|Campo|Descrição| |—|—| |`address`|O endereço técnico, por exemplo, `name@domain.com` conforme geralmente definido em RFC2822 e padrões subsequentes| |`productListItems`|Uma variedade de produtos na ordem| |`id`|O identificador de item de linha para esta entrada de produto. O produto em si é identificado através da `product` campo.| |`name`|O nome de exibição ou o nome legível do produto| |`SKU`|Unidade De Manutenção De Estoque. O identificador exclusivo do produto.| |`quantity`|O número de unidades de produto no carrinho| |`priceTotal`|O preço total do item de linha do produto| |`discountAmount`|Indica o valor do desconto aplicado| |`order`|Contém informações sobre o pedido| |`purchaseID`|Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva| |`purchaseOrderNumber`|Identificador exclusivo atribuído pelo comprador para esta compra ou contrato| |`lastUpdatedDate`|A hora em que um determinado registro de pedido foi atualizado pela última vez no sistema de comércio| |`personalEmail`|Um endereço de email pessoal| |`address`|O endereço técnico, por exemplo, &#39;name@domain.com&#39;, conforme geralmente definido em RFC2822 e padrões subsequentes|

### orderShippingCompleted

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um comprador retorna um item em um pedido. | `commerce.backofficeOrderShipmentCompleted` |

#### Dados coletados de orderShippingCompleted

A tabela a seguir descreve os dados coletados para esse evento.
|Campo|Descrição| |—|—| |`address`|O endereço técnico, por exemplo, `name@domain.com` conforme geralmente definido em RFC2822 e padrões subsequentes| |`productListItems`|Uma variedade de produtos na ordem| |`id`|O identificador de item de linha para esta entrada de produto. O produto em si é identificado através da `product` campo.| |`name`|O nome de exibição ou o nome legível do produto| |`SKU`|Unidade De Manutenção De Estoque. O identificador exclusivo do produto.| |`quantity`|O número de unidades de produto no carrinho| |`priceTotal`|O preço total do item de linha do produto| |`discountAmount`|Indica o valor do desconto aplicado| |`order`|Contém informações sobre o pedido| |`purchaseID`|Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva| |`priceTotal`|O preço total deste pedido após a aplicação de todos os descontos e impostos| |`currencyCode`|O código de moeda ISO 4217 usado para os totais do pedido| |`purchaseOrderNumber`|Identificador exclusivo atribuído pelo comprador para esta compra ou contrato| |`taxAmount`|O valor do imposto pago pelo comprador como parte do pagamento final.| |`createdDate`|A hora e a data em que um novo pedido é criado no sistema de comércio. Por exemplo, `2022-10-15T20:20:39+00:00`| |`payments`|A lista de pagamentos deste pedido| |`paymentType`|O método de pagamento deste pedido. Valores personalizados enumerados são permitidos.| |`currencyCode`|A [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado para este item de pagamento| |`paymentAmount`|O valor do pagamento| |`shipping`|Detalhes de remessa de um ou mais produtos| |`shippingMethod`|O método de entrega escolhido pelo cliente, como entrega padrão, entrega expressa, retirada na loja e assim por diante| |`address`|Endereço físico de entrega| |`street1`|Informações no nível da rua principal, número do apartamento, número da rua e nome da rua| |`street2`|Campo adicional para informações no nível da rua| |`city`|O nome da cidade| |`state`|O nome do estado. Este é um campo de forma livre.| |`postalCode`|O código postal da localização. Os códigos postais não estão disponíveis para todos os países. Em alguns países, conterá apenas parte do código postal.| |`country`|O nome do território administrado pelo governo. Exceto `xdm:countryCode`, este é um campo de formato livre que pode ter o nome do país em qualquer idioma.| |`shippingAmount`|O valor que o cliente teve de pagar pelo envio.| |`address`|O endereço técnico, por exemplo, `name@domain.com` conforme geralmente definido em RFC2822 e padrões subsequentes| |`billingAddress`|Endereço postal de cobrança| |`street1`|Informações no nível da rua principal, número do apartamento, número da rua e nome da rua| |`street2`|Campo adicional para informações no nível da rua| |`city`|O nome da cidade| |`state`|O nome do estado. Este é um campo de forma livre.| |`postalCode`|O código postal da localização. Os códigos postais não estão disponíveis para todos os países. Em alguns países, esses dados contêm apenas parte do código postal.| |`country`|O nome do território administrado pelo governo. Exceto `xdm:countryCode`, este é um campo de formato livre que pode ter o nome do país em qualquer idioma.| |`personalEmail`|Um endereço de email pessoal| |`address`|O endereço técnico, por exemplo, &#39;name@domain.com&#39;, conforme geralmente definido em RFC2822 e padrões subsequentes|
