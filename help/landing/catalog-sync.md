---
title: Sincronização do catálogo
description: '"Saiba como exportar dados de produtos do [!DNL Commerce] para [!DNL Commerce Services] de forma contínua para manter os serviços atualizados."'
source-git-commit: 5910874fbd386456c50c4d87098f72fef908a7ae
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Sincronização do catálogo

O Adobe Commerce e o Magento Open Source usam indexadores para compilar dados de catálogo em tabelas. The process is automatically triggered by [events](https://docs.magento.com/user-guide/system/index-management-events.html) such as a change to a product price or inventory level.

O processo de sincronização de catálogo é executado por hora para permitir [!DNL Commerce Services] para usar dados de catálogo. Catalog sync exports product data from the [!DNL Commerce] server to [!DNL Commerce Services] on an ongoing basis to keep the services up to date. Por exemplo, [!DNL Product Recommendations] O precisa de informações atuais do catálogo para retornar com precisão as recomendações com nomes, preços e disponibilidade corretos. Você pode usar o _Sincronização do catálogo_ painel para observar e gerenciar o processo de sincronização ou o [interface de linha de comando](#resynccmdline) para acionar a sincronização do catálogo e reindexar os dados do produto para consumo ao [!DNL Commerce Services].

>[!NOTE]
>
> Para usar o _Sincronização do catálogo_ no painel ou na interface da linha de comando, é necessário ter um [Chave da API e um espaço de dados SaaS configurado](saas.md).

## Acesso ao painel Sincronização de catálogo

Para acessar o painel Sincronização de catálogo, selecione **Sistema** > _Transferência de dados_ > **Sincronização do catálogo**.

Com o **Sincronização do catálogo** painel é possível:

- Visualizar o status de sincronização (**Em Andamento**, **Sucesso**, **Falha**)
- Exibir o número total de produtos sincronizados, se bem-sucedidos
- Pesquisar produtos sincronizados para visualizar seu estado atual
- Pesquisar catálogo da loja por nome, SKU e assim por diante
- Exibir detalhes sincronizados do produto no JSON para ajudar a diagnosticar uma discrepância de sincronização
- Reiniciar o processo de sincronização

### Última sincronização

Relata um status de sincronização de:

- **Sucesso** - Exibe a data e a hora em que a sincronização foi bem-sucedida e o número de produtos atualizados
- **Falha** - Exibe a data e a hora em que a sincronização foi tentada
- **Em Andamento** - Exibe a data e a hora da última sincronização bem-sucedida

>[!NOTE]
>
> O processo de sincronização de catálogo é executado automaticamente a cada hora. No entanto, se você não estiver vendo produtos em sua vitrine ou se os produtos não refletirem as alterações recentes feitas, será possível resolver [problemas de sincronização de catálogo](#resolvesync).

### Produtos sincronizados

Exibe o número total de produtos sincronizados do [!DNL Commerce] catálogo. Após a sincronização inicial, você deve esperar que apenas os produtos alterados sejam sincronizados.

## Ressincronizar {#resync}

Se você precisar iniciar uma ressincronização do catálogo antes que a sincronização agendada por hora ocorra, é possível forçar uma ressincronização.

>[!NOTE]
>
> Forçar uma ressincronização aciona uma ressincronização de todo o catálogo de produtos, o que pode aumentar a carga dos recursos de hardware.

1. No _Sincronização do catálogo_ painel, selecione **Configurações**.

   O _Configurações de sincronização do catálogo_ será exibida.

1. No _Ressincronizar Dados_ seção , clique em [!UICONTROL Resync].

   [!DNL Commerce] sincroniza seu catálogo durante a próxima janela de sincronização agendada. Dependendo do tamanho do catálogo, essa operação pode demorar muito.

## Produtos de catálogo sincronizado

O **Produtos de catálogo sincronizado** A tabela exibe as seguintes informações.

| Campo | Descrição |
|---|---|
| ID | Identificador exclusivo do produto |
| Nome | Nome da loja do produto |
| Tipo | Identifica o tipo de produto, como simples, configurável, baixável e assim por diante |
| Last Exported | Data em que o produto foi exportado com êxito do catálogo |
| Última modificação | Data em que o produto foi modificado pela última vez no catálogo |
| SKU | Exibe a unidade de manutenção de estoque do produto |
| Preço | Preço do produto |
| Visibilidade | Uma configuração de visibilidade do produto, conforme definido na variável [!DNL Commerce] catálogo |

## Resolver problemas de sincronização de catálogos {#resolvesync}

Quando você aciona uma ressincronização de dados, pode levar até uma hora para que os dados sejam atualizados e refletidos em componentes da interface do usuário, como unidades de recomendação. No entanto, se depois de esperar uma hora, você ainda observar discrepâncias entre o catálogo e o que aparece na loja ou se a sincronização do catálogo falhou, consulte o seguinte:

### Discrepância de dados

1. Display the detailed view of the product in question in the search results.
1. Copy the JSON output and verify that the content matches what you have in the [!DNL Commerce] catalog.
1. Se o conteúdo não corresponder, faça uma pequena alteração no produto no catálogo, como adicionar um espaço ou um ponto.
1. Aguarde uma ressincronização ou [acionar uma ressincronização manual](#resync).

### Sincronização não executada

Se a sincronização não estiver sendo executada em um agendamento ou nada estiver sincronizado, consulte o [KnowledgeBase](https://support.magento.com/hc/en-us/articles/360042224851).

### Sync failed

Se a sincronização de catálogo tiver um status de **Falha**, submete uma [tíquete de suporte](https://support.magento.com/hc/en-us/articles/360019088251).

## Interface de linha de comando {#resynccmdline}

O `saas:resync` faz parte do comando `magento/saas-export` pacote. Você pode instalar este pacote usando um dos [!DNL Commerce Services] produtos, como [!DNL Product Recommendations] ou [!DNL Live Search].

>[!NOTE]
>
> Quando você aciona uma ressincronização de dados a partir da linha de comando, pode levar até uma hora para que os dados sejam atualizados.

Opções de comando:

```bash
bin/magento saas:resync --feed <feed name> [no-reindex]
```

A tabela a seguir descreve o `saas:resync` parâmetros e descrições.

| Parâmetro | Descrição | Obrigatório? |
|---| ---| ---|
| `feed` | Especifica a entidade a ser ressincronizada, como `products` | Sim |
| `no-reindex` | Reenvia os dados do catálogo existente para [!DNL Commerce Services] sem reindexação. Quando esse parâmetro não é especificado, o comando executa uma reindexação completa antes da sincronização dos dados. | Não |

O nome do feed pode ser um dos seguintes:

- `products`— Produtos em seu catálogo
- `categories`— Categorias no catálogo
- `variants`— Variações de produto de um produto configurável, como cor e tamanho
- `productattributes`— Atributos de produto como `activity`, `gender`, `tops`, `bottoms`e assim por diante
- `productoverrides`— Regras específicas de preço e visibilidade de catálogo do cliente, como aquelas baseadas em permissões de categoria

### Examples

O exemplo a seguir reindexa os dados do produto da variável [!DNL Commerce] catálogo e ressincroniza aos serviços do Commerce:

```bash
bin/magento saas:resync --feed products
```

Se você não quiser executar um reíndice completo dos produtos, poderá sincronizar os dados do produto que já foram gerados:

```bash
bin/magento saas:resync --feed products --no-reindex
```
