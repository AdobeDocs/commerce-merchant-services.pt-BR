---
title: '"Instalar [!DNL Quick Checkout] para extensão do Adobe Commerce"'
description: '"Siga estas etapas para instalar [!DNL Quick Checkout] no seu projeto do Adobe Commerce."'
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: 27e91a640999cf83a0f0d6701e616f7ceecde12d
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# Instalar [!DNL Quick Checkout]

O [!DNL Quick Checkout] pode ser instalada com a extensão para Adobe Commerce e Magento Open Source [!DNL Composer keys], que estão vinculadas ao [Magento ID (mageid)](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target=&quot;_blank&quot;} foi fornecido no processo de assinatura. O Composer usa essas chaves durante a instalação inicial do Adobe Commerce ou em situações em que o [!DNL Composer keys] não foram salvas anteriormente no `auth.json` arquivo.

Consulte [obter as chaves de autenticação](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html)Tópico {target=&quot;_blank&quot;} para obter mais informações sobre como obter [!DNL Composer keys].

Há duas maneiras de instalar essa extensão — para [Adobe Commerce na infraestrutura de nuvem](#magento-commerce-cloud) ou [no local](#on-premises) instalações. Esses métodos exigem que você use a interface de linha de comando (CLI).

## Atualizar configuração de estabilidade mínima

Antes de instalar a extensão, verifique se `minimum-stability` no seu campo `composer.json` O arquivo está definido como `"stable"`:

`"minimum-stability": "stable"`

## Instalar a extensão

Você pode instalar o [!DNL Quick Checkout] extensão para o Adobe Commerce na infraestrutura de nuvem e instâncias locais.

### Adobe Commerce na infraestrutura de nuvem

Esse método é usado para instalar o [!DNL Quick Checkout] para uma instância Commerce Cloud.

1. Na estação de trabalho local, altere para o diretório raiz do projeto Cloud.

1. Atualize seu `composer.json` arquivo:

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. Atualize as dependências e instale a extensão:

   ```bash
   composer update
   ```

   O `composer update` O comando atualiza todas as dependências. Se você não quiser atualizar todas as dependências ao mesmo tempo, use este comando: `composer update magento/quick-checkout`.

1. Confirme e envie suas alterações por push.

### No local

Esse método é usado para instalar o [!DNL Quick Checkout] para uma instância no local.

1. Adicione o módulo Quick Checkout ao `require` da seção `composer.json` arquivo:

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. Atualize as dependências e instale a extensão:

   ```bash
   composer update
   ```

   O `composer update` O comando atualiza todas as dependências. Se você não quiser atualizar todas as dependências ao mesmo tempo, use este comando: `composer update magento/quick-checkout`.

1. Atualizar o Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```

1. Confirmar alterações.
1. Atualize sua instância local para garantir que o código comprometido seja implantado.

## Atualizar a extensão

Quando lançamos uma nova versão do [!DNL Quick Checkout], você pode atualizar facilmente sua extensão.

1. Para obter a versão mais recente do pacote:

   ```bash
   composer update
   ```

   O `composer update` O comando atualiza todas as dependências. Se você não quiser atualizar todas as dependências ao mesmo tempo, use este comando: `composer update magento/quick-checkout`.

1. Confirme e envie suas alterações por push.

## Solução de problemas

Você pode ver erros ao tentar instalar o [!DNL Quick Checkout] extensão.

Se encontrar problemas durante a [!DNL Quick Checkout] processo de instalação, consulte [Solução de problemas de check-out rápido](https://support.magento.com/hc/en-us/articles/6909450342541) no Centro de ajuda da Adobe Commerce.

## Pré-requisitos

Consulte a [pré-requisitos](../quick-checkout/prerequisites.md) para obter mais informações.
