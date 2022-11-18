---
title: Integração e instalação
description: Saiba como instalar [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: ea4b386d7e378b30641e623cb190923dc50563d8
workflow-type: tm+mt
source-wordcount: '456'
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
   "require":{
   "magento/composer-root-update-plugin":"^2.0.2",
   "magento/magento-cloud-metapackage":">=2.4.5 <2.4.6",
   "magento/catalog-service": "^1.0.0"
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
   "magento/composer-root-update-plugin":"^2.0.2",
   "magento/catalog-service": "^1.0.0"
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

## Serviço de catálogo e malha de API

O [Malha da API](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) permite que desenvolvedores integrem APIs privadas ou de terceiros e outras interfaces com produtos Adobe usando Adobe IO.

A primeira etapa para usar a malha de API com o serviço de catálogo é conectar a malha de API à sua instância. Veja as instruções detalhadas em [Criar uma malha](https://developer.adobe.com/graphql-mesh-gateway/gateway/create-mesh/).

Para concluir a configuração, será necessário [Pacote Adobe IO CLI](https://developer.adobe.com/runtime/docs/guides/tools/cli_install/) instalado.

Depois que a malha for configurada no Adobe IO, execute o seguinte comando para conectar a nova malha.

```bash
aio api-mesh:source:install "CommerceCatalogServiceGraph" -f variables.json
```

em que `variables.json` é um arquivo separado que armazena valores comumente usados para Adobe IO.
Por exemplo, a chave da API pode ser salva no arquivo :

```json
{
    "CATALOG_SERVICE_API_KEY":"your_api_key"
}
```

Após executar esse comando, o Serviço de catálogo deve estar sendo executado pela malha da API.

## Configurar exportação de catálogo

Depois de instalar [!DNL Catalog Service], você deve configurar o [Conector do Commerce Services](../landing/saas.md) especificando chaves de API e selecionando um espaço de dados SaaS.

Para garantir que a exportação do catálogo esteja sendo executada corretamente:

- Confirme que [trabalhos cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) estão em execução.
- Verifique o [indexadores](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) estão em execução.
- Certifique-se de que `Catalog Attributes Feed`, `Product Feed`, `Product Overrides Feed`e `Product Variant Feed` os indexadores são definidos como `Update by Schedule`.

## [!DNL Catalog Service] demonstração

Assista a este vídeo para saber mais sobre [!DNL Catalog Service] Instalação e ensaio:

>[!VIDEO](https://video.tv.adobe.com/v/3409390?quality=12&learn=on)
