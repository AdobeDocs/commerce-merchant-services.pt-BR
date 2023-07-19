---
title: Instalar e configurar o Adobe Experience Platform Connector a partir do Adobe Commerce
description: Saiba como instalar, configurar, atualizar e desinstalar o Adobe Experience Platform Connector do Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 64273ad4c1a54b150746a54896caf73ed612c2d1
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Instale e configure o conector do Experience Platform

Antes de instalar a extensão, [revisar os pré-requisitos](overview.md#prereqs).

## Instalar a extensão

A extensão do conector Experience Platform está disponível no [Adobe Marketplace](https://marketplace.magento.com/magento-experience-platform-connector.html). Ao instalar essa extensão a partir da linha de comando do servidor, ela se conecta à instalação do Adobe Commerce como um [serviço](../landing/saas.md). Quando o processo estiver concluído, **Conector Experience Platform** e **Conector dos Commerce Services** aparecerá no **Sistema** menu em **Serviços** no Commerce _Admin_.

>[!NOTE]
>
>![B2B para Adobe Commerce](../assets/b2b.svg) Para comerciantes B2B, há uma extensão separada que você deve instalar. Essa extensão adiciona suporte para eventos específicos B2B. [Saiba mais](#install-the-b2b-extension).


1. Para baixar o `experience-platform-connector` execute o seguinte a partir da linha de comando:

   ```bash
   composer require magento/experience-platform-connector
   ```

   Este metapackage contém os seguintes módulos e extensões:

   * `module-experience-connector-admin` - Atualiza a interface do administrador para que você possa selecionar a ID de sequência de dados para uma instância específica do Adobe Commerce
   * `module-experience-connector` - Define o `Organization ID` e `datastreamId` no SDK de eventos da loja
   * `data-services` - Fornece o contexto de atributo para eventos da loja. Por exemplo, quando ocorre um evento de check-out, são incluídas informações sobre quantos itens estavam no carrinho e dados de atributos de produto para esses itens.
   * `services-id` - Conecta sua instância do Adobe Commerce ao [SaaS Adobe Commerce](../landing/saas.md) uso de sandbox e chaves de API de produção e para o Adobe Experience Platform para recuperar a IMS Organization ID

1. (Opcional) Para incluir [!DNL Live Search] dados, que incluem eventos de pesquisa, instale o [[!DNL Live Search]](../live-search/install.md) extensão.

### Instalar a extensão B2B

Para comerciantes B2B, instale a seguinte extensão para incluir [lista de requisições](events.md#b2b-events) dados do evento.

Baixe o `magento/experience-platform-connector-b2b` executando o seguinte na linha de comando:

```bash
composer require magento/experience-platform-connector-b2b
```

## Atualize o conector do Experience Platform {#update}

Para atualizar o conector Experience Platform, execute o seguinte na linha de comando:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

ou, para os comerciantes B2B:

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
```

Para atualizar para uma versão principal, como 1.0.0 para 2.0.0, edite a raiz do projeto [!DNL Composer] `.json` do seguinte modo:

1. Abra a raiz `composer.json` arquivo e pesquisa `magento/experience-platform-connector`.

1. No `require` , atualize o número da versão da seguinte maneira:

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^2.0",
      ...
    }
   ```

1. **Salvar** `composer.json`. Em seguida, execute o seguinte a partir da linha de comando:

   ```bash
   composer update magento/experience-platform-connector –-with-dependencies
   ```

   ou, para os comerciantes B2B:

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## Desinstale o conector do Experience Platform {#uninstall}

Para desinstalar o conector Experience Platform, consulte [desinstalar módulos](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
