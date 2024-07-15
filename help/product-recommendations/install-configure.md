---
title: Instalar e configurar
description: Saiba como instalar, atualizar e desinstalar o  [!DNL Product Recommendations].
exl-id: fa599f72-1064-41da-ac54-2b3a3c16a1fe
role: Admin, Developer
source-git-commit: 96a5791c5716f612f473540f27bd3f99b1bfe7c8
workflow-type: tm+mt
source-wordcount: '486'
ht-degree: 0%

---

# Instalar e configurar

A implantação do [!DNL Product Recommendations] na vitrine e no Administrador requer a instalação do módulo e a configuração do [Commerce Services Connector](../landing/saas.md). À medida que as atualizações forem lançadas, você poderá atualizar facilmente sua instalação com a versão mais recente.

- [Instalar](#install)
- [Configurar](#configure)
- [Atualizar](#update)
- [Desinstalar](#uninstall)

## Instalar [!DNL Product Recommendations] {#install}

Como o módulo [!DNL Product Recommendations] é um metapackage independente, as atualizações são lançadas com mais frequência do que o Adobe Commerce. Para verificar se você está atualizado com os recursos e correções de erros mais recentes, consulte as [notas de versão](release-notes.md).

Instalar o módulo `magento/product-recommendations` com o Composer:

```bash
composer require magento/product-recommendations
```

### Adicionar suporte ao Page Builder {#pbsupport}

O [!DNL Product Recommendations] for Page Builder é um módulo opcional e é instalado separadamente. Para usar o [!DNL Product Recommendations] com o Page Builder, instale o módulo executando o seguinte comando:

```bash
composer require magento/module-page-builder-product-recommendations
```

Ao habilitar [!DNL Product Recommendations] no Page Builder, você pode adicionar uma [unidade de recomendação](https://experienceleague.adobe.com/docs/commerce-admin/page-builder/add-content/recommendations.html) existente e ativa a qualquer conteúdo criado no Page Builder, como páginas, blocos e blocos dinâmicos.

Consulte [Usar [!DNL Product Recommendations] com conteúdo do Page Builder](page-builder.md) para obter mais instruções.

### Adicionar tipo de recomendação de similaridade visual {#vissimsupport}

O tipo de recomendação _Semelhança visual_ permite implantar uma unidade de recomendação na página de detalhes do produto que exibe produtos que são [visualmente semelhantes](type.md#visualsim) ao produto que está sendo visualizado. Esse tipo de recomendação é mais útil quando imagens e aspectos visuais dos produtos são partes importantes da experiência de compra. Instale o tipo de recomendação _Similaridade visual_ executando o seguinte comando:

```bash
composer require magento/module-visual-product-recommendations
```

## Configurar [!DNL Product Recommendations] {#configure}

Após instalar o módulo `magento/product-recommendations`, você deve configurar o [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-admin/config/services/saas.html) especificando as Chaves de API e selecionando um Espaço de Dados SaaS.

Para garantir que a exportação de catálogo esteja sendo executada corretamente, confirme se os trabalhos [cron](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/configure-cron-jobs.html) e os [indexadores](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html) estão em execução e se o indexador `Product Feed` está definido como `Update by Schedule`.

Quando você vincula com êxito aos Serviços da Commerce por meio de chaves de API e especifica o Espaço de dados SaaS, a sincronização do catálogo é iniciada. Em seguida, você pode [verificar](verify.md) se os dados comportamentais estão sendo enviados para a loja.

## Atualize sua instalação do [!DNL Product Recommendations] {#update}

Como todo o Adobe Commerce, o [!DNL Product Recommendations] usa o Composer para instalação e atualizações. Para atualizar o módulo `magento/product-recommendations`, execute o seguinte:

```bash
composer update magento/product-recommendations --with-dependencies
```

Para atualizar para uma versão principal, como 3.0 para 4.0, você deve editar o arquivo raiz `composer.json` do seu projeto. (Consulte as [notas de versão](release-notes.md) para obter informações sobre a versão mais recente.) Por exemplo, vamos abrir o arquivo `composer.json` principal e pesquisar pelo módulo `magento/product-recommendations`:

```json
"require": {
    ...
    "magento/product-recommendations": "^3.0",
    ...
}
```

Vamos aumentar a versão principal de `3.0` para `4.0`:

```json
"require": {
    ...
    "magento/product-recommendations": "^4.0",
    ...
}
```

Salve o arquivo `composer.json` e execute:

```bash
composer update magento/product-recommendations --with-dependencies
```

Ou se você instalou os módulos `magento/module-visual-product-recommendations` e `magento/module-page-builder-product-recommendations`:

```bash
composer update --with-dependencies magento/product-recommendations magento/module-visual-product-recommendations magento/module-page-builder-product-recommendations
```

>[!NOTE]
>
> Nas versões 3.x.x do Product Recommendations, você só precisava de uma única chave de API. Nas versões 4.x.x e posteriores, você deve fornecer as chaves de API pública e privada de produção, bem como as chaves de API públicas e privadas de sandbox. Se você não fornecer ambos os pares de chaves de API, não poderá acessar o recurso Recommendations do produto no Administrador. A coleta de dados, no entanto, continuará em sua loja e as recomendações existentes continuarão a ser mostradas aos seus compradores.

## Firewalls

Para permitir que o Recommendations do Produto passe por um firewall, adicione `commerce.adobe.io` à lista de permissões.

## Desinstalar [!DNL Product Recommendations] {#uninstall}

Se necessário, você pode [desinstalar](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html) o módulo product-recommendations.
