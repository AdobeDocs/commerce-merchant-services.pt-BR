---
title: Visão Geral da Configuração para Atendimento da Loja
description: Saiba mais sobre os tipos de definições de configuração de Administrador disponíveis para personalizar os recursos de preenchimento estendido fornecidos pela solução Store Fulfillment e forneça um link para as instruções de conclusão da configuração.
role: Admin
level: Intermediate
feature: Shipping/Delivery, Configuration
exl-id: c432791a-94a0-457d-9ed9-8937846ce4f4
source-git-commit: 36b57648e156ead801764f3ee4e5e6a0f3245fe6
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Visão geral da configuração para Atendimento da loja

No Administrador do Adobe Commerce, as definições de configuração para Serviços de Atendimento da Loja pelas Tecnologias do Walmart Commerce são categorizadas por tipo.

**Definições de configuração de Abastecimento de Loja por tipo**

| **Tipo** | **Descrição** | **API configurável** |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| [Configuração geral](enable-general.md) | Integração geral configurada para a solução Store Fulfillment, seus recursos ativos e credenciais para se conectar aos serviços de fulfillment. | Não |
| [Configuração do e-mail de vendas](sales-emails.md) | Configurar modelos de email adicionais para notificações de clientes enviadas durante o processo de check-in. | Não |
| [Configuração da loja de comerciante](merchant-store-configuration.md) | Configure origens aprimoradas do Inventory management como lojas de comerciantes. | Sim |
| [Gerenciamento de Estoque de Produtos](product-stock.md) | Configurar as mensagens e os recursos do estoque de comerciantes disponíveis para os clientes. | Sim |
| [Transferência de origem do Inventory management](inventory-stock-transfer.md) | Configure um novo estoque, transfira o estoque do estoque padrão. | Sim |
| [Configuração de vários sites/escopos](multi-site-and-scope-config.md) | Configurar estoques e métodos de entrega para vários sites/escopos de loja. | Não |
| [Configuração do sistema de processo em segundo plano](background-processes.md) | Configure os cronogramas dos processos em segundo plano usados na sincronização de dados com os serviços de preenchimento. | Não |
| [Localização de armazenamento e configuração de mapeamento](store-location-map-provider-setup.md) | Configurar a capacidade de usar um provedor de distância para procurar lojas de varejo e exibir essas informações no mapa de SLS | Sim |
| [Configuração da experiência de check-in](check-in-experience-setup.md) | Configurar a cor do carro e as opções de fabricação do carro que estarão disponíveis durante o processo de check-in | Sim |
| [Configuração de usuário](user-setup.md) | Gerencie contas de usuário, funções e permissões para associados da loja que usam o aplicativo Store Assist. escopos. | Sim |
| [Configuração do aplicativo](app-setup.md) | Examine as configurações disponíveis para o Aplicativo de Assistência da Loja, necessárias para concluir o processo de integração. Essas configurações não podem ser definidas pelo administrador do Adobe Commerce. | Sim |

## Usar a referência de configuração

Visualize a referência de configuração para cada tipo de configuração selecionando o nome do tipo na _Definições de configuração de Abastecimento de Loja por tipo_ tabela.

Na referência de configuração de cada tipo, os detalhes da configuração são exibidos em uma tabela com os seguintes cabeçalhos de coluna:

- **Campo** refere-se ao nome do campo a ser configurado

- **Descrição** A seção fornece detalhes importantes sobre a finalidade e o comportamento do campo

- **Escopo** indica o escopo de configuração do Adobe Commerce para a configuração (global, site, loja)

- **Obrigatório** value indica se um valor deve ser definido no campo

Para referência técnica, você também pode encontrar o caminho de configuração interno para cada campo.
