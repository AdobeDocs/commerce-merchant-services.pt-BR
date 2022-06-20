---
title: Instalar e configurar o Adobe Experience Platform Connector no Adobe Commerce
description: Saiba como instalar, configurar, atualizar e desinstalar o Adobe Experience Platform Connector do Adobe Commerce.
source-git-commit: 9b5f2da08167e22bbba504009bccc87d0ab02c48
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Instalar e configurar o conector do Experience Platform

Antes de instalar a extensão, [revisar os pré-requisitos](overview.md#prereqs).

## Instalar a extensão

1. Instale o metapackage do conector Experience Platform.

   ```bash
   composer require magento/platform-connector
   ```

   Este metapackage contém os seguintes módulos:

   * `module-platform-connector-admin` - Atualiza a interface do usuário do administrador
   * `module-platform-connector` - Define o `ImsOrgId` e `datastreamId` no SDK de Eventos da loja do Magento

1. Instale a extensão Commerce Data Services para incluir eventos de perfil e de check-out.

   ```bash
   composer require magento/data-services
   ```

   A extensão Commerce Data Services fornece contexto de atributo para eventos de vitrine. Por exemplo, quando um evento de check-out ocorre, informações sobre quantos itens estavam no carrinho e os dados do atributo do produto para esses itens são incluídos.

1. Instale o Conector de serviço do Commerce.

   ```bash
   composer require magento/commerce-services
   ```

   O Commerce Service Connector permite conectar sua instância do Adobe Commerce ao [Adobe Commerce SaaS](../landing/saas.md) e à Adobe Experience Platform.

1. (Opcional) Para incluir [!DNL Live Search] os dados, que incluem eventos de pesquisa, instale o [[!DNL Live Search]](../live-search/install.md) extensão.

## Atualize o conector de Experience Platform {#update}

Para atualizar o conector de Experience Platform, execute o seguinte na linha de comando:

```bash
composer update magento/platform-connector --with-dependencies
```

Para atualizar para uma versão principal, como de 1.0.0 a 2.0.0, edite a raiz do projeto [!DNL Composer] `.json` como segue:

1. Abra a raiz `composer.json` arquivo e pesquisa por `magento/platform-connector`.

1. No `require` atualize o número da versão da seguinte maneira:

   ```json
   "require": {
      ...
      "magento/platform-connector": "^2.0",
      ...
    }
   ```

1. **Salvar** `composer.json`. Em seguida, execute o seguinte na linha de comando:

   ```bash
   composer update magento/platform-connector –-with-dependencies
   ```

## Desinstale o conector do Experience Platform {#uninstall}

Para desinstalar o conector Experience Platform, consulte [módulos de desinstalação](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html).
