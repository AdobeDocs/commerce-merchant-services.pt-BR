---
title: Requisitos de Atendimento da Loja
description: Requisitos para provisionamento e integração do [!DNL Store Fulfillment solution].
role: User, Admin
level: Intermediate
exl-id: f9e05049-5904-4f6c-b45d-9f81fbc76b69
source-git-commit: 4c10ab59ed304002cfde7398762bb70b223180ce
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 2%

---

# Requisitos de preenchimento de loja para o Adobe Commerce

As seções a seguir detalham os requisitos técnicos e comerciais para instalar e habilitar a solução Store Fulfillment para Adobe Commerce.

## Requisitos de versão de software e plataforma

A variável [!DNL Store Fulfillment] está disponível para clientes do Adobe Commerce nas seguintes plataformas.

- Adobe Commerce na infraestrutura em nuvem (ECE)
- Adobe Commerce no local (EE)

A solução Store Fulfillment é compatível com as versões de software listadas no *Compatibilidade de software* tabela.

**Compatibilidade de software**

| **Software** | **Versão Mínima** | **Versão Máxima** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.5 |
| Compositor | 1.x | 2.x |
| MariaDB | 10.2 | 10.4 |
| MySQL | 5.7 | 8.0 |
| PHP | 7.4 | 8.1 |

Para obter requisitos detalhados, consulte o Adobe Commerce [Requisitos do sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html) no *Guia de instalação do Adobe Commerce*.

## Requisitos do aplicativo Store Assist

O processo completo para gerenciar pedidos de retirada de lojas é gerenciado pelo aplicativo Store Assist instalado em dispositivos móveis. Esses dispositivos — fornecidos pelo varejista ou pelos funcionários da loja que usam seus smartphones pessoais — devem atender aos seguintes requisitos:

**Requisitos mínimos do sistema operacional**

- Android 6
- iOS 12

**Requisitos mínimos de hardware**

- 1 GB de RAM
- 600 MB de espaço livre em disco

## Requisitos comerciais

Sua empresa deve atender aos seguintes critérios mínimos para implementar a solução Store Fulfillment:

- Somente empresas com sede nos EUA

- Varejistas B2C (B2C), fabricantes de produtos embalados para o consumidor (CPG) que vendem diretamente aos consumidores (D2C) ou distribuidores que vendem diretamente a consumidores ou pequenas empresas

- Pelo menos um armazenamento físico ou depósito

- Gerencie seu inventário de produtos com o Inventory management for Adobe Commerce (também conhecido como MSI)

- Capacidade de agregar inventário de comerciante

- Armazene a disponibilidade do Wi-Fi em todos os locais que oferecem suporte à solução Store Fulfillment: velocidade mínima de 3 Mbps da Internet

- Associados de lojas e armazéns têm acesso a dispositivos móveis iOS ou Android durante seus turnos, pessoais ou fornecidos pelo comerciante

- Os produtos gerenciados usando a solução Store Fulfillment devem ter atributos de produto que incluam um código de produto SKU ou UPC
