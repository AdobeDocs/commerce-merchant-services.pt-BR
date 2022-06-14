---
title: Visão geral da configuração do sistema
description: Saiba mais sobre as categorias de configurações de Administração disponíveis para a solução de disponibilização de loja e como elas são configuradas.
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Visão geral da configuração do sistema

No Administrador do Adobe Commerce, as configurações dos Serviços de fornecimento de loja por Tecnologias do Walmart são categorizadas por tipo.

**Armazenar configurações de preenchimento por tipo**

| **Tipo** | **Descrição** | **API configurável** |
|-------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
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
