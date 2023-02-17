---
title: Segurança e conformidade
description: Analise os requisitos de segurança e conformidade do seu site.
exl-id: 083c5a12-1d78-48b5-b9e3-612b104ce7e0
source-git-commit: 17ba23192fed6cd219411420c5d56b42c94af0f5
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# Segurança e conformidade

A segurança é da maior preocupação no [!DNL Payment Services] e nenhuma informação regulamentada pelo setor privado ou de cartões de pagamento (PCI) é transmitida através de seu [!DNL Payment Services].

## Segurança comercial

[!DNL Adobe Commerce] e [!DNL Magento Open Source] inclui suporte para vários recursos de segurança.

Consulte [Segurança](https://docs.magento.com/user-guide/stores/security.html){target="_blank"} no guia do usuário principal para analisar as práticas recomendadas de segurança e saber como gerenciar sessões e credenciais de administração, implementar o CAPTCHA e gerenciar restrições do site.

## Conformidade com a PCI

O PCI (Payment Card Industry, setor de cartões de pagamento) estabeleceu um conjunto de requisitos para as empresas que aceitam o pagamento por cartão de crédito através da Internet. Além de manter um ambiente seguro, os comerciantes que lidam com as informações sobre os cartões de crédito dos clientes são responsáveis pelo cumprimento de algumas orientações normais.

Consulte [Diretrizes de conformidade PCI](https://docs.magento.com/user-guide/stores/compliance-pci.html){target="_blank"} para obter mais informações.

Os comerciantes podem concluir uma [questionário de autoavaliação (SAQ)](https://www.pcisecuritystandards.org/pci_security/completing_self_assessment){target="_blank"}, que é um instrumento de autovalidação para avaliar a segurança dos dados do titular do cartão.

### Campos de cartão de crédito

Com os Campos de cartão de crédito, nenhum dado regulamentado por PCI é transmitido pelos seus serviços. Você não precisa armazenar ou manter esses dados, o que reduz amplamente os problemas de conformidade com o PCI.

### 3DS

O PCI 3-D Secure (3DS) permite a autenticação do comprador com o emissor do cartão de crédito ao realizar compras online de cartão de crédito. Essa camada adicional de segurança ajuda a prevenir fraudes online e é exigida como parte dos regulamentos de conformidade da União Europeia (UE).

[!UICONTROL Payment Services] O oferece a funcionalidade 3DS para permitir que os comerciantes cumpram os regulamentos da UE e para proteger os clientes e comerciantes de atividades fraudulentas em suas lojas.

Se você for um comerciante na UE ou na Grã-Bretanha onde a conformidade com o 3DS é necessária, é necessário ativar manualmente o 3DS (é `Off` por padrão) em [Configurações](settings.md#credit-card-fields).

Os pedidos feitos para o comprador pela equipe do comerciante/loja não são configurados com medidas de conformidade 3DS.

Consulte [3DS em Configurações](settings.md#3ds) para obter mais informações.

### Salto de cartão

Quando um comprador [cofres — ou &quot;salva&quot; — suas informações de cartão de crédito](vaulting.md) para compras futuras em suas lojas, informações mínimas de cartão de crédito são compartilhadas com o comprador (últimos quatro dígitos, data de expiração do cartão e marca do cartão). As informações relativas ao cartão de crédito são armazenadas junto do prestador de pagamento. Quando um cartão expira ou já não necessita das informações guardadas, pode eliminar esse token de modo a que as informações deixem de estar armazenadas pelo prestador de serviços de pagamento.

Consulte [Vazamento do cartão de crédito](vaulting.md) para obter mais informações.

### Botões inteligentes PayPal

Com os botões inteligentes PayPal, nenhum dado regulamentado por PCI é transmitido entre seus serviços. Você não precisa armazenar ou manter esses dados, o que reduz amplamente os problemas de conformidade com o PCI.

Por motivos de segurança, o PayPal não passa o endereço de cobrança durante o check-out — país, email e nome são as únicas informações de faturamento usadas. Opcionalmente, você pode ativar o check-out do PayPal de seu site para retornar o endereço de faturamento completo, entrando em contato com o PayPal e concluindo um processo de verificação.

O PayPal também integrou a proteção à fraude que usa o aprendizado de máquina para ajudá-lo a combater a fraude. Consulte PayPal&#39;s [Documentação de proteção do vendedor](https://www.paypal.com/us/webapps/mpp/security/seller-protection) para obter mais informações.
