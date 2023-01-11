---
title: Instalar e configurar o Adobe Experience Platform Connector no Adobe Commerce
description: Saiba como instalar, configurar, atualizar e desinstalar o Adobe Experience Platform Connector do Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: 3d0de3eeb4aa96c996bc9fa38cffd7597e89e7ca
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Instale e configure o conector Experience Platform

Antes de instalar a extensão, [revisar os pré-requisitos](overview.md#prereqs).

## Instalar a extensão

A extensão Experience Platform connector é instalada a partir da linha de comando do servidor e se conecta à instalação do Adobe Commerce como uma [service](../landing/saas.md). Quando o processo estiver concluído, **Conector Experience Platform** aparece no **Sistema** menu em **Serviços** no Commerce _Administrador_.

O conector Experience Platform é instalado como uma extensão de [Adobe Marketplace](https://marketplace.magento.com/magento-experience-platform-connector.html).

1. Para baixar o `experience-platform-connector` , execute o seguinte na linha de comando:

   ```bash
   composer require magento/experience-platform-connector
   ```

   Esse metapackage contém os seguintes módulos e extensões:

   * `module-platform-connector-admin` - Atualiza a interface do usuário do administrador para que você possa selecionar a ID do conjunto de dados para uma instância específica do Adobe Commerce
   * `module-platform-connector` - Define o `Organization ID` e `datastreamId` no SDK de Eventos da loja
   * `data-services` - Fornece contexto de atributo para eventos de vitrine. Por exemplo, quando um evento de check-out ocorre, informações sobre quantos itens estavam no carrinho e os dados do atributo do produto para esses itens são incluídos.
   * `services-id` - Conecta sua instância do Adobe Commerce ao [Adobe Commerce SaaS](../landing/saas.md) uso de chaves de sandbox e de API de produção e para a Adobe Experience Platform para recuperar a IMS Organization ID

1. (Opcional) Para incluir [!DNL Live Search] os dados, que incluem eventos de pesquisa, instale o [[!DNL Live Search]](../live-search/install.md) extensão.

## Atualize o conector de Experience Platform {#update}

Para atualizar o conector de Experience Platform, execute o seguinte na linha de comando:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

Para atualizar para uma versão principal, como de 1.0.0 a 2.0.0, edite a raiz do projeto [!DNL Composer] `.json` como segue:

1. Abra a raiz `composer.json` arquivo e pesquisa por `magento/platform-connector`.

1. No `require` atualize o número da versão da seguinte maneira:

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^2.0",
      ...
    }
   ```

1. **Salvar** `composer.json`. Em seguida, execute o seguinte na linha de comando:

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

## Desinstale o conector do Experience Platform {#uninstall}

Para desinstalar o conector Experience Platform, consulte [módulos de desinstalação](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
