---
title: Instalar [!DNL Payment Services]
description: Instale a extensão Payments Services.
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: bcb817775fe9cd9ac7096931dd40d5ec0c4a5cfc
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---

# Instalar [!DNL Payment Services]

Instalar o [!DNL Payment Services] a extensão para Adobe Commerce e Magento Open Source é uma etapa prévia para usar [!DNL Payment Services].

![[!DNL Payment Services] visualização de administração de extensão](assets/admin-view.png)

O [!DNL Payment Services] A extensão para Adobe Commerce e Magento Open Source pode ser instalada com chaves Composer, que estão vinculadas à ID do Magento ([mageid](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) fornecido no processo de assinatura. O Composer usa essas chaves durante a instalação inicial do Adobe Commerce ou em situações em que as chaves do Composer não eram salvas anteriormente no `auth.json` arquivo.

Consulte [Obter as chaves de autenticação](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) para obter mais informações sobre como obter chaves Composer.

Há duas maneiras de instalar essa extensão — para [Adobe Commerce na infraestrutura de nuvem](https://devdocs.magento.com/payment-services/install-payments.html#magento-commerce-cloud) ou [No local](https://devdocs.magento.com/payment-services/install-payments.html#on-premises) instalações. Esses métodos exigem o uso da CLI (Command Line Interface, interface de linha de comando).

## Atualizar configuração de estabilidade mínima

Antes de instalar a extensão, você deve alterar a variável `minimum-stability` obrigação de `RC` (candidato a lançamento) em seu `composer.json` arquivo. Você pode usar um IDE ou seu editor de texto favorito (como Visual Studio Code ou Sublime Text).

Em seu `composer.json` arquivo, alterar `"minimum-stability": "stable"` para `"minimum-stability": "RC"`.

## Instalar a extensão

Você pode instalar o [!DNL Payment Services] extensão para o Adobe Commerce na infraestrutura de nuvem e instâncias locais.

### Adobe Commerce na infraestrutura de nuvem

Esse método é usado para instalar o [!DNL Payment Services] para uma instância Commerce Cloud.

1. Atualize seu `composer.json` arquivo:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Atualize as dependências e instale a extensão:

   ```bash
   composer update
   ```

   O `composer update` O comando atualiza todas as dependências. Se você não quiser atualizar todas as dependências ao mesmo tempo, use este comando: `composer require magento/payment-services`.

1. Confirme e envie suas alterações por push.

### No local

Esse método é usado para instalar o [!DNL Payment Services] para uma instância no local.

1. Para obter a extensão, execute estes comandos:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Atualize as dependências e instale a extensão:

   ```bash
   composer update
   ```

   O `composer update` O comando atualiza todas as dependências. Se você não quiser atualizar todas as dependências ao mesmo tempo, use este comando: `composer require magento/payment-services`.

1. Atualizar o Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```

1. Confirmar alterações.
1. Para garantir que o código comprometido seja implantado, atualize sua instância no local .

## Atualizar a extensão

Quando uma nova versão de [!DNL Payment Services] for lançado, você poderá atualizar facilmente sua extensão.

1. Para obter a versão mais recente do pacote:

   ```bash
   composer update
   ```

   O `composer update` O comando atualiza todas as dependências. Se você não quiser atualizar todas as dependências ao mesmo tempo, use este comando: `composer update magento/payment-services`.

1. Confirme e envie suas alterações por push.

## Solução de problemas

Você pode ver erros ao tentar instalar o [!DNL Payment Services] extensão. Use os seguintes métodos de solução de problemas para resolver os erros.

### Chaves do Composer Incorretas

Se você vir o seguinte erro indicando que você tem as chaves do Composer incorretas:

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Verifique se as chaves do Composer estão vinculadas à ID de Magento usada durante o [!DNL Payment Services] registro.

Para ver quais chaves do Composer estão configuradas:

1. Encontre a localização da variável `auth.json` arquivo:

   ```bash
   composer config --global home
   ```

1. Visualize o `auth.json` arquivo:

   ```bash
   cat /path/to/auth.json
   ```

1. Consulte [quais chaves estão associadas à sua ID de Magento](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### Memória insuficiente para PHP

Se você vir o seguinte erro indicando que não há memória suficiente para o PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Aumente o limite de memória](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) para PHP no seu ambiente em `php.ini`.

Como alternativa, você pode especificar o limite de memória usando este comando: `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

Por exemplo:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
