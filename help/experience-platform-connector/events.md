---
title: Eventos
description: Saiba quais dados cada evento captura.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 975854dbdae32e5e51bb57593cf122627d01571f
workflow-type: tm+mt
source-wordcount: '3141'
ht-degree: 0%

---

# Experience Platform Connector Events

Abaixo encontram-se os eventos Commerce disponíveis quando você instala a extensão Experience Platform connector . Os dados que esses eventos coletam são enviados para a borda do Adobe Experience Platform. Você também pode criar [eventos personalizados](custom-events.md) para coletar dados adicionais não fornecidos imediatamente.

Além dos dados que os eventos a seguir coletam, você também obtém [outros dados](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) fornecido pelo SDK da Web da Adobe Experience Platform.

## Eventos de vitrine

+++ Os eventos da loja coletam dados comportamentais anônimos dos compradores durante a navegação no site. Os dados coletados por esses eventos podem ser usados para criar promoções e campanhas direcionadas a um conjunto específico de compradores.

>[!NOTE]
>
>Todos os eventos de vitrine incluem o `identityMap` , que é um identificador exclusivo da pessoa.

### addToCart

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um produto é adicionado ao carrinho ou quando a quantidade de um produto no carrinho é aumentada. | `commerce.productListAdds` |

#### Dados coletados de addToCart

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `productListAdds` | Indica se um produto foi adicionado a um carrinho de compras. Um valor de `1` indica que um produto foi adicionado. |
| `productListItems` | Uma matriz de produtos adicionados ao carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O preço total do item de linha do produto |
| `quantity` | O número de unidades de produto adicionadas ao carrinho |
| `discountAmount` | Indica a quantia de desconto aplicada |
| `currencyCode` | O [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moeda do produto |
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
| `productListItems` | Uma matriz de produtos adicionados ao carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O preço total do item de linha do produto |
| `quantity` | O número de unidades de produto adicionadas ao carrinho |
| `discountAmount` | Indica a quantia de desconto aplicada |
| `currencyCode` | O [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moeda do produto |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |
| `cartID` | A ID exclusiva que identifica o carrinho do cliente |

### removeFromCart

| Descrição | Nome do evento XDM |
|---|---|
| Disparado sempre que um produto é removido ou sempre que a quantidade de um produto no carrinho é diminuída. | `commerce.productListRemovals` |

#### Dados coletados de removeFromCart

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `productListRemovals` | Indica se um produto foi removido do carrinho. Um valor de `1` indica que um produto foi removido do carrinho. |
| `productListItems` | Uma matriz de produtos removidos do carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O preço total do item de linha do produto |
| `quantity` | O número de unidades de produto removidas do carrinho |
| `discountAmount` | Indica a quantia de desconto aplicada |
| `currencyCode` | O [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moeda do produto |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |
| `cartID` | A ID exclusiva que identifica o carrinho do cliente |

### shoppingCartView

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando qualquer página de carrinho é carregada. | `commerce.productListViews` |

#### Dados coletados de shoppingCartView

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `productListViews` | Indica se uma lista de produtos foi visualizada |
| `productListItems` | Uma matriz de produtos no carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O preço total do item de linha do produto |
| `quantity` | O número de unidades de produto no carrinho |
| `discountAmount` | Indica a quantia de desconto aplicada |
| `currencyCode` | O [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moeda do produto |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |
| `cartID` | A ID exclusiva que identifica o carrinho do cliente |

### pageView

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando qualquer página é carregada. | `web.webpagedetails.pageViews` |

#### Dados coletados de pageView

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `pageViews` | Indica se uma página foi carregada. A `value` de `1` indica que a página foi carregada. |

### productPageView

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando qualquer página de produto é carregada. | `commerce.productViews` |

#### Dados coletados de productPageView

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `productViews` | Indica se o produto foi exibido |
| `productListItems` | Uma matriz de produtos no carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O preço total do item de linha do produto |
| `discountAmount` | Indica a quantia de desconto aplicada |
| `currencyCode` | O [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moeda do produto |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |

### startCheckout

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando o comprador clica em um botão de finalização. | `commerce.checkouts` |

#### Dados coletados do startCheckout

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `checkouts` | Indica se uma ação ocorreu durante o processo de finalização |
| `productListItems` | Uma matriz de produtos no carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O preço total do item de linha do produto |
| `quantity` | O número de unidades de produto no carrinho |
| `discountAmount` | Indica a quantia de desconto aplicada |
| `currencyCode` | O [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moeda do produto |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |
| `cartID` | A ID exclusiva que identifica o carrinho do cliente |

### completeCheckout

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando o comprador faz um pedido. | `commerce.order` |

#### Dados coletados do completeCheckout

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `purchases` | Indica se um pedido foi aceito |
| `order` | Contém informações sobre o pedido colocado para um ou mais produtos |
| `purchaseID` | Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva. |
| `orderType` | Indica o tipo de pedido que foi feito, como Check-out ou Compra instantânea |
| `payments` | A lista de pagamentos para esta ordem |
| `currencyCode` | O [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado para este item de pagamento. Por exemplo, `USD` ou `EUR`. |
| `paymentAmount` | O valor do pagamento |
| `paymentType` | O método de pagamento desta ordem. As opções são: `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other` |
| `transactionID` | O identificador exclusivo de transação para este item de pagamento |
| `shipping` | Detalhes de envio para um ou mais produtos. |
| `shippingMethod` | O método de envio escolhido pelo cliente, como delivery padrão, entrega acelerada, coleta na loja e assim por diante |
| `shippingAmount` | O custo total de envio dos itens no carrinho |
| `promotionID` | Identificador exclusivo da promoção, se houver |
| `personalEmail` | Especifica o endereço de email pessoal |
| `address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes |
| `productListItems` | Uma matriz de produtos no carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O preço total do item de linha do produto |
| `quantity` | O número de unidades de produto no carrinho |
| `discountAmount` | Indica a quantia de desconto aplicada |
| `currencyCode` | O [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado para os totais da ordem. |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |
+++

## Eventos de perfil

+++
Os eventos de perfil incluem informações da conta, como `signIn`, `signOut`, `createAccount`e `editAccount`. Esses dados são usados para ajudar a preencher os principais detalhes do cliente, necessários para melhor definir segmentos ou executar campanhas de marketing, como se você quisesse direcionar os compradores que moram em Nova York.

### signIn

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um comprador tenta entrar. | `userAccount.login` |

>[!NOTE]
>
> Esse evento é acionado quando a ação específica é tentada. Não indica que a ação foi bem sucedida.

#### Dados coletados do signIn

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `eventType` | O tipo de evento principal para esse registro de série de tempo, como: `userAccount.login` |
| `person` | Um ator, contato ou proprietário individual |
| `accountID` | Captura a ID da conta do usuário |
| `personalEmailID` | Especifica o identificador exclusivo para o email pessoal |
| `address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes |
| `userAccount` | Indica quaisquer detalhes de fidelidade, preferências, processos de logon e outras preferências de conta |
| `login` | Indica se um visitante tentou fazer logon |

### signOut

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um comprador tenta sair. | `userAccount.logout` |

>[!NOTE]
>
> Esse evento é acionado quando a ação específica é tentada. Não indica que a ação foi bem sucedida.

#### Dados coletados do signOut

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `eventType` | O tipo de evento principal para esse registro de série de tempo, como: `userAccount.logout` |
| `userAccount` | Indica quaisquer detalhes de fidelidade, preferências, processos de logon e outras preferências de conta |
| `logout` | Indica se um visitante tentou fazer logoff |

### createAccount

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um comprador tenta criar uma conta. | `userAccount.createProfile` |

>[!NOTE]
>
> Esse evento é acionado quando a ação específica é tentada. Não indica que a ação foi bem sucedida.

#### Dados coletados de createAccount

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `eventType` | O tipo de evento principal para esse registro de série de tempo, como: `account.createProfile` |
| `person` | Um ator, contato ou proprietário individual |
| `accountID` | Captura a ID da conta do usuário |
| `accountType` | Captura o tipo de conta de usuário, como `Personal` ou `Company`, se aplicável |
| `personalEmailID` | Especifica o identificador exclusivo para o email pessoal |
| `address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes |
| `userAccount` | Indica quaisquer detalhes de fidelidade, preferências, processos de logon e outras preferências de conta |
| `createProfile` | Indica se um usuário criou um perfil de conta |

### editAccount

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um comprador tenta editar uma conta. | `userAccount.updateProfile` |

>[!NOTE]
>
> Esse evento é acionado quando a ação específica é tentada. Não indica que a ação foi bem sucedida.

#### Dados coletados de editAccount

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `eventType` | O tipo de evento principal para esse registro de série de tempo, como: `account.updateProfile` |
| `person` | Um ator, contato ou proprietário individual |
| `accountID` | Captura a ID da conta do usuário |
| `accountType` | Captura o tipo de conta de usuário, como `Personal` ou `Company`, se aplicável |
| `personalEmailID` | Especifica o identificador exclusivo para o email pessoal |
| `personalEmail` | Especifica o endereço de email pessoal |
| `address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes |
| `userAccount` | Indica quaisquer detalhes de fidelidade, preferências, processos de logon e outras preferências de conta |
| `updateProfile` | Indica se um usuário atualizou seu perfil de conta |
+++

## Pesquisar eventos

+++ Os eventos de pesquisa fornecem dados relevantes para a intenção do comprador. O insight da intenção de um comprador ajuda os comerciantes a ver como os compradores estão procurando itens, no que clicam e, por fim, comprando ou abandonando. Um exemplo de como você pode usar esses dados é se deseja direcionar os compradores existentes que pesquisam pelo seu produto principal, mas nunca compram o produto.

### searchRequestSent

| Descrição | Nome do evento XDM |
|---|---|
| Disparado pelos seguintes eventos no provedor &quot;pesquisar à medida que você digita&quot;:<br>Pressione Enter, Clique _Exibir todos_<br> Disparado pelos seguintes eventos nas páginas de resultados da pesquisa:<br>Selecione um filtro, Altere a ordem de classificação (_Ordenar por_), Altere a direção da classificação (crescente ou decrescente), Altere o número de resultados por página (_Mostrar número por página_), Navegue até a próxima página, Navegue até a página anterior, Navegue até uma página diferente | `searchRequest` |

>[!NOTE]
>
>Os eventos de pesquisa não são suportados em uma Adobe Commerce Enterprise Edition com o módulo B2B instalado.

#### Dados coletados de searchRequestSent

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `searchRequest` | Indica se uma solicitação de pesquisa foi enviada |
| `filter` | Indica se algum filtro foi aplicado para limitar os resultados da pesquisa |
| `attribute` (filtro) | A faceta de um item usada para determinar se ele deve ser incluído nos resultados da pesquisa |
| `value` | Valores de atributos usados para determinar quais itens estão incluídos nos resultados da pesquisa |
| `isRange` | Quando verdadeiro, os valores indicam endpoints de um intervalo de valores aceitável |
| `sort` | Indica como os resultados da pesquisa devem ser classificados |
| `attribute` (classificação) | Um atributo usado para classificar itens nos resultados da pesquisa |
| `order` | A ordem na qual os resultados da pesquisa serão retornados |
| `query` | Os termos pesquisados |

### searchResponseReceived

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando o Live Search retorna resultados para a página de resultados de &quot;pesquisa ao digitar&quot; ou de pesquisa. | `searchResponse` |

>[!NOTE]
>
>Os eventos de pesquisa não são suportados em uma Adobe Commerce Enterprise Edition com o módulo B2B instalado.

#### Dados coletados de searchResponseReceived

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `searchResponse` | Indica se uma resposta de pesquisa foi recebida |
| `suggestions` | Uma matriz de sequências de caracteres que incluem os nomes de produtos e categorias existentes no catálogo que são semelhantes à consulta de pesquisa |
| `numberOfResults` | O número de produtos devolvidos |
| `productListItems` | Uma matriz de produtos no carrinho de compras. |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `productImageUrl` | URL da imagem principal do produto |

+++

## (Beta) Eventos do back-office

>[!NOTE]
>
>Para comerciantes já inscritos em nosso programa beta de back office, você tem acesso a eventos back office. Se você deseja participar do programa back office beta, entre em contato com [drios@adobe.com](mailto:drios@adobe.com).

+++ Os eventos de back-office contêm informações sobre o status de um pedido, como se um pedido foi feito, cancelado, reembolsado ou enviado. Os dados coletados por esses eventos do lado do servidor mostram uma visualização 360 do pedido do comprador. Isso pode ajudar os comerciantes a direcionar melhor ou analisar todo o status do pedido ao desenvolver campanhas de marketing. Por exemplo, você pode detectar tendências em determinadas categorias de produtos que têm um bom desempenho em épocas diferentes do ano. Por exemplo, roupas de inverno que vendem melhor durante meses mais frios ou certas cores de produtos que os compradores estão interessados ao longo dos anos. Além disso, os dados de status do pedido podem ajudar você a calcular o valor do cliente do tempo de vida, entendendo a propensão de um comprador para converter com base em pedidos anteriores.

### orderPlaced

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um comprador faz um pedido. | `commerce.orderPlaced` |

#### Dados coletados de orderPlaced

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `identityMap` | Contém o endereço de email que identifica o cliente |
| `address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes |
| `eventType` | `commerce.orderPlaced` |
| `productListItems` | Uma matriz de produtos no pedido |
| `name` | O nome de exibição ou nome legível do produto |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `quantity` | O número de unidades de produto no carrinho |
| `priceTotal` | O preço total do item de linha do produto |
| `discountAmount` | Indica a quantia de desconto aplicada |
| `order` | Contém informações sobre o pedido |
| `purchaseID` | Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva |
| `purchaseOrderNumber` | Identificador exclusivo atribuído pelo comprador para esta compra ou contrato |
| `payments` | A lista de pagamentos para esta ordem |
| `paymentType` | O método de pagamento desta ordem. Valores enumerados e personalizados são permitidos. |
| `currencyCode` | O [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado para este item de pagamento |
| `paymentAmount` | O valor do pagamento |
| `shipping` | Detalhes de envio para um ou mais produtos |
| `shippingMethod` | O método de envio escolhido pelo cliente, como delivery padrão, entrega acelerada, coleta na loja e assim por diante |
| `shippingAddress` | Endereço de entrega física |
| `street1` | Informações de nível de rua principal, número do apartamento, número da rua e nome da rua |
| `shippingAmount` | O valor que o cliente tinha que pagar pela remessa. |
| `billingAddress` | Endereço postal de cobrança |
| `street1` | Informações de nível de rua principal, número do apartamento, número da rua e nome da rua |
| `street2` | Campo adicional para informações de nível de rua |
| `city` | O nome da cidade |
| `state` | O nome do estado. Este é um campo de forma livre. |
| `postalCode` | O código postal da localização. Os códigos postais não estão disponíveis para todos os países. Em alguns países, apenas fará parte do código postal. |
| `country` | O nome do território administrado pelo governo. Exceto `xdm:countryCode`, esse é um campo de forma livre que pode ter o nome do país em qualquer idioma. |

### orderShipped

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um pedido é enviado. | `commerce.orderLineItemShipped` |

#### Dados coletados de orderShipped

A tabela a seguir descreve os dados coletados para esse evento.
|Campo|Descrição| |—|—| |`identityMap`|Contém o endereço de email que identifica o cliente| |`address`|O endereço técnico, por exemplo, `name@domain.com` como normalmente definido em RFC2822 e padrões subsequentes| |`eventType`|`commerce.orderLineItemShipped`| |`productListItems`|Uma matriz de produtos na ordem| |`name`|Nome de exibição ou nome legível do produto| |`SKU`|Unidade de Manutenção de Estoque. O identificador exclusivo do produto.| |`quantity`|O número de unidades de produto no carrinho| |`priceTotal`|O preço total do item da linha do produto| |`discountAmount`|Indica o valor de desconto aplicado| |`order`|Contém informações sobre o pedido| |`purchaseID`|Identificador único atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva| |`purchaseOrderNumber`|Identificador único atribuído pelo comprador para esta compra ou contrato| |`payments`|A lista de pagamentos para esta ordem| |`paymentType`|O método de pagamento desta ordem. Valores enumerados e personalizados são permitidos.| |`currencyCode`|O [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado para este item de pagamento| |`paymentAmount`|O valor do pagamento| |`shipping`|Pormenores sobre a expedição de um ou mais produtos| |`shippingMethod`|O método de envio escolhido pelo cliente, como delivery padrão, entrega acelerada, coleta na loja e assim por diante| |`shippingAddress`|Endereço de expedição física| |`street1`|Informação primária sobre o nível da rua, número do apartamento, número da rua e nome da rua| |`shippingAmount`|O montante que o cliente tinha de pagar pela expedição.| |`billingAddress`|Endereço postal de cobrança| |`street1`|Informação primária sobre o nível da rua, número do apartamento, número da rua e nome da rua| |`street2`|Campo adicional para informações sobre o nível da rua| |`city`|O nome da cidade| |`state`|O nome do estado. Este é um campo de forma livre.| |`postalCode`|O código postal da localização. Os códigos postais não estão disponíveis para todos os países. Em alguns países, apenas fará parte do código postal.| |`country`|Nome do território administrado pelo Estado. Exceto `xdm:countryCode`, este é um campo de forma livre que pode ter o nome do país em qualquer idioma.|

### orderCancelled

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um comprador cancela um pedido. | `commerce.orderCancelled` |

#### Dados coletados de orderCancelled

A tabela a seguir descreve os dados coletados para esse evento.
|Campo|Descrição| |—|—| |`identityMap`|Contém o endereço de email que identifica o cliente| |`address`|O endereço técnico, por exemplo, `name@domain.com` como normalmente definido em RFC2822 e padrões subsequentes| |`eventType`|`commerce.orderCancelled`| |`productListItems`|Uma matriz de produtos na ordem| |`name`|Nome de exibição ou nome legível do produto| |`SKU`|Unidade de Manutenção de Estoque. O identificador exclusivo do produto.| |`quantity`|O número de unidades de produto no carrinho| |`priceTotal`|O preço total do item da linha do produto| |`discountAmount`|Indica o valor de desconto aplicado| |`order`|Contém informações sobre o pedido| |`purchaseID`|Identificador único atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva| |`purchaseOrderNumber`|Identificador único atribuído pelo comprador para esta compra ou contrato|

### orderRefunded

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um comprador retorna um item em um pedido. | `commerce.creditMemoIssued` |

#### Dados coletados de orderRefunded

A tabela a seguir descreve os dados coletados para esse evento.
|Campo|Descrição| |—|—| |`identityMap`|Contém o endereço de email que identifica o cliente| |`address`|O endereço técnico, por exemplo, `name@domain.com` como normalmente definido em RFC2822 e padrões subsequentes| |`eventType`|`commerce.creditMemoIssued`| |`productListItems`|Uma matriz de produtos na ordem| |`order`|Contém informações sobre o pedido| |`purchaseID`|Identificador único atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva| |`purchaseOrderNumber`|Identificador único atribuído pelo comprador para esta compra ou contrato|
+++
