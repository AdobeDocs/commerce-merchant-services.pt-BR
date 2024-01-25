---
title: Integração e instalação
description: "Saiba como instalar [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: d02ffe4028bdf5765fb0f23fd210f398729bee62
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Integração e instalação

Os vídeos a seguir o orientam pelo [!DNL Catalog Service] processo.

**Parte 1**: integração e instalação

>[!VIDEO](https://video.tv.adobe.com/v/3415599)

**Parte 2**: Uso do [!DNL Catalog Service]

>[!VIDEO](https://video.tv.adobe.com/v/3415600)

>[!BEGINSHADEBOX]

## Pré-requisitos

O processo de integração do [!DNL Catalog Service] requer acesso à linha de comando do servidor. Se você não estiver familiarizado com o trabalho a partir da linha de comando, peça ajuda a um desenvolvedor ou integrador de sistemas.

**Requisitos de software**

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- Compositor: 2.x

**Plataformas compatíveis**

- Adobe Commerce na infraestrutura em nuvem: 2.4.4+
- Adobe Commerce no local: 2.4.4+

>[!ENDSHADEBOX]

## Endpoints

[!DNL Catalog Service] O tem dois endpoints disponíveis para integração:

- Sandbox (`https://catalog-service-sandbox.adobe.io/graphql`) — usado para teste e validação antes de entrar em funcionamento
- Produção (`https://catalog-service.adobe.io/graphql`) — usado para tráfego direto para comerciantes e sites do Commerce

Todas as instâncias de teste do Commerce devem usar o ponto de extremidade da sandbox.

O teste de carga só deve ser executado no endpoint da sandbox. Recomenda-se que uma [Tíquete de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) ser aberto durante o teste de carga para que a equipe de Serviços possa antecipar o tráfego adicional do servidor.

## Instalação e configuração

Para começar com [!DNL Catalog Service] para o Adobe Commerce, as seguintes etapas são obrigatórias:

- Instalar as extensões de exportação de dados
- Configurar o serviço e a exportação de dados
- Acessar o serviço

### Instalar as extensões de exportação de dados

O processo de integração do [!DNL Catalog Service] requer acesso à linha de comando do servidor.

A variável [!DNL Catalog Service] a extensão do pode ser instalada na infraestrutura em nuvem do Adobe Commerce e em instâncias locais.

A variável [!DNL Catalog Service] O é instalado com as chaves do Composer, que estão vinculadas à conta do Commerce [`mageid`](https://developer.adobe.com/commerce/marketplace/guides/sellers/profile-information/) fornecido durante o processo de inscrição. O Composer usa essas chaves durante a instalação inicial do Adobe Commerce ou em situações em que as chaves do Composer não eram salvas anteriormente em um ambiente externo `auth.json` arquivo.

Consulte [Obter suas chaves de autenticação](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html) para obter mais informações sobre como obter chaves do Composer.

#### Adobe Commerce na infraestrutura em nuvem

Use este método para instalar o [!DNL Catalog Service] extensão para uma instância Commerce Cloud.

1. Na estação de trabalho local, altere para o diretório do projeto.
1. Adicione o módulo Serviço de Catálogo.

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. Atualizar dependências de pacote.

   ```bash
   composer update
   ```

1. Confirmar e enviar alterações de código para a `composer.json` e `composer.lock` arquivos.

#### No local

Use este método para instalar o [!DNL Catalog Service] extensão para uma instância local.

1. Use o Composer para adicionar o módulo Serviço de catálogo ao seu projeto:

   ```bash
   composer require "magento/catalog-service" "^3.0.1"
   ```

1. Atualize as dependências e instale a extensão:

   ```bash
   composer update
   ```

1. Atualizar o Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```

### Configurar o serviço e a exportação de dados

Depois de instalar [!DNL Catalog Service], você deve configurar o [Conector dos Commerce Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html#apikey) especificando as chaves de API e selecionando um Espaço de dados SaaS.

Após a configuração SaaS ser concluída, execute uma sincronização de dados inicial seguindo o [Sincronização de catálogo](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/data-services/catalog-sync.html) guia.

Para garantir que a exportação de catálogo esteja sendo executada corretamente:

- Confirme se os trabalhos cron estão em execução.
- Verifique se os indexadores estão em execução.
- Certifique-se de que o `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, e `Product Variant Feed` indexadores são definidos como &quot;Atualizar por programação&quot;.

A sincronização inicial pode levar de alguns minutos a horas, dependendo do tamanho do catálogo. Após a sincronização inicial, o catálogo exporta dados do produto do servidor do Commerce para os Commerce services de forma contínua, a fim de manter os serviços atualizados.

### Acessar o serviço

A variável [!DNL Catalog Service] A API pode ser acessada usando comandos POST em HTTPS.

Para obter a chave de API, vá para a área Conector do Commerce Service no administrador e copie a chave de API pública.

Leia o [Documentação do GraphQL](https://developer.adobe.com/commerce/services/graphql/) para entender como consultar e enviar os cabeçalhos necessários para gerar solicitações de API.

Para permitir [!DNL Catalog Service] por meio de um firewall, adicione `commerce.adobe.io` para o incluo na lista de permissões ➡.

## Serviço de catálogo e API Mesh

A variável [Malha de API para o Construtor de aplicativos Adobe Developer](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) O permite aos desenvolvedores integrar APIs privadas ou de terceiros e outras interfaces com produtos Adobe usando o Adobe IO.

Consulte a [[!DNL Catalog Service] e API Mesh](mesh.md) tópico para obter detalhes sobre instalação e configuração.
