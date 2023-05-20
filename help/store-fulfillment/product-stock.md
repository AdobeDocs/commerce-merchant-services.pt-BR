---
title: Gerenciamento de Estoque de Produtos
description: Configurar as mensagens e os recursos do estoque de comerciantes disponíveis para os clientes.
role: User, Admin
level: Intermediate
exl-id: 3ac217f7-e823-4578-8416-5ecceb76aa87
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# Gerenciamento de Estoque de Produtos

Como comerciante, você pode usar o Adobe Commerce [Inventory management](https://docs.magento.com/user-guide/catalog/inventory-management.html) opções de estoque e origem. Além disso, você pode usar a solução Store Fulfillment para controlar outras opções de disponibilidade de estoque relacionadas às operações de sua loja de comerciantes.

- Opção de entrega doméstica de lojas comerciantes

- Permitir/Disponível para retirada de loja

- UPC / SKU / Outros identificadores exclusivos do produto

- Limite de Fora do Estoque

- Diminuindo o Inventário a partir de locais específicos na ordem

Configure as opções de Estoque de produtos no Administrador: **[!UICONTROL Catalog > Products > Select Product]**

## **Opções de estoque do produto**

| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------|
| **Disponível para entrega inicial** | Define a disponibilidade da Distribuição inicial (Entrega da loja) do produto. Quando ativado, qualquer local de loja do comerciante atribuído com estoque disponível para o produto é considerado qualificado para a opção Entrega doméstica. Quando essa opção está desativada, o produto nunca é qualificado para a Entrega inicial.</br></br>Na maioria dos casos, definir essa opção no nível da loja de comerciante é suficiente. No entanto, pode haver casos únicos de produtos específicos, como aqueles sob restrições federais de envio, que não devem ser qualificados para Entrega doméstica. | Site | Não |
| **[!UICONTROL Available for Store Pickup]** | Defina a disponibilidade da Seleção da loja para o produto. Quando habilitado, qualquer local de loja de comerciante atribuído com estoque disponível para o produto é considerado qualificado para a opção Retirada da loja. Quando desativado, o produto nunca está qualificado para Coleta na loja.</br></br>Essa opção pode ser útil para rastrear o inventário do comerciante no sistema que você não deseja vender do seu canal de comércio eletrônico. | Site | Não |
| **[!UICONTROL UPC / SKU / Custom Scannable Identifier]** | Este atributo já deve existir como um atributo de produto e está relacionado a **[!UICONTROL Barcode Source / Barcode Type]** configuração. Esse atributo é usado para rastrear um código de barras digitalizável para seus produtos. Esse valor pode ser enviado quando um pedido é enviado às lojas de comerciantes para separação. Os associados da loja podem usar o valor com a lista de separação para corresponder produtos na prateleira usando um scanner de código de barras. | Exibição da loja | Não |

{style="table-layout:auto"}

## Origens para estoque no nível de produto

| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|-----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Out of Stock Threshold]** | Defina o limite de estoque para o item em cada origem. Quando o estoque cai abaixo do limite, ele é considerado esgotado na origem.</br></br>Para usar a configuração global da loja, marque a opção **[!UICONTROL Use Default]** opção. | Global | Não |
| **[!UICONTROL Allow Store Pickup]** | Defina explicitamente se o item está disponível para retirada de armazenamento, independentemente da configuração disponível de estoque ou localização de armazenamento do comerciante.</br></br> Para usar a configuração de nível de produto, desmarque a opção [!UICONTROL Use Default] e faça sua seleção. Caso contrário, essa configuração será escolhida com base na configuração de **[!UICONTROL Allow In-Store Pickup]** que é definido na origem do estoque. | Global | Não |

{style="table-layout:auto"}

