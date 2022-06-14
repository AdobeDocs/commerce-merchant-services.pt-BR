---
title: '"[!DNL Payment Services] Notas de versão"'
description: Revise as notas de versão para obter informações sobre todas as [!DNL Payment Services] versões.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 6fc2db2ff842244af6a3c52b575b26233540931b
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Notas de versão

Essas notas de versão descrevem a versão inicial do [!DNL Payment Services] e incluem:

![Novo](../assets/new.svg) Novos recursos
![Problema corrigido](../assets/fix.svg) Correções e melhorias
![Problema conhecido](../assets/bug.svg) Problemas conhecidos

Consulte [Próximas versões](https://devdocs.magento.com/release/) para saber mais sobre os cronogramas de lançamento e suporte.

Consulte [Disponibilidade](https://devdocs.magento.com/release/availability.html) na documentação do desenvolvedor para saber mais sobre compatibilidade de produtos.

## v1.1.0

![Novo](../assets/new.svg)<!-- Issue PAY-2127 --> Versão geral de disponibilidade—[!DNL Payment Services] é agora [compatível com [!DNL Adobe Commerce] e [!DNL Magento Open Source] versões 2.4.0 a 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![Novo](../assets/new.svg)<!-- Issue PAY-2682 --> O [!DNL Payment Services] extensão para [!DNL Adobe Commerce] e [!DNL Magento Open Source] O agora está disponível para comerciantes canadenses. Os comerciantes podem visualizar a configuração de pagamentos em [Francês](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies) ou [Inglês](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.md#accepted-credit-cards-and-currencies).

![Novo](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] suporta [Dólares canadenses (CAD)](overview.md#accepted-credit-cards-and-currencies) para cartões de crédito e transações de PayPal.

![Novo](../assets/new.svg)<!-- Issue PAY-2680 --> Merchants podem [integrado [!DNL Payment Services]](onboard.md) em inglês ou francês.

![Novo](../assets/new.svg)<!-- Issue PAY-2678 --> Os comerciantes agora podem visualizar relatórios financeiros, ambos [Status do pagamento da ordem](order-payment-status.md) e [Relatórios de pagamentos](payouts.md), em dólares canadianos (CAD).

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] agora é compatível com o [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3017 --> Alerta do modo de sandbox aprimorado para exibir alertas adequados com várias lojas.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-2742 --> Agora é possível ativar e desativar os métodos de pagamento disponíveis, como Venmo, no nível de visualização da loja. Anteriormente, você podia configurar métodos de pagamento somente por site.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-2277 --> Agora é possível seletivamente [ativar ou desativar botões inteligentes PayPal individuais](settings.md#paypal-smart-buttons).

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-2561 --> Os produtos removidos anteriormente não aparecem no carrinho da _Pedido de revisão_ página.

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-2842 --> Testar transações com cartão de crédito [pode falhar com o PayPal](https://support.magento.com/hc/en-us/articles/5201041963917) ao processar pagamentos em um ambiente sandbox.

## v1.0.0

![Novo](../assets/new.svg)<!-- Issue PAY-2127 --> Versão geral de disponibilidade—[[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) agora é compatível com o [!DNL Adobe Commerce] e [!DNL Magento Open Source] versões 2.4.0 a 2.4.3-p1.

![Novo](../assets/new.svg)<!-- Issue PAY-124 --> O [!DNL Payment Services] extensão para [!DNL Adobe Commerce] e [!DNL Magento Open Source] pode ser instalado para [[!DNL Adobe Commerce] na infraestrutura em nuvem](install.md#adobe-commerce-on-cloud-infrastructure) ou [No local](install.md#on-premises) instâncias. Esses métodos exigem o uso de uma Interface de linha de comando.

![Novo](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] suporta um [conta sandbox](sandbox.md) que permite que os comerciantes avaliem a extensão no modo de teste.

![Novo](../assets/new.svg)<!-- Issue PAY-666 --> Merchants podem [configurar os Serviços de Pagamento](settings.md) extensão com comportamentos básicos de pagamento, como utilizar [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) alternância entre ambientes de sandbox ou de produção.

![Novo](../assets/new.svg)<!-- Issue PAY-780 --> Seus compradores podem fazer check-out com [!DNL Payment Services] ou via [criação manual de pedidos](create-order.md).

![Novo](../assets/new.svg)<!-- Issue PAY-1856 --> Relatórios abrangentes, por meio de [Status do pagamento da ordem](order-payment-status.md) e [Relatórios de pagamentos](payouts.md)estão disponíveis para [!DNL Payment Services] para fornecer uma visão clara dos pedidos da loja e dos pagamentos relacionados.

![Novo](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] O suporta preços em camadas flexíveis, com base no volume total de processamento, adaptados a qualquer comerciante.

![Novo](../assets/new.svg)<!-- Issue PAY-1443 --> Você pode facilmente [personalizar a aparência](payments-options.md) de botões inteligentes PayPal e campos de cartão de crédito para a extensão Serviços de Pagamento.

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-2473 --> Usando [chaves do Composer incorretas](https://support.magento.com/hc/en-us/articles/4406603542541) durante a instalação da extensão, impede que o usuário [autenticação](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) com as `MAGEID`.

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] relatórios [pode não sincronizar imediatamente](https://support.magento.com/hc/en-us/articles/4406114741517).

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-2475 --> Seu [Conta de sandbox PayPal](https://support.magento.com/hc/en-us/articles/4406954952461) para [!DNL Payment Services] não pode ser verificado se você criou essa conta durante a integração.
