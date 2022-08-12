---
title: '''[!DNL Quick Checkout] Notas de versão'''
description: Revise as notas de versão para obter informações sobre todas as [!DNL Quick Checkout] versões.
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
source-git-commit: 27e91a640999cf83a0f0d6701e616f7ceecde12d
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 1%

---

# Notas de versão

Essas notas de versão descrevem a versão inicial do [!DNL Quick Checkout] e incluem:

![Novo](../assets/new.svg) Novos recursos
![Problema corrigido](../assets/fix.svg) Correções e melhorias
![Problema conhecido](../assets/bug.svg) Problemas conhecidos

Consulte [Próximas versões](https://devdocs.magento.com/release/) para saber mais sobre os cronogramas de lançamento e suporte.

Consulte [Disponibilidade](https://devdocs.magento.com/release/availability.html) na documentação do desenvolvedor para saber mais sobre compatibilidade de produtos.

## v1.1.0

_12 de agosto de 2022_

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-375 --> Melhorias na experiência do usuário em [[!DNL Quick Checkout] Painel de administração](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) agora inclui apenas os parâmetros que estão visíveis e validados quando a extensão está ativada.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-349 --> Melhorias de compatibilidade para endereços de envio existentes com a wallet Bolt.

## v1.0.0

_9 de agosto de 2022_

![Novo](../assets/new.svg)<!-- Issue BOLT-341 --> Versão geral de disponibilidade—[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) O agora é compatível com as versões 2.4.1 a 2.4.4 do Adobe Commerce.

![Novo](../assets/new.svg)<!-- Issue BOLT-340 --> O [!DNL Quick Checkout] para o Adobe Commerce pode ser instalado para o Adobe Commerce [na infraestrutura em nuvem](install.md#adobe-commerce-on-cloud-infrastructure) ou [no local](install.md#on-premises) instâncias. Esses métodos exigem o uso de uma interface de linha de comando.

![Novo](../assets/new.svg)<!-- Issue BOLT-1 --> O [!DNL Quick Checkout] O para Adobe Commerce oferece uma loja otimizada que permite um [experiência de finalização com um clique](overview.md) sem campos de preenchimento exigidos aos consumidores.

![Novo](../assets/new.svg)<!-- Issue BOLT-1 --> O [!DNL Quick Checkout] para a Adobe Commerce reconhece automaticamente cada comprador em sua rede para [compras com um clique](checkout-flow.md) diretamente no seu site.

![Novo](../assets/new.svg)<!-- Issue BOLT-1 --> O [!DNL Quick Checkout] para Adobe Commerce permite que um comprador seja simultaneamente [conectado em redes Adobe Commerce e Bolt](checkout-flow.md/#quick-checkout-use-cases) para proporcionar uma melhor `one-click checkout` experiência.

![Novo](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] para Adobe Commerce oferece suporte a [conta sandbox](testing.md#testing-in-sandbox) que permite que os comerciantes avaliem a extensão no modo de teste.

![Novo](../assets/new.svg)<!-- Issue BOLT-780 --> Seus compradores podem fazer check-out através do [[!DNL Quick Checkout]](checkout-page.md) ou por meio de uma [criação manual de pedidos](create-order-admin.md).

![Novo](../assets/new.svg)<!-- Issue BOLT-666 --> Os comerciantes podem configurar o [!DNL Quick Checkout] com ações básicas de pagamento, como [`Authorize and Capture` ou `Authorize` ](onboarding.md#complete-admin-configuration)ou alternar entre ambientes de sandbox e de produção.

![Novo](../assets/new.svg)<!-- Issue BOLT-288 --> Personalizado [duração da sessão do usuário](user-session-lifetime.md) para [!DNL Quick Checkout] para Adobe Commerce.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-375 --> Melhorias na experiência do usuário em [[!DNL Quick Checkout] Painel de administração](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) O permite salvar sua configuração quando todos os parâmetros necessários forem fornecidos.

![Problema conhecido](../assets/bug.svg)<!-- Issue BOLT-342 --> Frequentes [solução de problemas](https://support.magento.com/hc/en-us/articles/6909450342541) problemas durante a instalação de [!DNL Quick Checkout].
