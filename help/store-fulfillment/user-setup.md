---
title: Configuração do usuário
description: 'Configure fontes aprimoradas do Inventory management como lojas de merchant. '
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# Configuração do usuário

Os usuários do aplicativo Store Assist são gerenciados no Adobe Commerce. No entanto, esses usuários não interagem diretamente com a Adobe Commerce. O gerenciamento de usuários é configurado no Adobe Commerce para habilitar conexões seguras entre o Adobe Commerce e o aplicativo.

O modelo Usuário do aplicativo de preenchimento da loja é separado de outros modelos de usuário do Adobe Commerce. O aplicativo mantém seu próprio modelo de permissão por meio de funções de usuário e usuários que podem ser atribuídos a todos os locais ou a locais específicos. As seguintes permissões são suportadas: Ordem de separação, Ordem de dispensa e Redução de quantidade de item (e cancelamento).

>[!TIP]
>
>Para obter melhores resultados, [configurar a conexão](connect-set-up-service.md) antes de adicionar usuários e permissões para a Store Associates que usam o aplicativo Store Assist.

## Aplicativo de assistência da loja - Funções do usuário

Durante a configuração inicial do usuário para o aplicativo de assistência da loja, crie funções de usuário para personalizar permissões de usuário para o aplicativo de assistência da loja. Por exemplo, você pode criar funções diferentes para gerentes de loja e associados de loja e atribuir recursos de função diferentes para gerenciar permissões para cada tipo de usuário.

Configurar funções de usuário de **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]**.

### Informações da função

| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|----------------------------|-------------------------|-----------|--------------|
| **[!UICONTROL Role Name]** | Ative ou desative o usuário. | Global | Sim |

### Recursos de função

| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Resource Access]** | Liste os grupos de permissões disponíveis que podem ser atribuídos a uma função de usuário. No momento, a Solução de disponibilização de armazenamento não tem diferentes níveis de permissão definidos para funções de recursos. Todas as funções de usuário têm o mesmo acesso a recursos. | Global | Sim |

## Auxiliar de armazenamento - Informações do usuário

Gerencie perfis de usuário do aplicativo de assistência da loja nas configurações do Sistema de administração:  **[!UICONTROL System > Store Fulfillment App Permissions > All Store Fulfillment App Users]**.


| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL is Active]** | Ative ou desative o usuário. | Global | Sim |
| **[!UICONTROL User Name]** | Nome de usuário associado ao usuário | Global | Sim |
| **[!UICONTROL First Name]** | Nome associado ao usuário | Global | Não |
| **[!UICONTROL Last Name]** | Sobrenome associado ao usuário | Global | Não |
| **[!UICONTROL Role]** | Função associada ao usuário | Global | Não |
| **[!UICONTROL Access to all locations]** | Atribua aos usuários acesso a todas as lojas ou selecione lojas individualmente. | Global | Não |
| **Localidade da interface** | Se a loja tiver vários idiomas, defina a Localidade da interface para o idioma a ser usado na interface do Administrador. | Global | Não |
| **Ativo de** | Para definir uma data inicial, selecione o ícone de calendário. | Global | Não |
| **Ativo para** | Defina a Data de expiração selecionando o ícone do calendário. Definir uma data de expiração é útil para configurar atribuições temporárias de usuário ou função. Após a data de expiração, o status da conta de usuário é alterado para `Inactive`, mas a conta ainda pode ser atualizada, se necessário. | Global | Não |





