---
title: Eventos
description: Saiba quais dados cada evento captura.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 572df7558e825a7a7c442e47af787c209dbe4ee3
workflow-type: tm+mt
source-wordcount: '6906'
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
| `commerce.productListAdds` | Indica se um produto foi adicionado a um carrinho de compras. Um valor de `1` indica que um produto foi adicionado. |
| `commerce.cart.cartID` | A ID exclusiva que identifica o carrinho do cliente. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |
| `productListItems` | Uma variedade de produtos que foram adicionados ao carrinho de compras. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.priceTotal` | O preço total do item de linha do produto. |
| `productListItems.quantity` | O número de unidades de produto no carrinho. |
| `productListItems.discountAmount` | Indica o valor de desconto aplicado. |
| `productListItems.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL da imagem principal do produto. |
| `productListItems.selectedOptions` | Campo usado para um produto configurável. |
| `productListItems.selectedOptions.attribute` | Identifica um atributo do produto configurável, como `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifica o valor do atributo, como `small` ou `black`. |

### openCart

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um novo carrinho é criado, ou seja, quando um produto é adicionado a um carrinho vazio. | `commerce.productListOpens` |

#### Dados coletados do openCart

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `commerce.productListOpens` | Indica se um carrinho foi criado. Um valor de `1` indica que um carrinho foi criado. |
| `commerce.cart.cartID` | A ID exclusiva que identifica o carrinho do cliente. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |
| `productListItems` | Uma variedade de produtos que foram adicionados ao carrinho de compras. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.priceTotal` | O preço total do item de linha do produto. |
| `productListItems.quantity` | O número de unidades de produto no carrinho. |
| `productListItems.discountAmount` | Indica o valor de desconto aplicado. |
| `productListItems.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL da imagem principal do produto. |
| `productListItems.selectedOptions` | Campo usado para um produto configurável. |
| `productListItems.selectedOptions.attribute` | Identifica um atributo do produto configurável, como `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifica o valor do atributo, como `small` ou `black`. |

### removeFromCart

| Descrição | Nome do evento XDM |
|---|---|
| Acionado sempre que um produto é removido ou sempre que a quantidade de um produto no carrinho é reduzida. | `commerce.productListRemovals` |

#### Dados coletados de removeFromCart

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `commerce.productListRemovals` | Indica se um produto foi removido do carrinho. Um valor de `1` indica que um produto foi removido do carrinho. |
| `commerce.cart.cartID` | A ID exclusiva que identifica o carrinho do cliente. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |
| `productListItems` | Uma variedade de produtos que foram adicionados ao carrinho de compras. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.priceTotal` | O preço total do item de linha do produto. |
| `productListItems.quantity` | O número de unidades de produto no carrinho. |
| `productListItems.discountAmount` | Indica o valor de desconto aplicado. |
| `productListItems.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL da imagem principal do produto. |
| `productListItems.selectedOptions` | Campo usado para um produto configurável. |
| `productListItems.selectedOptions.attribute` | Identifica um atributo do produto configurável, como `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifica o valor do atributo, como `small` ou `black`. |

### shoppingCartView

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando qualquer página do carrinho é carregada. | `commerce.productListViews` |

#### Dados coletados de shoppingCartView

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `commerce.productListViews` | Indica se uma lista de produtos foi exibida. |
| `commerce.cart.cartID` | A ID exclusiva que identifica o carrinho do cliente. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |
| `productListItems` | Uma variedade de produtos que foram adicionados ao carrinho de compras. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.priceTotal` | O preço total do item de linha do produto. |
| `productListItems.quantity` | O número de unidades de produto no carrinho. |
| `productListItems.discountAmount` | Indica o valor de desconto aplicado. |
| `productListItems.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL da imagem principal do produto. |
| `productListItems.selectedOptions` | Campo usado para um produto configurável. |
| `productListItems.selectedOptions.attribute` | Identifica um atributo do produto configurável, como `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifica o valor do atributo, como `small` ou `black`. |

### pageView

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando qualquer página é carregada. | `web.webpagedetails.pageViews` |

#### Dados coletados de pageView

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `web.webPageDetails.pageViews` | Indica se uma página foi carregada. A `value` de `1` indica que a página foi carregada. |
| `web.webPageDetails.URL` | O URL normativo ou usual da página da Web. Pode ser o URL real usado para acessar a página, que seria registrado usando `Web Link`. |
| `web.webPageDetails.name` | O nome normativo da página da Web. Esse nome não é necessariamente o título da página ou associado diretamente ao conteúdo da página, mas é usado para organizar as páginas de um site para fins de classificação. |
| `web.webReferrer.URL` | O URL da página da Web que um comprador visitou antes de clicar em um link para seu site. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |

### productPageView

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando qualquer página de produto é carregada. | `commerce.productViews` |

#### Dados coletados de productPageView

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `commerce.productViews` | Indica se o produto foi visualizado. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |
| `productListItems` | Uma variedade de produtos que foram adicionados ao carrinho de compras. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.priceTotal` | O preço total do item de linha do produto. |
| `productListItems.quantity` | O número de unidades de produto no carrinho. |
| `productListItems.discountAmount` | Indica o valor de desconto aplicado. |
| `productListItems.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL da imagem principal do produto. |
| `productListItems.selectedOptions` | Campo usado para um produto configurável. |
| `productListItems.selectedOptions.attribute` | Identifica um atributo do produto configurável, como `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifica o valor do atributo, como `small` ou `black`. |

### startCheckout

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando o comprador clica em um botão de check-out. | `commerce.checkouts` |

#### Dados coletados de startCheckout

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `commerce.checkouts` | Indica se uma ação ocorreu durante o processo de check-out. |
| `commerce.cart.cartID` | A ID exclusiva que identifica o carrinho do cliente. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |
| `productListItems` | Uma variedade de produtos que foram adicionados ao carrinho de compras. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.priceTotal` | O preço total do item de linha do produto. |
| `productListItems.quantity` | O número de unidades de produto no carrinho. |
| `productListItems.discountAmount` | Indica o valor de desconto aplicado. |
| `productListItems.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `productListItems.productImageUrl` | URL da imagem principal do produto. |
| `productListItems.selectedOptions` | Campo usado para um produto configurável. |
| `productListItems.selectedOptions.attribute` | Identifica um atributo do produto configurável, como `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifica o valor do atributo, como `small` ou `black`. |

### completeCheckout

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando o comprador faz um pedido. | `commerce.order` |

#### Dados coletados de completeCheckout

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `commerce.purchases` | Indica se um pedido foi aceito. |
| `commerce.order` | Contém informações sobre o pedido feito de um ou mais produtos. |
| `commerce.order.purchaseID` | Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva. |
| `commerce.order.payments` | A lista de pagamentos deste pedido. |
| `commerce.order.payments.paymentTransactionID` | Identificador exclusivo desta transação de pagamento. |
| `commerce.order.payments.paymentAmount` | O valor do pagamento. |
| `commerce.order.payments.paymentType` | O método de pagamento deste pedido. As opções são: `cash`, `credit_card`, `debit_card`, `gift_card`, `check`, `paypal`, `wire_transfer`, `credit_card_reference`, `other`. |
| `commerce.order.payments.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `commerce.order.taxAmount` | O valor do imposto pago pelo comprador como parte do pagamento final. |
| `commerce.order.discountAmount` | Indica o valor do desconto aplicado a todo o pedido. |
| `commerce.order.createdDate` | A hora e a data em que um novo pedido é criado no sistema de comércio. Por exemplo, `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | Detalhes de remessa de um ou mais produtos. |
| `commerce.shipping.shippingMethod` | O método de entrega escolhido pelo cliente, como entrega padrão, entrega expressa, retirada na loja e assim por diante. |
| `commerce.shipping.shippingAmount` | O valor que o cliente teve de pagar pelo envio. |  | `shipping` | Detalhes de remessa de um ou mais produtos. |
| `commerce.shipping.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |
| `personalEmail` | Um endereço de email pessoal. |
| `personalEmail.address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes. |
| `productListItems` | Uma variedade de produtos que foram adicionados ao carrinho de compras. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.priceTotal` | O preço total do item de linha do produto. |
| `productListItems.quantity` | O número de unidades de produto no carrinho. |
| `productListItems.discountAmount` | Indica o valor de desconto aplicado. |
| `productListItems.productImageUrl` | URL da imagem principal do produto. |
| `productListItems.selectedOptions` | Campo usado para um produto configurável. |
| `productListItems.selectedOptions.attribute` | Identifica um atributo do produto configurável, como `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifica o valor do atributo, como `small` ou `black`. |

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
| `person` | Um ator, contato ou proprietário individual. |
| `person.accountID` | Registra a ID da conta do usuário. |
| `person.accountType` | Registra o tipo de conta do usuário, como `Personal` ou `Company`, se aplicável. |
| `person.personalEmailID` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes. |
| `personalEmail` | Captura detalhes de contato - um email e informações associadas. |
| `personalEmail.address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes. |
| `userAccount` | Indica detalhes de fidelidade, preferências, processos de logon e outras preferências de conta. |
| `userAccount.login` | Indica se um visitante tentou fazer logon. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |

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
| `userAccount` | Indica detalhes de fidelidade, preferências, processos de logon e outras preferências de conta. |
| `userAccount.logout` | Indica se um visitante tentou fazer logoff. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |

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
| `person` | Um ator, contato ou proprietário individual. |
| `person.accountID` | Registra a ID da conta do usuário. |
| `person.accountType` | Registra o tipo de conta do usuário, como `Personal` ou `Company`, se aplicável. |
| `person.personalEmailID` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes. |
| `personalEmail` | Captura detalhes de contato - um email e informações associadas. |
| `personalEmail.address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes. |
| `userAccount` | Indica detalhes de fidelidade, preferências, processos de logon e outras preferências de conta. |
| `userAccount.updateProfile` | Indica se um usuário atualizou seu perfil de conta. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |

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
| `person` | Um ator, contato ou proprietário individual. |
| `person.accountID` | Registra a ID da conta do usuário. |
| `person.accountType` | Registra o tipo de conta do usuário, como `Personal` ou `Company`, se aplicável. |
| `person.personalEmailID` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes. |
| `personalEmail` | Captura detalhes de contato - um email e informações associadas. |
| `personalEmail.address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes. |
| `userAccount` | Indica detalhes de fidelidade, preferências, processos de logon e outras preferências de conta. |
| `userAccount.updateProfile` | Indica se um usuário atualizou seu perfil de conta. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |

## Pesquisar eventos

Os eventos de pesquisa fornecem dados relevantes para a intenção do comprador. O insight sobre a intenção do comprador ajuda os comerciantes a ver como eles estão procurando por itens, em que clicam e, em última análise, compram ou abandonam os produtos. Um exemplo de como você pode usar esses dados é se quiser direcionar os compradores existentes que pesquisam pelo seu produto principal, mas nunca compram o produto.

Use o `searchRequest.id` e `searchResponse.id` campos encontrados em ambos os `searchRequestSent` e `searchResponseReceived` eventos para fazer referência cruzada de uma solicitação de pesquisa com a resposta de pesquisa correspondente.

### searchRequestSent

| Descrição | Nome do evento XDM |
|---|---|
| Acionado pelos seguintes eventos no popover &quot;pesquisar ao digitar&quot;:<br><br>Pressione Enter E Clique _Exibir todos_<br><br> Acionado pelos seguintes eventos nas páginas de resultados da pesquisa:<br><br>Selecione um filtro e Altere a ordem de classificação (_Classificar por_), Alterar a direção da classificação (crescente ou decrescente), Alterar o número de resultados por página (_Mostrar # por página_), Navegar até a próxima página, Navegar até a página anterior, Navegar até uma página diferente | `searchRequest` |

>[!NOTE]
>
>Os eventos de pesquisa não são suportados em uma Adobe Commerce Enterprise Edition com a extensão B2B instalada.

#### Dados coletados de searchRequestSent

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `searchRequest` | Indica se uma solicitação de pesquisa foi enviada. |
| `searchRequest.id` | O identificador exclusivo para esta solicitação de pesquisa específica. |
| `searchRequest.value` | O valor quantificável da solicitação. |
| `siteSearch` | Contém informações sobre a pesquisa. |
| `siteSearch.filter` | Indica se algum filtro foi aplicado para limitar os resultados da pesquisa. |
| `siteSearch.filter.attribute` (filtro) | A faceta de um item usada para determinar se ele deve ser incluído nos resultados da pesquisa. |
| `siteSearch.filter.isRange` | Quando verdadeiro, os valores indicam pontos de extremidade de um intervalo aceitável de valores. |
| `siteSearch.filter.value` | Valor de atributo usado para determinar quais itens são incluídos nos resultados da pesquisa. |
| `siteSearch.sort` | Indica como os resultados da pesquisa devem ser classificados. |
| `siteSearch.sort.attribute` (classificar) | Um atributo usado para classificar itens nos resultados da pesquisa. |
| `siteSearch.sort.order` | A ordem na qual retornar os resultados da pesquisa. |
| `siteSearch.query` | Os termos procurados. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |

### searchResponseReceived

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando o Live Search retorna resultados para o pop-over &quot;pesquisar ao digitar&quot; ou para a página de resultados da pesquisa. | `searchResponse` |

>[!NOTE]
>
>Os eventos de pesquisa não são suportados em uma Adobe Commerce Enterprise Edition com a extensão B2B instalada.

#### Dados coletados de searchResponseReceived

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `searchResponse` | Indica se uma resposta de pesquisa foi recebida. |
| `searchResponse.id` | O identificador exclusivo para esta resposta de pesquisa específica. |
| `searchResponse.value` | O valor quantificável da resposta. |
| `siteSearch.numberOfResults` | O número de produtos devolvidos. |
| `siteSearch.suggestions` | Uma matriz de strings que inclui os nomes de produtos e categorias existentes no catálogo que são semelhantes à consulta de pesquisa. |
| `productListItems` | Uma variedade de produtos que foram adicionados ao carrinho de compras. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.productImageUrl` | URL da imagem principal do produto. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |

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
| `commerce.requisitionListOpens` | Indica a inicialização de uma nova lista de requisições. |
| `commerce.requisitionList` | As propriedades da lista de requisições criadas pelo cliente. |
| `commerce.requisitionList.ID` | Identificador exclusivo da lista de requisições. |
| `commerce.requisitionList.name` | Nome da lista de requisições especificada pelo cliente. |
| `commerce.requisitionList.description` | Descrição da lista de requisições especificada pelo cliente. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |

### addToRequisitionList

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando um comprador adiciona um produto a uma lista de requisições existente ou ao criar uma nova lista. | `commerce.requisitionListAdds` |

#### Dados coletados de addToRequisitionList

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `commerce.requisitionListAdds` | Indica a adição de um ou mais produtos a uma lista de requisições. |
| `commerce.requisitionList` | As propriedades da lista de requisições criadas pelo cliente. |
| `commerce.requisitionList.ID` | Identificador exclusivo da lista de requisições. |
| `commerce.requisitionList.name` | Nome da lista de requisições especificada pelo cliente. |
| `commerce.requisitionList.description` | Descrição da lista de requisições especificada pelo cliente. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |
| `productListItems` | Uma matriz de produtos que foram adicionados à lista de requisições. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.priceTotal` | O preço total do item de linha do produto. |
| `productListItems.quantity` | O número de unidades de produto no carrinho. |
| `productListItems.discountAmount` | Indica o valor de desconto aplicado. |
| `productListItems.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `productListItems.selectedOptions` | Campo usado para um produto configurável. |
| `productListItems.selectedOptions.attribute` | Identifica um atributo do produto configurável, como `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifica o valor do atributo, como `small` ou `black`. |

### removeFromRequisitionList

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um comprador remove um produto de uma lista de requisições. | `commerce.requisitionListRemovals` |

#### Dados coletados de removeFromRequisitionList

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `commerce.requsitionListRemovals` | Indica a remoção de um ou mais produtos de uma lista de requisições. |
| `commerce.requisitionList` | As propriedades da lista de requisições criadas pelo cliente. |
| `commerce.requisitionList.ID` | Identificador exclusivo da lista de requisições. |
| `commerce.requisitionList.name` | Nome da lista de requisições especificada pelo cliente. |
| `commerce.requisitionList.description` | Descrição da lista de requisições especificada pelo cliente. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |
| `productListItems` | Uma matriz de produtos que foram adicionados à lista de requisições. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.priceTotal` | O preço total do item de linha do produto. |
| `productListItems.quantity` | O número de unidades de produto no carrinho. |
| `productListItems.discountAmount` | Indica o valor de desconto aplicado. |
| `productListItems.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `productListItems.selectedOptions` | Campo usado para um produto configurável. |
| `productListItems.selectedOptions.attribute` | Identifica um atributo do produto configurável, como `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifica o valor do atributo, como `small` ou `black`. |

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
| `commerce.order` | Contém informações sobre o pedido. |
| `commerce.order.purchaseID` | Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva. |
| `commerce.order.payments` | A lista de pagamentos deste pedido. |
| `commerce.order.payments.paymentTransactionID` | Identificador exclusivo desta transação de pagamento. |
| `commerce.order.payments.paymentAmount` | O valor do pagamento. |
| `commerce.order.payments.paymentType` | O método de pagamento deste pedido. Valores personalizados enumerados são permitidos. |
| `commerce.order.payments.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `commerce.order.taxAmount` | O valor do imposto pago pelo comprador como parte do pagamento final. |
| `commerce.order.discountAmount` | Indica o valor do desconto aplicado a todo o pedido. |
| `commerce.order.createdDate` | A hora e a data em que um novo pedido é criado no sistema de comércio. Por exemplo, `2022-10-15T20:20:39+00:00`. |
| `commerce.order.currencyCode` | O código de moeda ISO 4217 usado para os totais do pedido. |
| `commerce.shipping` | Detalhes de remessa de um ou mais produtos. |
| `commerce.shipping.shippingMethod` | O método de entrega escolhido pelo cliente, como entrega padrão, entrega expressa, retirada na loja e assim por diante. |
| `commerce.shipping.shippingAmount` | O valor que o cliente teve de pagar pelo envio. |
| `commerce.shipping.currencyCode` | O código de moeda ISO 4217 usado para o total de remessa. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |
| `commerce.billing.address` | Endereço postal para cobrança. |
| `commerce.billing.address.street1` | Informações no nível da rua principal, número do apartamento, número da rua e nome da rua |
| `commerce.billing.address.street2` | Campo adicional para informações no nível da rua. |
| `commerce.billing.address.city` | O nome da cidade. |
| `commerce.billing.address.state` | O nome do estado. Este é um campo de forma livre. |
| `commerce.billing.address.postalCode` | O código postal da localização. Os códigos postais não estão disponíveis para todos os países. Em alguns países, conterá apenas parte do código postal. |
| `commerce.billing.address.country` | O nome do território administrado pelo governo. Exceto `xdm:countryCode`, este é um campo de formato livre que pode ter o nome do país em qualquer idioma. |
| `personalEmail` | Um endereço de email pessoal. |
| `personalEmail.address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes. |
| `productListItems` | Uma variedade de produtos no pedido. |
| `productListItems.id` | O identificador de item de linha para esta entrada de produto. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.priceTotal` | O preço total do item de linha do produto. |
| `productListItems.quantity` | O número de unidades de produto no carrinho. |
| `productListItems.discountAmount` | Indica o valor de desconto aplicado. |
| `productListItems.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `productListItems.selectedOptions` | Campo usado para um produto configurável. |
| `productListItems.selectedOptions.attribute` | Identifica um atributo do produto configurável, como `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifica o valor do atributo, como `small` ou `black`. |
| `productListItems.categories` | Contém informações sobre a categoria de um produto. |
| `productListItems.categories.id` | O identificador exclusivo da categoria. |
| `productListItems.categories.name` | O nome da categoria. |
| `productListItems.categories.path` | O caminho para a categoria. |
| `productListItems.productImageUrl` | URL da imagem principal do produto. |

### orderInvoiced

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando um comerciante envia uma NFF para solicitar pagamento. | `commerce.backofficeOrderInvoiced` |

#### Dados coletados de orderInvoiced

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `commerce.order` | Contém informações sobre o pedido. |
| `commerce.order.purchaseID` | Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva. |
| `commerce.order.priceTotal` | O preço total deste pedido após a aplicação de todos os descontos e impostos. |
| `commerce.order.currencyCode` | O código de moeda ISO 4217 usado para os totais do pedido. |
| `commerce.order.purchaseOrderNumber` | Identificador exclusivo atribuído pelo comprador para esta compra ou contrato. |
| `commerce.order.payments` | A lista de pagamentos deste pedido. |
| `commerce.order.payments.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `commerce.order.payments.paymentType` | O método de pagamento deste pedido. Valores personalizados enumerados são permitidos. |
| `commerce.order.payments.paymentAmount` | O valor do pagamento. |
| `commerce.shipping` | Detalhes de remessa de um ou mais produtos. |
| `commerce.shipping.shippingMethod` | O método de entrega escolhido pelo cliente, como entrega padrão, entrega expressa, retirada na loja e assim por diante. |
| `commerce.shipping.shippingAmount` | O valor que o cliente teve de pagar pelo envio. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |
| `personalEmail` | Um endereço de email pessoal. |
| `personalEmail.address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes. |
| `productListItems` | Uma variedade de produtos no pedido. |
| `productListItems.id` | O identificador de item de linha para esta entrada de produto. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.priceTotal` | O preço total do item de linha do produto. |
| `productListItems.quantity` | O número de unidades de produto no carrinho. |
| `productListItems.discountAmount` | Indica o valor de desconto aplicado. |
| `productListItems.categories` | Contém informações sobre a categoria de um produto. |
| `productListItems.categories.id` | O identificador exclusivo da categoria. |
| `productListItems.categories.name` | O nome da categoria. |
| `productListItems.categories.path` | O caminho para a categoria. |

### orderItemsShipped

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um pedido é enviado. | `commerce.backofficeOrderItemsShipped` |

#### Dados coletados de orderItemsShipped

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `commerce.order` | Contém informações sobre o pedido. |
| `commerce.order.purchaseID` | Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva. |
| `commerce.order.payments` | A lista de pagamentos deste pedido. |
| `commerce.order.payments.paymentTransactionID` | Identificador exclusivo desta transação de pagamento. |
| `commerce.order.payments.paymentAmount` | O valor do pagamento. |
| `commerce.order.payments.paymentType` | O método de pagamento deste pedido. Valores personalizados enumerados são permitidos. |
| `commerce.order.payments.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `commerce.order.priceTotal` | O preço total deste pedido após a aplicação de todos os descontos e impostos. |
| `commerce.order.purchaseOrderNumber` | Identificador exclusivo atribuído pelo comprador para esta compra ou contrato. |
| `commerce.order.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `commerce.order.lastUpdatedDate` | A hora em que um determinado registro de pedido foi atualizado pela última vez no sistema de comércio. |
| `commerce.shipping` | Detalhes de remessa de um ou mais produtos. |
| `commerce.shipping.shippingMethod` | O método de entrega escolhido pelo cliente, como entrega padrão, entrega expressa, retirada na loja e assim por diante. |
| `commerce.shipping.shippingAmount` | O valor que o cliente teve de pagar pelo envio. |
| `commerce.shipping.address` | O endereço físico de entrega. |
| `commerce.shipping.address.street1` | Informações no nível da rua principal, número do apartamento, número da rua e nome da rua. |
| `commerce.shipping.address.street2` | Segunda linha opcional de informações da rua. |
| `commerce.shipping.address.city` | O nome da cidade. |
| `commerce.shipping.address.state` | O nome do Estado. Este é um campo de forma livre. |
| `commerce.shipping.address.postalCode` | O código postal da localização. Os códigos postais não estão disponíveis para todos os países. Em alguns países, conterá apenas parte do código postal. |
| `commerce.shipping.address.country` | O nome do território administrado pelo governo. Exceto `xdm:countryCode`, este é um campo de formato livre que pode ter o nome do país em qualquer idioma. |
| `commerce.shipping.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `commerce.shipping.trackingNumber` | O número de rastreamento fornecido pela transportadora para uma remessa de item de pedido. |
| `commerce.shipping.trackingURL` | O URL para rastrear o status de envio de um item do pedido. |
| `commerce.shipping.shipDate` | A data em que um ou mais itens de uma ordem são entregues. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |
| `commerce.billing.address` | Endereço postal para cobrança. |
| `commerce.billing.address.street1` | Informações no nível da rua principal, número do apartamento, número da rua e nome da rua |
| `commerce.billing.address.street2` | Campo adicional para informações no nível da rua. |
| `commerce.billing.address.city` | O nome da cidade. |
| `commerce.billing.address.state` | O nome do estado. Este é um campo de forma livre. |
| `commerce.billing.address.postalCode` | O código postal da localização. Os códigos postais não estão disponíveis para todos os países. Em alguns países, conterá apenas parte do código postal. |
| `commerce.billing.address.country` | O nome do território administrado pelo governo. Exceto `xdm:countryCode`, este é um campo de formato livre que pode ter o nome do país em qualquer idioma. |
| `personalEmail` | Um endereço de email pessoal. |
| `personalEmail.address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes. |
| `productListItems` | Uma variedade de produtos no pedido. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.priceTotal` | O preço total do item de linha do produto. |
| `productListItems.quantity` | O número de unidades de produto no carrinho. |
| `productListItems.discountAmount` | Indica o valor de desconto aplicado. |
| `productListItems.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `productListItems.selectedOptions` | Campo usado para um produto configurável. |
| `productListItems.selectedOptions.attribute` | Identifica um atributo do produto configurável, como `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifica o valor do atributo, como `small` ou `black`. |
| `productListItems.categories` | Contém informações sobre a categoria de um produto. |
| `productListItems.categories.id` | O identificador exclusivo da categoria. |
| `productListItems.categories.name` | O nome da categoria. |
| `productListItems.categories.path` | O caminho para a categoria. |

### orderCanceled

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando um comprador cancela um pedido. | `commerce.backofficeOrderCancelled` |

#### Dados coletados de orderCanceled

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `commerce.order` | Contém informações sobre o pedido. |
| `commerce.order.purchaseID` | Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva. |
| `commerce.order.purchaseOrderNumber` | Identificador exclusivo atribuído pelo comprador para esta compra ou contrato. |
| `commerce.order.cancelDate` | A data e a hora em que um comprador cancela um pedido. |
| `commerce.order.lastUpdatedDate` | A hora em que um determinado registro de pedido foi atualizado pela última vez no sistema de comércio. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |
| `personalEmail` | Um endereço de email pessoal. |
| `personalEmail.address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes. |

### orderLineItemReembolsado

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando um comprador é reembolsado por um item devolvido. | `commerce.backofficeCreditMemoIssued` |

#### Dados coletados de orderLineItemRefund

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `commerce.order` | Contém informações sobre o pedido. |
| `commerce.order.purchaseID` | Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva. |
| `commerce.order.lastUpdatedDate` | A hora em que um determinado registro de pedido foi atualizado pela última vez no sistema de comércio. |
| `commerce.order.purchaseOrderNumber` | Identificador exclusivo atribuído pelo comprador para esta compra ou contrato. |
| `commerce.refunds` | A lista de reembolsos para este pedido. |
| `commerce.refunds.transactionID` | Identificador exclusivo deste reembolso. |
| `commerce.refunds.refundAmount` | O valor da restituição. |
| `commerce.refunds.refundPaymentType` | O método de pagamento deste pedido. Valores personalizados enumerados são permitidos. |
| `commerce.refunds.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `personalEmail` | Um endereço de email pessoal. |
| `personalEmail.address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes. |
| `productListItems` | Uma variedade de produtos no pedido. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.priceTotal` | O preço total do item de linha do produto. |
| `productListItems.quantity` | O número de unidades de produto no carrinho. |
| `productListItems.discountAmount` | Indica o valor de desconto aplicado. |
| `productListItems.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `productListItems.selectedOptions` | Campo usado para um produto configurável. |
| `productListItems.selectedOptions.attribute` | Identifica um atributo do produto configurável, como `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifica o valor do atributo, como `small` ou `black`. |
| `productListItems.categories` | Contém informações sobre a categoria de um produto. |
| `productListItems.categories.id` | O identificador exclusivo da categoria. |
| `productListItems.categories.name` | O nome da categoria. |
| `productListItems.categories.path` | O caminho para a categoria. |

### orderItemsReturnInitiated

| Descrição | Nome do evento XDM |
|---|---|
| Disparado quando um comprador solicita o retorno de um item. | `commerce.backofficeOrderItemsReturnInitiated` |

#### Dados coletados de orderItemsReturnInitiated

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `commerce.order` | Contém informações sobre o pedido. |
| `commerce.order.purchaseID` | Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva. |
| `commerce.order.returns` | As informações de RMA (Autorização para devolução de produto) deste pedido. |
| `commerce.order.returns.returnID` | O identificador exclusivo desta RMA (Autorização para devolução de produto). |
| `commerce.order.returns.returnStatus` | O status atual da RMA (Autorização de devolução de produto), como Pendente, Fechado etc. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |
| `personalEmail` | Um endereço de email pessoal. |
| `personalEmail.address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes. |
| `productListItems` | Uma variedade de produtos no pedido. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.quantity` | O número de unidades de produto no carrinho. |
| `productListItems.selectedOptions` | Campo usado para um produto configurável. |
| `productListItems.selectedOptions.attribute` | Identifica um atributo do produto configurável, como `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifica o valor do atributo, como `small` ou `black`. |
| `productListItems.categories` | Contém informações sobre a categoria de um produto. |
| `productListItems.categories.id` | O identificador exclusivo da categoria. |
| `productListItems.categories.name` | O nome da categoria. |
| `productListItems.categories.path` | O caminho para a categoria. |
| `productListItems.returnItem` | As informações de RMA (Autorização para Devolução de Mercadoria) para este item. |
| `productListItems.returnItem.returnStatus` | O status do item devolvido, como Pendente, Aprovado, etc. |
| `productListItems.returnItem.returnReason` | O motivo pelo qual uma devolução é solicitada para este item. |
| `productListItems.returnItem.returnItemCondition` | A condição do item para o qual a devolução é solicitada. |
| `productListItems.returnItem.returnResolution` | A resolução solicitada do item que está sendo devolvido, como Reembolso, Troca, etc. |
| `productListItems.returnItem.returnQuantityRequested` | O número deste item que o comprador solicitou devolução. |
| `productListItems.returnItem.returnQuantityAuthorized` | O número deste item que está autorizado a ser devolvido. |
| `productListItems.returnItem.eturnQuantityReceived` | O número de itens devolvidos recebidos. |
| `productListItems.returnItem.returnQuantityApproved` | O número deste item com devolução totalmente concluída e aprovada. |

### orderItemReturnCompleted

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando um item que um comprador solicitou devolver é concluído. | `commerce.backofficeOrderItemsReturnCompleted` |

#### Dados coletados de orderItemReturnCompleted

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `commerce.order` | Contém informações sobre o pedido. |
| `commerce.order.purchaseID` | Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva. |
| `commerce.order.returns` | As informações de RMA (Autorização para devolução de produto) deste pedido. |
| `commerce.order.returns.returnID` | O identificador exclusivo desta RMA (Autorização para devolução de produto). |
| `commerce.order.returns.returnStatus` | O status atual da RMA (Autorização de devolução de produto), como Pendente, Fechado etc. |
| `commerce.commerceScope` | Indica onde um evento ocorreu (exibição de loja, loja, site e assim por diante). |
| `commerce.commerceScope.environmentID` | A ID do ambiente. Uma ID alfanumérica de 32 dígitos separada por hifens. |
| `commerce.commerceScope.storeCode` | O código de armazenamento exclusivo. Você pode ter muitas lojas por site. |
| `commerce.commerceScope.storeViewCode` | O código exclusivo de exibição da loja. Você pode ter muitas exibições de loja por loja. |
| `commerce.commerceScope.websiteCode` | O código exclusivo do site. Você pode ter muitos sites em um ambiente. |
| `personalEmail` | Um endereço de email pessoal. |
| `personalEmail.address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes. |
| `productListItems` | Uma variedade de produtos no pedido. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.selectedOptions` | Campo usado para um produto configurável. |
| `productListItems.selectedOptions.attribute` | Identifica um atributo do produto configurável, como `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifica o valor do atributo, como `small` ou `black`. |
| `productListItems.categories` | Contém informações sobre a categoria de um produto. |
| `productListItems.categories.id` | O identificador exclusivo da categoria. |
| `productListItems.categories.name` | O nome da categoria. |
| `productListItems.categories.path` | O caminho para a categoria. |
| `productListItems.returnItem` | As informações de RMA (Autorização para Devolução de Mercadoria) para este item. |
| `productListItems.returnItem.returnStatus` | O status do item devolvido, como Pendente, Aprovado, etc. |
| `productListItems.returnItem.returnReason` | O motivo pelo qual uma devolução é solicitada para este item. |
| `productListItems.returnItem.returnItemCondition` | A condição do item para o qual a devolução é solicitada. |
| `productListItems.returnItem.returnResolution` | A resolução solicitada do item que está sendo devolvido, como Reembolso, Troca, etc. |
| `productListItems.returnItem.returnQuantityRequested` | O número deste item que o comprador solicitou devolução. |
| `productListItems.returnItem.returnQuantityAuthorized` | O número deste item que está autorizado a ser devolvido. |
| `productListItems.returnItem.eturnQuantityReceived` | O número de itens devolvidos recebidos. |
| `productListItems.returnItem.returnQuantityApproved` | O número deste item com devolução totalmente concluída e aprovada. |

### orderShippingCompleted

| Descrição | Nome do evento XDM |
|---|---|
| Acionado quando uma remessa é concluída. | `commerce.backofficeOrderShipmentCompleted` |

#### Dados coletados de orderShippingCompleted

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `commerce.order` | Contém informações sobre o pedido. |
| `commerce.order.purchaseID` | Identificador exclusivo atribuído pelo vendedor para esta compra ou contrato. Não há garantia de que a ID seja exclusiva. |
| `commerce.order.payments` | A lista de pagamentos deste pedido. |
| `commerce.order.payments.paymentTransactionID` | Identificador exclusivo desta transação de pagamento. |
| `commerce.order.payments.paymentAmount` | O valor do pagamento. |
| `commerce.order.payments.paymentType` | O método de pagamento deste pedido. Valores personalizados enumerados são permitidos. |
| `commerce.order.payments.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `commerce.order.taxAmount` | O valor do imposto pago pelo comprador como parte do pagamento final. |
| `commerce.order.createdDate` | A hora e a data em que um novo pedido é criado no sistema de comércio. Por exemplo, `2022-10-15T20:20:39+00:00`. |
| `commerce.shipping` | Detalhes de remessa de um ou mais produtos. |
| `commerce.shipping.shippingMethod` | O método de entrega escolhido pelo cliente, como entrega padrão, entrega expressa, retirada na loja e assim por diante. |
| `commerce.shipping.shippingAmount` | O valor que o cliente teve de pagar pelo envio. |
| `commerce.shipping.shipDate` | A data em que um ou mais itens de uma ordem são entregues. |
| `commerce.shipping.address` | O endereço físico de entrega. |
| `commerce.shipping.address.street1` | Informações no nível da rua principal, número do apartamento, número da rua e nome da rua. |
| `commerce.shipping.address.street2` | Segunda linha opcional de informações da rua. |
| `commerce.shipping.address.city` | O nome da cidade. |
| `commerce.shipping.address.state` | O nome do Estado. Este é um campo de forma livre. |
| `commerce.shipping.address.postalCode` | O código postal da localização. Os códigos postais não estão disponíveis para todos os países. Em alguns países, conterá apenas parte do código postal. |
| `commerce.shipping.address.country` | O nome do território administrado pelo governo. Exceto `xdm:countryCode`, este é um campo de formato livre que pode ter o nome do país em qualquer idioma. |
| `commerce.billing.address` | Endereço postal para cobrança. |
| `commerce.billing.address.street1` | Informações no nível da rua principal, número do apartamento, número da rua e nome da rua |
| `commerce.billing.address.street2` | Campo adicional para informações no nível da rua. |
| `commerce.billing.address.city` | O nome da cidade. |
| `commerce.billing.address.state` | O nome do estado. Este é um campo de forma livre. |
| `commerce.billing.address.postalCode` | O código postal da localização. Os códigos postais não estão disponíveis para todos os países. Em alguns países, conterá apenas parte do código postal. |
| `commerce.billing.address.country` | O nome do território administrado pelo governo. Exceto `xdm:countryCode`, este é um campo de formato livre que pode ter o nome do país em qualquer idioma. |
| `personalEmail` | Um endereço de email pessoal. |
| `personalEmail.address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes. |
| `productListItems` | Uma variedade de produtos no pedido. |
| `productListItems.SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `productListItems.name` | O nome de exibição ou o nome legível do produto. |
| `productListItems.priceTotal` | O preço total do item de linha do produto. |
| `productListItems.quantity` | O número de unidades de produto no carrinho. |
| `productListItems.discountAmount` | Indica o valor de desconto aplicado. |
| `productListItems.currencyCode` | A variável [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado, como `USD` ou `EUR`. |
| `productListItems.selectedOptions` | Campo usado para um produto configurável. |
| `productListItems.selectedOptions.attribute` | Identifica um atributo do produto configurável, como `size` ou `color`. |
| `productListItems.selectedOptions.value` | Identifica o valor do atributo, como `small` ou `black`. |
| `productListItems.categories` | Contém informações sobre a categoria de um produto. |
| `productListItems.categories.id` | O identificador exclusivo da categoria. |
| `productListItems.categories.name` | O nome da categoria. |
| `productListItems.categories.path` | O caminho para a categoria. |
