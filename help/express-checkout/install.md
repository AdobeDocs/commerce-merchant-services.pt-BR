---
title: Instale o [!DNL Express Checkout] para extensão do Adobe Commerce
description: Siga estas etapas para instalar o [!DNL Upgrade Compatibility Tool] para seu projeto do Adobe Commerce.
exl-id: e1dabc9a-0ab0-4f8d-98d3-7a32abbedcb8
source-git-commit: 163dd5260908b4ea3a8bfbcfdb834531d1603734
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# Instale o [!DNL Express Checkout]

>[!IMPORTANT]
>
> Esse recurso destina-se somente aos usuários do EAP (Early Adobe Program) e ainda não está acessível para todos os clientes. Atualmente limitado a clientes dos EUA. Entre em contato com o Suporte da Adobe Commerce para obter assistência e perguntas.

O [!DNL Express Checkout] O para Adobe Commerce alimenta uma experiência de check-out contínua projetada para converter compradores convidados únicos em titulares de conta fiéis.

O [!DNL Express Checkout] A extensão para Adobe Commerce e Magento Open Source pode ser instalada com chaves Composer, que estão vinculadas a [Magento ID (mageid)](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions){target=&quot;_blank&quot;} foi fornecido no processo de assinatura. O Composer usa essas chaves durante a instalação inicial do Adobe Commerce ou em situações em que as chaves do Composer não eram salvas anteriormente no `auth.json` arquivo.

Consulte [obter as chaves de autenticação](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html){target=&quot;_blank&quot;} para obter mais informações sobre como obter chaves do Composer.

Há duas maneiras de instalar essa extensão — para [Adobe Commerce na infraestrutura de nuvem](#magento-commerce-cloud) ou [no local](#on-premises) instalações. Esses métodos exigem o uso da CLI (Command Line Interface, interface de linha de comando).

## Atualizar configuração de estabilidade mínima

Antes de instalar a extensão, é possível alterar a variável `minimum-stability` obrigação de `RC` (candidato a lançamento) em seu `composer.json` se quiser tentar a versão do candidato a lançamento. Você pode usar um IDE ou seu editor de texto favorito (como Visual Studio Code ou Sublime Text).

Em seu `composer.json` arquivo, alterar `"minimum-stability": "stable"` para `"minimum-stability": "RC"`.

## Instalar a extensão

Você pode instalar o [!DNL Express Checkout] extensão para o Adobe Commerce na infraestrutura de nuvem e instâncias locais.

### Adobe Commerce na infraestrutura de nuvem

Esse método é usado para instalar o [!DNL Express Checkout] para uma instância Commerce Cloud.

1. Na estação de trabalho local, altere para o diretório raiz do projeto Cloud.

1. Atualize seu `composer.json` arquivo:

   ```bash
   composer require magento/express-checkout --no-update
   ```

1. Atualize as dependências e instale a extensão:

   ```bash
   composer update
   ```

   O `composer update` O comando atualiza todas as dependências. Se você não quiser atualizar todas as dependências ao mesmo tempo, use este comando: `composer update magento/express-checkout`.

1. Confirme e envie suas alterações por push.

### No local

Esse método é usado para instalar o [!DNL Express Checkout] para uma instância no local.

1. Adicione o módulo Express Checkout ao `require` da seção `composer.json` arquivo:

   ```bash
   composer require magento/express-checkout --no-update
   ```

1. Atualize as dependências e instale a extensão:

   ```bash
   composer update
   ```

   O `composer update` O comando atualiza todas as dependências. Se você não quiser atualizar todas as dependências ao mesmo tempo, use este comando: `composer update magento/express-checkout`.

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

Quando lançamos uma nova versão do [!DNL Express Checkout], você pode atualizar facilmente sua extensão.

1. Para obter a versão mais recente do pacote:

   ```bash
   composer update
   ```

   O `composer update` O comando atualiza todas as dependências. Se você não quiser atualizar todas as dependências ao mesmo tempo, use este comando: `composer update magento/express-checkout`.

1. Confirme e envie suas alterações por push.

## Solução de problemas

Você pode ver erros ao tentar instalar o [!DNL Express Checkout] extensão.

Consulte a [solução de problemas](../express-checkout/troubleshooting.md) para obter mais informações se encontrar qualquer problema ao instalar o [!DNL Express Checkout].

## Pré-requisitos

Consulte a [pré-requisitos](../express-checkout/prerequisites.md) para obter mais informações.
