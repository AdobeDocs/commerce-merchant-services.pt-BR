---
title: Sincronização do catálogo
description: Saiba como exportar dados do produto do [!DNL Commerce] para [!DNL Commerce Services] de forma contínua, a fim de manter os serviços atualizados.
exl-id: 19d29731-097c-4f5f-b8c0-12f9c91848ac
source-git-commit: c68bf177f79c37cc57b4cc5979b18e1fd4a7e17d
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 0%

---

# Sincronização do catálogo

O Adobe Commerce e o Magento Open Source usam indexadores para compilar dados de catálogo em tabelas. O processo é acionado automaticamente por [events](https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/index-management.html#events-that-trigger-full-reindexing) como uma alteração no preço do produto ou no nível de inventário.

O processo de sincronização de catálogo é executado por hora para permitir [!DNL Commerce] para usar dados de catálogo. A sincronização de catálogo exporta dados do produto do [!DNL Commerce] para [!DNL Commerce] serviços de forma contínua para manter os serviços atualizados. Por exemplo, [[!DNL Product Recommendations]](/help/product-recommendations/overview.md) O precisa de informações atuais do catálogo para retornar com precisão as recomendações com nomes, preços e disponibilidade corretos. Você pode usar o _Sincronização do catálogo_ painel para observar e gerenciar o processo de sincronização ou o [interface de linha de comando](#resynccmdline) para acionar a sincronização do catálogo e reindexar os dados do produto para consumo ao [!DNL Commerce] serviços.

>[!NOTE]
>
> Para usar o _Sincronização do catálogo_ no painel ou na interface da linha de comando, é necessário ter um [Chave da API e um espaço de dados SaaS configurado](saas.md).

## Acesso ao painel Sincronização de catálogo

>[!NOTE]
>
> O _Sincronização do catálogo_ o painel só estará disponível quando a função _Recommendations do produto_ Os módulos são instalados e refletem as projeções de dados relacionadas somente a esse recurso. Suporte para outros serviços comerciais, como _Live Search_ e _Serviço de catálogo_ estão planejadas para o futuro.

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
| Última exportação | Data em que o produto foi exportado com êxito do catálogo |
| Última modificação | Data em que o produto foi modificado pela última vez no catálogo |
| SKU | Exibe a unidade de manutenção de estoque do produto |
| Preço | Preço do produto |
| Visibilidade | Uma configuração de visibilidade do produto, conforme definido na variável [!DNL Commerce] catálogo |

## Resolver problemas de sincronização de catálogos {#resolvesync}

Quando você aciona uma ressincronização de dados, pode levar até uma hora para que os dados sejam atualizados e refletidos em componentes da interface do usuário, como unidades de recomendação. No entanto, se depois de esperar uma hora, você ainda observar discrepâncias entre o catálogo e o que aparece na loja ou se a sincronização do catálogo falhou, consulte o seguinte:

### Discrepância de dados

1. Exiba a exibição detalhada do produto em questão nos resultados da pesquisa.
1. Copie a saída JSON e verifique se o conteúdo corresponde ao que você tem no [!DNL Commerce] catálogo.
1. Se o conteúdo não corresponder, faça uma pequena alteração no produto no catálogo, como adicionar um espaço ou um ponto.
1. Aguarde uma ressincronização ou [acionar uma ressincronização manual](#resync).

### Sincronização não executada

Se a sincronização não estiver sendo executada em um agendamento ou nada estiver sincronizado, consulte o [KnowledgeBase](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/troubleshoot-product-recommendations-module-in-magento-commerce.html).

### Falha na sincronização

Se a sincronização de catálogo tiver um status de **Falha**, submete uma [tíquete de suporte](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Interface de linha de comando {#resynccmdline}

O `saas:resync` faz parte do comando `magento/saas-export` pacote. Você pode instalar este pacote usando um dos [!DNL Commerce Services] produtos, como [[!DNL Product Recommendations]](/help/product-recommendations/install-configure.md) ou [[!DNL Live Search]](/help/live-search/install.md).

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

### Exemplos

O exemplo a seguir reindexa os dados do produto da variável [!DNL Commerce] catálogo e ressincroniza aos serviços do Commerce:

```bash
bin/magento saas:resync --feed products
```

Se você não quiser executar um reíndice completo dos produtos, poderá sincronizar os dados do produto que já foram gerados:

```bash
bin/magento saas:resync --feed products --no-reindex
```
