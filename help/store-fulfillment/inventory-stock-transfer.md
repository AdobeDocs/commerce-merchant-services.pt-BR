---
title: Transferência do Inventory management Source
description: "Configure os estoques do  [!DNL Store Fulfillment solution]  com o Adobe Commerce Inventory management. Configure um novo estoque e transfira o estoque do estoque padrão para que você possa atribuí-lo às fontes configuradas para habilitar os recursos de Retirada da Loja exigidos pela solução de Atendimento da Loja."
role: Admin
level: Intermediate
feature: Shipping/Delivery, Inventory, Configuration
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Transferência do Inventory management Source

A solução [!DNL Store Fulfillment] usa o Adobe Commerce Inventory management nativo. Por padrão, a configuração [!DNL Commerce] atribui todo o inventário da Web ao estoque padrão, que não pode ter fontes adicionais atribuídas. Como um site só pode ter um único estoque atribuído, um comerciante deve configurar um novo estoque e, opcionalmente, transferir seu inventário de origem padrão para uma origem atribuída ao escopo apropriado. Em seguida, a origem pode ser atribuída ao novo estoque.

>[!IMPORTANT]
>
>Os comerciantes devem manter a fonte padrão para todos os produtos incluídos em grupos e tipos de produtos de pacote. Esses produtos precisam de uma quantidade de estoque que atenda ao limite de quantidade mínima para itens de estoque e inclua um status de estoque de [!UICONTROL In Stock].

Essas alterações de configuração ajudam você a realizar três coisas:

1. [Transferir estoque para origem](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) para mover o estoque padrão/origem para o novo estoque/origem.

1. [Atribuir fontes](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) em massa para adicionar as novas fontes para todos os seus produtos.

1. [Conclua as atualizações em massa dos atributos de produto](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) para adicionar os atributos `Allow Store Pickup` e `Allow Home Delivery` aos produtos existentes. Quando a solução é instalada, os atributos têm os *valores padrão* ideais. No entanto, esses atributos não são aplicados aos produtos existentes até que você conclua o processo de updaContes em massa.

O estoque é deduzido da origem selecionada (localização da loja de varejo ou depósito de comércio eletrônico). As origens usadas como depósitos de comércio eletrônico devem ser atribuídas ao mesmo estoque que o local de retirada da loja e priorizadas antes dos locais de varejo. Para obter informações adicionais, consulte [Priorizando fontes para um estoque](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html).

Para obter mais informações sobre gerenciamento de inventário, estoques e fontes, consulte a documentação do usuário do Adobe Commerce:

- [Gerenciando o inventário](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [Gerenciando Quantidades de Inventário](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [Gerenciando o Stock](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [Gerenciando fontes](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [Priorizando fontes para um estoque](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [Atualizações em massa para atributos de produto](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>A alteração da configuração para fontes de estoque e estoque também pode ter impacto downstream nos sistemas integrados. Certifique-se de entender como as alterações na configuração do inventário afetam esses sistemas.
