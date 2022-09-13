---
title: '"Integração e instalação"'
description: '"Saiba como instalar [!DNL Catalog Service]"'
source-git-commit: 7f6955ffc52669ff3b95957642b3a115bf1eb741
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---


# Integração e instalação

Os parceiros e clientes são bem-vindos a começar a usar o [!DNL Catalog Service] para Adobe Commerce Beta versão lançada em 9 de agosto de 2022. Para participar, você deve ler e concordar com a nossa [Termos do programa Adobe Commerce Beta](https://experiencecloudpanel.adobe.com/h/s/6eGskQlHvLSHztsNmKCWMy).

Depois de assinar o contrato, entre em contato com nossa equipe no [#storefront-services](https://magentocommeng.slack.com/archives/C03HVPG8RS4) canal Slack público. Forneceremos todas as informações e os próximos passos necessários para trabalhar com a [!DNL Catalog Service] Versão beta.

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

O [!DNL Catalog Service] O é instalado com chaves Composer, que estão vinculadas à ID do Magento ([mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) fornecido no processo de assinatura. O Composer usa essas chaves durante a instalação inicial do [!DNL Adobe Commerce]ou em situações em que as chaves do Composer não eram salvas anteriormente no `auth.json` arquivo.

Consulte [Obter as chaves de autenticação](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) para obter mais informações sobre como obter chaves Composer.

### Adobe Commerce na infraestrutura de nuvem

Use este método para instalar o [!DNL Catalog Service] para uma instância Commerce Cloud.

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

   <!-- What if the customer already has other services installed, and some of these lines are already present? Do they need to delete the duplications? What if the version numbers are different? -->

1. Atualize as dependências e instale a extensão:

   ```bash
   composer update
   ```

   O comando atualiza todas as dependências.

1. Confirme e envie suas alterações por push.

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

Para garantir que a exportação do catálogo esteja sendo executada corretamente, confirme se a variável [trabalhos cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) e [indexadores](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) estão em execução e o indexador Feed do produto está definido como Atualizar por agendamento.