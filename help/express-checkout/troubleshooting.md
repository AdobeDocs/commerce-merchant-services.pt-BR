---
title: Solução de problemas para o [!DNL Express Checkout]
description: Troubleshoot errors, known issues you may experience while using the [!DNL Express Checkout] for Adobe Commerce extension.
exl-id: a379ff81-360d-4cb9-a123-47e8cbc0cdbd
source-git-commit: 1a7df2c5581ea6d590aa1a2f701b4428371d2299
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Solução de problemas [!DNL Express Checkout] para Adobe Commerce

>[!IMPORTANT]
>
> This feature is for Early Adopter Program (EAP) users only and is not yet accessible for all customers. Currently limited to US customers. Contact Adobe Commerce Support for assistance and questions.

Use the following troubleshooting methods to resolve these specific issues.

## Chaves do Composer Incorretas

Caso veja o seguinte erro indicando que você tem as chaves do Composer incorretas:

```terminal
Could not find a matching version of package magento/express-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

Verifique se as chaves do Composer estão vinculadas à ID de Magento usada durante o registro do Check-out expresso.

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

## Minimum stability in the `composer.json` is set to stable

If you see the following error denoting you have the incorrect Composer keys:

```terminal
Could not find a matching version of package magento/express-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Defina a estabilidade mínima para `RC` no `composer.json` arquivo.

## Memória insuficiente para PHP

Se você vir o seguinte erro indicando que não há memória suficiente para o PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Aumente o limite de memória](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) para PHP no seu ambiente em `php.ini`.

Como alternativa, você pode especificar o limite de memória usando este comando: `php -d memory_limit=-1 [path to composer]/composer require magento/express-checkout`.

Por exemplo:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/express-checkout
```

## Invalid shipping address

There is a known issue for the [!DNL Express Checkout].

Quando o endereço de envio padrão não é válido, o cliente é redirecionado para a etapa de endereço de envio. A vitrine mostra somente endereços de envio válidos.

>[!WARNING]
>
> se não houver endereços de envio válidos, o cliente não verá nenhum endereço de envio disponível.

Consulte a [detalhes de envio](../express-checkout/shipping-details.md) para obter mais informações.

## Adicionar linhas de endereço de rua com um novo endereço de envio

There is a known issue for the [!DNL Express Checkout].

Quando você [fazer logon com uma conta Bolt](https://help.bolt.com/shoppers/guides/checkout/log-in/) você pode adicionar um novo endereço de envio com uma limitação de 4 linhas por endereço de rua.

O Adobe Commerce geralmente pode ser configurado para suportar até 20 linhas de endereço de rua.

## Caixa de seleção `enable terms and conditions` não exibindo corretamente

There is a known issue for the [!DNL Express Checkout].

Ao ativar a variável `Enable terms and conditions` na caixa de seleção em Admin e faça logon com uma [!DNL Bolt] , a `Enable terms and conditions` não é exibida durante o check-out. Consulte a [fazer logon](https://help.bolt.com/shoppers/account/login-dashboard/) [!DNL Bolt] para obter mais informações.

See [terms and conditions](https://docs.magento.com/user-guide/sales/terms-and-conditions.html) topic for more information on the Admin configuration.

## Comportamento inesperado ao `Display Billing Address On` está definida como `payment page`

Há um problema conhecido para a variável [!DNL Express Checkout].

Se você definir a variável `Display Billing Address On` para `payment page` e [fazer logon com uma conta Bolt](https://help.bolt.com/shoppers/guides/checkout/log-in/) ao verificar o `My billing and shipping address are the same` caixa de seleção:

![Mesmo endereço](assets/checked-address.png)

Botão de opção exibido `use existing card`.

See [Checkout](https://docs.magento.com/user-guide/configuration/sales/checkout.html) topic for more information on the `Display Billing Address On` parameter.

## Translating the [!DNL Express Checkout] extension

Adobe Commerce enables you to localize your store for multiple regions and markets. Você pode até mesmo localizar mensagens de erro na visualização de Administração.

Consulte a [tradução e localização](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html) para obter mais informações.

## Get help

Contact Adobe Commerce Support for any assistance.
