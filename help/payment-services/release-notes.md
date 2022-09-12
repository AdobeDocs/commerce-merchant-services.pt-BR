---
title: "[!DNL Payment Services] Notas de versão"
description: Revise as notas de versão para obter informações sobre todas as [!DNL Payment Services] versões.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
source-git-commit: 4e6bf72033495683491b0c59a544d1474f6c1486
workflow-type: tm+mt
source-wordcount: '1029'
ht-degree: 0%

---

# Notas de versão

Essas notas de versão descrevem a versão inicial do [!DNL Payment Services] e incluem:

![Novo](../assets/new.svg) Novos recursos
![Problema corrigido](../assets/fix.svg) Correções e melhorias
![Problema conhecido](../assets/bug.svg) Problemas conhecidos

Para ver as alterações e correções dos recursos lançadas fora da versão normal do recurso, consulte as seções Atualizações do serviço hospedado .

Consulte [Próximas versões](https://devdocs.magento.com/release/) para saber mais sobre os cronogramas de lançamento e suporte.

Consulte [Disponibilidade](https://devdocs.magento.com/release/availability.html) na documentação do desenvolvedor para saber mais sobre compatibilidade de produtos.

## Atualizações do serviço hospedado

Essas notas de versão descrevem as alterações de recursos e correções que ocorreram e foram lançadas fora das versões regulares de recursos com versão para o serviço hospedado.

+++Atualizações do serviço hospedado

_12 de setembro de 2022_

![Novo](../assets/new.svg)<!-- Issue PAY-3705 --> O `increment_id` O agora está disponível para uso na reconciliação de pagamentos em sistemas ERP externos. Ele é propagado para o [`custom_id` _e_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system), visível no webhook do PayPal e nos detalhes da atividade do comerciante para um pagamento.

_31 de agosto de 2022_

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3629 --> Quando um novo comerciante acessa a Página inicial dos Serviços de Pagamento pela primeira vez, a página agora é carregada imediatamente para exibir o conteúdo, em vez de exigir uma atualização da página.

_9 de agosto de 2021_

![Novo](../assets/new.svg)<!-- Issue PAY-3420 --> O Apple Pay agora está disponível como um botão inteligente do PayPal. Essa [opção de pagamento](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) permite que os clientes usem o recurso de ID de toque em seus dispositivos iOS ou macOS para selecionar o Apple Pay. O Apple Pay processa o pagamento usando as credenciais de pagamento de cartão de crédito e débito armazenadas no dispositivo.

_28 de junho de 2021_

![Novo](../assets/new.svg)<!-- Issue PAY-1720 --> Os litígios para pedidos de armazenamento agora estão disponíveis em [o relatório de status do pagamento da ordem](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). Você pode tomar medidas em disputas navegando diretamente para o Centro de Resolução do PayPal de [!DNL Payment Services].

![Novo](../assets/new.svg)<!-- Issue PAY-2854 --> Melhorias na experiência do usuário em [!DNL Payment Services] Home inclui a capacidade de modificar uma configuração no nível de herança atual e melhorias na exibição do cabeçalho e da navegação.

![Novo](../assets/new.svg)<!-- Issue PAY-2854 --> Agora você pode ver avisos ao alternar do modo sandbox para o modo de produção e ao tentar sair de uma exibição com atualizações que não foram salvas.

![Novo](../assets/new.svg)<!-- Issue PAY-2761 --> Agora é possível personalizar os dados exibidos na variável [Relatório de status do pagamento da ordem](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) e [Relatório de pagamentos](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) mostrando ou ocultando colunas usando o controle Configurações de coluna .

+++

## v1.3.1

_6 de setembro de 2022_

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3663 --> Agora, quando uma loja de um comerciante está capturando um pedido autorizado com uma moeda não global, o processo de captura é concluído e nenhum erro é mostrado.

## v1.3.0

_9 de agosto de 2022_

![Novo](../assets/new.svg)<!-- Issue PAY-XX --> Versão geral de disponibilidade—[!DNL Payment Services] é agora [compatível com [!DNL Adobe Commerce] e [!DNL Magento Open Source] versões 2.4.0 a 2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-x --> O Apple Pay agora é compatível com o navegador Safari v15.5 em dispositivos móveis e desktop.

## v1.2.0

_29 de junho de 2022_

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-x --> O Apple Pay é incompatível com o navegador Safari v15.5 em dispositivos móveis e desktop. Ao usar o Safari versão 15.5, não é possível concluir o check-out com o Apple Pay.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3264 --> Anteriormente, quando um usuário conectado selecionava um endereço de faturamento/envio diferente do padrão para sua conta, o check-out falhava. Corrigimos esse problema e agora o endereço de faturamento/envio selecionado é enviado (em vez do endereço salvo padrão) e o check-out é concluído com êxito.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3314 --> Se você desativar os botões inteligentes PayPal para finalização, nenhum erro será exibido.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3330 --> Os pagamentos não falham mais durante o check-out quando um usuário convidado insere um número de telefone que inclui traços.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> Quando as credenciais do Commerce Services forem inválidas, a variável [!DNL Payment Services] A página inicial agora será exibida no Administrador. Um erro de credenciais é exibido para alertá-lo de que suas credenciais são inválidas.

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] atualmente é incompatível com o `commerce-data-export` v101.20 e superior, o que o torna incompatível com o [[!DNL Channel manager] extensão](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## v1.1.0

_31 de março de 2022_

![Novo](../assets/new.svg)<!-- Issue PAY-2127 --> Versão geral de disponibilidade—[!DNL Payment Services] é agora [compatível com [!DNL Adobe Commerce] e [!DNL Magento Open Source] versões 2.4.0 a 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![Novo](../assets/new.svg)<!-- Issue PAY-2682 --> O [!DNL Payment Services] extensão para [!DNL Adobe Commerce] e [!DNL Magento Open Source] O agora está disponível para comerciantes canadenses. Os comerciantes podem visualizar a configuração de pagamentos em [Francês](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) ou [Inglês](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![Novo](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] suporta [Dólares canadenses (CAD)](overview.md#accepted-credit-cards-and-currencies) para cartões de crédito e transações de PayPal.

![Novo](../assets/new.svg)<!-- Issue PAY-2680 --> Merchants podem [integrado [!DNL Payment Services]](onboard.md) em inglês ou francês.

![Novo](../assets/new.svg)<!-- Issue PAY-2678 --> Os comerciantes agora podem visualizar relatórios financeiros, ambos [Status do pagamento da ordem](order-payment-status.md) e [Relatórios de pagamentos](payouts.md), em dólares canadianos (CAD).

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-2710 --> [!DNL Payment Services] agora é compatível com o [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3017 --> Alerta do modo de sandbox aprimorado para exibir alertas adequados com várias lojas.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-2742 --> Agora é possível ativar e desativar os métodos de pagamento disponíveis, como Venmo, no nível de visualização da loja. Anteriormente, você podia configurar métodos de pagamento somente por site.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-2277 --> Agora é possível seletivamente [ativar ou desativar botões inteligentes PayPal individuais](settings.md#payment-buttons).

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-2561 --> Os produtos removidos anteriormente não aparecem no carrinho da _Pedido de revisão_ página.

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-2842 --> Testar transações com cartão de crédito [pode falhar com o PayPal](https://support.magento.com/hc/en-us/articles/5201041963917) ao processar pagamentos em um ambiente sandbox.

## v1.0.0

_29 de novembro de 2021_

![Novo](../assets/new.svg)<!-- Issue PAY-2127 --> Versão geral de disponibilidade—[[!DNL Payment Services]](https://marketplace.magento.com/magento-payment-services.html) agora é compatível com o [!DNL Adobe Commerce] e [!DNL Magento Open Source] versões 2.4.0 a 2.4.3-p1.

![Novo](../assets/new.svg)<!-- Issue PAY-124 --> O [!DNL Payment Services] extensão para [!DNL Adobe Commerce] e [!DNL Magento Open Source] pode ser instalado para [[!DNL Adobe Commerce] na infraestrutura em nuvem](install.md#adobe-commerce-on-cloud-infrastructure) ou [No local](install.md#on-premises) instâncias. Esses métodos exigem o uso de uma Interface de linha de comando.

![Novo](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] suporta um [conta sandbox](sandbox.md) que permite que os comerciantes avaliem a extensão no modo de teste.

![Novo](../assets/new.svg)<!-- Issue PAY-666 --> Merchants podem [configurar os Serviços de Pagamento](settings.md) extensão com comportamentos básicos de pagamento, como utilizar [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) alternância entre ambientes de sandbox ou de produção.

![Novo](../assets/new.svg)<!-- Issue PAY-780 --> Seus compradores podem fazer check-out com [!DNL Payment Services] ou via [criação manual de pedidos](create-order.md).

![Novo](../assets/new.svg)<!-- Issue PAY-1856 --> Relatórios abrangentes, por meio de [Status do pagamento da ordem](order-payment-status.md) e [Relatórios de pagamentos](payouts.md)estão disponíveis para [!DNL Payment Services] para fornecer uma visão clara dos pedidos da loja e dos pagamentos relacionados.

![Novo](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] O suporta preços em camadas flexíveis, com base no volume total de processamento, adaptados a qualquer comerciante.

![Novo](../assets/new.svg)<!-- Issue PAY-1443 --> Você pode facilmente [personalizar a aparência](payments-options.md) de botões inteligentes PayPal e campos de cartão de crédito para [!DNL Payment Services] extensão.

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-2473 --> Usando [chaves do Composer incorretas](https://support.magento.com/hc/en-us/articles/4406603542541) durante a instalação da extensão, impede que o usuário [autenticação](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) com as `MAGEID`.

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] relatórios [pode não sincronizar imediatamente](https://support.magento.com/hc/en-us/articles/4406114741517).

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-2475 --> Seu [Conta de sandbox PayPal](https://support.magento.com/hc/en-us/articles/4406954952461) para [!DNL Payment Services] não pode ser verificado se você criou essa conta durante a integração.
