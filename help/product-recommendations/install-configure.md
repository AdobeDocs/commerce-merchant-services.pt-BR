---
title: Instalar e configurar
description: Saiba como instalar, atualizar e desinstalar [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
role: Admin, Developer
source-git-commit: 9ae4aff1851e9ce9920c4fbf11d2616d6f0f6307
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# Instalar e configurar

Implantação [!DNL Product Recommendations] para sua loja e o Administrador exige que você instale o módulo e configure o [Conector dos Commerce Services](../landing/saas.md). À medida que as atualizações forem lançadas, você poderá atualizar facilmente sua instalação com a versão mais recente.

- [Instalar](#install)
- [Configurar](#configure)
- [Atualizar](#update)
- [Desinstalar](#uninstall)

## Instalar [!DNL Product Recommendations] {#install}

Como a variável [!DNL Product Recommendations] O módulo do é um metapackage independente, as atualizações são lançadas com mais frequência do que o Adobe Commerce. Para verificar se você está atualizado com os recursos e correções de erros mais recentes, consulte o [notas de versão](release-notes.md).

Instale o `magento/product-recommendations` módulo com o Composer:

```bash
composer require magento/product-recommendations
```

### Adicionar suporte ao Page Builder {#pbsupport}

[!DNL Product Recommendations] O para Page Builder é um módulo opcional e é instalado separadamente. Para usar [!DNL Product Recommendations] com o Page Builder, instale o módulo executando o seguinte comando:

```bash
composer require magento/module-page-builder-product-recommendations
```

Ao ativar [!DNL Product Recommendations] no Page Builder, é possível adicionar um existente, ativo [unidade de recomendação](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) a qualquer conteúdo criado no Page Builder, como páginas, blocos e blocos dinâmicos.

Consulte [Usar [!DNL Product Recommendations] com conteúdo do Page Builder](page-builder.md) para obter mais instruções.

### Adicionar tipo de recomendação de similaridade visual {#vissimsupport}

A variável _Semelhança visual_ o tipo de recomendação permite implantar uma unidade de recomendação na página de detalhes do produto que exibe os produtos que são [visualmente semelhante](type.md#visualsim) ao produto que está sendo visualizado. Esse tipo de recomendação é mais útil quando imagens e aspectos visuais dos produtos são partes importantes da experiência de compra. Instale o _Semelhança visual_ tipo de recomendação executando o seguinte comando:

```bash
composer require magento/module-visual-product-recommendations
```

## Configurar [!DNL Product Recommendations] {#configure}

Depois de instalar o `magento/product-recommendations` , você deve configurar o [Conector dos Commerce Services](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) especificando chaves de API e selecionando um espaço de dados SaaS.

Para garantir que a exportação de catálogo esteja sendo executada corretamente, confirme se [cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) tarefas e o [indexadores](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) estão em execução e a variável `Product Feed` indexador está definido como `Update by Schedule`.

Quando você vincula com êxito ao Commerce Services por meio de chaves de API e especifica o Espaço de dados SaaS, a sincronização do catálogo é iniciada. Você pode então [verificar](verify.md) que os dados comportamentais estão sendo enviados para sua loja.

## Atualize seu [!DNL Product Recommendations] instalação {#update}

Como todo o Adobe Commerce, [!DNL Product Recommendations] O usa o Composer para instalação e atualizações. Para atualizar o `magento/product-recommendations` , execute o seguinte:

```bash
composer update magento/product-recommendations --with-dependencies
```

Para atualizar para uma versão principal, como de 3.0 para 4.0, você deve editar a raiz `composer.json` para o seu projeto. (Consulte a [notas de versão](release-notes.md) para obter informações sobre a versão mais recente.) Por exemplo, vamos abrir a página principal `composer.json` arquivo e pesquisar pelo `magento/product-recommendations` módulo:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

Vamos recuperar a versão principal do `3.0` para `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

Salve o `composer.json` arquivar e executar:

```bash
composer update magento/product-recommendations --with-dependencies
```

Ou se tiver instalado o `magento/module-visual-product-recommendations` e `magento/module-page-builder-product-recommendations` módulos:

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> Nas versões 3.x.x do Product Recommendations, você só precisava de uma única chave de API. Nas versões 4.x.x e posteriores, você deve fornecer as chaves de API pública e privada de produção, bem como as chaves de API públicas e privadas de sandbox. Se você não fornecer ambos os pares de chaves de API, não poderá acessar o recurso Recommendations do produto no Administrador. A coleta de dados, no entanto, continuará em sua loja e as recomendações existentes continuarão a ser mostradas aos seus compradores.

## Desinstalar [!DNL Product Recommendations] {#uninstall}

Se necessário, você pode [desinstalar](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) o módulo de recomendações de produto.
