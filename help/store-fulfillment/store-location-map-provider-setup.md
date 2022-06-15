---
title: Localização do armazenamento e configuração do sistema de mapeamento
description: Configure um provedor de distância para oferecer suporte ao mapeamento de localização da loja na interface do usuário da loja. As soluções de fornecimento de armazenamento exigem um provedor de distância para permitir a pesquisa em lojas de varejo e outros recursos de mapeamento e agendamento para o fluxo de trabalho de cumprimento completo.
role: User, Admin
level: Intermediate
source-git-commit: 42b0118b427b1e04186793b4a57c058bc1cabdd4
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---


# Configuração de localização e mapeamento do armazenamento

Ative o local da loja e os recursos de mapeamento para o Cumprimento da loja configurando um [fornecedor de distância](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) para procurar locais de loja de varejo.

**Requisitos**

Durante o processo de configuração, você fornece uma chave de API do Google para a plataforma Google Maps . Se não tiver um, [gerar um da plataforma Google Maps](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

Para configurar o provedor de distância:

1. No [!UICONTROL Stores > General] no Admin, adicione a integração Google Maps para o tipo de conteúdo Map .

   - Ir para **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - Adicionar sua chave de API do Google a **[!UICONTROL Google Maps API Key]** campo.

1. No [!UICONTROL Stores > Inventory] na configuração Admin, selecione o provedor de distância para o Cumprimento da Loja.

   - Ir para **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - Expanda o **[!UICONTROL Distance Provider for Distance Based SSA]** seção.

   - Defina as **Provedor** para **Google Map**.

1. Defina as configurações para o **[!UICONTROL Google Distance Provider]**.

   - Adicione seu **Chave da API do Google**.

   - Definir **[!UICONTROL Computation Mode]** para `Driving` e **[!UICONTROL Value]** para `Distance`
