---
title: Várias configurações de site e escopo
description: Configure estoques e métodos de entrega para vários sites e escopos de armazenamento.
role: User, Admin
level: Intermediate
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---


# Várias configurações de site e escopo

É possível definir a variável [Escopo](https://docs.magento.com/user-guide/configuration/scope.html) para obter alguns elementos para acomodar vários sites, lojas e visualizações de loja:

- [Gerenciar estoque](https://docs.magento.com/user-guide/catalog/inventory-stock.html) por escopo

- Gerenciar [!DNL Delivery Methods] por escopo

Você pode atribuir estoque a um site ou escopo de loja. Em seguida, atualize as fontes de armazenamento para definir os métodos de delivery disponíveis (delivery inicial, retirada de loja).

Depois de atualizar a configuração com êxito, as opções de retirada da loja na página de detalhes do produto (PDP) na loja da Adobe Commerce podem ser selecionadas somente para produtos disponíveis em uma fonte de estoque que permite a retirada da loja.

## Gerenciar configurações de coleta na loja

Ative ou desative o [!UICONTROL In-Store Pickup] opções para cada site ou escopo de armazenamento da [Configurações do Método de Delivery](enable-general.md#delivery-methods) em Admin.

1. Navegar para **[!UICONTROL Stores > Configuration]**.

1. Selecione o escopo (Site a ser armazenado) a ser configurado.

1. Com o escopo selecionado, navegue até **[!UICONTROL Sales > Delivery Methods]**.

1. Desative ou ative o **[!UICONTROL In-Store Pickup]** Método de delivery.

Você também pode gerenciar se a coleta em curbside ou na loja está disponível globalmente nesta seção.

Gerencie o [!UICONTROL In-Store Pickup] e [!UICONTROL Delivery Method] configurações por fonte de estoque. Existem várias outras configurações para proporcionar flexibilidade total sobre sua implementação.
