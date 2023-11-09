---
title: Sincronização de catálogo
description: Saiba como exportar dados do produto do [!DNL Commerce] servidor para [!DNL Commerce Services].
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
feature: Catalog Management, Data Import/Export, Catalog Service
source-git-commit: 92129633adadd3ed699ae6427c01622dcb6ae3b4
workflow-type: tm+mt
source-wordcount: '1167'
ht-degree: 0%

---


# Sincronização de catálogo

O Adobe Commerce usa indexadores para compilar dados de catálogo em tabelas. O processo é automaticamente acionado por [events](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) como uma alteração no preço de um produto ou no nível do inventário.

O serviço de Sincronização do catálogo move os dados do produto de um [!DNL Adobe Commerce] para a instância [!DNL Commerce Services] plataforma para manter os dados atualizados. Por exemplo, [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) exige informações atuais do catálogo para retornar com precisão as recomendações com nomes, preços e disponibilidade corretos. Use o _Sincronização de catálogo_ painel de controle para observar e gerenciar o processo de sincronização ou a [interface de linha de comando](#resynccmdline) para acionar uma sincronização de catálogo e reindexar dados do produto para consumo por [!DNL Commerce Services].

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
- Exibir o número total de produtos sincronizados
- Pesquisar produtos sincronizados para exibir seu estado atual
- Pesquise o catálogo da loja por nome, SKU etc.
- Exibir detalhes do produto sincronizado no JSON para ajudar a diagnosticar uma discrepância de sincronização
- Reiniciar o processo de sincronização

### Última sincronização

Relata um status de sincronização de:

- **Sucesso** - Exibe a data e a hora em que a sincronização foi bem-sucedida e o número de produtos atualizados
- **Failed** - Exibe a data e a hora em que a sincronização foi tentada
- **Em andamento** - Exibe a data e a hora da última sincronização bem-sucedida

O processo de sincronização de catálogo é executado automaticamente a cada hora. Se você não estiver vendo os produtos esperados na loja ou se os produtos não refletirem as alterações recentes feitas, é possível resolver [problemas de sincronização do catálogo](#resolvesync).

### Produtos sincronizados

Exibe o número total de produtos sincronizados do [!DNL Commerce] catálogo. Após a sincronização inicial, somente os produtos alterados devem ser sincronizados.

## Ressincronizar {#resync}

Se precisar iniciar uma ressincronização do catálogo antes que a sincronização agendada por hora ocorra, você poderá forçar uma ressincronização.

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
| Tipo | Identifica o tipo do produto, como simples, configurável ou baixável |
| Última exportação | Data em que o produto foi exportado com êxito do catálogo pela última vez |
| Última modificação | Data da última modificação do produto no catálogo |
| SKU | Exibe a unidade de manutenção de estoque do produto |
| Preço | Preço do produto |
| Visibilidade | Uma configuração de visibilidade do produto, conforme definido na [!DNL Commerce] catálogo |

## Resolver problemas de sincronização do catálogo {#resolvesync}

Quando você aciona uma ressincronização de dados, pode levar até uma hora para que os dados sejam atualizados e refletidos em componentes da interface do usuário, como unidades de recomendação. Se você ainda vir discrepâncias entre o catálogo e os dados na loja, ou se a sincronização do catálogo falhar, consulte o seguinte:

### Discrepância de dados

1. Exiba a exibição detalhada do produto em questão nos resultados da pesquisa.
1. Copie a saída JSON e verifique se o conteúdo corresponde ao que você tem na [!DNL Commerce] catálogo.
1. Se o conteúdo não corresponder, faça uma pequena alteração no produto no catálogo, como adicionar um espaço ou um ponto.
1. Aguarde uma ressincronização ou [acionar uma ressincronização manual](#resync).

### A sincronização não está em execução

Se a sincronização não estiver sendo executada de acordo com um agendamento ou se nada estiver sincronizado, consulte esta [KnowledgeBase](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html) artigo.

### Falha na sincronização

Se a sincronização do catálogo tiver um status de **Failed**, envie um [tíquete de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Interface de linha de comando {#resynccmdline}

A variável `saas:resync` faz parte do `magento/saas-export` pacote e está disponível imediatamente com um dos [!DNL Commerce Services] produtos, como [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) ou [[!DNL Live Search]](/help/live-search/install.md).

>[!NOTE]
>
> Ao executar uma sincronização de dados pela primeira vez, execute o `productattributes` feed primeiro, seguido por `productoverrides`, antes de executar o `products` feed.

Opções de comando:

```bash
bin/magento saas:resync --feed <feed name> [no-reindex|cleanup-feed]
```

A tabela a seguir descreve as `saas:resync` parâmetros e descrições.

| Parâmetro | Descrição | Obrigatório? |
|---| ---| ---|
| `feed` | Especifica qual entidade deve ser ressincronizada, como `products` | Sim |
| `no-reindex` | Reenvia os dados existentes do catálogo para [!DNL Commerce Services] sem reindexação. Quando esse parâmetro não é especificado, o comando executa uma reindexação completa antes de sincronizar os dados. | Não |
| `cleanup-feed` | Limpe a tabela indexadora de feed antes de uma sincronização. | Não |

O nome do feed pode ser um dos seguintes:

- `products`— Produtos em seu catálogo
- `productattributes`— Atributos do produto, como `activity`, `gender`, `tops`, `bottoms`e assim por diante
- `variants`— Variações de um produto configurável, como cor e tamanho
- `prices` — Preços dos produtos
- `scopesCustomerGroup` — Grupos de clientes
- `scopesWebsite` — Sites com visualizações da loja
- `categories`— Categorias no catálogo
- `categoryPermissions` - Permissões para cada uma das categorias
- `productoverrides`— regras de visibilidade de catálogos e preços específicos do cliente, como aquelas baseadas em permissões de categoria

Dependendo de qual [Commerce Services](../landing/saas.md) instalados, você pode ter um conjunto diferente de feeds disponíveis para `saas:resync` comando.

Não é recomendável executar o `saas:resync` de forma regular. Talvez seja necessário executar o comando manualmente em dois cenários:

- A sincronização inicial
- A variável [ID do espaço de dados SaaS](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) foi alterado

### Sincronização inicial

Quando você aciona um `saas:resync` na linha de comando, dependendo do tamanho do catálogo, pode levar de alguns minutos a algumas horas para que os dados sejam atualizados.

Para a sincronização inicial, é recomendável executar comandos na seguinte ordem:

```bash
bin/magento saas:resync --feed productattributes
bin/magento saas:resync --feed products
bin/magento saas:resync --feed scopesCustomerGroup
bin/magento saas:resync --feed scopesWebsite
bin/magento saas:resync --feed prices
bin/magento saas:resync --feed productoverrides
bin/magento saas:resync --feed variants
bin/magento saas:resync --feed categories
bin/magento saas:resync --feed categoryPermissions 
```

### Solução de problemas

Se você não vir os dados esperados em [!DNL Commerce Service], verifique se ocorreu um problema durante a sincronização com o [!DNL Adobe Commerce] para a instância [!DNL Commerce Service] plataforma.

Há dois arquivos de log no `var/log/` diretório:

- `commerce-data-export-errors.log` - se ocorreu um erro durante _coletando_ fase
- `saas-export-errors.log` - se ocorreu um erro durante _transmissão_ fase

#### Verificar a carga do feed

Pode ser útil ver a carga do feed que foi enviada para o [!DNL Commerce Service]. Isso pode ser feito passando a variável de ambiente `EXPORTER_EXTENDED_LOG=1`. A variável `no-reindex` sinalizador significa que somente os dados coletados no momento são enviados.

```bash
EXPORTER_EXTENDED_LOG=1 bin/magento saas:resync --feed=products --no-reindex
```

A carga está disponível em `var/log/saas-export.log`.

#### Preservar conteúdo na tabela de índice do feed

A partir de `magento/module-data-exporter:103.0.0` alguns feeds: feed de produto, feeds de preço, mantêm somente os dados mínimos necessários na tabela de índice.

A preservação de dados de carga na tabela de índice não é recomendada na produção, mas pode ser útil em uma instância do desenvolvedor. Isso é feito passando o `PERSIST_EXPORTED_FEED=1` variável de ambiente:

```bash
PERSIST_EXPORTED_FEED=1 bin/magento saas:resync --feed=products
```

#### Criação de perfil

Se o processo de reindexação de um feed específico demorar um tempo excessivo, execute o profiler para coletar dados adicionais que podem ser úteis para a Equipe de suporte. Para fazer isso, passe o `EXPORTER_PROFILER=1`variável de ambiente:

```bash
EXPORTER_PROFILER=1 bin/magento indexer:reindex catalog_data_exporter_products
```

Os dados do profiler são armazenados no `var/log/commerce-data-export.log` com o formato:

`<Provider class name>, <# of processed entities>, <execution time im ms>, <memory consumption in Mb>`

#### Enviar uma solicitação de suporte

Se você vir erros não relacionados à configuração ou extensões de terceiros, envie um [tíquete de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) com o máximo de informação possível.
