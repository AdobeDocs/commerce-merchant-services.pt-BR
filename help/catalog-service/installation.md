---
title: Integração e instalação
description: Saiba como instalar [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 683b599e183f1269cdd6c3772d1b33c43cf1156e
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Integração e instalação

## Pré-requisitos

O processo de integração para [!DNL Catalog Service] requer acesso à linha de comando do servidor. Se você não estiver familiarizado com o trabalho a partir da linha de comando, peça ajuda a um desenvolvedor ou integrador de sistemas.

### Requisitos de software

- Adobe Commerce 2.4.x
- PHP 8.1, 7.4, 7.3
- Compositor: 2.x, 1.x

### Plataformas compatíveis

- Adobe Commerce na infraestrutura de nuvem: 2.4.x
- Adobe Commerce nas instalações: 2.4.x

## Instalar a extensão

Você pode instalar o [!DNL Catalog Service] extensão para o Adobe Commerce na infraestrutura de nuvem e instâncias locais.

O [!DNL Catalog Service] O é instalado com chaves Composer, que estão vinculadas à conta do Commerce [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) fornecido no processo de assinatura. O Composer usa essas chaves durante a instalação inicial do [!DNL Adobe Commerce]ou em situações em que as chaves do Composer não eram salvas anteriormente no `auth.json` arquivo.

Consulte [Obter as chaves de autenticação](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) para obter mais informações sobre como obter chaves Composer.

### Adobe Commerce na infraestrutura de nuvem

Use este método para instalar o [!DNL Catalog Service] para uma instância Commerce Cloud.

1. Abra o `<Commerce_root>/composer.json` em um editor de texto e atualize o `require` seção como segue:

   ```json
   "require": {
    "magento/composer-root-update-plugin": "^2.0.2",
    "magento/magento-cloud-metapackage": ">=2.4.5 <2.4.6",
    "magento/saas-export": "^101.4.0",
    "magento/commerce-data-export": "^101.3.1",
    "magento/commerce-data-export-ee": "^101.3.1",
    "magento/services-id": "^3.0.1",
    "magento/services-connector": "1.2.1"
    }
   ```

1. Teste a nova configuração localmente e atualize as dependências:

   ```bash
   composer update
   ```

   O comando atualiza todas as dependências.

1. Confirme e envie suas alterações para `composer.json` e `composer.lock`.

### No local

Use este método para instalar o [!DNL Catalog Service] extensão para uma instância local.

1. Abra o `<Commerce_root>/composer.json` em um editor de texto e atualize o `require` seção como segue:

   ```json
   "require": {
     "magento/magento-cloud-metapackage": ">=2.4.3 <2.4.4",
     "magento/composer-root-update-plugin": "~1.1",
     "magento/saas-export": "^101.3.1",
     "magento/commerce-data-export": "^101.2.4",    
     "magento/commerce-data-export-ee": "^101.2.4",
     "magento/services-id": "^3.0.0",
     "magento/services-connector": "1.2.1"
   }
   ```

1. Atualize as dependências e instale a extensão:

   ```bash
   composer update
   ```

   O comando atualiza todas as dependências.

1. Atualizar o Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```

## Configurar exportação de catálogo

Depois de instalar [!DNL Catalog Service], você deve configurar o [Conector do Commerce Services](../landing/saas.md) especificando chaves de API e selecionando um espaço de dados SaaS.

Para garantir que a exportação do catálogo esteja sendo executada corretamente:

- Confirme que [trabalhos cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) estão em execução.
- Verifique o [indexadores](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) estão em execução.
- Certifique-se de que `Catalog Attributes Feed`, `Product Feed`, `Product Overrides Feed`e `Product Variant Feed` os indexadores são definidos como `Update by Schedule`.

## [!DNL Catalog Service] demonstração

Assista a este vídeo para saber mais sobre [!DNL Catalog Service] Instalação e ensaio:

>[!VIDEO](https://video.tv.adobe.com/v/3409390?quality=12&learn=on)
