---
title: '[!DNL Quick Checkout] Notas de versão'
description: Revise as notas de versão para obter informações sobre todas as [!DNL Quick Checkout] versões.
exl-id: 511be2fc-d24d-4323-a47a-d376e38a5c47
source-git-commit: 66082614ffe6456e2c24a1e8d9baaa1113fb7ffb
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 0%

---

# Notas de versão

Essas notas de versão descrevem a versão inicial do [!DNL Quick Checkout] e incluem:

![Novo](../assets/new.svg) Novos recursos
![Problema corrigido](../assets/fix.svg) Correções e melhorias
![Problema conhecido](../assets/bug.svg) Problemas conhecidos

Consulte [Próximas versões](https://devdocs.magento.com/release/) para saber mais sobre os cronogramas de lançamento e suporte.

Consulte [Disponibilidade](https://devdocs.magento.com/release/availability.html) na documentação do desenvolvedor para saber mais sobre compatibilidade de produtos.

## Atualizações do painel de administração

Essas notas de versão descrevem as alterações de recursos e correções que ocorreram e foram lançadas fora das versões regulares de recursos com versão para o painel Administrador.

+++Atualizações no painel de administração

_14 de dezembro de 2022_

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-524 --> O [!DNL Quick Checkout] O painel de administração agora mostra o total correto de pedidos e as informações atualizadas dos relatórios.

_30 de novembro de 2022_

![Novo](../assets/new.svg)<!-- Issue BOLT-502 --> Agora, o [relatórios](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) tem uma nova predefinição &quot;Ano passado&quot;.

![Novo](../assets/new.svg)<!-- Issue BOLT-471 --> Melhorias na experiência do usuário na [!DNL Quick Checkout] O painel de administração mostra mais informações em [Dicas de ferramentas](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html).

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-514 --> Melhorias na experiência do usuário na [!DNL Quick Checkout] O painel de administração mostra os números totais corretos dos pedidos, a consistência em cores e as legendas corretas para todos os gráficos.

_2 de novembro de 2022_

![Novo](../assets/new.svg)<!-- Issue BOLT-293 --> Agora, o [relatórios](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) na guia no [!DNL Quick Checkout] O painel de administração mostra gráficos e informações de relatório das estatísticas de experiência de check-out da sua loja.

![Novo](../assets/new.svg)<!-- Issue BOLT-422 --> O [_Visão geral_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-overview) A seção do tópico Relatórios mostra informações detalhadas sobre o desempenho de check-out da sua loja, incluindo o tempo médio de check-out, novas contas criadas durante o check-out e o abandono do check-out.

![Novo](../assets/new.svg)<!-- Issue BOLT-423 --> O [_Tendências_](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#reports-trends) A seção da guia Relatórios mostra suas tendências de experiência de check-out filtradas por tipo de conta e novas contas criadas durante o check-out.

![Novo](../assets/new.svg)<!-- Issue BOLT-439 --> O **Relatórios** exibições de guia [predefinições de filtro padrão](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html#filter-data) que podem ser usados para mostrar intervalos de dados específicos.

![Novo](../assets/new.svg)<!-- Issue BOLT-433 --> Agora você pode ver um _Nenhum dado disponível_ aviso para um gráfico quando uma solicitação não retorna dados.

![Novo](../assets/new.svg)<!-- Issue BOLT-473 --> Melhorias na experiência do usuário na [!DNL Quick Checkout] O painel de administração inclui a capacidade de ativar um [rastreamento de checkout](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) configuração que permite que o Adobe Commerce compartilhe informações de relatórios com Bolt.

_5 de outubro de 2022_

![Novo](../assets/new.svg)<!-- Issue BOLT-379 --> Agora, quando um novo comerciante acessa o [!DNL Quick Checkout] Painel de administração pela primeira vez em [tour de recursos com Gainsight](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) é exibido.

![Novo](../assets/new.svg)<!-- Issue BOLT-377 --> O **Relatórios** na guia no [!DNL Quick Checkout] O painel de administração mostra gráficos e análises de relatórios.

![Novo](../assets/new.svg)<!-- Issue BOLT-377 --> O **Relatórios** na guia no [!DNL Quick Checkout] O painel de administração mostra o intervalo de datas e as predefinições de filtro para gráficos e análises de relatórios.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-369 --> Agora, o [[!DNL Quick Checkout] Painel de administração](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) exibe a versão do aplicativo no rodapé.

+++

## v1.6.0

_9 de fevereiro de 2023_

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-567 --> Melhorias na experiência do usuário ao [fazendo um pedido](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) usando o [Entrega na loja](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/delivery/basic-methods/shipping-in-store-delivery.html) com o método [!DNL Quick Checkout] desativado.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-569 --> Melhorias na funcionalidade de logout que permitem aos compradores [logout da rede Bolt](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/user-session-lifetime.html).

## v1.5.0

_18 de janeiro de 2023_

![Novo](../assets/new.svg)<!-- Issue BOLT-522 --> Uma nova configuração pode ser ativada/desabilitada para detectar se [compradores](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/manage-checkout/checkout-options/checkout-adobe-commerce.html) pode ser conectado automaticamente no Bolt.

![Novo](../assets/new.svg)<!-- Issue BOLT-523 --> Uma nova configuração pode ser ativada/desativada, permitindo que os comerciantes especifiquem se os compradores podem fazer logon automaticamente em ambas as redes ou apenas Bolt network.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-542 --> Melhorias na experiência do usuário ao [salvar cartão ou endereço em uma conta Bolt](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html) quando um comprador fornece email.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-550 --> Melhorias na experiência do usuário em [logon automático](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#configure-service-settings) quando um usuário Bolt fornece email.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-544 --> Aprimoramentos de compatibilidade para [URLs de retorno de chamada](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#check-shopper-valid-account) com [vários sites](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/multi-sites/ms-overview.html) em Bolt.

## v1.4.0

_30 de novembro de 2022_

![Novo](../assets/new.svg)<!-- Issue BOLT-513 --> Agora, quando um cliente do Adobe Commerce está conectado à loja durante o processo de finalização e tem uma conta Bolt, uma opção para fazer logon na conta Bolt do comprador é exibida.

![Novo](../assets/new.svg)<!-- Issue BOLT-512 --> Uma nova configuração detecta automaticamente se os compradores conectados também podem ser conectados no Bolt.

![Novo](../assets/new.svg)<!-- Issue BOLT-480 --> Uma nova configuração no [!DNL Quick Checkout] O Painel de administração permite que você altere o fluxo de navegação padrão para a variável **Envio** assim que um cliente Bolt fizer logon. Por padrão, ele é configurado para **Pagamentos** página.

## v1.3.0

_2 de novembro de 2022_

![Novo](../assets/new.svg)<!-- Issue BOLT-293 --> Agora, [!DNL Quick Checkout] inclui a capacidade de ativar uma [rastreamento de checkout](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/settings-quick-checkout.html#service-settings) configuração que permite que o Adobe Commerce compartilhe informações de relatórios com Bolt.

![Novo](../assets/new.svg)<!-- Issue BOLT-461 --> Agora você pode ver uma mensagem de aviso em [!DNL Quick Checkout] Painel de administração se [rastreamento de checkout](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-reporting/reports.html) está desativada.

## v1.2.0

_8 de setembro de 2022_

![Novo](../assets/new.svg)<!-- Issue BOLT-341 --> Versão geral de disponibilidade—[[!DNL Quick Checkout]](https://marketplace.magento.com/magento-quick-checkout.html) O agora é compatível com a versão 2.4.5 do Adobe Commerce.

![Novo](../assets/new.svg)<!-- Issue BOLT-328 --> [!DNL Quick Checkout] para Adobe Commerce e Magento Open Source fornece um [Exibição do painel de administração](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) com todas as informações necessárias para configurar e usar a extensão do .

![Novo](../assets/new.svg)<!-- Issue BOLT-364 --> Um usuário administrador [pode configurar funções e permissões de usuário](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/user-roles-setup.html) para permitir que outros usuários visualizem a variável [!DNL Quick Checkout] Painel de administração.

![Novo](../assets/new.svg)<!-- Issue BOLT-377 --> [!DNL Quick Checkout] O painel de administração agora contém um cabeçalho de página que inclui seções específicas, como **Visão geral**, **Relatórios** e **Configurações**.

![Novo](../assets/new.svg)<!-- Issue BOLT-379 --> Quando um novo comerciante acessa o [!DNL Quick Checkout] Painel de administração pela primeira vez em que um widget de Boas-vindas é exibido, que fornece um tour de recursos.

![Novo](../assets/new.svg)<!-- Issue BOLT-378 --> [!DNL Quick Checkout] [Exibição do painel de administração](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) incorpora um **Configuração** etapa exibida quando a API e as chaves publicáveis não são fornecidas na variável [Configurações](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) exibir.

![Novo](../assets/new.svg)<!-- Issue BOLT-380 --> [!DNL Quick Checkout] [Exibição do painel de administração](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) incorpora um **Recursos** que muda dependendo do estágio de integração.

![Novo](../assets/new.svg)<!-- Issue BOLT-381 --> [!DNL Quick Checkout] [Exibição do painel de administração](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/quick-checkout-admin-panel/admin-panel.html) inclui um **Ajuda e suporte** seção.

![Problema corrigido](../assets/fix.svg)<!-- Issue BOLT-369 --> O [[!DNL Quick Checkout] Painel de administração](https://experienceleague.adobe.com/docs/commerce-merchant-services/quick-checkout/getting-started/onboarding.html#enable-extension) agora exibe a versão da extensão no rodapé.

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

![Problema conhecido](../assets/bug.svg)<!-- Issue BOLT-342 --> Frequentes [solução de problemas](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/quick-checkout-issues.html) problemas durante a instalação de [!DNL Quick Checkout].
