---
title: Integração
description: Conheça os requisitos e as plataformas compatíveis na [!DNL Product Recommendations].
exl-id: ad47ac39-8f6f-4765-84ad-9e3d104385db
source-git-commit: 209bdf9c69ff81481d6df7cb8e8832deef13c9f4
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Integração

O processo de integração do [!DNL Product Recommendations] requer acesso à linha de comando do servidor e consiste nas seguintes etapas. Se você não estiver familiarizado com o trabalho a partir da linha de comando, peça ajuda a um desenvolvedor ou integrador de sistemas.

- [Fluxo de trabalho de implementação](implementation-workflow.md)
- [Instalar e configurar](install-configure.md)
- [Configurações](settings.md)
- [Verificar](verify.md)
- [Ambiente de preparo](staging-environment.md)

## Requisitos

- Adobe Commerce 2.4.4+
- PHP 8.1, 8.2
- Compositor 2

### Plataformas compatíveis

- Adobe Commerce no local (EE): 2.4.4+
- Adobe Commerce na nuvem (ECE): 2.4.4+

### Suporte ao Page Builder

[!DNL Product Recommendations] podem ser adicionados a uma página como um tipo de conteúdo do Page Builder. Para adicionar suporte do Page Builder ao Product Recommendations, consulte [Instalar e configurar](install-configure.md).

Consulte [[!DNL Page Builder] Integração](page-builder.md) para obter instruções sobre como adicionar [!DNL Product Recommendations] em [!DNL Page Builder] conteúdo.

### Indexação de preços SaaS

Recomendações de produtos que os clientes podem usar [Indexação de preços SaaS](../price-index/index.md), que fornece atualizações de alterações de preço e tempo de sincronização mais rápidos.

### Suporte B2B {#b2bsupport}

As vitrines B2B geralmente exigem uma lógica complexa que determina a visibilidade e os preços do produto para cada comprador ou grupo de clientes. [!DNL Product Recommendations] now [suporte](release-notes.md) essa funcionalidade respeitando [permissões de categoria](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/category-permissions.html), [catálogos compartilhados](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html), e [preços específicos do grupo de clientes](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html). Por exemplo, se você tiver ocultado determinadas categorias do segmento de cliente de varejo, um comprador nesse segmento não receberia recomendações para produtos nessas categorias. Além disso, ao definir um catálogo compartilhado para grupos de clientes e empresas específicos, esses compradores veem recomendações somente para produtos que podem acessar. Todos os produtos recomendados refletem o preço correto específico do grupo de clientes com base no grupo de clientes de cada comprador.

>[!NOTE]
>
>Os comerciantes podem personalizar e estender widgets ou elementos de vitrine usando o [Serviço de catálogo](../catalog-service/overview.md) API da loja, mas qualquer personalização está fora do escopo para a equipe de suporte do Adobe.
