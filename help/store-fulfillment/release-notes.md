---
title: '[!DNL Store Fulfillment by Walmart Commerce Technologies] Notas de versão'
description: "Revise as notas de versão para obter informações sobre tudo [!DNL Store Fulfillment by Walmart Commerce Technologies] lançamentos."
role: Admin, User, Leader
feature: Shipping/Delivery, Release Notes
exl-id: 04dcec10-fff8-483d-a2c1-4b58e063e0f0
source-git-commit: db1d5523f48f5686c2a28c7dfb7b1175238b37cf
workflow-type: tm+mt
source-wordcount: '514'
ht-degree: 1%

---

# Notas de versão

Estas notas de versão descrevem a versão inicial do [!DNL Store Fulfillment Services by Walmart Commerce Technologies] e incluem:

![Novo](../assets/new.svg) Novos recursos
![Problema corrigido](../assets/fix.svg) Correções e aprimoramentos
![Problema conhecido](../assets/bug.svg) Problemas conhecidos

Consulte [Versões futuras](https://experienceleague.adobe.com/docs/commerce-operations/release/planning/schedule.html) para saber mais sobre as programações de lançamento e o suporte.

Consulte [Disponibilidade do produto](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html) para saber quais versões do Adobe Commerce são compatíveis com essa extensão.

## v1.5.0

*3 de agosto de 2023*

[!BADGE Compatível]{type=Informative tooltip="Compatível"}[Adobe Commerce 2.4.4 a 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html), incluindo as versões de patch de segurança 2.4.6-p1, 2.4.5-p3 e 2.4.4-p4

Esta versão inclui as seguintes atualizações:

![Novo](../assets/fix.svg) Atualização da extensão para oferecer suporte ao [Versões de patch de segurança do Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-operations/release/notes/security-patches/overview.html) 2.4.6-p1, 2.4.5-p3 e 2.4.4-p4.

![Novo](../assets/new.svg)<!-- WMTP-918 --> Adição de suporte para o [Envio assíncrono](sales-emails.md) opção de configuração para emails de vendas. Os comerciantes que atualizam para a versão 1.5.0 têm a opção de enviar emails imediatamente (padrão) ou de forma assíncrona.

![Novo](../assets/new.svg)<!-- WMTP-916--> Atualização do [Configuração de origens](merchant-store-configuration.md) para suportar formatos de número de telefone internacionais.

![Novo](../assets/new.svg) Foi adicionada uma lógica para impedir que os valores de reembolso excedam o valor restante ou faturado.

![Novo](../assets/new.svg)<!-- WMTP-882 --> Substituído `google.map.LatLng` objeto com literais JSON para oferecer suporte à compatibilidade com versões mais antigas do [!DNL Google Maps].

![Problema corrigido](../assets/fix.svg)<!-- WMTP- --> Atualização do script que cria o `[!DNL Available for Store Pickup]` e `[!DNL Available for Home Delivery]` atributos de produto para evitar conflito de categoria de atributo.

![Problema corrigido](../assets/fix.svg)<!-- WMTP-915 --> Correção de um problema de compatibilidade que causava um loop infinito ao carregar e salvar algumas entidades.

![Problema corrigido](../assets/fix.svg)<!-- WMTP-921 --> Correção de um problema que impedia [!DNL Ship to Store] validação de cota acionada quando um item é adicionado ao carrinho a partir de uma página de detalhes do produto (PDP).

![Problema corrigido](../assets/fix.svg)<!-- WMTP- 932 --> Correção de um problema de check-out que permitia aos clientes selecionar o método de entrega residencial para itens que não eram qualificados para entrega residencial.

![Problema corrigido](../assets/fix.svg) Atualizações de instalação:

- <!-- WMTP-880--> Correção de um problema que fazia com que um código de site incorreto fosse retornado ao instalar o [!DNL Store Fulfillment] extensão.

- <!-- WMTP-878--> Correção de um problema para inteiros SKU que exigia que o tipo de dados fosse convertido em tipo de string durante a instalação.

![Problema corrigido](../assets/fix.svg)<!-- WMTP-915--> Correção de uma falha causada pela ausência de um código de erro de check-in.

![Problema corrigido](../assets/fix.svg)<!-- WMTP-932 --> Correção de um erro relacionado à rejeição parcial durante operações de dispensação.

![Novo](../assets/new.svg)<!-- WMTP-953 --> O endpoint da API Cancelar foi atualizado para consumir o parâmetro de status como um objeto opcional.

![Novo](../assets/new.svg)<!-- WMTP-960 --> Detalhes de registro aprimorados para o endpoint da API Dispense.

## v1.4.0

*13 de abril de 2023*

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/fix.svg) [!DNL Store Fulfillment] agora é [compatível com [!DNL Adobe Commerce] 2.4.4 a 2.4.6](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.3.0

*27 de fevereiro de 2023*

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

Esta versão inclui a seguinte atualização:

![Novo](../assets/fix.svg)<!-- WMTP-795 --> Adição da capacidade de desabilitar a solução Atendimento da Loja para um site específico, alterando o escopo padrão da configuração Configuração do Sistema de site para global.

## v1.2.0

*27 de setembro de 2022*

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

Esta versão inclui a seguinte atualização:

![Novo](../assets/fix.svg) [!DNL Store Fulfillment] agora é [compatível com [!DNL Adobe Commerce] 2.4.4 a 2.4.5](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html).


## v1.1.0

*15 de julho de 2022*

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

Estabilidade: disponibilidade geral

![Novo](../assets/fix.svg)<!-- WMTP-731 --> Simplificou a [Configuração da experiência de check-in](check-in-experience-setup.md) para o aplicativo Store Assist, adicionando a marca de carro padrão e as seleções de modelo. Na versão anterior, os comerciantes tinham que configurar manualmente a marca do carro e as seleções do modelo.

## v1.0.0

*4 de março de 2022*

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

Estabilidade: disponibilidade geral

## Aplicativo de assistência da loja

Para obter informações sobre novos lançamentos do aplicativo Store Assist, consulte as informações do aplicativo no [Apple App Store](https://apps.apple.com/us/app/store-assist-by-walmart/id1609281539){target="_blank"} or [Google Play store](https://play.google.com/store/apps/details?id=com.walmart.faas.storeassist){target="_blank"}.
