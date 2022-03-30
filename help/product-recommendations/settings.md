---
title: Configurações
description: Saiba como alterar a fonte de seu [!DNL Product Recommendations] e como ativar as recomendações visuais.
source-git-commit: 8c85d26474e371d30b76499f312553a07e329a80
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Configurações

Quando você [configurar um espaço de dados SaaS](https://docs.magento.com/user-guide/configuration/services/saas.html) para o Recommendations, o espaço de dados SaaS coleta dados de catálogo e dados comportamentais da loja. [Adobe Sensei](https://www.adobe.com/sensei.html) O analisa esses dados e calcula as associações de produtos usadas para fornecer o Recommendations do produto.

Ambientes não relacionados à produção para teste ou armazenamento temporário geralmente não têm a quantidade ou a qualidade dos dados comportamentais da loja para fornecer recomendações realistas do produto. O comportamento real do comprador em escala pode ser capturado somente em um ambiente de produção. Para resolver esse problema, o Adobe Commerce permite usar recomendações de produto do ambiente de produção com outros espaços de dados SaaS de não produção. Usar os dados de vitrine reais em um ambiente de não produção permite que você visualize as recomendações que seus compradores veem e experimente com diferentes tipos de recomendação e locais de posicionamento. O Recommendations de um espaço de dados SaaS diferente pode ser visualizado por compradores, mas não clicado.

## Escolha a fonte de recomendações

Para alterar a fonte dos dados de recomendações do produto, escolha o espaço de dados SaaS com os dados comportamentais que deseja usar. Antes de começar, verifique se:

- A coleta de dados da vitrine deve ser [configurado e ativado](install-configure.md) para seu ambiente de produção e [verificado](verify.md) que os dados comportamentais estão sendo enviados ao Adobe Commerce.
- Seu catálogo de ambiente de não produção deve ser basicamente o mesmo do catálogo de produção. Usar catálogos similares garante que as unidades de recomendação do produto retornem imitando as unidades em produção.

1. Faça logon no Administrador do ambiente de não produção do Adobe Commerce.

1. No _Administrador_ barra lateral, vá para **Marketing** > _Promoções_ > **Recommendations do produto**.

1. Clique em **Configurações**.

   ![configurações de recomendação do produto](assets/settings.png)
   _Configurações_

1. No _Origem do Recommendations_ ative a **Buscar recomendações de um espaço de dados SaaS diferente** opção. O _Origem do Recommendations_ aparece somente em um ambiente não relacionado à produção.

   Uma lista de _Espaços de dados SaaS disponíveis_ é exibido.

   ![configurações de recomendação do produto](assets/settings-select-saas.png)
   _Configurações_

1. Selecione o espaço de dados SaaS que tem dados de comprador que deseja usar.

1. Clique em **Salvar alterações**.

   O Adobe Commerce agora busca recomendações do espaço de dados selecionado.

   >[!NOTE]
   >
   > Embora você possa exibir as recomendações buscadas em outro espaço de dados SaaS na loja de não produção, não é possível clicar nas recomendações.

### Configurar um novo espaço de dados SaaS

1. Na seção Origem do Recommendations , clique em **Editar configuração**.

1. Siga as instruções para configurar um novo [Commerce Service].

## Ativar recomendações visuais

Se a variável [Visual Product Recommendations](install-configure.md) estiver instalado, você deve habilitar o Visual Recommendations para usar o [Similaridade visual](type.md#visualsim) tipo de recomendação.

No _Visual Recommendations_ seção, conjunto **Habilitar o Visual Recommendations** para a posição ativa.
