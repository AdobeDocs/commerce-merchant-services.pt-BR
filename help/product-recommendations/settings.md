---
title: Configurações
description: Saiba como alterar a fonte de seus dados do  [!DNL Product Recommendations]  e como habilitar recomendações visuais.
exl-id: 8c074e11-e0cb-4d55-b646-30279c79bbc2
source-git-commit: 3a5dec9422aa34eeb204b9fe6f089551e4038f1c
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 0%

---

# Configurações

Quando você [configura um espaço de dados SaaS](../landing/saas.md#saas-configuration) para o Recommendations, o espaço de dados SaaS coleta dados de catálogo e armazena dados comportamentais de frente. O [Adobe Sensei](https://www.adobe.com/sensei.html) analisa esses dados e calcula as associações de produtos usadas para servir o Product Recommendations.

Ambientes de não produção para teste ou preparo geralmente não têm a quantidade ou a qualidade dos dados comportamentais da loja para atender às recomendações realistas do produto. O comportamento real do comprador em escala pode ser capturado somente em um ambiente de produção. Para resolver esse problema, o Adobe Commerce permite usar as recomendações de produto do ambiente de produção com outros espaços de dados SaaS que não sejam de produção. A utilização de dados reais da loja em um ambiente de não produção permite visualizar as recomendações que seus compradores veem e experimentar com diferentes tipos de recomendações e locais de posicionamento. O Recommendations de um espaço de dados SaaS diferente pode ser visualizado pelos compradores, mas não clicado.

As ordens de preparo são registradas usando o preparo `environmentId`. Isso não afeta os dados de produção. Os dados de produção são recuperados usando o `alternateEnvironmentId`.

>[!NOTE]
>
>Ao usar Recommendations de Produto por meio de REST, o parâmetro `alternateEnvironmentId` pode ser usado para especificar outros dataspaces. Ao usar o Recommendations de produto por meio do GraphQL, esse parâmetro não está disponível.

## Escolher a fonte de recomendações

Para alterar a origem dos dados de recomendações de produtos, escolha o espaço de dados SaaS com os dados comportamentais que deseja usar. Antes de começar, verifique se:

- A coleta de dados da loja deve ser [configurada e habilitada](install-configure.md) para o ambiente de produção e [verificou](verify.md) se os dados comportamentais estão sendo enviados para a Adobe Commerce.
- Seu catálogo de ambientes de não produção deve ser essencialmente o mesmo que seu catálogo de produção. Usar catálogos semelhantes garante que as unidades de recomendação do produto retornem imitando de perto as que estão em produção.

1. Faça logon no Admin do seu ambiente de não produção do Adobe Commerce.

1. Na barra lateral _Admin_, vá para **Marketing** > _Promoções_ > **Recommendations de Produtos**.

1. Clique em **Configurações**.

   ![configurações de recomendação do produto](assets/settings.png)
   _Configurações_

1. Na seção _fonte do Recommendations_, habilite a opção **Buscar recomendações de um espaço de dados SaaS diferente**. A seção _origem do Recommendations_ só aparece em um ambiente de não produção.

   Uma lista de _Espaços de dados SaaS disponíveis_ é exibida.

   ![configurações de recomendação do produto](assets/settings-select-saas.png)
   _Configurações_

1. Selecione o espaço de dados SaaS que contém os dados do comprador que você deseja usar.

1. Clique em **Salvar alterações**.

   O Adobe Commerce agora busca recomendações do espaço de dados selecionado.

   >[!NOTE]
   >
   > Embora você possa visualizar as recomendações buscadas de outro espaço de dados SaaS na loja de não produção, não é possível clicar nas recomendações.

### Configurar um novo espaço de dados SaaS

1. Na seção de origem do Recommendations, clique em **Editar Configuração**.

1. Siga as instruções para configurar um novo [[!DNL Commerce] serviço](/help/landing/saas.md).

## Habilitar recomendações visuais

Se o módulo [Visual Product Recommendations](install-configure.md) estiver instalado, você deverá habilitar o Visual Recommendations para usar o tipo de recomendação [Similaridade Visual](type.md#visualsim).

Na seção _Visual Recommendations_, defina **Habilitar Visual Recommendations** para a posição ativa.
