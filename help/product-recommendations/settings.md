---
title: Configurações
description: Saiba como alterar a origem do seu [!DNL Product Recommendations] dados e como ativar recomendações visuais.
exl-id: 8c074e11-e0cb-4d55-b646-30279c79bbc2
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Configurações

Quando você [configurar um espaço de dados SaaS](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) para o Recommendations, o espaço de dados SaaS coleta dados de catálogo e dados comportamentais de vitrine. [Adobe Sensei](https://www.adobe.com/sensei.html) O analisa esses dados e calcula as associações de produtos usadas para servir o Recommendations de produtos.

Ambientes de não produção para teste ou preparo geralmente não têm a quantidade ou a qualidade dos dados comportamentais da loja para atender às recomendações realistas do produto. O comportamento real do comprador em escala pode ser capturado somente em um ambiente de produção. Para resolver esse problema, o Adobe Commerce permite usar as recomendações de produto do ambiente de produção com outros espaços de dados SaaS que não sejam de produção. A utilização de dados reais da loja em um ambiente de não produção permite visualizar as recomendações que seus compradores veem e experimentar com diferentes tipos de recomendações e locais de posicionamento. O Recommendations de um espaço de dados SaaS diferente pode ser visualizado pelos compradores, mas não clicado.

## Escolher a fonte de recomendações

Para alterar a origem dos dados de recomendações de produtos, escolha o espaço de dados SaaS com os dados comportamentais que deseja usar. Antes de começar, verifique se:

- A coleção de dados da vitrine eletrônica deve ser [configurado e habilitado](install-configure.md) para seu ambiente de produção e [verificado](verify.md) que os dados comportamentais estão sendo enviados ao Adobe Commerce.
- Seu catálogo de ambientes de não produção deve ser essencialmente o mesmo que seu catálogo de produção. Usar catálogos semelhantes garante que as unidades de recomendação do produto retornem imitando de perto as que estão em produção.

1. Faça logon no Admin do seu ambiente de não produção do Adobe Commerce.

1. No _Admin_ barra lateral, vá para **Marketing** > _Promoções_ > **Recommendations do produto**.

1. Clique em **Configurações**.

   ![configurações de recomendação do produto](assets/settings.png)
   _Configurações_

1. No _Origem do Recommendations_ habilite a opção **Buscar recomendações de um espaço de dados SaaS diferente** opção. A variável _Origem do Recommendations_ aparece somente em um ambiente de não produção.

   Uma lista de _Espaços de dados Saas disponíveis_ é exibida.

   ![configurações de recomendação do produto](assets/settings-select-saas.png)
   _Configurações_

1. Selecione o espaço de dados SaaS que contém os dados do comprador que você deseja usar.

1. Clique em **Salvar alterações**.

   O Adobe Commerce agora busca recomendações do espaço de dados selecionado.

   >[!NOTE]
   >
   > Embora você possa visualizar as recomendações buscadas de outro espaço de dados SaaS na loja de não produção, não é possível clicar nas recomendações.

### Configurar um novo espaço de dados SaaS

1. Na seção de origem do Recommendations, clique em **Editar configuração**.

1. Siga as instruções para configurar um novo [[!DNL Commerce] serviço](/help/landing/saas.md).

## Habilitar recomendações visuais

Se a variável [Visual Product Recommendations](install-configure.md) estiver instalado, você deve habilitar o Visual Recommendations para usar o [Similaridade visual](type.md#visualsim) tipo de recomendação.

No _Visual Recommendations_ seção, definir **Ativar o Visual Recommendations** para a posição ativa.
