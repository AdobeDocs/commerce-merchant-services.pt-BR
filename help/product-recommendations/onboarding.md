---
title: Integração
description: Saiba mais sobre os requisitos e as plataformas compatíveis na [!DNL Product Recommendations].
source-git-commit: 4ad607c8595b25d01b5f5020b787fc1d35d4df25
workflow-type: tm+mt
source-wordcount: '222'
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

- Adobe Commerce 2.3.x, 2.4.x
- PHP 7.3 / 7.4
- Composer

### Plataformas compatíveis

- Adobe Commerce no local (EE) : 2.4.x
- Adobe Commerce on Cloud (ECE) : 2.4.x

### Suporte ao Page Builder

[!DNL Product Recommendations] pode ser adicionado a uma página como um tipo de conteúdo do Page Builder. Para adicionar suporte do Page Builder ao Product Recommendations, consulte [Instalar e configurar](install-configure.md).

### Suporte a B2B {#b2bsupport}

As lojas B2B geralmente exigem uma lógica complexa que dita a visibilidade e o preço do produto para cada comprador ou grupo de clientes. [!DNL Product Recommendations] now [suporte](release-notes.md) essa funcionalidade ao atender [permissões de categoria](https://docs.magento.com/user-guide/catalog/category-permissions.html), [catálogos compartilhados](https://docs.magento.com/user-guide/catalog/catalog-shared.html)e [preços específicos do grupo de clientes](https://docs.magento.com/user-guide/catalog/pricing-advanced.html). Por exemplo, se você ocultou determinadas categorias do segmento de clientes de varejo, um comprador nesse segmento não receberia recomendações para produtos nessas categorias. Além disso, ao definir um catálogo compartilhado para grupos de clientes e empresas específicos, esses compradores verão recomendações somente para produtos que podem acessar. Todos os produtos recomendados refletem o preço correto específico do grupo de clientes com base no grupo de clientes de cada comprador.
