---
title: Integração
description: Saiba mais sobre os requisitos e as plataformas compatíveis na [!DNL Product Recommendations].
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
source-git-commit: e74bc4aeaa154e751f8d986e0426dd19d55d335e
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Integração

O processo de integração para [!DNL Product Recommendations] O requer acesso à linha de comando do servidor e consiste nas etapas a seguir. Se você não estiver familiarizado com o trabalho a partir da linha de comando, peça ajuda a um desenvolvedor ou integrador de sistemas.

- [Fluxo de trabalho de implementação](implementation-workflow.md)
- [Instalar e configurar](install-configure.md)
- [Configurações](settings.md)
- [Verificar](verify.md)
- [Ambiente de preparo](staging-environment.md)

## Requisitos

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- Composer 2

### Plataformas compatíveis

- Adobe Commerce no local (EE) : 2.4.4+
- Adobe Commerce on Cloud (ECE) : 2.4.4+

### Suporte ao Page Builder

[!DNL Product Recommendations] pode ser adicionado a uma página como um tipo de conteúdo do Page Builder. Para adicionar suporte do Page Builder ao Product Recommendations, consulte [Instalar e configurar](install-configure.md).

Consulte [[!DNL Page Builder] Integração](page-builder.md) para obter instruções sobre como adicionar [!DNL Product Recommendations] em [!DNL Page Builder] conteúdo.

### Indexação de preços de SaaS

Os clientes do Recommendations de produto podem usar [Indexação de preços de SaaS](../price-index/index.md), que oferece atualizações de preço e tempo de sincronização mais rápidos.

### Suporte a B2B {#b2bsupport}

As lojas B2B geralmente exigem uma lógica complexa que dita a visibilidade e o preço do produto para cada comprador ou grupo de clientes. [!DNL Product Recommendations] now [suporte](release-notes.md) essa funcionalidade ao atender [permissões de categoria](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html), [catálogos compartilhados](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)e [preços específicos do grupo de clientes](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html). Por exemplo, se você ocultou determinadas categorias do segmento de clientes de varejo, um comprador nesse segmento não receberia recomendações para produtos nessas categorias. Além disso, ao definir um catálogo compartilhado para grupos de clientes e empresas específicos, esses compradores verão recomendações somente para produtos que podem acessar. Todos os produtos recomendados refletem o preço correto específico do grupo de clientes com base no grupo de clientes de cada comprador.
