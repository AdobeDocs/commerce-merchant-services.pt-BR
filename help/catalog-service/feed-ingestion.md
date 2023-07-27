---
title: Serviço de assimilação de feed
description: Saiba mais sobre o serviço de assimilação de feed do Adobe Commerce
source-git-commit: b484429a529acfa95f70c5a55b6a5fcdedc887b3
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 0%

---


# Serviço de assimilação de feed

>[!NOTE]
>
>No momento, o Serviço de assimilação de feed está em beta privado. Ele ainda não está disponível para uso geral.

O Serviço de assimilação de feeds diminui o tempo necessário para processar alterações de produtos (atualizações de preços, adição de novos atributos), ignorando a instância do Adobe Commerce e movendo os dados do catálogo de um ERP (Enterprise Resource Planning, planejamento de recursos corporativos) de terceiros diretamente para os serviços da Adobe Commerce.

Este serviço é para clientes que armazenam e gerenciam seu catálogo de produtos em um sistema externo ao aplicativo principal do Adobe Commerce.

Clientes com catálogos grandes e complexos ou catálogos que recebem atualizações frequentes estão preocupados com o fato de que os novos dados podem levar mais tempo do que o desejado para serem exibidos no armazenamento dinâmico. Como o Serviço de catálogo sabe quais dados ele precisa para processar essas atualizações, não há necessidade de enviar os dados por meio do produto principal do Commerce, apenas para ser encaminhado ao Serviço de catálogo. A remoção desta etapa intermediária é onde os ganhos de eficiência são encontrados.

## Fluxos de assimilação de feed

Dependendo da configuração do Adobe Commerce, o armazenamento de dados e os fluxos de dados podem tomar caminhos diferentes.

* Em uma instância padrão do Adobe Commerce, o catálogo de produtos é armazenado no banco de dados principal.
* Ao usar os Serviços da Adobe Commerce, os dados do catálogo são copiados do banco de dados principal para o serviço e são processados e entregues a partir desse banco de dados.
* Ao armazenar dados de catálogo em um sistema de terceiros (ERP, MDM, PIM), os dados fluem pelo aplicativo principal do Commerce e, em seguida, para os Commerce services.
* Com o Serviço de assimilação de feed, os dados do produto vão diretamente do sistema de terceiros para a infraestrutura de Commerce services.

![Serviço de assimilação de feed](assets/feed-ingestion.png)

Ao ignorar o aplicativo principal do Commerce e mover dados diretamente para os serviços do Commerce, as atualizações de produtos são refletidas na loja mais rapidamente. Os dados principais do catálogo, como SKUs, são enviados ao aplicativo principal do Commerce para processamento separado.

## Associar-se ao beta

O serviço de assimilação de feed foi criado para:

* Clientes de empresas de médio porte com implementações headless
* Clientes com catálogos grandes e complexos
* Clientes que não usam o administrador do Adobe Commerce para gerenciar dados de catálogo, em vez disso usam um ERP ou sistema de terceiros para gerenciar dados de catálogo

Se você estiver interessado em participar do programa beta, entre em contato com a equipe em XXXXX@adobe.com.
