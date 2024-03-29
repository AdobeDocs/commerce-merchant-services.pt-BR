---
title: Instalar [!DNL Payment Services]
description: Instale a extensão Serviços de Pagamentos.
exl-id: babaa91a-9376-4acb-b934-a89f9df52016
role: Admin
feature: Payments, Checkout, Install, Upgrade
source-git-commit: 6ba5a283d9138b4c1be11b80486826304c63247f
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Instalar [!DNL Payment Services]

Download e instalação do [!DNL Payment Services] extensão para [!DNL Adobe Commerce] e [!DNL Magento Open Source] é uma etapa de pré-requisito para usar o [!DNL Payment Services].

![[!DNL Payment Services] exibição do administrador da extensão](assets/admin-view.png){width="300" zoomable="yes"}

## Baixar a extensão

Primeiro, baixe a extensão de [Commerce Marketplace](https://experienceleague.adobe.com/docs/commerce-admin/start/resources/commerce-marketplace.html) antes de instalá-lo.

1. Navegue até a [Extensão de serviços de pagamento no Commerce Marketplace](https://commercemarketplace.adobe.com/magento-payment-services.html).
1. Para escolher a edição e a versão, alterne **[!UICONTROL Edition]** e **[!UICONTROL Your store version]** às suas seleções preferidas.
1. Clique em **[!UICONTROL Add to Cart]**.
1. Conclua o check-out e clique em **[!UICONTROL Place Order]**.
1. Verifique o email associado ao download do Marketplace para obter a confirmação e os detalhes do pedido.

## Instalar a extensão

Você pode instalar o [!DNL Payment Services] extensão para ambos [!DNL Adobe Commerce] na infraestrutura em nuvem e em instâncias locais, que estão vinculadas à sua conta do Commerce [mageid](https://devdocs.magento.com/marketplace/sellers/profile-personal.html#field-descriptions) fornecido no processo de inscrição. [!DNL Magento Open Source] Os clientes do usam as instruções no local.

O Composer usa essas chaves durante a instalação inicial do [!DNL Adobe Commerce], ou em situações nas quais as chaves do Composer não foram salvas anteriormente no `auth.json` arquivo.

Consulte [Obter suas chaves de autenticação](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) para obter mais informações sobre como obter chaves do Composer.

Consulte [Instalar uma extensão](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/extensions.html) para obter mais informações sobre o que considerar antes de baixar e instalar uma extensão.

### [!DNL Adobe Commerce] na infraestrutura em nuvem

Este método é usado para instalar o [!DNL Payment Services] extensão para uma instância Commerce Cloud.

1. Atualize seu `composer.json` arquivo:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Atualize as dependências e instale a extensão:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Use o `composer update` comando para atualizar todas as dependências raiz.

1. Confirme e envie suas alterações.

### No local e outras configurações

Este método é usado para instalar o [!DNL Payment Services] extensão para uma instância local e [!DNL Magento Open Source] clientes.

1. Para obter a extensão, execute estes comandos:

   ```bash
   composer require magento/payment-services --no-update
   ```

1. Atualize as dependências e instale a extensão:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Use o `composer update` comando para atualizar todas as dependências raiz.

1. Atualize sua instância:

   ```bash
   bin/magento setup:upgrade
   ```

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```

1. Confirmar alterações.
1. Para garantir que o código comprometido seja implantado, atualize a instância.

## Atualizar a extensão

Quando uma nova versão do [!DNL Payment Services] for lançado, você poderá atualizar facilmente sua extensão.

1. Para obter a versão mais recente do pacote:

   ```bash
   composer update magento/payment-services --with-dependencies
   ```

   Use o `composer update` comando para atualizar todas as dependências raiz.

1. Confirme e envie suas alterações.

## Solução de problemas

Você pode ver erros ao tentar instalar o [!DNL Payment Services] extensão. Use os seguintes métodos de solução de problemas para resolver os erros.

### Chaves do compositor incorretas

Se você vir o seguinte erro que indica que você tem as chaves do Composer incorretas:

```terminal
Could not find a matching version of package magento/payment-services. Check the package spelling, your version constraint and that the package is available in a stability which matches your minimum-stability (stable).
```

Verifique se as chaves do Composer são válidas e se você tem acesso a outros pacotes de Magento.

Para ver quais chaves do Composer estão configuradas:

1. Localize o `auth.json` arquivo:

   ```bash
   composer config --global home
   ```

1. Exibir o `auth.json` arquivo:

   ```bash
   cat /path/to/auth.json
   ```

1. Consulte [quais chaves estão associadas à sua conta do Commerce `MageID`](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html).

### Memória insuficiente para o PHP

Se você vir o seguinte erro indicando que você não tem memória suficiente para o PHP:

```terminal
Fatal error: Allowed memory size of 2146435072 bytes exhausted (tried to allocate 4096 bytes) in phar:///usr/local/bin/composer/src/Composer/DependencyResolver/RuleWatchGraph.php on line 52
```

[Aumente o limite de memória](https://devdocs.magento.com/cloud/project/magento-app-php-ini.html#increase-php-memory-limit) para PHP em seu ambiente no `php.ini`.

Como alternativa, você pode especificar o limite de memória usando este comando: `php -d memory_limit=-1 [path to composer]/composer require magento/payment-services`.

Por exemplo:

```bash
php -d memory_limit=-1 vendor/bin/composer require magento/payment-services
```
