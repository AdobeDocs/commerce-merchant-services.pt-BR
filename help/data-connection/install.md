---
title: Instalar [!DNL Data Connection]
description: Saiba como instalar, atualizar e desinstalar o [!DNL Data Connection] extensão do Adobe Commerce.
exl-id: e78e8ab0-8757-4ab6-8ee1-d2e137fe6ced
role: Admin, Developer
feature: Install
source-git-commit: 688eabddaf4b3faab98c60cf440fe6e9c6772790
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Instalar [!DNL Data Connection]

Antes de instalar a extensão, [revisar os pré-requisitos](overview.md#prereqs).

## Instalar a extensão

A variável [!DNL Data Connection] A extensão do está disponível no [Adobe Marketplace](https://commercemarketplace.adobe.com/magento-experience-platform-connector.html). Ao instalar essa extensão a partir da linha de comando do servidor, ela se conecta à instalação do Adobe Commerce como um [serviço](../landing/saas.md). Quando o processo estiver concluído, **[!DNL Data Connection]** e **Conector dos Commerce Services** aparecerá no **Sistema** menu em **Serviços** no Commerce _Admin_.

>[!IMPORTANT]
>
>Embora o nome da extensão tenha sido alterado de Experience Platform para [!DNL Data Connection], o nome do pacote permanece `experience-platform-connector` para suportar compatibilidade com versões anteriores.

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

1. (Opcional) Para incluir dados B2B, que incluem [eventos de requisição](events.md#b2b-events), instale o [Extensão B2B](#install-the-b2b-extension).

### Instalar os eventos do Adobe I/O

Depois de instalar o `experience-platform-connector` extensão, você deve instalar os Eventos Adobe I/O para Adobe Commerce.

As etapas a seguir se aplicam ao Adobe Commerce na infraestrutura em nuvem e às instalações locais.

1. Se você estiver executando o Commerce 2.4.4 ou 2.4.5, use o seguinte comando para carregar os módulos de evento:

   ```bash
   composer require magento/commerce-eventing=^1.0 --no-update
   ```

   O Commerce 2.4.6 e versões posteriores carregam esses módulos automaticamente.

1. Atualize as dependências do projeto.

   ```bash
   composer update
   ```

1. Ative os novos módulos:

   ```bash
   bin/magento module:enable Magento_AdobeCommerceEventsClient Magento_AdobeCommerceEventsGenerator Magento_AdobeIoEventsClient Magento_AdobeCommerceOutOfProcessExtensibility
   ```

Finalize a instalação com base no tipo de implantação: local ou Adobe Commerce na infraestrutura em nuvem.

#### No local

Em ambientes locais, você deve habilitar manualmente a geração de código e os Eventos do Adobe Commerce:

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

## Atualize o [!DNL Data Connection] extensão {#update}

Para atualizar o [!DNL Data Connection] , execute o seguinte a partir da linha de comando:

```bash
composer update magento/experience-platform-connector --with-dependencies
```

Ou, para os comerciantes B2B:

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

   Ou, para os comerciantes B2B:

   ```bash
   composer update magento/experience-platform-connector-b2b --with-dependencies
   ```

## Desinstale o [!DNL Data Connection] extensão {#uninstall}

Para desinstalar o [!DNL Data Connection] consulte [desinstalar módulos](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html).
