---
title: Instalação
description: '"Instale o [!DNL Store Fulfillment solution] para uma loja da Adobe Commerce usando o Composer para PHP."'
role: User, Admin
level: Intermediate
exl-id: 6613268a-7d22-4c54-af89-834921b7f262
source-git-commit: 66c4ca972004c43fa55795006b1511820ca9b514
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---


# Instalação

Conclua a instalação inicial do [!DNL Store Fulfillment for Adobe Commerce by Walmart Commerce Technologies] em um ambiente de não produção com o gerenciador de filas em execução e o armazenamento em cache configurado para permitir a manipulação de exceções. Certifique-se de que seu ambiente de desenvolvimento inclua ferramentas de desenvolvimento para garantir práticas recomendadas para operar e manter sua instância do Adobe Commerce.

## Pré-requisitos

Revise o [requisitos](solution-requirements.md) para a solução Store Fulfillment e reúna as informações necessárias antes de instalar o [!DNL Store Fulfillment] para Adobe Commerce.

Se tiver instalado uma versão de pré-lançamento ou beta da extensão Loja de fornecimento para Adobe Commerce, use o seguinte comando para removê-la antes de instalar a versão atual.

```terminal
rm -rf composer.lock vendor/walmart &&
composer require walmart/magento-bopis-metapackage:1.0.0
```

## Requisitos de instalação

- **Acesso ao Arquivo de software da Loja da Walmart Commerce Technologies (arquivo .zip)**-Durante o processo de integração e ativação, trabalhe com seu Gerente de conta para obter acesso ao arquivo de instalação da extensão de disponibilização da loja.

- **Informações da conta do Adobe Commerce**-Instalação do [!DNL Store Fulfillment] a solução exige um [Conta comercial](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}. Você precisa de uma ID de conta e credenciais com acesso de Proprietário ou Administrador ao [!DNL Adobe Commerce] projeto.

- Para [!DNL Adobe Commerce] em projetos de infraestrutura em nuvem, os instaladores de software devem ter acesso de administrador ao projeto do Cloud. Consulte [Gerenciar o acesso do usuário](https://devdocs.magento.com/cloud/project/user-admin.html).

- **Experiência usando o Composer e a[!DNL Commerce CLI]**—Consulte [Instalação geral da CLI](https://devdocs.magento.com/extensions/install/){target=&quot;_blank&quot;} para obter informações sobre como usar essas ferramentas para instalar e gerenciar extensões no [!DNL Adobe Commerce] plataforma.

- **Experiência ao instalar extensões de terceiros no Adobe Commerce**-Para referência, consulte a documentação do Adobe Commerce.

   - [Instalar uma extensão para uma instância do Adobe Commerce on cloud Infrastructure](https://devdocs.magento.com/cloud/howtos/install-components.html#install-an-extension).

   - [Instalar uma extensão para uma instância local do Adobe Commerce](https://devdocs.magento.com/extensions/install/).

### Etapa 1: Baixe o pacote de extensão

Siga as instruções fornecidas pelos representantes da conta para baixar o arquivo de arquivamento que contém os pacotes Composer para instalar a extensão Serviços de preenchimento da loja.

### Etapa 2: Extrair artefatos de extensão para seu aplicativo

Extraia o arquivo de arquivamento que contém o pacote de integração para instalar a extensão Store Fulfillment Services.

1. Crie um diretório de destino para os arquivos extraídos.

   - Na linha de comando, vá para o diretório raiz doc do servidor da Web.

   - Crie um `artifacts` diretório.

1. Extraia o arquivo de arquivamento para o novo diretório.

1. Verifique se os arquivos extraídos estão revisando a lista de arquivos.

   ```
   ../var/www/html/artifacts]$ ls -a
   .
   ..
   bopis-sdk.zip
   module-magento-bopis-alternate-pickup-contact-admin-ui.zip
   module-magento-bopis-alternate-pickup-contact-api.zip
   ```

### Etapa 3: Configurar seu aplicativo usando o Composer

Use o Composer para configurar o diretório de origem para a instalação e instalar a extensão Store Fulfillment Services .

1. Configure o repositório de origem para a instalação do Composer.

   ```bash
   composer config repositories.artifacts artifact artifacts/
   ```

1. Adicione a extensão Store Fulfillment Services a `composer.json`.

   ```bash
   composer require walmart/magento-bopis-metapackage:1.0.0
   ```

>[!NOTE]
>
>Para obter melhor desempenho em instâncias locais do Adobe Commerce, você pode [atualizar a configuração de carregamento automático](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/deployment-flow.html#update-the-autoloader): `composer dump-autoload --optimize`

### Etapa 4: Atualizar o esquema e os dados do banco de dados

Conclua a instalação usando o `bin/magento setup:upgrade` para atualizar o esquema do banco de dados e os dados com as alterações para oferecer suporte à solução de disponibilização da loja.

>Observação:
>Para projetos de infraestrutura em nuvem do Adobe Commerce, não é necessário registrar a extensão . Em vez disso, confirme as alterações de código da etapa anterior e envie-as para a ramificação de ambiente. Os comandos para atualizar o schema do banco de dados e os dados são executados automaticamente durante o processo de build e implantação da nuvem.

### Etapa 5: Conclua a instalação

1. Registre a extensão com o Adobe Commerce usando o `setup:upgrade` comando Magento CLI.

   ```terminal
   bin/magento setup:upgrade
   ```

1. Se solicitado, recompile seu [!DNL Commerce] projeto.

   ```bash
   bin/magento setup:di:compile
   ```

1. Limpe o cache.

   ```bash
   bin/magento cache:clean
   ```

1. Desative o modo de manutenção.

   ```bash
   bin/magento maintenance:disable
   ```

### Etapa 6: Verifique a instalação

No servidor do Adobe Commerce, verifique se os módulos da extensão Store Fulfillment Services estão instalados e ativados.

1. Faça logon no servidor.

   Para instalações no Adobe Commerce na infraestrutura de nuvem, [usar SSH para fazer logon no ambiente remoto](https://devdocs.magento.com/cloud/env/environments-ssh.html#ssh).

1. Verifique se os módulos de Serviços de Atendimento da Loja estão ativados.

   ```bash
   bin/magento module:status  --enabled | grep Walmart
   ```

   A saída deve incluir os seguintes módulos:

   ```
   Walmart_BopisBase
   Walmart_BopisAlternatePickupContact
   Walmart_BopisAlternatePickupContactFrontend
   Walmart_BopisApiConnector
   Walmart_BopisAlternatePickupContactAdminUi
   Walmart_BopisCheckoutPickInStoreApi
   Walmart_BopisInventorySourceAdminUi
   Walmart_BopisCheckoutPickInStore
   Walmart_BopisInventoryCatalogApi
   Walmart_BopisPreferredLocationApi
   Walmart_BopisHomeDeliveryApi
   Walmart_BopisHomeDelivery
   Walmart_BopisPreferredLocation
   Walmart_BopisInventoryCatalog
   Walmart_BopisPreferredLocationFrontend
   Walmart_BopisCheckoutPickInStoreAdminUi
   Walmart_BopisInventorySourceApi
   Walmart_BopisInventorySourceFaasSync
   Walmart_BopisInventorySourceReservation
   Walmart_BopisLocationCheckInApi
   Walmart_BopisLogging
   Walmart_BopisStoreAssociateApi
   Walmart_BopisLocationCheckInFrontend
   Walmart_BopisStoreAssociate
   Walmart_BopisOperationQueue
   Walmart_BopisOperationQueueAdminUi
   Walmart_BopisOperationQueueApi
   Walmart_BopisOrderFaasSync
   Walmart_BopisOrderUpdateApi
   Walmart_BopisLocationCheckIn
   Walmart_BopisInventoryCatalogAdminUi
   Walmart_BopisPreferredLocationAdminUi
   Walmart_BopisDeliverySelection
   Walmart_BopisCheckoutPickInStoreFrontend
   Walmart_BopisLocationCheckInAdminUi
   Walmart_BopisStoreAssociateAdminUi
   Walmart_BopisOrderUpdate
   Walmart_BopisStoreAssociateTfa
   Walmart_BopisStoreAssociateTfaApi
   ```

### Etapas adicionais

Se necessário, use a `[setup:static-content: deploy](https://devdocs.magento.com/guides/v2.4/reference/cli/magento-commerce.html#setupstatic-contentdeploy)` comando CLI para implantar arquivos de visualização estáticos no ambiente de produção.

```terminal
php bin/magento setup:static-content:deploy -f
```

O `-f` é necessária se você estiver usando um tema em branco.

>[!NOTE]
>
>Para obter mais informações, consulte [Práticas recomendadas de implantação de conteúdo estático no Adobe Commerce](https://support.magento.com/hc/en-us/articles/360031624091) no Centro de ajuda da Adobe Commerce.
