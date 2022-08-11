---
title: Instalar [!DNL Payment Services]
description: Instale a extensão Payments Services.
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
source-git-commit: 43599d041899251f7716e215284b6eff9312943d
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Instalar [!DNL Payment Services]

Download e instalação do [!DNL Payment Services] extensão para [!DNL Adobe Commerce] e [!DNL Magento Open Source] é uma etapa prévia para usar [!DNL Payment Services].

![[!DNL Payment Services] visualização de administração de extensão](assets/admin-view.png)

## Baixe a extensão

Primeiro, baixe a extensão do de [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) antes de instalá-lo.

1. Navegue até o [Extensão Serviços de Pagamento no Commerce Marketplace](https://marketplace.magento.com/magento-payment-services.html).
1. Para escolher a edição e a versão, alterne **[!UICONTROL Edition]** e **[!UICONTROL Your store version]** às suas seleções preferidas.
1. Clique em **[!UICONTROL Add to Cart]**.
1. Conclua o check-out e clique em **[!UICONTROL Place Order]**.
1. Verifique o email associado ao download do Marketplace para obter informações e confirmação do pedido.

## Instalar a extensão

Você pode instalar o [!DNL Payment Services] extensão para ambos [!DNL Adobe Commerce] sobre a infraestrutura de nuvem e as instâncias locais, que estão vinculadas à ID do Magento ([mageid](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions)) fornecido no processo de assinatura, com chaves Composer. [!DNL Magento] Os clientes do Open Source utilizam as instruções no local.

O Composer usa essas chaves durante a instalação inicial do [!DNL Adobe Commerce]ou em situações em que as chaves do Composer não eram salvas anteriormente no `auth.json` arquivo.

Consulte [Obter as chaves de autenticação](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) para obter mais informações sobre como obter chaves Composer.

Consulte [Instalar uma extensão](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) para obter mais informações sobre o que considerar antes de baixar e instalar uma extensão.

### [!DNL Adobe Commerce] na infraestrutura em nuvem

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

### Configurações no local e outras configurações

Esse método é usado para instalar o [!DNL Payment Services] extensão de uma instância no local e [!DNL Magento] Clientes de código aberto.

1. Para obter a extensão, execute estes comandos:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Atualize as dependências e instale a extensão:

   ```bash
   composer update
   ```

   O `composer update` O comando atualiza todas as dependências. Se você não quiser atualizar todas as dependências ao mesmo tempo, use este comando: `composer require magento/payment-services`.

1. Atualize sua instância:

   ```bash
   bin/magento setup:upgrade
   ```

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```

1. Confirmar alterações.
1. Para garantir que o código confirmado seja implantado, atualize sua instância .

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
