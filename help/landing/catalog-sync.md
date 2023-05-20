---
title: Sincronização de catálogo
description: Saiba como exportar dados do produto do [!DNL Commerce] servidor para [!DNL Commerce Services] de forma contínua para manter os serviços atualizados.
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
source-git-commit: 3931a8c2e19f0024017682b029451bf1670d94b1
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# Sincronização de catálogo

O Adobe Commerce e o Magento Open Source usam indexadores para compilar dados de catálogo em tabelas. O processo é automaticamente acionado por [events](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) como uma alteração no preço de um produto ou no nível do inventário.

O processo de sincronização do catálogo é executado a cada hora para permitir [!DNL Commerce] serviços para usar dados de catálogo. A sincronização do catálogo exporta dados do produto do [!DNL Commerce] servidor para [!DNL Commerce] serviços de forma contínua para manter os serviços atualizados. Por exemplo, [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) O precisa das informações atuais do catálogo para retornar com precisão as recomendações com nomes, preços e disponibilidade corretos. Você pode usar o _Sincronização de catálogo_ painel de controle para observar e gerenciar o processo de sincronização ou a [interface de linha de comando](#resynccmdline) para acionar a sincronização do catálogo e reindexar os dados do produto para consumo por [!DNL Commerce] serviços.

>[!NOTE]
>
> Para usar o _Sincronização de catálogo_ ou na interface de linha de comando, você deve ter uma [Chave da API e um espaço de dados SaaS configurado](saas.md).

## Acesso ao painel Sincronização do catálogo

>[!NOTE]
>
> A variável _Sincronização de catálogo_ o painel só estará disponível quando a variável _Recommendations do produto_ Os módulos do são instalados e refletem projeções de dados relacionadas somente a esse recurso. Suporte para outros Commerce Services, como _Live Search_ e _Serviço de catálogo_ estão planejados para o futuro.

Para acessar o painel Sincronização de catálogo, selecione **Sistema** > _Transferência de dados_ > **Sincronização de catálogo**.

Com o **Sincronização de catálogo** painel é possível:

- Exibir o status da sincronização (**Em andamento**, **Sucesso**, **Failed**)
- Exibir o número total de produtos sincronizados, se bem-sucedido
- Pesquisar produtos sincronizados para exibir seu estado atual
- Pesquisar catálogo da loja por nome, SKU e assim por diante
- Exibir detalhes do produto sincronizado no JSON para ajudar a diagnosticar uma discrepância de sincronização
- Reiniciar o processo de sincronização

### Última sincronização

Relata um status de sincronização de:

- **Sucesso** - Exibe a data e a hora em que a sincronização foi bem-sucedida e o número de produtos atualizados
- **Failed** - Exibe a data e a hora em que a sincronização foi tentada
- **Em andamento** - Exibe a data e a hora da última sincronização bem-sucedida

>[!NOTE]
>
> O processo de sincronização de catálogo é executado automaticamente a cada hora. No entanto, se você não estiver vendo produtos na loja ou se os produtos não refletirem as alterações recentes feitas, é possível resolver [problemas de sincronização do catálogo](#resolvesync).

### Produtos sincronizados

Exibe o número total de produtos sincronizados do [!DNL Commerce] catálogo. Após a sincronização inicial, você deve esperar que somente os produtos alterados sejam sincronizados.

## Ressincronizar {#resync}

Se você precisar iniciar uma ressincronização do catálogo antes que a sincronização agendada por hora ocorra, é possível forçar uma ressincronização.

>[!NOTE]
>
> Forçar uma ressincronização aciona uma ressincronização de todo o catálogo de produtos, o que pode aumentar a carga dos recursos de hardware.

1. No _Sincronização de catálogo_ painel, selecione **Configurações**.

   A variável _Configurações de sincronização do catálogo_ é exibida.

1. No _Ressincronizar Dados_ clique em [!UICONTROL Resync].

   [!DNL Commerce] sincroniza seu catálogo durante a próxima janela de sincronização agendada. Dependendo do tamanho do catálogo, essa operação pode levar muito tempo.


## Produtos de catálogo sincronizados

A variável **Produtos de catálogo sincronizados** A tabela exibe as seguintes informações.

| Campo | Descrição |
|---|---|
| ID | Identificador exclusivo do produto |
| Nome | Nome da vitrine do produto |
| Tipo | Identifica o tipo do produto, como simples, configurável, para download e assim por diante |
| Última exportação | Data em que o produto foi exportado com êxito do catálogo pela última vez |
| Última modificação | Data da última modificação do produto no catálogo |
| SKU | Exibe a unidade de manutenção de estoque do produto |
| Preço | Preço do produto |
| Visibilidade | Uma configuração de visibilidade do produto, conforme definido na [!DNL Commerce] catálogo |

## Resolver problemas de sincronização do catálogo {#resolvesync}

Quando você aciona uma ressincronização de dados, pode levar até uma hora para que os dados sejam atualizados e refletidos nos componentes da interface do usuário, como unidades de recomendação. No entanto, se depois de aguardar uma hora você ainda notar discrepâncias entre o catálogo e o que aparece na loja ou se a sincronização do catálogo falhar, consulte o seguinte:

### Discrepância de dados

1. Exiba a exibição detalhada do produto em questão nos resultados da pesquisa.
1. Copie a saída JSON e verifique se o conteúdo corresponde ao que você tem na [!DNL Commerce] catálogo.
1. Se o conteúdo não corresponder, faça uma pequena alteração no produto no catálogo, como adicionar um espaço ou um ponto.
1. Aguarde uma ressincronização ou [acionar uma ressincronização manual](#resync).

### A sincronização não está em execução

Se a sincronização não estiver sendo executada de acordo com um agendamento ou se nada estiver sincronizado, consulte o [KnowledgeBase](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html).

### Falha na sincronização

Se a sincronização do catálogo tiver um status de **Failed**, envie um [tíquete de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Interface de linha de comando {#resynccmdline}

A variável `saas:resync` faz parte do `magento/saas-export` pacote. Você pode instalar esse pacote usando um dos [!DNL Commerce Services] produtos, como [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) ou [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> Ao executar uma sincronização de dados pela primeira vez, é importante executar o `productattributes` feed primeiro, seguido por `productoverrides`, antes de executar o `products` feed.

Opções de comando:

```bash
bin/magento saas:resync --feed <feed name> [no-reindex]
```

A tabela a seguir descreve as `saas:resync` parâmetros e descrições.

| Parâmetro | Descrição | Obrigatório? |
|---| ---| ---|
| `feed` | Especifica qual entidade deve ser ressincronizada, como `products` | Sim |
| `no-reindex` | Reenvia os dados existentes do catálogo para [!DNL Commerce Services] sem reindexação. Quando esse parâmetro não é especificado, o comando executa uma reindexação completa antes de sincronizar os dados. | Não |

O nome do feed pode ser um dos seguintes:

- `products`— Produtos em seu catálogo
- `categories`— Categorias no catálogo
- `variants`— Variações de um produto configurável, como cor e tamanho
- `productattributes`— Atributos do produto, como `activity`, `gender`, `tops`, `bottoms`e assim por diante
- `productoverrides`— regras de visibilidade de catálogos e preços específicos do cliente, como aquelas baseadas em permissões de categoria

Quando você aciona uma ressincronização de dados na linha de comando, pode levar até uma hora para os dados serem atualizados.

Se você estiver usando [Indexação de preços SaaS](../price-index/index.md) e precisar sincronizar novamente, execute o seguinte comando:

```bash
bin/magento saas:resync --feed=scopesCustomerGroup
bin/magento saas:resync --feed=scopesWebsite
bin/magento saas:resync --feed=prices
```

### Exemplos

O exemplo a seguir reindexa os dados do produto do [!DNL Commerce] catálogo e ressincroniza com os Commerce services:

```bash
bin/magento saas:resync --feed products
```

Se não quiser executar uma reindexação completa dos produtos, sincronize os dados do produto que já foram gerados:

```bash
bin/magento saas:resync --feed products --no-reindex
```
