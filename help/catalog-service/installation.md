---
title: Integração e instalação
description: Saiba como instalar [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: e11b4e86efe3483717cf4484a7fcce6e23015f4c
workflow-type: tm+mt
source-wordcount: '575'
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

## Ambientes

O Serviço de catálogo tem dois ambientes disponíveis para integração:

- Sandbox (https://catalog-service-sandbox.adobe.io/graphql) - usada para testes e validação antes de entrar em funcionamento
- Produção (https://catalog-service.adobe.io/graphql)-) usada para tráfego ao vivo para comerciantes e sites do Commerce

## Instalação e configuração

Para começar a usar o Serviço de catálogo do Adobe Commerce , as etapas a seguir são necessárias:

- Instalar as extensões de exportação de dados
- Configurar o serviço e a exportação de dados
- Acessar o serviço

### Instalar as extensões de exportação de dados

O processo de integração do Serviço de catálogo requer acesso à linha de comando do servidor.

A extensão Serviço de catálogo pode ser instalada na infraestrutura de nuvem da Adobe Commerce e em instâncias locais.

O Serviço de catálogo é instalado com chaves Composer, que estão vinculadas à conta Comércio [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) fornecido durante o processo de assinatura. O Composer usa essas chaves durante a instalação inicial do Adobe Commerce ou em situações em que as chaves do Composer não eram salvas anteriormente em uma chave externa `auth.json` arquivo.

Consulte [Obter as chaves de autenticação](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) para obter mais informações sobre como obter chaves Composer.

#### Adobe Commerce na infraestrutura de nuvem

Use este método para instalar a extensão Serviço de Catálogo para uma instância do Commerce Cloud.

1. Abra o `<Commerce_root>/composer.json` em um editor de texto e atualize a seção de solicitação da seguinte maneira:

   ```json
   "require": {
     "magento/module-saas-catalog": "^101.4.0",
     "magento/module-saas-product-override": "^101.4.0",
     "magento/module-saas-product-variant": "^101.4.0",
     "magento/module-bundle-product-data-exporter": "^101.3.1",
     "magento/module-catalog-data-exporter": "^101.3.1",
     "magento/module-catalog-inventory-data-exporter": "^101.3.1",
     "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
     "magento/module-configurable-product-data-exporter": "^101.3.1",
     "magento/module-data-exporter": "^101.3.1",
     "magento/module-parent-product-data-exporter": "^101.3.1",
     "magento/module-product-override-data-exporter": "^101.3.1",
     "magento/data-services": "^7.0.11",
     "magento/services-id": "^3.0.1",
     "magento/services-connector": "1.2.1",
     "magento/module-catalog-service-installer": "1.0.1"
   }
   ```

1. Teste a nova configuração localmente e atualize as dependências:

```bash
composer update
```

O comando atualiza todas as dependências.

1. Confirme e envie suas alterações para `composer.json` e `composer.lock`.

#### No local

Use este método para instalar a extensão Serviço de Catálogo para uma instância no local.

1. Abra o `<Commerce_root>/composer.json` em um editor de texto e atualize a seção de solicitação da seguinte maneira:

```json
"require": {
 "magento/module-saas-catalog": "^101.4.0",
 "magento/module-saas-product-override": "^101.4.0",
 "magento/module-saas-product-variant": "^101.4.0",
 "magento/module-bundle-product-data-exporter": "^101.3.1",
 "magento/module-catalog-data-exporter": "^101.3.1",
 "magento/module-catalog-inventory-data-exporter": "^101.3.1",
 "magento/module-catalog-url-rewrite-data-exporter": "^101.3.1",
 "magento/module-configurable-product-data-exporter": "^101.3.1",
 "magento/module-data-exporter": "^101.3.1",
 "magento/module-parent-product-data-exporter": "^101.3.1",
 "magento/module-product-override-data-exporter": "^101.3.1",
 "magento/data-services": "^7.0.11",
 "magento/services-id": "^3.0.1",
 "magento/services-connector": "1.2.1",
 "magento/module-catalog-service-installer": "1.0.1"
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

### Configurar o serviço e a exportação de dados

Depois de instalar o Serviço de catálogo, você deve configurar o [Conector do Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/experience-platform-connector/fundamentals/install.html?lang=en) especificando as chaves da API e selecionando um espaço de dados SaaS.

Depois que a configuração de SaaS for concluída, execute uma sincronização de dados inicial seguindo o guia de Sincronização de catálogo.

Para garantir que a exportação do catálogo esteja sendo executada corretamente:

- Confirme se os trabalhos do cron estão em execução.
- Verifique se os indexadores estão em execução.
- Certifique-se de que `Catalog Attributes Feed, Product Feed, Product Overrides Feed`e `Product Variant Feed` os indexadores são definidos como &quot;Atualizar por agendamento&quot;.

A sincronização inicial pode levar de alguns minutos a horas, dependendo do tamanho do catálogo. Após a sincronização inicial, o Catálogo exporta os dados do produto do servidor do Commerce para os serviços do Commerce de forma contínua para manter os serviços atualizados.

### Acessar o serviço

A API do Serviço de catálogo pode ser acessada por comandos POST em HTTPS.

Para obter a chave da api, acesse a área Conector do serviço de comércio no administrador e copie a chave da API pública.

Leia o [Documentação do GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) para entender como consultar e enviar os cabeçalhos necessários para gerar solicitações de API.

## Serviço de catálogo e malha de API

O [Mensagem de API para o Adobe Developer App Builder](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) permite que desenvolvedores integrem APIs privadas ou de terceiros e outras interfaces com produtos Adobe usando Adobe IO.

Consulte a  [Serviço de catálogo e malha de API](mesh.md) tópico para detalhes de instalação e configuração.
