---
title: Transferência de origem do Inventory management
description: '"Configure os estoques para o [!DNL Store Fulfillment solution] com o Adobe Commerce Inventory management. Configure um novo estoque e transfira o inventário do estoque padrão para que você possa atribuí-lo a fontes configuradas para ativar os recursos de Coleta da loja exigidos pela solução de Encerramento da loja."'
role: User, Admin
level: Intermediate
exl-id: 669d4dce-4cac-4bde-acc5-26c70a51f7f1
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---


# Transferência de origem do Inventory management

O [!DNL Store Fulfillment] A solução usa a Adobe Commerce Inventory management nativa. Por padrão, a variável [!DNL Commerce] a configuração atribui todo o inventário da Web ao estoque padrão, que não pode ter fontes adicionais atribuídas. Como um site só pode receber um único estoque, um comerciante deve configurar um novo estoque e, opcionalmente, transferir seu inventário de origem padrão para uma origem que esteja atribuída ao escopo apropriado. Em seguida, a fonte pode ser atribuída ao novo estoque.

Essas alterações de configuração ajudam você a realizar três tarefas:

1. [Transferir inventário para origem](https://docs.magento.com/user-guide/catalog/inventory-bulk-transfer-inventory.html) para mover o inventário do estoque/origem padrão para o novo estoque/origem.

1. [Atribuir fontes em massa](https://docs.magento.com/user-guide/catalog/inventory-bulk-assign-sources.html) para adicionar as novas fontes para todos os seus produtos.

1. [Atualizações em massa completas para atributos de produto](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html) para adicionar o `Allow Store Pickup` e `Allow Home Delivery` para produtos existentes. Quando a solução é instalada, os atributos têm o melhor *default* valores. No entanto, esses atributos não são aplicados aos produtos existentes até que você conclua o processo de atualizações em massa.

O inventário é deduzido da origem selecionada (local de loja de varejo ou depósito de comércio eletrônico). As origens usadas como depósitos de comércio eletrônico devem ser atribuídas ao mesmo estoque que o local de retirada da loja e priorizadas antes dos locais de varejo. Para obter mais informações, consulte [Priorização de Fontes para um Estoque](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html).

Para obter mais informações sobre gerenciamento de inventário, estoques e fontes, consulte a documentação do usuário do Adobe Commerce:

- [Gerenciamento de inventário](https://docs.magento.com/user-guide/catalog/inventory-management.html)

- [Gerenciando Quantidades de Inventário](https://docs.magento.com/user-guide/catalog/inventory-manage-inventory-quantities.html)

- [Gerenciamento de estoque](https://docs.magento.com/user-guide/catalog/inventory-stock.html)

- [Gerenciar fontes](https://docs.magento.com/user-guide/catalog/inventory-sources.html)

- [Priorização de Fontes para um Estoque](https://docs.magento.com/user-guide/catalog/inventory-stock-priority.html)

- [Atualizações em massa para atributos de produto](https://docs.magento.com/user-guide/stores/bulk-product-attribute-update.html)


>[!IMPORTANT]
>
>Alterar a configuração de inventário e fontes de estoque também pode ter impacto downstream em sistemas integrados. Certifique-se de entender como as alterações na configuração do inventário afetam esses sistemas.
