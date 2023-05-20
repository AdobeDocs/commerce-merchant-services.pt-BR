---
title: '[!DNL Quick Checkout] Notas de versão'
description: Revise as notas de versão para obter informações sobre tudo [!DNL Quick Checkout] versões.
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
source-git-commit: d58193b622a1851259b2191ea54ac6b59029dd64
workflow-type: tm+mt
source-wordcount: '1402'
ht-degree: 0%

---

# Notas de versão

Estas notas de versão descrevem a versão inicial do [!DNL Quick Checkout] e incluem:

![Novo](../assets/new.svg) Novos recursos
![Problema corrigido](../assets/fix.svg) Correções e aprimoramentos
![Problema conhecido](../assets/bug.svg) Problemas conhecidos

Consulte [Versões futuras](https://devdocs.magento.com/release/) para saber mais sobre as programações de lançamento e o suporte.

Consulte [Disponibilidade](https://devdocs.magento.com/release/availability.html) na documentação do desenvolvedor para saber mais sobre a compatibilidade do produto.

## Atualizações do painel do administrador

Essas notas de versão descrevem alterações e correções de recursos que ocorreram e foram lançadas fora das versões de recursos com versão normal do painel do Administrador.

+++Atualizações do painel do administrador

_25 de abril de 2023_

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-452 --> A variável [!DNL Quick Checkout] **Fazer um tour** O botão agora exibe um cursor de mão clicável ao passar o mouse sobre ele.

_19 de abril de 2023_

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-596 --> A variável [!DNL Quick Checkout] A página Relatórios agora mostra corretamente o gráfico Novas contas ao analisar datas para o formato ISO 8601.

_14 de dezembro de 2022_

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-524 --> A variável [!DNL Quick Checkout] O painel Admin agora mostra o total correto de pedidos e as informações de relatórios atualizadas.

_30 de novembro de 2022_

![Novo](../assets/new.svg)<!-- Issue BOLT-502 --> Agora, a variável [relatórios](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) A guia tem uma nova predefinição &quot;Ano passado&quot;.

![Novo](../assets/new.svg)<!-- Issue BOLT-471 --> Melhorias na experiência do usuário no [!DNL Quick Checkout] Painel de administração para mostrar mais informações no [Dicas de ferramenta](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html).

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-514 --> Melhorias na experiência do usuário no [!DNL Quick Checkout] O painel Admin mostra os números corretos dos pedidos totais, a consistência nas cores e as legendas corretas para todos os gráficos.

_2 de novembro de 2022_

![Novo](../assets/new.svg)<!-- Issue BOLT-293 --> Agora, a variável [relatórios](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) na guia [!DNL Quick Checkout] O painel Admin mostra gráficos e informações de relatórios das estatísticas de experiência de check-out da sua loja.

![Novo](../assets/new.svg)<!-- Issue BOLT-422 --> A variável [_Visão geral_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-overview) A seção do tópico Relatórios mostra informações detalhadas sobre o desempenho de check-out da loja, incluindo o tempo médio de check-out, as novas contas criadas durante o check-out e o abandono do check-out.

![Novo](../assets/new.svg)<!-- Issue BOLT-423 --> A variável [_Tendências_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-trends) A seção da guia Relatórios mostra as tendências de experiência de check-out filtradas por tipo de conta e por novas contas criadas durante o check-out.

![Novo](../assets/new.svg)<!-- Issue BOLT-439 --> A variável **Relatórios** exibições da guia [predefinições de filtro padrão](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#filter-data) que podem ser usados para mostrar intervalos de dados específicos.

![Novo](../assets/new.svg)<!-- Issue BOLT-433 --> Agora você pode ver uma _Não há dados disponíveis_ aviso para um gráfico quando uma solicitação não retorna dados.

![Novo](../assets/new.svg)<!-- Issue BOLT-473 --> Melhorias na experiência do usuário com o [!DNL Quick Checkout] O painel de administração inclui a capacidade de ativar um [rastreamento de check-out](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) configuração que permite ao Adobe Commerce compartilhar informações de relatórios com o Bolt.

_5 de outubro de 2022_

![Novo](../assets/new.svg)<!-- Issue BOLT-379 --> Agora, quando um novo comerciante acessa o [!DNL Quick Checkout] Painel de administração pela primeira vez em [tour em destaque disponibilizado pela Gainsight](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) é exibida.

![Novo](../assets/new.svg)<!-- Issue BOLT-377 --> A variável **Relatórios** na guia [!DNL Quick Checkout] O painel Admin mostra gráficos e análises de relatórios.

![Novo](../assets/new.svg)<!-- Issue BOLT-377 --> A variável **Relatórios** na guia [!DNL Quick Checkout] O painel Admin mostra o intervalo de datas e as predefinições de filtro para gráficos e análises de relatórios.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-369 --> Agora, a variável [[!DNL Quick Checkout] Painel de administração](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) exibe a versão do aplicativo no rodapé.

+++

## v1.8.0

_24 de fevereiro de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg)<!-- Issue BOLT-520 --> Versão de disponibilidade geral—[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) O agora está pré-instalado nas versões 2.4.6 e mais recentes do Adobe Commerce Cloud.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-592 --> Melhorias na experiência do usuário ao fazer um pedido no [Painel de administração](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/create-order-admin.html) usar [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/stored-payment-methods.html) como um método de pagamento. Essa funcionalidade permite que os clientes façam um pedido com o Braintree como método de pagamento durante o checkout quando [!DNL Quick Checkout] está ativado.

## v1.7.0

_22 de fevereiro de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Problema corrigido](../assets/fix.svg)<!-- Issue AC-8002 --> Melhorias na experiência do usuário ao fazer um pedido usando uma [Multisenvio](https://experienceleague.adobe.com/docs/commerce-admin/config/sales/multishipping-settings.html) método. Essa funcionalidade permite a exibição de métodos de pagamento durante o check-out quando [!DNL Quick Checkout] está ativado.

## v1.6.0

_9 de fevereiro de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-567 --> Melhorias na experiência do usuário ao [colocação de um pedido](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) usando o [Entrega na loja](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/basic-methods/shipping-in-store-delivery.html) com o [!DNL Quick Checkout] desativado.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-569 --> Melhorias na funcionalidade de logout que permitem aos compradores [fazer logout da rede Bolt](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/user-session-lifetime.html).

## v1.5.0

_18 de janeiro de 2023_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg)<!-- Issue BOLT-522 --> Uma nova configuração pode ser ativada/desativada para detectar se [compradores](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-options/checkout-adobe-commerce.html) pode ser automaticamente conectado no Bolt.

![Novo](../assets/new.svg)<!-- Issue BOLT-523 --> Uma nova configuração pode ser habilitada/desabilitada, permitindo que os comerciantes especifiquem se os compradores podem ser conectados automaticamente a ambas as redes ou apenas à rede Bolt.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-542 --> Melhorias na experiência do usuário ao [salvar cartão ou endereço em uma conta do Bolt](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) quando um comprador fornece email.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-550 --> Melhorias na experiência do usuário no [logon automático](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#configure-service-settings) quando um usuário do Bolt fornece email.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-544 --> Melhorias de compatibilidade do [URLs de retorno de chamada](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#check-shopper-valid-account) com [vários sites](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/multi-sites/ms-overview.html) em Parafuso.

## v1.4.0

_30 de novembro de 2022_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg)<!-- Issue BOLT-513 --> Agora, quando um cliente do Adobe Commerce é conectado à loja durante o processo de finalização e tem uma conta do Bolt, uma opção para fazer logon na conta do Bolt do comprador é exibida.

![Novo](../assets/new.svg)<!-- Issue BOLT-512 --> Uma nova configuração detecta automaticamente se os compradores conectados também podem ser conectados no Bolt.

![Novo](../assets/new.svg)<!-- Issue BOLT-480 --> Uma nova configuração no [!DNL Quick Checkout] O Painel de administração permite alterar o fluxo de navegação padrão para a variável **Envio** depois que um cliente do Bolt faz logon. Por padrão, é configurado para o **Pagamentos** página.

## v1.3.0

_2 de novembro de 2022_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg)<!-- Issue BOLT-293 --> Agora, [!DNL Quick Checkout] inclui a capacidade de habilitar um [rastreamento de check-out](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) configuração que permite ao Adobe Commerce compartilhar informações de relatórios com o Bolt.

![Novo](../assets/new.svg)<!-- Issue BOLT-461 --> Agora você pode ver uma mensagem de aviso em seu [!DNL Quick Checkout] Painel de administração se [rastreamento de check-out](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) A configuração do está desativada.

## v1.2.0

_8 de setembro de 2022_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg)<!-- Issue BOLT-341 --> Versão de disponibilidade geral—[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) O agora é compatível com o Adobe Commerce versões 2.4.5.

![Novo](../assets/new.svg)<!-- Issue BOLT-328 --> [!DNL Quick Checkout] para Adobe Commerce e Magento Open Source fornece uma [Exibição do painel do administrador](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) com todas as informações necessárias para configurar e usar a extensão.

![Novo](../assets/new.svg)<!-- Issue BOLT-364 --> Um usuário administrador [pode configurar funções e permissões de usuário](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/user-roles-setup.html) para permitir que outros usuários visualizem a [!DNL Quick Checkout] Painel de administração.

![Novo](../assets/new.svg)<!-- Issue BOLT-377 --> [!DNL Quick Checkout] O painel Admin agora contém um cabeçalho de página que inclui seções específicas, como **Visão geral**, **Relatórios**, e **Configurações**.

![Novo](../assets/new.svg)<!-- Issue BOLT-379 --> Quando um novo comerciante acessa o [!DNL Quick Checkout] Painel de administração pela primeira vez, um widget de boas-vindas é exibido e fornece um tour de recursos.

![Novo](../assets/new.svg)<!-- Issue BOLT-378 --> [!DNL Quick Checkout] [Exibição do painel do administrador](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) incorpora um **Configuração** que aparece quando a API e as chaves publicáveis não são fornecidas na variável [Configurações](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) exibição.

![Novo](../assets/new.svg)<!-- Issue BOLT-380 --> [!DNL Quick Checkout] [Exibição do painel do administrador](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) incorpora um **Recursos** que muda dependendo do estágio de integração.

![Novo](../assets/new.svg)<!-- Issue BOLT-381 --> [!DNL Quick Checkout] [Exibição do painel do administrador](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) inclui um **Ajuda e suporte** seção.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-369 --> A variável [[!DNL Quick Checkout] Painel de administração](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) O agora exibe a versão da extensão no rodapé.

## v1.1.0

_12 de agosto de 2022_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-375 --> Melhorias na experiência do usuário no [[!DNL Quick Checkout] Painel de administração](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) Agora, inclua apenas os parâmetros que estão visíveis e validados quando a extensão estiver ativada.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-349 --> Melhorias de compatibilidade para endereços de envio existentes com a Bolt wallet.

## v1.0.0

_9 de agosto de 2022_

[!BADGE Compatibilidade]{type=Informative tooltip="Compatibilidade"}

![Novo](../assets/new.svg)<!-- Issue BOLT-341 --> Versão de disponibilidade geral—[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) O agora é compatível com as versões 2.4.1 a 2.4.4 do Adobe Commerce.

![Novo](../assets/new.svg)<!-- Issue BOLT-340 --> A variável [!DNL Quick Checkout] para Adobe Commerce pode ser instalado para Adobe Commerce [na infraestrutura em nuvem](install.md#adobe-commerce-on-cloud-infrastructure) ou [no local](install.md#on-premises) instâncias. Esses métodos exigem o uso de uma interface de linha de comando.

![Novo](../assets/new.svg)<!-- Issue BOLT-1 --> A variável [!DNL Quick Checkout] O para Adobe Commerce traz uma vitrine otimizada que permite uma [experiência de check-out com um clique](overview.md) sem campos de preenchimento obrigatórios para os consumidores.

![Novo](../assets/new.svg)<!-- Issue BOLT-1 --> A variável [!DNL Quick Checkout] para Adobe Commerce reconhece automaticamente cada comprador em sua rede para [compras com um clique](checkout-flow.md) diretamente no seu site.

![Novo](../assets/new.svg)<!-- Issue BOLT-1 --> A variável [!DNL Quick Checkout] para Adobe Commerce permite que um comprador seja simultaneamente [conectado em redes Adobe Commerce e Bolt](checkout-flow.md/#quick-checkout-use-cases) para proporcionar uma melhor `one-click checkout` experiência.

![Novo](../assets/new.svg)<!-- Issue BOLT-218 --> [!DNL Quick Checkout] O para Adobe Commerce suporta uma [conta de sandbox](testing.md#testing-in-sandbox) que permite aos comerciantes avaliar a extensão no modo de teste.

![Novo](../assets/new.svg)<!-- Issue BOLT-780 --> Seus compradores podem fazer check-out por meio da [[!DNL Quick Checkout]](checkout-page.md) ou por meio de uma [criação manual de ordem](create-order-admin.md).

![Novo](../assets/new.svg)<!-- Issue BOLT-666 --> Os comerciantes podem configurar o [!DNL Quick Checkout] com ações básicas de pagamento, como [`Authorize and Capture` ou `Authorize` ](onboarding.md#complete-admin-configuration)ou alternando entre ambientes de sandbox e produção.

![Novo](../assets/new.svg)<!-- Issue BOLT-288 --> Personalizado [tempo de vida da sessão do usuário](user-session-lifetime.md) para [!DNL Quick Checkout] para Adobe Commerce.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-375 --> Melhorias na experiência do usuário no [[!DNL Quick Checkout] Painel de administração](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) O permite salvar a configuração quando todos os parâmetros necessários forem fornecidos.

![Problema conhecido](../assets/bug.svg)<!-- Issue BOLT-342 --> Comum [solução de problemas](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) problemas durante a instalação do [!DNL Quick Checkout].
