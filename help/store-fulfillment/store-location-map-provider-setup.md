---
title: Localização de armazenamento e configuração do sistema de mapeamento
description: Configure um provedor de distância para oferecer suporte ao mapeamento de localização de loja na interface de loja. As soluções de Atendimento da Loja exigem um provedor à distância para habilitar a pesquisa na loja de varejo e outros recursos de mapeamento e agendamento para o fluxo de trabalho de atendimento completo.
role: User, Admin
level: Intermediate
exl-id: d09c4652-e2eb-49dc-8c42-2aa9b6be5d6b
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Localização de armazenamento e configuração de mapeamento

Habilite o local de armazenamento e os recursos de mapeamento para Atendimento de Loja configurando um [provedor de distância](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html) para pesquisar locais de loja de varejo.

**Requisitos**

Durante o processo de configuração, você fornece uma chave de API do Google para a plataforma Google Maps. Se você não tiver um, [gerar um a partir da plataforma Google Maps](https://docs.magento.com/user-guide/catalog/inventory-configure-distance-priority.html#configure-google-maps).

Para configurar o provedor de distância:

1. No **[!UICONTROL Stores > General]** em Admin, adicione a integração do Google Maps para o tipo de conteúdo Map.

   - Ir para **[!UICONTROL Stores > Configuration  > General > Content Management]**.

   - Adicione sua chave de API do Google a **[!UICONTROL Google Maps API Key]** campo.

1. No **[!UICONTROL Stores > Inventory]** em Admin, selecione o provedor de distância para Atendimento da Loja.

   - Ir para **[!UICONTROL Stores > Configuration > Catalog > Inventory]**.

   - Expanda a **[!UICONTROL Distance Provider for Distance Based SSA]** seção.

   - Defina o **Provedor** para **Mapa do Google**.

1. Definir configurações para o **[!UICONTROL Google Distance Provider]**.

   - Adicione **Chave da API do Google**.

   - Definir **[!UICONTROL Computation Mode]** para `Driving` e **[!UICONTROL Value]** para `Distance`
