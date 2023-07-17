---
title: "Instalar [!DNL Quick Checkout] para extensão do Adobe Commerce"
description: "Siga estas etapas para instalar [!DNL Quick Checkout] no seu projeto do Adobe Commerce."
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
feature: Checkout, Services, Install
source-git-commit: b1984a26463e14b8dc9a789421e49e5ea81ad039
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# Instalar [!DNL Quick Checkout]

A variável [!DNL Quick Checkout] extensão para o Adobe Commerce e [!DNL Magento Open Source] pode ser instalado com [!DNL Composer keys], vinculados à conta do Commerce [`mageid`](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target="_blank"} fornecido no processo de inscrição. O Composer usa essas chaves durante a instalação inicial do Adobe Commerce ou em situações em que o [!DNL Composer keys] não foram salvas anteriormente na `auth.json` arquivo.

Consulte [obter suas chaves de autenticação](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target="_blank"} tópico para obter mais informações sobre como obter [!DNL Composer keys].

Há duas maneiras de instalar essa extensão: para [Adobe Commerce na infraestrutura em nuvem](#magento-commerce-cloud) ou [no local](#on-premises) instalações. Esses métodos exigem que você use a interface de linha de comando (CLI).

## Atualizar configuração de estabilidade mínima

Antes de instalar a extensão, verifique se `minimum-stability` no seu `composer.json` o arquivo está definido como `"stable"`:

`"minimum-stability": "stable"`

## Instalar a extensão

Você pode instalar o [!DNL Quick Checkout] extensão para Adobe Commerce na infraestrutura em nuvem e instâncias locais.

### Adobe Commerce na infraestrutura em nuvem

Este método é usado para instalar o [!DNL Quick Checkout] extensão para uma instância Commerce Cloud.

1. Na estação de trabalho local, altere para o diretório raiz do projeto na nuvem.

1. Atualize seu `composer.json` arquivo:

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. Atualize as dependências e instale a extensão:

   ```bash
   composer update
   ```

   A variável `composer update` atualiza todas as dependências. Se não quiser atualizar todas as dependências ao mesmo tempo, use este comando: `composer update magento/quick-checkout`.

1. Confirme e envie suas alterações.

### No local

Este método é usado para instalar o [!DNL Quick Checkout] extensão para uma instância local.

1. Adicione o módulo Check-out rápido à `require` seção do `composer.json` arquivo:

   ```bash
   composer require magento/quick-checkout --no-update
   ```

1. Atualize as dependências e instale a extensão:

   ```bash
   composer update
   ```

   A variável `composer update` atualiza todas as dependências. Se não quiser atualizar todas as dependências ao mesmo tempo, use este comando: `composer update magento/quick-checkout`.

1. Atualizar o Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```

1. Confirmar alterações.
1. Atualize sua instância local para garantir que o código confirmado seja implantado.

## Atualizar a extensão

Quando lançamos uma nova versão do [!DNL Quick Checkout], você pode atualizar facilmente sua extensão.

1. Para obter a versão mais recente do pacote:

   ```bash
   composer update
   ```

   A variável `composer update` atualiza todas as dependências. Se não quiser atualizar todas as dependências ao mesmo tempo, use este comando: `composer update magento/quick-checkout`.

1. Confirme e envie suas alterações.

## Solução de problemas

Você pode ver erros ao tentar instalar o [!DNL Quick Checkout] extensão.

Se você encontrar problemas durante o [!DNL Quick Checkout] processo de instalação, consulte [Solução de problemas de Check-out rápido](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) na Central de ajuda do Adobe Commerce.

## Pré-requisitos

Consulte a [pré-requisitos](../quick-checkout/prerequisites.md) para obter mais informações.
