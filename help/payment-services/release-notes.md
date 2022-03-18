---
title: '"[!DNL Payment Services] Notas de versão"'
description: Revise as notas de versão para obter informações sobre todas as [!DNL Payment Services] versões.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: eb8fdba65b4b64730d0ad4fa6e0c9b64bdadc7df
workflow-type: tm+mt
source-wordcount: '270'
ht-degree: 1%

---

# Notas de versão

Essas notas de versão descrevem a versão inicial do [!DNL Payment Services] e incluem:

![Novo](../assets/new.svg) Novos recursos
![Problema corrigido](../assets/fix.svg) Correções e melhorias
![Problema conhecido](../assets/bug.svg) Problemas conhecidos

## v1.0.0

![Novo](../assets/new.svg)<!-- Issue PAY-2127 --> Versão de disponibilidade geral. [Serviços de pagamento](https://marketplace.magento.com/magento-payment-services.html) O agora é compatível com Adobe Commerce e Magento Open Source versões 2.4.0 a 2.4.3-p1.

![Novo](../assets/new.svg)<!-- Issue PAY-124 --> O [!DNL Payment Services] A extensão para Adobe Commerce e Magento Open Source pode ser instalada para [Adobe Commerce na infraestrutura de nuvem](install.md#magento-commerce-cloud) ou [No local](install.md#on-premises) instâncias. Esses métodos exigem o uso de uma Interface de linha de comando.

![Novo](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] suporta um [conta sandbox](onboard.md#enable-sandbox-testing) que permite que os comerciantes avaliem a extensão no modo de teste.

![Novo](../assets/new.svg)<!-- Issue PAY-666 --> Merchants podem [configurar Serviços de Pagamento](configure-admin.md) extensão com comportamentos de pagamento básicos (como captura de autenticação junto e alternância entre sandbox ou ambientes de produção).

![Novo](../assets/new.svg)<!-- Issue PAY-780 --> Os compradores podem fazer check-out com [!DNL Payment Services] ou você pode fazer o pedido pelo telefone e [criar um pedido inteiro](create-order.md) no Administrador para eles.

![Novo](../assets/new.svg)<!-- Issue PAY-1856 --> [!DNL Payment Services] ofereça relatórios abrangentes aos comerciantes para que você possa obter uma visão clara de seus pedidos e pagamentos de loja.

![Novo](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] O suporta preços hierárquicos (baseados em TPV) adaptados a qualquer comerciante.

![Novo](../assets/new.svg)<!-- Issue PAY-1443 --> É possível personalizar a aparência dos botões PayPal e dos campos CC para o [Serviços de pagamento](https://devdocs.magento.com/payment-services/customize-buttons-messaging.html) extensão.

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-2473 --> Usando [chaves do compositor incorretas](https://support.magento.com/hc/en-us/articles/4406603542541) durante a instalação da extensão impede que o usuário [autenticar](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) com correto `MAGEID`.

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] [relatórios](https://support.magento.com/hc/en-us/articles/4406114741517) O status de pagamento de Pagamento e Pedido pode não ser sincronizado imediatamente.

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-2475 --> [Conta de sandbox PayPal](https://support.magento.com/hc/en-us/articles/4406954952461) para [!DNL Payment Services] não pode ser verificado.
