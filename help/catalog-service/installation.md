---
title: Integração e instalação
description: "Saiba como instalar [!DNL Catalog Service]"
exl-id: 4e9fbdc9-67a1-4703-b8c0-8b159e0cc2a7
source-git-commit: a2841b809cfc52798dc3f1bdcc033a77333bf0e5
workflow-type: tm+mt
source-wordcount: '797'
ht-degree: 0%

---

# Integração e instalação

Instale o Serviço de catálogo para solicitar e receber dados do produto de uma instância do Commerce usando o [API GraphQL do serviço de catálogo](https://developer.adobe.com/commerce/services/graphql/catalog-service/). O Serviço de catálogo é fornecido como um metapackage de compositor no repositório repo.magento.com.

>[!NOTE]
>
>Se sua instância do Commerce usa o Live Search ou o Product Recommendations, o Serviço de Catálogo será instalado ou atualizado automaticamente quando você integrar ou atualizar esses serviços. Para obter detalhes, consulte as instruções de instalação do [Live Search](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install) e [Recommendations do produto](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/product-recommendations/getting-started/install-configure).



## Requisitos do sistema

**Requisitos de software**

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2, 8.3
- Compositor: 2.x

**Plataformas compatíveis**

- Adobe Commerce na infraestrutura em nuvem: 2.4.4+
- Adobe Commerce no local: 2.4.4+

## Endpoints

[!DNL Catalog Service] O tem dois endpoints disponíveis para integração:

- Sandbox (`https://catalog-service-sandbox.adobe.io/graphql`) — usado para teste e validação antes de entrar em funcionamento
- Produção (`https://catalog-service.adobe.io/graphql`) — usado para tráfego direto para comerciantes e sites da Commerce

Todas as instâncias de teste do Commerce usam o ponto de extremidade da sandbox.

Execute todos os testes de carga no endpoint da sandbox. Antes de começar o teste de carga, envie um [Tíquete de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) para que a equipe de Serviços possa antecipar o tráfego adicional do servidor.

## Instalação e configuração

Para começar com [!DNL Catalog Service] para o Adobe Commerce, as seguintes etapas são obrigatórias:

- Instalar a extensão Serviço de Catálogo (`magento/catalog-service`)
- Configurar o serviço e a exportação de dados
- Acessar o serviço

### Instalar a extensão Serviço de Catálogo

>[!BEGINSHADEBOX]

**Pré-requisito**

- Access [repo.magento.com](https://repo.magento.com) para instalar a extensão. Para geração de chaves e obtenção dos direitos necessários, consulte [Obter suas chaves de autenticação](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/authentication-keys). Para instalações em nuvem, consulte [Guia da infraestrutura do Commerce na nuvem](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/authentication-keys)

- Acesso à linha de comando do servidor de aplicativos do Adobe Commerce.

>[!ENDSHADEBOX]

Instale a versão mais recente da extensão Serviços de catálogo (`magento/catalog-service`) em uma instância do Adobe Commerce que esteja executando o Adobe Commerce versão 2.4.4 ou posterior. O Serviço de catálogo é fornecido como um metapackage de compositor do [repo.magento.com](https://repo.magento.com) repositório.

>[!BEGINTABS]

>[!TAB Infraestrutura em nuvem]

Use este método para instalar o [!DNL Catalog Service] extensão para uma instância Commerce Cloud.

1. Na estação de trabalho local, altere para o diretório do projeto do Adobe Commerce na infraestrutura em nuvem.

   >[!NOTE]
   >
   >Para obter informações sobre como gerenciar os ambientes de projeto do Commerce localmente, consulte [Gerenciamento de ramificações com a CLI](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/cli-branches) no _Guia do usuário do Adobe Commerce na infraestrutura em nuvem_.

1. Confira a ramificação do ambiente para atualizar usando a CLI do Adobe Commerce Cloud.

   ```shell
   magento-cloud environment:checkout <environment-id>
   ```

1. Adicione o módulo Serviço de Catálogo.

   ```bash
   composer require "magento/catalog-service" "^3.0.1" --no-update
   ```

1. Atualizar dependências de pacote.

   ```bash
   composer update "magento/catalog-service"
   ```

1. Confirmar e enviar alterações de código para a `composer.json` e `composer.lock` arquivos.

1. Adicionar, confirmar e enviar as alterações de código para o `composer.json` e `composer.lock` para o ambiente de nuvem.

   ```shell
   git add -A
   git commit -m "Add catalog service module"
   git push origin <branch-name>
   ```

   Enviar as atualizações inicia o [Processo de implantação da nuvem do Commerce](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/deploy/process) para aplicar as alterações. Verifique o status da implantação no [implantar log](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/test/log-locations#deploy-log).

>[!TAB No local]

Use este método para instalar o [!DNL Catalog Service] extensão para uma instância local.

1. Use o Composer para adicionar o módulo Serviço de catálogo ao seu projeto:

   ```bash
   composer require "magento/catalog-service" "^3.0.1"  --no-update
   ```

1. Atualize as dependências e instale a extensão:

   ```bash
   composer update  "magento/catalog-service"
   ```

1. Atualizar o Adobe Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Limpe o cache:

   ```bash
   bin/magento cache:clean
   ```

   >[!TIP]
   >
   >Em alguns casos, especialmente ao implantar na produção, você pode evitar a limpeza do código compilado, pois pode levar algum tempo. Certifique-se de fazer backup do sistema antes de fazer qualquer alteração.

>[!ENDTABS]

### Configurar o serviço e a exportação de dados

Depois de instalar o [!DNL Catalog Service], conclua as seguintes tarefas para integrar o serviço de Catálogo à sua instância do Adobe Commerce. Essa integração permite a sincronização de dados e a comunicação entre a instância do Commerce, o Serviço de catálogo e outros serviços de suporte.

1. Configurar o [Conector dos Commerce Services](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/user-guides/integration-services/saas) especificando as chaves de API e selecionando um Espaço de dados SaaS.

   A configuração do Commerce Services Connector é um processo único necessário para usar serviços da Adobe Commerce, como o Serviço de catálogo, o Live Search e o Product Recommendations. Se você já tiver configurado o conector para outro serviço, ignore esta etapa.

1. Execute uma sincronização de dados inicial a partir do [Painel de gerenciamento de dados](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).

   A sincronização inicial pode levar de alguns minutos a horas, dependendo do tamanho do catálogo. Você pode monitorar o status de sincronização no painel de Gerenciamento de dados. Após a sincronização inicial, o Catálogo exporta dados do produto de forma contínua para manter os serviços atualizados.

Para garantir que a exportação de catálogo esteja sendo executada corretamente:

- [Confirme se os trabalhos cron estão em execução](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-readiness-check-issues).
- Verifique se os indexadores estão sendo executados no [Admin](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management) ou usando o comando da CLI do Commerce `bin/magento indexer:info`.
- Verifique se `Catalog Attributes Feed, Product Feed, Product Overrides Feed`, e `Product Variant Feed` indexadores estão definidos como `Update by Schedule`.

### Acessar o serviço

A variável [!DNL Catalog Service] A API do GraphQL pode ser acessada no ` https://catalog-service.adobe.io/graphql` usando comandos POST em HTTPS.

Em suas consultas do GraphQL, você deve especificar vários cabeçalhos HTTP, incluindo a chave de API pública adicionada à configuração do Adobe Commerce Services Connector no Administrador. Para obter detalhes, consulte [GraphQL de serviços de vitrine](https://developer.adobe.com/commerce/services/graphql/) documentação.

### Configuração do firewall

Para permitir [!DNL Catalog Service] por meio de um firewall, adicione `commerce.adobe.io` para o incluo na lista de permissões ➡.

## Serviço de catálogo e API Mesh

A variável [Malha de API para o Construtor de aplicativos Adobe Developer](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/) O permite aos desenvolvedores integrar APIs privadas ou de terceiros e outras interfaces com produtos Adobe usando o Adobe IO.

Consulte a [[!DNL Catalog Service] e API Mesh](mesh.md) tópico para obter detalhes sobre instalação e configuração.

## Painel de gerenciamento de dados

Para obter mais informações sobre [!DNL Catalog Service] sincronização de dados, consulte o [Painel de gerenciamento de dados](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/data-transfer/data-dashboard).
