---
title: "[!DNL Manage the Data Export extension]"
description: "Saiba como atualizar o [!DNL Data Export] e para remover ou desativar serviços de exportação de dados que não são necessários."
role: Admin, Developer
recommendations: noCatalog
source-git-commit: 8230756c203cb2b4bdb4949f116c398fcaab84ff
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---


# Gerenciar a extensão de exportação de dados SaaS

A variável [!DNL data export] A extensão para serviços SaaS é uma coleção de módulos que permitem a coleta e a sincronização de dados entre o Adobe Commerce e os serviços conectados da Commerce.

Módulos específicos são incluídos nos metapackages para extensões do Adobe Commerce Services, como [Live Search](/help/live-search/overview.md), [Recommendations do produto](/help/product-recommendations/overview.md), e [Serviço de catálogo](/help/catalog-service/overview.md). Se você estiver usando esses serviços, nenhuma instalação separada será necessária para habilitar a extensão Exportação de dados.

## Remova ou desative os recursos de exportação de dados do Commerce

Se você não precisar de um dos módulos de exportação de dados de comércio instalados, use o `magento:module:disable` Comando da CLI para desativá-la.

Por exemplo, há uma variável [API de categorias](https://developer.adobe.com/commerce/services/graphql/catalog-service/categories/) que usa os dados de feed de permissão das categorias internamente. Se você não estiver usando essa API, poderá desativar a exportação de dados para o feed de permissões de categorias.

```shell script
bin/magento module:disable Magento_CategoryPermissionDataExporter Magento_SaaSCategoryPermissions
```

### Atualizar um módulo para uma versão específica

Você pode atualizar qualquer um dos módulos de exportação de dados de comércio instalados usando o Composer. Por exemplo, você pode atualizar um módulo para uma versão especificada e também atualizar quaisquer dependências necessárias.

1. Faça logon no servidor de aplicativos do Commerce.

1. Na linha de comando, atualize o módulo usando o Composer:

   ```bash
   composer require magento/module-saas-price:103.3.1 --with-all-dependencies
   ```

Se a instância do Commerce for implantada na infraestrutura em nuvem, atualize a extensão do diretório do projeto em nuvem. Consulte [Atualizar uma extensão](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions#upgrade-an-extension) no _Guia da infraestrutura do Adobe Commerce na nuvem_.




