---
title: Requisitos de cumprimento da loja
description: Requisitos em matéria de provisionamento e integração [!DNL Store Fulfillment solution].
role: User, Admin
level: Intermediate
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 2%

---

# Requisitos de preenchimento da loja para a Adobe Commerce

As seções a seguir detalham os requisitos técnicos e comerciais para instalar e habilitar a solução Store Fulfillment para Adobe Commerce.

## Requisitos da versão da plataforma e do software

O [!DNL Store Fulfillment] A solução está disponível para clientes da Adobe Commerce nas seguintes plataformas.

- Adobe Commerce on cloud Infrastructure (ECE)
- Adobe Commerce nas instalações (EE)

A solução Store Fulfillment é compatível com as versões de software listadas na *Compatibilidade de software* tabela.

**Compatibilidade de software**

| **Software** | **Versão mínima** | **Versão máxima** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.5 |
| Composer | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

Para saber mais sobre os requisitos, consulte a Adobe Commerce [Requisitos do sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) no *Guia de instalação do Adobe Commerce*.

## Requisitos do aplicativo Store Assist

O processo completo para gerenciar pedidos de retirada de loja é gerenciado por meio do aplicativo Store Assist instalado em dispositivos móveis. Esses dispositivos—fornecidos pela varejista ou por funcionários de loja usando seus smartphones pessoais—devem atender aos seguintes requisitos:

**Requisitos mínimos do sistema operacional**

- Android 6
- iOS 12

**Requisitos mínimos de hardware**

- 1 GB de RAM
- 600 MB de espaço livre em disco

## Requisitos de empresa

Sua empresa deve atender aos seguintes critérios mínimos para implementar a solução de fornecimento de armazenamento:

- Somente empresas com base nos EUA

- B2C (Business to Consumer) Retalhistas, Bens de Consumo Embalados (CPG) Fabricantes que vendem diretamente aos consumidores (D2C) ou distribuidores que vendem diretamente aos consumidores ou às pequenas empresas

- Pelo menos um armazém físico

- Gerencie o inventário de produtos com o Inventory management for Adobe Commerce (também conhecido como MSI)

- Capacidade de sindicalizar inventário de merchant

- Armazene a disponibilidade do Wi-Fi em todos os locais que oferecem suporte à solução de disponibilização da loja: Velocidade mínima de Internet de 3 Mbps

- Os associados de armazenamento e depósito têm acesso a dispositivos móveis iOS ou Android durante seus turnos, pessoais ou fornecidos pelo comerciante

- Os produtos gerenciados por meio da solução Store Fulfillment devem ter atributos de produto que incluam um código de produto SKU ou UPC
