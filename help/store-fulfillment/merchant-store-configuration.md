---
title: Configuração de lojas de merchant
description: Configure fontes aprimoradas do Inventory management como lojas de merchant.
role: User, Admin
level: Intermediate
exl-id: 7c3444d0-5ecb-4ac1-aa81-e48eea290f5d
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '1209'
ht-degree: 0%

---

# Configuração de Lojas de Merchant (Origem)

Essa solução aprimora os recursos nativos do Inventory management estendendo as fontes de estoque com recursos orientados a operações para comerciantes.

- Adicionar coordenadas geográficas para a localização da loja
- Designar a fonte como uma [!DNL Store Pickup Location] e especificar recursos de entrega disponíveis (Entregar para Loja, Entregar de Loja)
- Especifique as opções de retirada disponíveis (na loja ou no lado da curinga), as instruções de retirada personalizadas e outras informações para comunicar detalhes e instruções de retirada aos clientes

Os termos _source_ e _localização da loja de merchant_ são utilizadas permutavelmente. Todos os registros são fontes de inventário, mas as fontes também podem ser locais de armazenamento de merchant, dependendo das configurações.

Gerencie a configuração das Lojas de merchant no Administrador: **[!UICONTROL Stores > Inventory > Sources >  Edit Source]**.

>[!NOTE]
>
>Durante o processo de configuração, pode ser necessário liberar o cache após criar fontes ou atualizar as fontes existentes.

## **Geral**

<table>
<tbody>
<tr>
<th>Campo</th>
<th>Descrição</th>
<th>Escopo</th>
<th>Obrigatório</th>
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>Coordenada latitudinal da localização da loja do comerciante. Essas informações necessárias são usadas na pesquisa de local e na colocação de mapa na experiência de loja. O valor deve corresponder ao endereço exato do armazenamento para passar na validação.</td>
<td>Global</td>
<td>Sim</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>Coordenadas longitudinais da localização do armazenamento comercial. Essas informações necessárias são usadas na pesquisa de local e na colocação de mapa na experiência de loja. O valor deve corresponder ao endereço exato do armazenamento para passar na validação.</td>
<td>Global</td>
<td>Sim</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>Designe a origem como um local disponível da retirada da loja. Essa configuração determina se a origem é sincronizada e exibida para os visitantes.</td>
<td>Global</td>
<td>Não</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong><br><code>Extension Attribute: allow_ship_to_store</code></td>
<td>Configure recursos de entrega para loja no nível de origem. Para obter mais informações, consulte a opção [General Configuration](enable-general.md) , <strong>[!UICONTROL Enable Ship To Store]
</tr>
<tr>
<td><strong>[!UICONTROL Latitude]</strong></br><code>Base Attribute: latitude</code></td>
<td>Coordenada latitudinal da localização da loja do comerciante. Essas informações necessárias são usadas na pesquisa de local e na colocação de mapa na experiência de loja. O valor deve corresponder ao endereço exato do armazenamento para passar na validação.</td>
<td>Global</td>
<td>Sim</td>
</tr>
<tr>
<td><strong>[!UICONTROL Longitude]</strong></br><code>Base Attribute: Longitude</code></td>
<td>Coordenadas longitudinais da localização do armazenamento comercial. Essas informações necessárias são usadas na pesquisa de local e na colocação de mapa na experiência de loja. O valor deve corresponder ao endereço exato do armazenamento para passar na validação.</td>
<td>Global</td>
<td>Sim</td>
</tr>
<tr>
<td><strong>[!UICONTROL Use as Pickup Location]</br></strong><code>Base Attribute: is_pickup_location_active</code></td>
<td>Designe a origem como um local disponível da retirada da loja. Essa configuração determina se a origem é sincronizada e exibida para os visitantes.</td>
<td>Global</td>
<td>Não</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship to Store]</strong></br> <code>Extension Attribute: [!DNL allow_ship_to_store]</code></td>
<td>Configure recursos de entrega para loja no nível de origem. Para obter mais informações, consulte a opção [General Configuration](enable-general.md) , <strong>[!UICONTROL Enable Ship To Store]</strong>.</td>
<td>Global</td>
<td>Não</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></br><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td>
 <td>Configure recursos de entrega da loja no nível de origem. Para obter mais informações, consulte a opção [General Configuration](enable-general.md) , [!UICONTROL Enable Ship From Store].</td>
<td>Global</td>
<td>Não</td>
</tr>
<tr>
<td>Global</td>
<td>Não</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong><code>Extension Attribute: [!DNL use_as_shipping_source]</code></td><td></td><td></td><td></td></tr></tbody></table>



| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Latitude]**</br>`Base Attribute: latitude` | Coordenada latitudinal da localização da loja do comerciante. Essas informações necessárias são usadas na pesquisa de local e na colocação de mapa na experiência de loja. O valor deve corresponder ao endereço exato do armazenamento para passar na validação. | Global | Sim |
| **[!UICONTROL Longitude]**</br>`Base Attribute: Longitude` | Coordenadas longitudinais da localização do armazenamento comercial. Essas informações necessárias são usadas na pesquisa de local e na colocação de mapa na experiência de loja. O valor deve corresponder ao endereço exato do armazenamento para passar na validação. | Global | Sim |
| **[!UICONTROL Use as Pickup Location]**</br>`Base Attribute:[!DNL is_pickup_location_active]` | Designe a origem como um local disponível da retirada da loja. Essa configuração determina se a origem é sincronizada e exibida para os visitantes. | Global | Não |
| **[!UICONTROL Enable Ship to Store]**</br>`Extension Attribute: [!DNL allow_ship_to_store]` | Configure recursos de entrega para loja no nível de origem. Para obter mais informações, consulte o [Configuração geral](enable-general.md) , **[!UICONTROL Enable Ship To Store]**. | Global | Não |
| **[!UICONTROL Enable Ship From Store]**</br>`Extension Attribute: [!DNL use_as_shipping_source]` | Configure recursos de entrega da loja no nível de origem. Para obter mais informações, consulte o [Configuração geral](enable-general.md) , [!UICONTROL Enable Ship From Store] | Global | Não |

{style=&quot;table-layout:auto&quot;}

## Configuração do local de coleta

| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|-----------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Allow In-Store Pickup]**</br>`Extension Attribute: [!DNL store_pickup_enabled]` | Uma das duas opções de retirada. [!DNL In-Store Pickup] refere-se à capacidade de permitir que um cliente entre no local de armazenamento de merchant para recuperar sua ordem. </br></br>Quando ativada, essa opção pode ser apresentada ao cliente durante o check-out. </br></br>Essa opção também substitui a configuração global para [!UICONTROL Enable In-store Pickup] que foi configurado no [!UICONTROL Delivery Method] para [!UICONTROL In-store Pickup] | Global | Não |
| **Instruções de retirada na loja**</br>`Extension Attribute: store_pickup_instructions` | Uma mensagem personalizável entregue ao cliente na **Pedido pronto para retirada na loja** notificação por email. | Global | Não |
| **Permitir Curva**</br>`Extension Attribute: curbside_enabled` | Uma das duas opções de retirada. A entrega de lado a lado permite que um cliente estacione seu veículo em um ponto designado no local da loja de produtos. Nesse cenário, o pedido é entregue ao cliente por um associado de loja. </br></br>Quando ativada, essa opção pode ser apresentada ao cliente durante o check-out. Além disso, o cliente pode ser convidado a descrever o seu veículo e o seu local de estacionamento durante o processo de check-in. </br></br>Essa opção também substitui a configuração global para **Ativar a retirada do lado do cursor** que foi configurado no **Método de entrega** para **Coleta na loja** | Global | Não |
| **[!UICONTROL Curbside Instructions]**</br>`Extension Attribute: curbside_instructions` | Uma mensagem personalizável entregue ao cliente na [!UICONTROL Order Ready For Pickup in Store] notificação por email. | Global | Não |
| **[!UICONTROL Estimated Pickup Lead Time]**</br>`Extension Attribute: pickup_lead_time` | O número de minutos necessários antes do recebimento, seleção e preparação de um pedido. </br></br>Essas informações são usadas para exibir horários estimados para a retirada de pedidos para clientes no site.</br></br> A configuração dessa opção substitui a configuração global para **Lead Time de retirada estimado** configurado para o **Método de entrega** no **Coleta na loja** configuração. | Global | Não |
| **[!UICONTROL Estimated Pickup Time Label]**</br>`Extension Attribute: pickup_time_label` | Rótulo que exibe o número de minutos até que um pedido esteja pronto para ser selecionado.</br></br> Ao personalizar este rótulo, você pode usar o código %1 para inserir seu **Lead Time de retirada estimado**.</br></br> A configuração dessa opção substitui a configuração global para [!UICONTROL Estimated Pickup Time Label] configurado para o [!UICONTROL Delivery Method] no [!UICONTROL In-store Pickup]. | Global | Não |

### **Horas de abertura**

| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Location Timezone]**</br>`Extension Attribute: timezone` | O fuso horário da localização do armazenamento de produtos. Para cada dia, defina as horas de abertura e fechamento.</br></br>Essas configurações são usadas para otimizar os tempos estimados de retirada e nos relatórios do serviço de cumprimento. | Global | Sim |
| **[!UICONTROL Opening Hours]**</br>`Internal Attribute: inventory_source_opening_hours_dynamic_rows` | O horário de funcionamento do local da loja de merchant. </br></br>Essas informações podem ser usadas para otimizar os tempos estimados de retirada e nos relatórios do serviço de cumprimento. | Global | Sim |

### Configurar as opções da interface da experiência de check-in



| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|---------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Use Parking Spots]**</br>`Extension Attribute: parking_spots_enabled` | Especifique se o local da loja de merchant tem locais de estacionamento designados para coleta de lado. </br></br>Quando ativado, você pode configurar pontos de estacionamento disponíveis. | Global | Não |
| **[!UICONTROL Is Parking Spot a Mandatory Field?]**</br>`Extension Attribute: parking_spot_mandatory` | Especifique se a identificação do ponto de estacionamento é necessária para clientes durante a experiência de compra.</br></br>Se estiver habilitado, o cliente será solicitado a especificar seu local de estacionamento à chegada. Se estiver desativado, o cliente poderá ignorar esta entrada. | Global | Não |
| **[!UICONTROL Parking Spots List]**</br> `Internal Attribute: inventory_source_parking_spot_dynamic_rows` | Os lugares de estacionamento disponíveis neste local de loja de produtos para a recolha de curbside. Use a interface fornecida para nomear cada ponto.</br></br> Não é necessário nomear cada ponto de estacionamento, apenas os pontos designados para o lado da orla. Por exemplo, você pode ter linhas A-G de estacionamento disponíveis, mas apenas os primeiros 8 pontos da linha A são designados para retirada de lado da curva. Nesse cenário, você pode definir 8 pontos; ex: A1, A2, A3 e assim por diante. | Global | Não |
| **[!UICONTROL Allow "Other" Parking Spot Field]**</br>`Extension Attribute: custom_parking_spot_enabled` | Quando ativada, essa configuração permite que o cliente descreva o local de estacionamento durante a Check-in. | Global | Não |
| **[!UICONTROL Use Car Color]**</br>`Extension Attribute: use_car_color` | Especifique se deseja oferecer suporte à coleção de cores do veículo do cliente durante a Check-in. </br></br> As seleções disponíveis para [!UICONTROL Car Color] são configuradas no Administrador [configurações do sistema para a experiência de check-in](check-in-experience-setup.md). | Global | Não |
| **[!UICONTROL Is Car Color a Mandatory Field?]**</br>`Extension Attribute: car_color_mandatory` | Especifique se a identificação da cor do veículo é necessária para os clientes durante a Entrada.</br></br>Se estiver habilitado, o cliente será solicitado a especificar a cor do veículo à chegada. Se estiver desativado, o cliente poderá ignorar esta entrada. | Global | Não |
| **[!UICONTROL Use Car Make]** </br>`Extension Attribute: use_car_make` | Especifique se deseja oferecer suporte à coleção de veículos feitos pelo cliente durante o Check-in.</br></br> As seleções disponíveis para [!UICONTROL Car Make] são configuradas no Administrador [configurações do sistema para a experiência de check-in](check-in-experience-setup.md). | Global | Não |
| **[!UICONTROL Is Car Make a Mandatory Field?]**</br>`Extension Attribute: car_make_mandatory` | Especifique se a identificação da marca de veículo é necessária para os clientes durante a Check-in.</br></br>Se estiver habilitado, o cliente será solicitado a especificar a marca do veículo à chegada. Se estiver desativado, o cliente poderá ignorar esta entrada. | Global | Não |
| **[!UICONTROL Use Additional Information]**</br> `Extension Attribute: use_additional_information` | Especifique se deseja oferecer suporte à coleta de informações adicionais do cliente durante o Check-in. | Global | Não |
| **[!UICONTROL Is Additional Information a Mandatory Field?]**</br>`Extension Attribute: additional_information_mandatory` | Especifique se são necessárias informações adicionais para os clientes durante o Check-in. </br></br>Se estiver habilitado, será solicitado ao cliente que insira informações adicionais na chegada. Se estiver desativado, o cliente poderá ignorar esta entrada. | Global | Não |
