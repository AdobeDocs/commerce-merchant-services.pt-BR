---
title: Configuração de vários sites e escopos
description: Configure estoques e métodos de entrega para vários sites e escopos de loja.
role: Admin
level: Experienced
feature: Shipping/Delivery, Inventory, Configuration
exl-id: 8939046e-1c26-4380-83be-ff8e074e591d
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '181'
ht-degree: 0%

---

# Configuração de vários sites e escopos

Você pode definir o [Escopo](https://docs.magento.com/user-guide/configuration/scope.html) para alguns elementos para acomodar vários sites, lojas e visualizações de loja:

- [Gerenciar Estoque](https://docs.magento.com/user-guide/catalog/inventory-stock.html) por escopo

- Gerenciar [!DNL Delivery Methods] por escopo

Você pode atribuir estoque a um site ou escopo de loja. Em seguida, atualize as fontes da loja para definir os métodos de entrega disponíveis (entrega doméstica, retirada da loja).

Depois de atualizar a configuração com êxito, as opções de retirada da loja na página de detalhes do produto (PDP) na loja da Adobe Commerce podem ser selecionadas apenas para produtos disponíveis em uma fonte de estoque que permite a retirada da loja.

## Gerenciar configurações de retirada na loja

Habilite ou desabilite as opções [!UICONTROL In-Store Pickup] para cada escopo de site ou de repositório a partir das [Configurações do Método de Entrega](enable-general.md#delivery-methods) no Administrador.

1. Navegue até **[!UICONTROL Stores > Configuration]**.

1. Selecione o escopo (Site a ser Armazenado) a ser configurado.

1. Com o escopo selecionado, navegue até **[!UICONTROL Sales > Delivery Methods]**.

1. Desabilite ou habilite o método de entrega **[!UICONTROL In-Store Pickup]**.

Você também pode gerenciar se a coleta na berma ou na loja está disponível globalmente nesta seção.

Gerenciar as configurações de [!UICONTROL In-Store Pickup] e [!UICONTROL Delivery Method] por fonte de estoque. Existem várias outras configurações para obter total flexibilidade sobre sua implementação.
