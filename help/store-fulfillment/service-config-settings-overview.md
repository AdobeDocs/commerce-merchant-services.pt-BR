---
title: Visão geral da configuração para o cumprimento da loja
description: Saiba mais sobre as categorias de configurações de Administração disponíveis para a solução de disponibilização de loja e como elas são configuradas.
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# Visão geral da configuração para o cumprimento da loja

No Administrador do Adobe Commerce, as configurações dos Serviços de fornecimento de loja por Tecnologias do Walmart são categorizadas por tipo.

**Armazenar configurações de preenchimento por tipo**

| **Tipo** | **Descrição** | **API configurável** |
|--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| [Configuração geral](enable-general.md) | Integração geral configurada para a solução de fornecimento de armazenamento, seus recursos ativos e credenciais para se conectar aos serviços de cumprimento. | Não |
| [Configuração de email de vendas](sales-emails.md) | Configure modelos de email adicionais para notificações de clientes enviadas durante o processo de check-in. | Não |
| [Configuração da loja de merchant](merchant-store-configuration.md) | Configure fontes aprimoradas do Inventory management como lojas de merchant. | Sim |
| [Gerenciamento de estoque de produtos](product-stock.md) | Configure as mensagens de estoque do comerciante e os recursos disponíveis para os clientes. | Sim |
| [Transferência de origem do Inventory management](inventory-stock-transfer.md) | Configure um novo estoque, transfira o inventário para fora do estoque padrão. | Sim |
| [Configuração de Vários Sites/Escopo](multi-site-and-scope-config.md) | Configure estoques e métodos de entrega para vários sites/escopos de loja. | Não |
| [Configuração do Sistema de Processos em Segundo Plano](background-processes.md) | Configure os agendamentos para processos em segundo plano usados na sincronização de dados com os serviços de cumprimento. | Não |
| [Configuração de localização e mapeamento da loja](store-location-map-provider-setup.md) | Configure a capacidade de usar um provedor de distância para procurar lojas de varejo e exibir essas informações no mapa do SLS | Sim |
| [Configuração da experiência de check-in](store-location-map-provider-setup.md) | Configure a cor do carro e as opções de fabricação do carro que estarão disponíveis durante o processo de check-in | Sim |
| [Configuração do usuário](user-setup.md) | Gerencie contas de usuário, funções e permissões para os associados da loja que usam o aplicativo Store Assist. escopos. | Sim |
| [Configuração do aplicativo](app-setup.md) | Revise as configurações disponíveis para o aplicativo de assistência da loja necessário para concluir o processo de integração. Essas configurações não podem ser configuradas no Administrador do Adobe Commerce. | Sim |


## Usar a referência de configuração

Visualize a referência de configuração para cada tipo de configuração selecionando o nome do tipo na variável _Armazenar configurações de preenchimento por tipo_ tabela.

Na referência de configuração para cada tipo, os detalhes de configuração são exibidos em uma tabela com os seguintes cabeçalhos de coluna:

- **Campo** refere-se ao nome do campo a ser configurado

- **Descrição** fornece detalhes importantes sobre a finalidade e o comportamento do campo

- **Escopo** indica o escopo de configuração do Adobe Commerce para a configuração (global, site, loja)

- **Obrigatório** indica se um valor deve ser definido no campo

Para referência técnica, também é possível encontrar o caminho de configuração interna para cada campo.
