---
title: Serviço de assimilação de dados
description: Saiba mais sobre o serviço de assimilação de dados do Adobe Commerce
exl-id: bb5aec74-faca-42ec-9fdb-3261677d451e
source-git-commit: a2f933151481cbdd39d66a0dfbd36e6c339ede62
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# Serviço de assimilação de dados

O serviço de assimilação de dados permite que clientes com catálogos grandes e/ou complexos enviem dados diretamente para os serviços da Adobe Commerce.

O Serviço de assimilação de dados diminui o tempo necessário para processar alterações de produtos (atualizações de preços, adição de novos atributos), ignorando a instância do Adobe Commerce e movendo os dados do catálogo de um ERP (Enterprise Resource Planning, planejamento de recursos corporativos) de terceiros diretamente para os serviços da Adobe Commerce.

Este serviço é para clientes que armazenam e gerenciam seu catálogo de produtos em um sistema externo ao aplicativo principal do Adobe Commerce. Ele é fornecido como uma API, para que os clientes possam integrá-lo aos sistemas existentes, fornecendo flexibilidade adicional na forma como é implantado.

Clientes com catálogos grandes e complexos ou catálogos que recebem atualizações frequentes estão preocupados com o fato de que os novos dados podem levar mais tempo do que o desejado para serem exibidos no armazenamento dinâmico. Como o Serviço de catálogo sabe quais dados ele precisa para processar essas atualizações, não há necessidade de enviar os dados por meio do produto principal do Commerce, apenas para ser encaminhado ao Serviço de catálogo. A remoção desta etapa intermediária é onde os ganhos de eficiência são encontrados.

## Fluxos de assimilação de dados

Dependendo da configuração do Adobe Commerce, o armazenamento de dados e os fluxos de dados podem tomar caminhos diferentes.

* Em uma instância padrão do Adobe Commerce, o catálogo de produtos é armazenado no banco de dados principal.
* Ao usar os Serviços da Adobe Commerce, os dados do catálogo são copiados do banco de dados principal para o serviço e são processados e entregues a partir desse banco de dados.
* Ao armazenar dados de catálogo em um sistema de terceiros (ERP, MDM, PIM), os dados fluem pelo aplicativo principal do Commerce e, em seguida, para os Commerce services.
* Com o Serviço de assimilação de dados, os dados do produto vão diretamente do sistema de terceiros para a infraestrutura de Commerce services.

![Serviço de assimilação de dados](assets/data-ingestion.png)

Ao ignorar o aplicativo principal do Commerce e mover dados diretamente para os serviços do Commerce, as atualizações de produtos são refletidas na loja mais rapidamente. Os dados principais do catálogo, como SKUs, são enviados ao aplicativo principal do Commerce para processamento separado.

## API

A variável [Documentação da API do serviço de assimilação de dados](https://developer.adobe.com/commerce/services/data-ingestion) A seção fornece detalhes sobre como implementar o serviço.
