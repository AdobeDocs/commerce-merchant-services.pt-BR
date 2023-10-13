---
title: Instalar o Adobe Experience Platform Connector
description: Saiba como instalar, atualizar e desinstalar o Adobe Experience Platform Connector do Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 24494546d6d21cf46e3cb9f0fdd503ec8007daf8
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# Instalar o conector do Adobe Experience Platform

Antes de instalar a extensão, [revisar os pré-requisitos](overview.md#prereqs).

## Instalar a extensão

A extensão do conector Experience Platform está disponível no [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html). Ao instalar essa extensão a partir da linha de comando do servidor, ela se conecta à instalação do Adobe Commerce como um [serviço](../landing/saas.md). Quando o processo estiver concluído, **Conector Experience Platform** e **Conector dos Commerce Services** aparecerá no **Sistema** menu em **Serviços** no Commerce _Admin_.

>[!NOTE]
>
>![B2B para Adobe Commerce](../assets/b2b.svg) Para comerciantes B2B, há uma extensão separada que você deve instalar. Essa extensão adiciona suporte para eventos específicos B2B. [Saiba mais](#install-the-b2b-extension).

1. Para baixar o `experience-platform-connector` execute o seguinte a partir da linha de comando:

   ```bash
   composer require magento/experience-platform-connector
   ```

   Este metapackage contém os seguintes módulos e extensões:

   * `module-experience-connector-admin` - Atualiza a interface do administrador para que você possa selecionar a ID de sequência de dados para uma instância específica do Adobe Commerce.
   * `module-experience-connector` - Define o `Organization ID` e `datastreamId` no SDK de eventos da loja.
   * `data-services` - Fornece o contexto de atributo para eventos da loja. Por exemplo, quando ocorre um evento de check-out, são incluídas informações sobre quantos itens estavam no carrinho e dados de atributos de produto para esses itens.
   * `services-id` - Conecta sua instância do Adobe Commerce ao [SaaS Adobe Commerce](../landing/saas.md) usando sandbox, chaves de API de produção e para o Adobe Experience Platform a fim de recuperar a IMS Organization ID.
   * `orders-connector` - Conecta o serviço de status do pedido à sua instância do Adobe Commerce.

1. (Opcional) Para incluir [!DNL Live Search] dados, que incluem [pesquisar eventos](events.md#search-events), instale o [[!DNL Live Search]](../live-search/install.md) extensão.

### Configurar o conector de pedidos

Depois de instalar o `experience-platform-connector`, você deve finalizar a instalação do `orders-connector` módulo com base no tipo de implantação: local ou Adobe Commerce na infraestrutura em nuvem.

#### No local

Em ambientes locais, é necessário habilitar manualmente a geração de código e os Eventos do Adobe Commerce:

```bash
bin/magento events:generate:module
bin/magento module:enable Magento_AdobeCommerceEvents
bin/magento setup:upgrade
bin/magento setup:di:compile
bin/magento config:set adobe_io_events/eventing/enabled 1
```

#### Na infraestrutura em nuvem

Na infraestrutura do Adobe Commerce na nuvem, ative a opção `ENABLE_EVENTING` variável global no `.magento.env.yaml`. [Saiba mais](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-global.html#enable_eventing).

```bash
stage:
   global:
      ENABLE_EVENTING: true
```

Confirme e envie por push os arquivos atualizados para o ambiente em nuvem. Quando a implantação for concluída, habilite o envio de eventos com o seguinte comando:

```bash
bin/magento config:set adobe_io_events/eventing/enabled 1
```

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

Para atualizar para uma versão principal, como 2.0.0 para 3.0.0, edite a raiz do projeto [!DNL Composer] `.json` do seguinte modo:

1. Abra a raiz `composer.json` arquivo e pesquisa `magento/experience-platform-connector`.

1. No `require` , atualize o número da versão da seguinte maneira:

   ```json
   "require": {
      ...
      "magento/experience-platform-connector": "^3.0",
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
