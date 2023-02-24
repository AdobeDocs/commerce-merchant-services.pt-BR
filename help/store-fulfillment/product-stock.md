---
title: Gerenciamento de estoque de produtos
description: Configure as mensagens de estoque do comerciante e os recursos disponíveis para os clientes.
role: User, Admin
level: Intermediate
exl-id: 3ac217f7-e823-4578-8416-5ecceb76aa87
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# Gerenciamento de estoque de produtos

Como comerciante, você pode usar o Adobe Commerce [Inventory management](https://docs.magento.com/user-guide/catalog/inventory-management.html) opções de estoque e origem. Além disso, você pode usar a solução de Abastecimento da Loja para controlar outras opções de disponibilidade de inventário relacionadas às operações da loja de merchant.

- Opção de entrega em casa de lojas Merchant

- Permitir/Disponível para a Coleta da Loja

- UPC / SKU / Outros identificadores de produto exclusivos

- Limite esgotado

- Redução do Inventário a partir de locais específicos sob pedido

Configure as opções de Estoque de produtos em Admin: **[!UICONTROL Catalog > Products > Select Product]**

## **Opções de Estoque de Produtos**

| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------|
| **Disponível para entrega em casa** | Define a disponibilidade da Entrega principal (Entrega da loja) para o produto. Quando ativadas, quaisquer locais de loja de merchant atribuídos com inventário disponível para o produto são considerados elegíveis para a opção Entrega inicial. Quando essa opção está desativada, o produto nunca é qualificado para Entrega inicial.</br></br>Na maioria dos casos, definir essa opção no nível da loja do comerciante é suficiente. No entanto, pode haver casos únicos para produtos específicos, como os sujeitos a restrições de envio federais, que não devem ser qualificados para Entrega Doméstica. | Site | Não |
| **[!UICONTROL Available for Store Pickup]** | Defina a disponibilidade da retirada da loja para o produto. Quando ativado, quaisquer locais de loja de merchant atribuídos com inventário disponível para o produto são considerados elegíveis para a opção Coleta da loja. Quando desativado, o produto nunca é qualificado para a retirada da loja.</br></br>Essa opção pode ser útil para rastrear o inventário comercial no sistema que você não deseja vender do seu canal de comércio eletrônico. | Site | Não |
| **[!UICONTROL UPC / SKU / Custom Scannable Identifier]** | Esse atributo já deve existir como um atributo de produto e está relacionado a **[!UICONTROL Barcode Source / Barcode Type]** configuração. Esse atributo é usado para rastrear um código de barras scannable para seus produtos. Esse valor pode ser enviado quando um pedido é enviado às suas lojas de merchant para separação. Os associados de armazenamento podem usar o valor com a lista de separação para corresponder produtos na estante usando um scanner de código de barras. | Exibição da loja | Não |

{style=&quot;table-layout:auto&quot;}

## Fontes para o inventário no nível do produto

| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|-----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Out of Stock Threshold]** | Defina o limite de estoque para o item em cada origem. Quando o estoque cair abaixo do limite, ele será considerado esgotado na origem.</br></br>Para usar a configuração de armazenamento global, marque a opção **[!UICONTROL Use Default]** opção. | Global | Não |
| **[!UICONTROL Allow Store Pickup]** | Defina explicitamente se o item está disponível para retirada de loja, independentemente da configuração de inventário ou local de loja de merchant disponível.</br></br> Para usar a configuração de nível de produto, desmarque a opção [!UICONTROL Use Default] e faça sua seleção. Caso contrário, essa configuração será escolhida com base na configuração de **[!UICONTROL Allow In-Store Pickup]** que é definido na fonte de estoque. | Global | Não |

{style=&quot;table-layout:auto&quot;}

