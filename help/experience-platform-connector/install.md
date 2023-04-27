---
title: Instalar e configurar o Adobe Experience Platform Connector no Adobe Commerce
description: Saiba como instalar, configurar, atualizar e desinstalar o Adobe Experience Platform Connector do Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
source-git-commit: 898d49cbeb4711862a47693a0d608b74730dc845
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Instale e configure o conector Experience Platform

Antes de instalar a extensão, [revisar os pré-requisitos](overview.md#prereqs).

## Instalar a extensão

A extensão do conector Experience Platform está disponível no [Adobe Marketplace](https://marketplace.magento.com/magento-experience-platform-connector.html). Ao instalar essa extensão a partir da linha de comando do servidor, ela se conecta à instalação do Adobe Commerce como uma [service](../landing/saas.md). Quando o processo estiver concluído, **Conector Experience Platform** e **Conector do Commerce Services** aparecerá no **Sistema** menu em **Serviços** no Commerce _Administrador_.

>[!NOTE]
>
>![B2B para Adobe Commerce](../assets/b2b.svg) Para comerciantes B2B, há uma extensão separada que você deve instalar. Essa extensão adiciona suporte para eventos específicos B2B. [Saiba mais](#install-the-b2b-extension).


1. Para baixar o `experience-platform-connector` , execute o seguinte na linha de comando:

   ```bash
   composer require magento/experience-platform-connector
   ```

   Esse metapackage contém os seguintes módulos e extensões:

   * `module-experience-connector-admin` - Atualiza a interface do usuário do administrador para que você possa selecionar a ID do conjunto de dados para uma instância específica do Adobe Commerce
   * `module-experience-connector` - Define o `Organization ID` e `datastreamId` no SDK de Eventos da loja
   * `data-services` - Fornece contexto de atributo para eventos de vitrine. Por exemplo, quando um evento de check-out ocorre, informações sobre quantos itens estavam no carrinho e os dados do atributo do produto para esses itens são incluídos.
   * `services-id` - Conecta sua instância do Adobe Commerce ao [Adobe Commerce SaaS](../landing/saas.md) uso de chaves de sandbox e de API de produção e para a Adobe Experience Platform para recuperar a IMS Organization ID

1. (Opcional) Para incluir [!DNL Live Search] os dados, que incluem eventos de pesquisa, instale o [[!DNL Live Search]](../live-search/install.md) extensão.

### Instalar a extensão B2B

Para comerciantes B2B, instale a seguinte extensão para incluir [lista de requisições](events.md#b2b-events) dados do evento.

Baixe o `magento/experience-platform-connector-b2b` executando o seguinte na linha de comando:

```bash
composer require magento/experience-platform-connector-b2b
```

## Atualize o conector de Experience Platform {#update}

Para atualizar o conector de Experience Platform, execute o seguinte na linha de comando:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

ou, para os comerciantes B2B:

```bash
composer update magento/experience-platform-connector-b2b --with-dependencies
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

   ou, para os comerciantes B2B:

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## Desinstale o conector do Experience Platform {#uninstall}

Para desinstalar o conector Experience Platform, consulte [módulos de desinstalação](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
