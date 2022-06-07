---
title: '"Solução de problemas para o [!DNL Quick Checkout]"'
description: '"Solucione erros, problemas conhecidos que você pode enfrentar ao usar o [!DNL Quick Checkout] para extensão do Adobe Commerce."'
exl-id: a379ff81-360d-4cb9-a123-47e8cbc0cdbd
source-git-commit: 9841db7616c8aa6d5bc5af3e6e92c0abe9a4a1e2
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# Solução de problemas [!DNL Quick Checkout] para Adobe Commerce

Use os seguintes métodos de solução de problemas para resolver esses problemas específicos.

## Incorreto [!DNL Composer keys]

Se vir o seguinte erro indicando que você tem o erro incorreto [!DNL Composer keys]:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (RC).
```

Verifique se a sua [!DNL Composer keys] são vinculadas à ID do Magento usada durante o registro do Check-out rápido.

Para ver qual [!DNL Composer keys] estão configuradas:

1. Encontre a localização da variável `auth.json` arquivo:

   ```bash
   composer config --global home
   ```

1. Visualize o `auth.json` arquivo:

   ```bash
   cat /path/to/auth.json
   ```

1. Consulte [quais chaves estão associadas à sua ID de Magento](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

## Estabilidade mínima na `composer.json` está definido como estável

Se vir o seguinte erro indicando que você tem o erro incorreto [!DNL Composer keys]:

```terminal
Could not find a matching version of package magento/quick-checkout. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Defina a estabilidade mínima para `RC` no `composer.json` arquivo.

## Memória insuficiente para PHP

Se você vir o seguinte erro indicando que não há memória suficiente para o PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Aumente o limite de memória](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) para PHP no seu ambiente em `php.ini`.

Como alternativa, você pode especificar o limite de memória usando este comando: `php -d memory_limit=-1 [path to composer]/composer require magento/quick-checkout`.

Por exemplo:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/quick-checkout
```

## Endereço de entrega inválido

Há um problema conhecido para a variável [!DNL Quick Checkout].

Quando o endereço de envio padrão não é válido, o cliente é redirecionado para a etapa de endereço de envio. A vitrine mostra somente endereços de envio válidos.

>[!WARNING]
>
> se não houver endereços de envio válidos, o cliente não verá nenhum endereço de envio disponível.

Consulte a [detalhes de envio](../quick-checkout/shipping-details.md) para obter mais informações.

## Adicionar linhas de endereço de rua com um novo endereço de envio

Há um problema conhecido para a variável [!DNL Quick Checkout].

Quando você [fazer logon com uma [!DNL Bolt] account](https://help.bolt.com/shoppers/guides/checkout/log-in/) você pode adicionar um novo endereço de envio com uma limitação de 4 linhas por endereço de rua.

O Adobe Commerce geralmente pode ser configurado para suportar até 20 linhas de endereço de rua.

## Caixa de seleção `enable terms and conditions` não exibindo corretamente

Há um problema conhecido para a variável [!DNL Quick Checkout].

Ao ativar a variável `Enable terms and conditions` na caixa de seleção em Admin e faça logon com uma [!DNL Bolt] , a `Enable terms and conditions` não é exibida durante o check-out. Consulte a [Fazer logon](https://help.bolt.com/shoppers/account/login-dashboard/) [!DNL Bolt] para obter mais informações.

Consulte [termos e condições](https://docs.magento.com/user-guide/sales/terms-and-conditions.html) para obter mais informações sobre a Configuração de administração.

## Comportamento inesperado ao `Display Billing Address On` está definida como `payment page`

Há um problema conhecido para a variável [!DNL Quick Checkout].

Se você definir a variável `Display Billing Address On` para `payment page` e [fazer logon com uma [!DNL Bolt] account](https://help.bolt.com/shoppers/guides/checkout/log-in/) ao verificar o `My billing and shipping address are the same` caixa de seleção exibida o botão de opção `use existing card`.

![Mesmo endereço](assets/checked-address.png)

Consulte a [Check-out](https://docs.magento.com/user-guide/configuration/sales/checkout.html) tópico para obter mais informações sobre `Display Billing Address On` parâmetro.

## Tradução da variável [!DNL Quick Checkout] extensão

O Adobe Commerce permite que você localize sua loja para várias regiões e mercados. Você pode até mesmo localizar mensagens de erro na visualização de Administração.

Consulte a [tradução e localização](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html) para obter mais informações.

## Liberar o cache

1. Navegar para **[!UICONTROL System]** > **[!UICONTROL Cache Management]** e clique em **[!UICONTROL Flush Cache]** para atualizar todos os caches inválidos.

## Obter ajuda

Contato [Suporte Adobe Commerce](mailto:quick-checkout-support@adobe.com) para obter assistência.
