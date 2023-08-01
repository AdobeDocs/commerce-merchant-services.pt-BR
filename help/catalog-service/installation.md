---
title: Integração e instalação
description: Saiba como instalar [!DNL Catalog Service]
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: 04b1553e7cc16d142b72553ca2a6bb9d6a6b5eb4
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---

# Integração e instalação

Consulte uma apresentação do processo do Serviço de catálogo.

Parte 1:

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

Parte 2:

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

## Pré-requisitos

O processo de integração do [!DNL Catalog Service] requer acesso à linha de comando do servidor. Se você não estiver familiarizado com o trabalho a partir da linha de comando, peça ajuda a um desenvolvedor ou integrador de sistemas.

### Requisitos de software

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- Compositor: 2.x

### Plataformas compatíveis

- Adobe Commerce na infraestrutura em nuvem: 2.4.4+
- Adobe Commerce no local: 2.4.4+

## Ambientes

O Serviço de catálogo tem dois ambientes disponíveis para integração:

- Sandbox (https://catalog-service-sandbox.adobe.io/graphql) - usada para teste e validação antes de entrar em funcionamento
- Produção (https://catalog-service.adobe.io/graphql)- usado para tráfego direto para comerciantes e sites do Commerce

O teste de carga só deve ser executado no ambiente de sandbox. Recomenda-se que uma [Tíquete de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) ser aberto durante o teste de carga para que a equipe de Serviços possa antecipar o tráfego adicional do servidor.

## Instalação e configuração

Para começar a usar o Serviço de catálogo do Adobe Commerce, as seguintes etapas são necessárias:

- Instalar as extensões de exportação de dados
- Configurar o serviço e a exportação de dados
- Acessar o serviço

### Instalar as extensões de exportação de dados

O processo de integração do Serviço de Catálogo requer acesso à linha de comando do servidor.

A extensão do Serviço de catálogo pode ser instalada na infraestrutura em nuvem do Adobe Commerce e em instâncias locais.

O Serviço de catálogo é instalado com chaves do Composer, que estão vinculadas à conta do Commerce [mageid](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-personal/#field-descriptions) fornecido durante o processo de inscrição. O Composer usa essas chaves durante a instalação inicial do Adobe Commerce ou em situações em que as chaves do Composer não eram salvas anteriormente em um ambiente externo `auth.json` arquivo.

Consulte [Obter suas chaves de autenticação](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) para obter mais informações sobre como obter chaves do Composer.

#### Adobe Commerce na infraestrutura em nuvem

Use esse método para instalar a extensão Serviço de Catálogo para uma instância do Commerce Cloud.

1. Abra o `<Commerce_root>/composer.json` em um editor de texto e atualize a seção exigida da seguinte maneira:

```json
"require": {
  "magento/catalog-service": "^2.2.0"
}
```

1. Teste a nova configuração localmente e atualize as dependências:

```bash
composer update
```

O comando atualiza todas as dependências.

1. Confirme e envie suas alterações para `composer.json` e `composer.lock`.

#### No local

Use esse método para instalar a extensão Serviço de Catálogo para uma instância local.

1. Abra o `<Commerce_root>/composer.json` em um editor de texto e atualize a seção exigida da seguinte maneira:

```json
"require": {
    "magento/catalog-service": "^2.2.0"
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

Depois de instalar o Serviço de Catálogo, você deve configurar o [Conector dos Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) especificando as chaves de API e selecionando um Espaço de dados SaaS.

Após a configuração SaaS ser concluída, execute uma sincronização de dados inicial seguindo o [Sincronização de catálogo](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) guia.

Para garantir que a exportação de catálogo esteja sendo executada corretamente:

- Confirme se os trabalhos cron estão em execução.
- Verifique se os indexadores estão em execução.
- Certifique-se de que o `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, e `Product Variant Feed` indexadores são definidos como &quot;Atualizar por programação&quot;.

A sincronização inicial pode levar de alguns minutos a horas, dependendo do tamanho do catálogo. Após a sincronização inicial, o catálogo exporta dados do produto do servidor do Commerce para os Commerce services de forma contínua, a fim de manter os serviços atualizados.

### Acessar o serviço

A API do Serviço de catálogo é acessível por meio de comandos POST em HTTPS.

Para obter a chave de API, vá para a área Conector do Commerce Service no administrador e copie a chave de API pública.

Leia o [Documentação do GraphQL](https://developer.adobe.com/commerce/webapi/graphql/) para entender como consultar e enviar os cabeçalhos necessários para gerar solicitações de API.

Para permitir o Serviço de Catálogo por meio de um firewall, adicione `commerce.adobe.io` à lista de permissões.

## Serviço de catálogo e API Mesh

A variável [Malha de API para o Construtor de aplicativos Adobe Developer](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) O permite aos desenvolvedores integrar APIs privadas ou de terceiros e outras interfaces com produtos Adobe usando o Adobe IO.

Consulte a  [Serviço de catálogo e API Mesh](mesh.md) tópico para obter detalhes sobre instalação e configuração.
