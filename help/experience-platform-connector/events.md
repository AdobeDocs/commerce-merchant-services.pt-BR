---
title: Eventos
description: Saiba quais dados cada evento captura e visualize a definição completa do esquema.
exl-id: b0c88af3-29c1-4661-9901-3c6d134c2386
source-git-commit: 589d22f488572411b6632ac37d7bc5b752f72e2d
workflow-type: tm+mt
source-wordcount: '1818'
ht-degree: 0%

---

# Experience Platform Connector Events

Abaixo encontram-se os eventos Commerce disponíveis quando você instala a extensão Experience Platform connector . Os dados que esses eventos coletam são enviados para a borda do Adobe Experience Platform. Você também pode criar [eventos personalizados](custom-events.md) para coletar dados adicionais não fornecidos imediatamente.

Além dos dados que os eventos a seguir coletam, você também obtém [dados adicionais](https://experienceleague.adobe.com/docs/experience-platform/edge/data-collection/automatic-information.html) fornecido pelo SDK da Web da Adobe Experience Platform.

>[!NOTE]
>
>Todos os eventos incluem a variável `personID` , que é um identificador exclusivo da pessoa.

## addToCart

Disparado quando um produto é adicionado ao carrinho ou quando a quantidade de um produto no carrinho é aumentada. [Schema completo](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/addToCartAEP.ts).

### Tipo

Loja

### Dados coletados

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `productListAdds` | Indica se um produto foi adicionado a um carrinho de compras. Um valor de `1` indica que um produto foi adicionado. |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O total deste pedido após todos os descontos e impostos terem sido aplicados |
| `quantity` | O número de unidades que o cliente indicou que necessitam do produto |
| `discountAmount` | Indica a quantia de desconto aplicada |
| `currencyCode` | O [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moeda do produto |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |
| `cartID` | A ID exclusiva que identifica o carrinho do cliente |

## shoppingCartView

Disparado quando qualquer página de carrinho é carregada. [Schema completo](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/viewAEP.ts).

### Tipo

Loja

### Dados coletados

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `productListViews` | Indica se uma lista de produtos foi visualizada |
| `productListItems` | Uma matriz de produtos adicionados a um carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O total deste pedido após todos os descontos e impostos terem sido aplicados |
| `quantity` | O número de unidades que o cliente indicou que necessitam do produto |
| `discountAmount` | Indica a quantia de desconto aplicada |
| `currencyCode` | O [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moeda do produto |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |
| `cartID` | A ID exclusiva que identifica o carrinho do cliente |

## pageView

Disparado quando qualquer página é carregada. [Schema completo](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/page/viewAEP.ts).

### Tipo

Loja

### Dados coletados

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `pageViews` | Indica se uma página foi carregada. A `value` de `1` indica que a página foi carregada. |

## productPageView

Disparado quando qualquer página de produto é carregada. [Schema completo](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/product/viewAEP.ts).

### Tipo

Loja

### Dados coletados

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `productViews` | Indica se o produto foi exibido |
| `productListItems` | Uma matriz de produtos adicionados a um carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O total deste pedido após todos os descontos e impostos terem sido aplicados |
| `discountAmount` | Indica a quantia de desconto aplicada |
| `currencyCode` | O [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moeda do produto |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |

## startCheckout

Disparado quando o comprador clica em um botão de finalização. [Schema completo](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/shoppingCart/initiateCheckoutAEP.ts).

### Tipo

Loja

### Dados coletados

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `checkouts` | Indica se uma ação ocorreu durante o processo de finalização |
| `productListItems` | Uma matriz de produtos adicionados a um carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O total deste pedido após todos os descontos e impostos terem sido aplicados |
| `quantity` | O número de unidades que o cliente indicou que necessitam do produto |
| `discountAmount` | Indica a quantia de desconto aplicada |
| `currencyCode` | O [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) moeda do produto |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |
| `cartID` | A ID exclusiva que identifica o carrinho do cliente |

## completeCheckout

Disparado quando o comprador faz um pedido. [Schema completo](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/checkout/placeOrderAEP.ts).

### Tipo

Loja

### Dados coletados

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
| `productListItems` | Uma matriz de produtos adicionados a um carrinho de compras |
| `SKU` | Unidade de manutenção de estoque. O identificador exclusivo do produto. |
| `name` | O nome de exibição ou nome legível do produto |
| `priceTotal` | O total deste pedido após todos os descontos e impostos terem sido aplicados |
| `quantity` | O número de unidades que o cliente indicou que necessitam do produto |
| `discountAmount` | Indica a quantia de desconto aplicada |
| `currencyCode` | O [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217) código de moeda usado para os totais da ordem. |
| `productImageUrl` | URL da imagem principal do produto |
| `selectedOptions` | Campo usado para um produto configurável. `attribute` identifica um atributo do produto configurável, como `size` ou `color` e `value` identifica o valor do atributo, como `small` ou `black`. |

## signIn

Disparado quando um comprador tenta entrar. [Schema completo](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signInAEP.ts).

>[!NOTE]
>
> Esse evento é acionado quando a ação específica é tentada. Não indica que a ação foi bem sucedida.

### Tipo

Perfil

### Dados coletados

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

## signOut

Disparado quando um comprador tenta sair. [Schema completo](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/signOutAEP.ts).

>[!NOTE]
>
> Esse evento é acionado quando a ação específica é tentada. Não indica que a ação foi bem sucedida.

### Tipo

Perfil

### Dados coletados

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `eventType` | O tipo de evento principal para esse registro de série de tempo, como: `userAccount.logout` |
| `userAccount` | Indica quaisquer detalhes de fidelidade, preferências, processos de logon e outras preferências de conta |
| `logout` | Indica se um visitante tentou fazer logoff |

## createAccount

Disparado quando um comprador tenta criar uma conta. [Schema completo](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/createAccountAEP.ts).

>[!NOTE]
>
> Esse evento é acionado quando a ação específica é tentada. Não indica que a ação foi bem sucedida.

### Tipo

Perfil

### Dados coletados

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

## editAccount

Disparado quando um comprador tenta editar uma conta. [Schema completo](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/account/editAccountAEP.ts).

>[!NOTE]
>
> Esse evento é acionado quando a ação específica é tentada. Não indica que a ação foi bem sucedida.

### Tipo

Perfil

### Dados coletados

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

## searchRequestSent

Disparado pelos seguintes eventos no provedor &quot;pesquisar à medida que você digita&quot;:

- Pressione Enter
- Clique em _Exibir todos_

Disparado pelos seguintes eventos nas páginas de resultados da pesquisa:

- Selecionar um filtro
- Altere a ordem de classificação (_Ordenar por_)
- Alterar a direção da classificação (crescente ou decrescente)
- Alterar o número de resultados por página (_Mostrar número por página_)
- Navegue até a próxima página
- Navegar até a página anterior
- Navegar para uma página diferente

[Schema completo](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchRequestSentAEP.ts).

>[!NOTE]
>
>Os eventos de pesquisa não são suportados em uma Adobe Commerce Enterprise Edition com o módulo B2B instalado.

### Tipo

Pesquisar

### Dados coletados

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

## searchResponseReceived

Disparado quando o Live Search retorna resultados para a página de resultados de &quot;pesquisa ao digitar&quot; ou de pesquisa.

[Schema completo](https://github.com/adobe/magento-storefront-event-collector/blob/main/src/handlers/search/searchResponseReceivedAEP.ts)

>[!NOTE]
>
>Os eventos de pesquisa não são suportados em uma Adobe Commerce Enterprise Edition com o módulo B2B instalado.

### Tipo

Pesquisar

### Dados coletados

A tabela a seguir descreve os dados coletados para esse evento.

| Campo | Descrição |
|---|---|
| `searchResponse` | Indica se uma resposta de pesquisa foi recebida |
| `suggestions` | Uma matriz de sequências de caracteres que incluem os nomes de produtos e categorias existentes no catálogo que são semelhantes à consulta de pesquisa |
| `numberOfResults` | O número de produtos devolvidos |
| `productListItems` | Uma matriz de produtos adicionada a um carrinho de compras. Inclui o `SKU`(Unidade de manutenção de existências) e `name` do produto (nome de exibição ou nome legível). |
