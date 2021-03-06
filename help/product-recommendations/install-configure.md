---
title: Instalar e configurar
description: Saiba como instalar, atualizar e desinstalar [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
source-git-commit: cfeb8b4f8e2dc1e9d2d4c0be7a7bc522488418bc
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Instalar e configurar

Implantação [!DNL Product Recommendations] para sua loja e o Admin requer que você instale o módulo e configure a variável [Conector do Commerce Services](../landing/saas.md). À medida que as atualizações são lançadas, você pode atualizar facilmente sua instalação com a versão mais recente.

- [Instalar](#install)
- [Configurar](#configure)
- [Atualizar](#update)
- [Desinstalar](#uninstall)

## Instalar [!DNL Product Recommendations] {#install}

Porque a variável [!DNL Product Recommendations] é um metapackage independente, as atualizações são lançadas com mais frequência do que a Adobe Commerce. Para verificar se você está atualizado com as correções e os recursos de erros mais recentes, consulte o [notas de versão](release-notes.md).

Instale o `magento/product-recommendations` módulo com Composer:

```bash
composer require magento/product-recommendations
```

### Adicionar suporte ao Page Builder {#pbsupport}

[!DNL Product Recommendations] para o Page Builder são um módulo opcional e é instalado separadamente. Para usar [!DNL Product Recommendations] com o Page Builder, instale o módulo executando o seguinte comando:

```bash
composer require magento/module-page-builder-product-recommendations
```

Ao ativar [!DNL Product Recommendations] no Page Builder, é possível adicionar um [unidade de recomendação](https://docs.magento.com/user-guide/cms/page-builder-add-recommendations.html) para qualquer conteúdo criado no Page Builder, como páginas, blocos e blocos dinâmicos.

### Adicionar tipo de recomendação de semelhança visual {#vissimsupport}

O _Similaridade visual_ o tipo de recomendação permite implantar uma unidade de recomendação na página de detalhes do produto, que exibe os produtos que são [visualmente semelhante](type.md#visualsim) ao produto que está sendo visualizado. Esse tipo de recomendação é mais útil quando imagens e aspectos visuais dos produtos são partes importantes da experiência de compras. Instale o _Similaridade visual_ tipo de recomendação executando o seguinte comando:

```bash
composer require magento/module-visual-product-recommendations
```

## Configurar [!DNL Product Recommendations] {#configure}

Depois de instalar o `magento/product-recommendations` você deve configurar o [Conector do Commerce Services](https://docs.magento.com/user-guide/configuration/services/saas.html) especificando chaves de API e selecionando um espaço de dados SaaS.

Para garantir que a exportação do catálogo esteja sendo executada corretamente, confirme se a variável [cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) os postos de trabalho e [indexadores](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-index.html) estão em execução e o `Product Feed` indexer está definido como `Update by Schedule`.

Quando você vincula com êxito o Commerce Services por meio de chaves de API e especifica o SaaS Data Space, a sincronização do catálogo é iniciada. Você pode [verify](verify.md) esses dados comportamentais estão sendo enviados para a sua loja.

## Atualize seu [!DNL Product Recommendations] instalação {#update}

Como toda a Adobe Commerce, [!DNL Product Recommendations] O usa o Composer para instalação e atualizações. Para atualizar o `magento/product-recommendations` execute o seguinte módulo:

```bash
composer update magento/product-recommendations --with-dependencies
```

Para atualizar para uma versão principal, como de 3.0 para 4.0, você deve editar a raiz `composer.json` para o seu projeto. (Consulte o [notas de versão](release-notes.md) para obter informações sobre a versão mais recente.) Por exemplo, vamos abrir o `composer.json` e pesquise a `magento/product-recommendations` módulo:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

Vamos ampliar a versão principal de `3.0` para `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

Salve as `composer.json` e executar:

```bash
composer update magento/product-recommendations --with-dependencies
```

>[!NOTE]
>
> Nas versões 3.x.x do Product Recommendations, você só precisava de uma única chave de API. Nas versões 4.x.x e superior, você deve fornecer chaves de API públicas e privadas de produção, bem como chaves de API públicas e privadas de sandbox. Se você não fornecer ambos os pares de chaves de API, não poderá acessar o recurso Recommendations do produto no Administrador. A coleta de dados, no entanto, continuará em sua loja e as recomendações existentes continuarão a ser exibidas aos seus compradores.

## Desinstalar [!DNL Product Recommendations] {#uninstall}

Se necessário, é possível [desinstalar](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-uninstall-mods.html) o módulo do produto-recommendations.
