---
title: "[!DNL Payment Services] Notas de versão"
description: Revise as notas de versão para obter informações sobre tudo [!DNL Payment Services] versões.
exl-id: 104aa2c7-7735-4ac2-8ed1-a03cd9911273
feature: Payments, Release Notes
source-git-commit: 9b4ce379728b126390177d64c10d57b2c587619c
workflow-type: tm+mt
source-wordcount: '2502'
ht-degree: 0%

---

# Notas de versão

Estas notas de versão descrevem a versão inicial do [!DNL Payment Services] e incluem:

![Novo](../assets/new.svg) Novos recursos
![Problema corrigido](../assets/fix.svg) Correções e aprimoramentos
![Problema conhecido](../assets/bug.svg) Problemas conhecidos

Para alterações e correções de recursos lançadas fora da versão normal do, revise o _Atualizações do serviço hospedado_ seções.

Saiba mais sobre as próximas versões do, o suporte ao produto e quais versões do Adobe Commerce oferecem suporte ao [!DNL Payment Services] extensão, consulte a seção Adobe Commerce [Programação de lançamento](https://experienceleague.adobe.com/en/docs/commerce-operations/release/planning/schedule) e [Disponibilidade do produto](https://experienceleague.adobe.com/en/docs/commerce-operations/release/product-availability) tópicos.

## Atualizações do serviço hospedado

Essas notas de versão descrevem alterações e correções de recursos que ocorreram e foram lançadas fora das versões de recursos regulares do serviço hospedado.

+++Atualizações do serviço hospedado

_5 de março de 2024_

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-5252 --> Agora, os comerciantes podem copiar dados das grades do Painel selecionando o conteúdo de uma única célula.

_10 de outubro de 2023_

![Novo problema](../assets/fix.svg)<!-- Issue PAY-4888 --> Agora, os comerciantes podem filtrar as transações com cartão de crédito e débito pelos últimos quatro dígitos do número do cartão na [Relatório de transações](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html).

_12 de julho de 2023_

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-4587 --> Um problema introduzido no [!DNL Payment Services] A versão 2.1.0 que impedia que as anulações de autorização colocadas por versões anteriores da extensão agora é resolvida. Comerciantes que usam qualquer versão do [!DNL Payment Services] pode anular autorizações.

_9 de junho de 2023_

![Novo](../assets/new.svg)<!-- Issue PAY-4288 --> Agora, os comerciantes podem [configurar _somente_ Botões de pagamento do PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#use-only-paypal-payment-buttons)—e _não_ use a opção de pagamento com cartão de crédito do PayPal. Isso permite que os comerciantes forneçam várias opções de pagamento, incluindo os botões de pagamento Venmo e PayPal, e usem um fornecedor de cartão de crédito existente em vez da opção de pagamento com cartão de crédito PayPal.

![Novo](../assets/new.svg)<!-- Issue PAY-4050 --> Adição de um [visualização de visualização de dados](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#order-payment-status-data-visualization-view), que aparece na Página Inicial do Serviço de Pagamento, para o relatório Status do pagamento da ordem.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-4486--> Anteriormente, o botão PayPal PayLater não aparecia no checkout para comerciantes do Reino Unido. Esse problema está resolvido.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-4485--> As visualizações de dados de relatório agora aparecem em [!DNL Payment Services] Início quando[!DNL Payment Services] está desativado.

_25 de janeiro de 2023_

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-4102 --> Novas instalações de [!DNL Payment Services] não podem configurar os Serviços da Commerce, renderizando [!DNL Payment Services] inoperante. Para corrigir esse problema, atualize o [!DNL Payment Services] extensão para a versão 1.5.3.

_12 de setembro de 2022_

![Novo](../assets/new.svg)<!-- Issue PAY-3705 --> A variável `increment_id` O agora está disponível para uso na reconciliação de pagamentos em sistemas ERP externos. Ele é propagado para a variável [`custom_id` _e_ `invoice_id`](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/data.html#reconcile-with-erp-system), visíveis no webhook do PayPal e nos detalhes de atividade do comerciante para um pagamento.

_31 de agosto de 2022_

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3629 --> Quando um novo comerciante acessa o [!DNL Payment Services] Página inicial pela primeira vez, a página agora é carregada imediatamente para exibir o conteúdo em vez de exigir uma atualização da página.

_9 de agosto de 2021_

![Novo](../assets/new.svg)<!-- Issue PAY-3420 --> O Apple Pay agora está disponível como um botão inteligente do PayPal. Este [opção de pagamento](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-options.html#apple-pay-button) O permite que os clientes usem o recurso Touch ID no dispositivo iOS ou macOS para selecionar o Apple Pay. O Apple Pay processa o pagamento usando as credenciais de pagamento de cartão de crédito e débito armazenadas no dispositivo.

_28 de junho de 2021_

![Novo](../assets/new.svg)<!-- Issue PAY-1720 --> Contestações para ordens de armazenamento agora estão disponíveis em [o relatório Order payment status](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#view-disputes). Você pode resolver disputas navegando diretamente para o Centro de Resolução do PayPal a partir de [!DNL Payment Services].

![Novo](../assets/new.svg)<!-- Issue PAY-2854 --> Melhorias na experiência do usuário do [!DNL Payment Services] Página inicial inclui a capacidade de modificar uma configuração no nível de herança atual e melhorias na exibição do cabeçalho e da navegação.

![Novo](../assets/new.svg)<!-- Issue PAY-2854 --> Agora você pode ver avisos ao alternar do modo de sandbox para o modo de produção e ao tentar sair de uma exibição com atualizações que não foram salvas.

![Novo](../assets/new.svg)<!-- Issue PAY-2761 --> Agora é possível personalizar os dados exibidos na variável [Relatório de status do pagamento da ordem](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html#show-and-hide-columns) e a variável [Relatório de pagamentos](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/payouts.html#show-and-hide-columns) mostrando ou ocultando colunas usando o controle Configurações de coluna.

+++

## v2.6.0

_4 de junho de 2024_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- PAY-4877 --> Agora, [!DNL Payment Services] suporta [Recursos de preços N2/N3](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/levels-card-payment-transactions.html). Este recurso só está disponível para [!DNL Payment Services] clientes com preços IC++ ativados. Se quiser usar dados de processamento L2/L3 para [!DNL Payment Services], entre em contato com [!DNL Payment Services] gerente de conta.

![Correção](../assets/fix.svg)<!-- PAY-5455 -->[!DNL Payment Services] permite ativar o Apple Pay diretamente da extensão sem baixar e hospedar o [arquivo de associação de domínio](https://developer.paypal.com/docs/checkout/apm/apple-pay/#register-your-live-domain).

## v2.5.0

_23 de abril de 2024_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg)<!-- Issue PAY-5396 -->[!DNL Payment Services] O agora suporta [Diretrizes do Adobe Commerce para o `--db-prefix` parâmetro](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/advanced#install-from-the-command-line) para Adobe Commerce versões 2.4.7 e mais recentes.

## v2.4.3

_16 de abril de 2024_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg)<!-- Issue PAY-5106 --> Correção de um problema que preenchia incorretamente os totais do valor do pedido durante o checkout entre o PayPal e o Adobe Commerce. Agora, os comerciantes podem garantir que os totais do valor do pedido estejam corretos ao fazer um pedido.

## v2.4.2

_11 de abril de 2024_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- Issue xxx --> Adição de suporte para o Adobe Commerce 2.4.7.

## v2.4.1

_4 de abril de 2024_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg)<!-- PAY-5322 --> Correção de um problema de compatibilidade de PCI com versões mais recentes da Adobe Commerce. Agora, [!DNL Payment Services] O é adaptado aos requisitos de finalização de compra no Adobe Commerce como a opção de pagamento.

![Correção](../assets/fix.svg)<!-- PAY-5323 --> PayLater e Venmo são exibidos corretamente no Adobe Commerce. Correção de um erro que impedia o Administrador de mostrar as opções de alternância PayLater e Venmo.

## v2.4.0

_20 de março de 2024_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- PAY-4868 --> Os comerciantes podem [configurar o Google Pay durante toda a experiência de compra](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html), semelhante a outros botões de pagamento no[!DNL Payment Services] por meio do Administrador.

![Novo](../assets/new.svg)<!-- PAY-4381 --> [Os Serviços de pagamento oferecem suporte ao Google Pay por meio do GraphQL](https://developer.adobe.com/commerce/webapi/graphql/payment-services/) permitindo que os comerciantes tenham uma experiência headless no Commerce com o método de pagamento Google Pay.

![Novo](../assets/new.svg)<!-- PAY-4878 --> Agora, a variável [!DNL Payment Services] o recurso básico de check-out é fornecido para os comerciantes de Adobe Commerce e Magento Open Source.[!DNL Payment Services] O agora oferece suporte a comerciantes com empresas em qualquer uma das 200 regiões do mundo.[!DNL Payment Services] o check-out básico fornece opções de débito/crédito, PayPal, Venmo (quando disponível) e PayLater (quando disponível) em uma integração de autoatendimento.

![Correção](../assets/fix.svg)<!-- PAY-5291 --> O recebimento da confirmação de pagamento para algumas transações pode estar atrasado. Nesse caso, agora os comerciantes podem obter um status de pagamento atualizado para um pedido. [Os serviços de pagamento detectam o status pendente de uma transação de pagamento](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/order-payment-status.html) em um pedido, detectando transações pendentes e monitorando proativamente essas transações e atualizando quando o status pendente foi capturado.

## v2.3.4

_1 de março de 2024_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- PAY-5244 --> Correção da compatibilidade de check-out assíncrono.

![Correção](../assets/fix.svg)<!-- PAY-5253 --> Correção de um erro em que um token do Vault não pertencente a [!DNL Payment Services] não pôde ser excluído.

## v2.3.3

_14 de fevereiro de 2024_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- PAY-5048 --> Suporte adicionado para PHP 8.3

![Correção](../assets/fix.svg)<!-- PAY-5048 --> Correção de um erro com o `is_deleted` sinalizador. Agora, os pedidos não falham devido à `Rejected` Status de enviado da extensão.

## v2.3.2

_26 de janeiro de 2024_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg)<!-- PAY-5183 --> Correção de problemas de desempenho REST/GraphQL. Agora, o botão de cartão de crédito é renderizado quando buscado pela API.

## v2.3.1

_7 de dezembro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- PAY-5047 --> A marca do cartão de crédito/débito ou o tipo de método de pagamento agora está disponível nos seguintes locais:
- a página de pedido do cliente na loja
- o email de confirmação do pedido enviado ao comprador
- do [exibição dos detalhes do pedido](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/order-management/orders/order-processing.html#view-an-order) no Administrador do Commerce.

## v2.3.0

_1 de dezembro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- PAY-4381 --> [Os serviços de pagamento agora oferecem suporte à integração com o GraphQL](https://developer.adobe.com/commerce/webapi/graphql/payment-services/). Com suporte da GraphQL para botões de pagamento do PayPal, campos hospedados e Apple Pay,[!DNL Payment Services] O agora é compatível com uma configuração do Commerce headless.

## v2.2.1

_27 de setembro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-4870 --> Correção de um problema que preenchia incorretamente o novo atributo de cabeçalho na Loja ao enviar a versão da extensão com a versão mais recente. Anteriormente, com o `1.3.0` do conector Commerce Services, não foi possível estender o `User-Agent header` do [!DNL Payment Services] extensão.

## v2.2.0

_30 de agosto de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- PAY-4638 --> Adição de um [integração com Signifyd](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/security-compliance/fraud-protection.html), que fornece serviços automatizados de proteção contra fraudes.

![Novo](../assets/new.svg)<!-- PAY-3981 --> [Apple Pay promovido para uma opção de pagamento separada](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html?lang=en#apple-pay-button), fora dos botões de pagamento do PayPal, para aumentar a visibilidade do comprador da opção de pagamento e permitir que os comerciantes controlem a disposição e o estilo do Apple Pay.

![Novo](../assets/new.svg)<!-- PAY-4002 --> Melhoria na experiência do usuário de checkout de campos de cartão de crédito, incluindo aprimoramentos de estilo, como adicionar ícones de pagamento, para reduzir a carga cognitiva do comprador e aumentar as conversões.

![Novo](../assets/new.svg)<!-- PAY-4002 --> Adição da funcionalidade para permitir que os comerciantes [classificar a ordem de suas opções de pagamento](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#payment-buttons) para priorizar determinadas opções de pagamento. Essa funcionalidade incentiva uma taxa de conversa de check-out mais alta.

![Novo](../assets/new.svg)<!-- PAY-4035 --> Agora, os comerciantes podem monitorar com eficiência a integridade de suas lojas e identificar quaisquer problemas de transação usando o novo [Relatório de transações](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/reporting/transactions.html) disponível no[!DNL Payment Services] Página inicial do administrador. O relatório também apresenta dados sobre taxas de autorização de transações e tendências de transações negativas.

## v2.1.0

_9 de junho de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- Issue xxx --> Adição de suporte para o Adobe Commerce 2.4.7-beta1.

![Novo](../assets/new.svg)<!-- Issue xxx --> Adicionado [disponibilidade nos seguintes países e moedas associadas](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#availability): Austrália, França, Reino Unido.

![Novo](../assets/new.svg)<!-- Issue PAY-4296 --> Adicionado [recursos expandidos para funções de Administrador](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-roles) para garantir que os usuários administradores possam criar e gerenciar pedidos para clientes e possam visualizar[!DNL Payment Services] no menu Vendas.

![Novo](../assets/new.svg)<!-- Issue PAY-4236 --> Adicionado [anulação automática para pedidos que incorrem em erros durante a finalização da compra](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/checkout.html#order-auto-voided-if-error).

![Novo](../assets/new.svg)<!-- Issue PAY-4183 --> Funcionalidade criada para [mostrar o botão de opção de pagamento de cartão de crédito/débito](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#debit-or-credit-card-button) na página de check-out.

## v2.0.0

_10 de março de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- Issue PAY-4152 --> Suporte adicionado para PHP 8.2 e Adobe Commerce 2.4.6. Não compatível com PHP 7.x.

## v1.6.1

_10 de março de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg)<!-- Issue PAY-4226 --> Correção de um problema que impedia novas [!DNL Payment Services] comerciantes usem o check-out na Admin.[!DNL Payment Services] A estava usando anteriormente a ID de cliente da Commerce, que não existe para novos clientes.

![Correção](../assets/fix.svg)<!-- Issue PAY-4205 --> Correção de um problema que fazia com que o estado do endereço de entrega especificado fosse substituído pelo estado nas configurações de imposto padrão durante a finalização da compra usando o [Opção do PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/payments-options.html#paypal-smart-buttons). Agora, os clientes podem ter seus pedidos entregues em um estado diferente daquele configurado como padrão nas configurações de imposto do comerciante.

![Correção](../assets/fix.svg)<!-- Issue PAY-4202 --> Correção de um problema que impedia os clientes de usar a compartimentalização de cartão para concluir uma compra ou excluir um método de pagamento com cofre de uma loja [usando o `Authorize and Capture` ação de pagamento](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/get-started/production.html#set-payment-services-as-payment-method). Anteriormente, um erro &quot;ID do Provider Vault não encontrada&quot; aparecia quando o cliente tentava usar ou modificar seus cartões de crédito com cofre.

## v1.6.0

_17 de fevereiro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- Issue PAY-3540 --> Adicionado [Recurso de conformidade PCI 3DS para comerciantes que fazem transações na União Europeia (UE) e na Grã-Bretanha](security.md#3ds). Esse nível adicional de segurança, que exige que os compradores se autentiquem junto ao emissor do cartão de crédito, ajuda a evitar fraudes on-line e é exigido como parte das regulamentações de conformidade da União Europeia (UE).

![Novo](../assets/new.svg)<!-- Issue PAY-3609 --> Adicionada a capacidade de [Ativar a compartimentalização de cartão no Administrador](vaulting.md#use-vaulting-in-the-admin). Isso permite que os comerciantes criem um pedido para clientes no Administrador usando seus métodos de pagamento com cofre.

## v1.5.4

_29 de janeiro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-4110 --> Correção de um problema que impedia os compradores de fazer um pedido usando botões de pagamento na página do produto, minicarrinho e carrinho. Os compradores agora podem concluir os pedidos com sucesso.

## v1.5.3

_25 de janeiro de 2023_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-4102 --> Liberação de uma correção para um problema conhecido incompatível com versões anteriores. Essa versão bloqueia a versão da extensão de ID de serviço para a versão estável mais recente, o que reativa as novas [!DNL Payment Services] instalações para configurar os Serviços da Commerce.

## v1.5.2

_22 de dezembro de 2022_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3992 --> Faturamento aprimorado no [!DNL Payment Services] quando um método de pagamento é recusado.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3999 -->[!DNL Payment Services] agora exibe corretamente os botões de pagamento do PayPal para comerciantes que usam [Acionar o Checkout](https://commercemarketplace.adobe.com/swissup-firecheckout.html){target=_blank} modelo personalizado para a página de check-out. Anteriormente, a minicart exibia intermitentemente os botões.

## v1.5.1

_23 de novembro de 2022_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- Issue PAY-3923 -->[!DNL Payment Services] agora inclui o número da versão no cabeçalho do agente do usuário para que as solicitações possam rastrear, filtrar ou descontinuar pontos de extremidade não utilizados.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3968 -->[!DNL Payment Services] O agora exibe corretamente os dados do pedido quando um pedido é feito na página do produto usando os botões de pagamento.

## v1.5.0

_18 de novembro de 2022_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- Issue PAY-3880 --> Um comprador pode agora [guardar (salvar) as informações de cartão de crédito durante a finalização da compra](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html) para usar em uma compra posterior para a mesma loja ou outra loja na mesma conta de comerciante.

![Novo](../assets/new.svg)<!-- Issue PAY-3950 --> Os comerciantes agora podem ativar o [Recurso de compra instantânea do Commerce](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/checkout-instant-purchase.html) para que os compradores possam (utilizar [informações de cartão de crédito com cofre](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/payments-checkout/vaulting.html)) para agilizar o check-out.

## v1.4.1

_14 de outubro de 2022_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Correção](../assets/fix.svg)<!-- Issue PAY-3766 --> Quando o método de pagamento de um cliente é recusado, a mensagem de erro visível é mais descritiva. Ele aconselha o cliente a inserir novamente as informações de pagamento e tentar novamente, tentar outro método de pagamento ou entrar em contato com o banco sobre a transação recusada.

## v1.4.0

_30 de setembro de 2022_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- Issue PAY-784 -->[!DNL Payment Services] agora inclui a capacidade de configurar uma conta de comerciante para [usar várias contas comerciais do PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#use-multiple-paypal-accounts). Isso permite que o comerciante opere suas lojas em vários países usando moedas diferentes ou use o Adobe Commerce para uma parte da sua empresa.

![Novo](../assets/new.svg)<!-- Issue PAY-3231 --> Os comerciantes podem [adicionar um [!UICONTROL Soft Descriptor]](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#add-soft-descriptor) para configurações de sites ou exibições de loja individuais que são mostradas nos extratos bancários de transação do cliente para definir marcas, lojas ou linhas de produtos.

![Novo](../assets/new.svg)<!-- Issue PAY-3707 --> [Ativar ou desativar campos de cartão de crédito e botões de pagamento do PayPal](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/configure/settings.html#configure-payment-options) para check-out em[!DNL Payment Services] configurações.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3546 --> Quando um cliente clica em **[!UICONTROL Edit cart]**, a página redireciona para a página do carrinho e mostra os itens atualizados em vez de mostrar um carrinho vazio.

## v1.3.1

_6 de setembro de 2022_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3663 --> Agora, quando a loja de um comerciante está capturando um pedido autorizado com uma moeda não global, o processo de captura é concluído e nenhum erro é exibido.

## v1.3.0

_9 de agosto de 2022_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- Issue PAY-XX --> Versão de disponibilidade geral—[!DNL Payment Services] agora é [com suporte do [!DNL Adobe Commerce] e [!DNL Magento Open Source] versões 2.4.0 a 2.4.5](https://devdocs.magento.com/release/availability.html#compatibility).

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-x --> O Apple Pay agora é compatível com o navegador Safari v15.5 em dispositivos móveis e desktop.

## v1.2.0

_29 de junho de 2022_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-x --> O Apple Pay é incompatível com o navegador Safari v15.5 no celular e no desktop. Ao usar o Safari versão 15.5, não é possível concluir o check-out com o Apple Pay.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3264 --> Anteriormente, quando um usuário conectado selecionava um endereço de faturamento/envio diferente do endereço padrão para sua conta, o check-out falhava. Agora, o endereço de cobrança/entrega selecionado é enviado (em vez do endereço salvo padrão) e o check-out é concluído com êxito.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3314 --> Se você desativar os botões de pagamento do PayPal para check-out, nenhum erro será exibido.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3330 --> Os pagamentos não falham mais durante o check-out quando um usuário convidado insere um número de telefone que inclui traços.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3338 PAY-2502 --> Quando as credenciais dos Serviços da Commerce forem inválidas,[!DNL Payment Services] O agora o alerta exibindo um erro de credenciais do [!DNL Payment Services] Página inicial do Administrador.

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-0 --> [!DNL Payment Services] é incompatível com `commerce-data-export` v101.20 e superior, o que a torna incompatível com o [[!DNL Channel manager] extensão](https://experienceleague.adobe.com/docs/commerce-channels/channel-manager/guide-overview.html).

## v1.1.0

_31 de março de 2022_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- Issue PAY-2127 --> Versão de disponibilidade geral—[!DNL Payment Services] agora é [com suporte do [!DNL Adobe Commerce] e [!DNL Magento Open Source] versões 2.4.0 a 2.4.4](https://devdocs.magento.com/release/availability.html#compatibility).

![Novo](../assets/new.svg)<!-- Issue PAY-2682 --> A variável [!DNL Payment Services] extensão para [!DNL Adobe Commerce] e [!DNL Magento Open Source] O agora está disponível para comerciantes canadenses. Os comerciantes podem exibir a configuração de pagamentos em [Francês](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html?lang=fr#carte-de-cr%C3%A9dit-et-devises-accept%C3%A9es) ou [Inglês](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html#accepted-credit-cards-and-currencies).

![Novo](../assets/new.svg)<!-- Issue PAY-2681 --> [!DNL Payment Services] suporta [Dólares canadenses (CAD)](overview.md#accepted-credit-cards-and-currencies) para cartões de crédito e transações do PayPal.

![Novo](../assets/new.svg)<!-- Issue PAY-2680 --> Os comerciantes podem [integrado [!DNL Payment Services]](onboard.md) extensão em inglês ou francês.

![Novo](../assets/new.svg)<!-- Issue PAY-2678 --> Os comerciantes agora podem exibir relatórios financeiros, tanto o [Status do pagamento da ordem](order-payment-status.md) e [Relatórios de pagamentos](payouts.md), em dólares canadenses (CAD).

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-2710 -->[!DNL Payment Services] agora é compatível com [PHP 8.1](https://www.php.net/releases/8.1/en.php).

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-3017 --> Melhoria do alerta do modo de sandbox para exibir alertas adequados com vários armazenamentos.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-2742 --> Agora é possível ativar e desativar os métodos de pagamento disponíveis, como Venmo, no nível de exibição da loja. Anteriormente, só era possível configurar métodos de pagamento por site.

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-2277 --> Agora você pode selecionar [ativar ou desativar botões de pagamento individuais do PayPal](settings.md#payment-buttons).

![Problema corrigido](../assets/fix.svg)<!-- Issue PAY-2561 --> Os produtos removidos anteriormente não aparecem no carrinho do _Revisar pedido_ página.

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-2842 --> Testar transações de cartão de crédito [pode falhar com o PayPal](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-cc-sandbox-failure.html) ao processar pagamentos em um ambiente de sandbox.

## v1.0.0

_29 de novembro de 2021_

[!BADGE Compatível]{type=Informative tooltip="Compatível"}

![Novo](../assets/new.svg)<!-- Issue PAY-2127 --> Versão de disponibilidade geral—[[!DNL Payment Services]](https://commercemarketplace.adobe.com/magento-payment-services.html) agora é compatível com o [!DNL Adobe Commerce] e [!DNL Magento Open Source] versões 2.4.0 a 2.4.3-p1.

![Novo](../assets/new.svg)<!-- Issue PAY-124 --> A variável [!DNL Payment Services] extensão para [!DNL Adobe Commerce] e [!DNL Magento Open Source] pode ser instalado para [[!DNL Adobe Commerce] na infraestrutura em nuvem](install.md#adobe-commerce-on-cloud-infrastructure) ou [No local](install.md#on-premises) instâncias. Esses métodos exigem o uso de uma interface de linha de comando.

![Novo](../assets/new.svg)<!-- Issue PAY-1986 --> [!DNL Payment Services] suporta uma [conta de sandbox](sandbox.md) que permite aos comerciantes avaliar a extensão no modo de teste.

![Novo](../assets/new.svg)<!-- Issue PAY-666 --> Os comerciantes podem [configurar os Serviços de pagamento](settings.md) extensão com comportamentos básicos de pagamento, como utilizar [`Authorize and Capture`](production.md#set-payment-services-as-payment-method) alternar entre ambientes de sandbox ou produção.

![Novo](../assets/new.svg)<!-- Issue PAY-780 --> Seus compradores podem fazer check-out com [!DNL Payment Services] ou via [criação manual de ordem](create-order.md).

![Novo](../assets/new.svg)<!-- Issue PAY-1856 --> Relatórios abrangentes, via [Status do pagamento da ordem](order-payment-status.md) e [Relatórios de pagamentos](payouts.md), estão disponíveis para [!DNL Payment Services] para dar a você uma visão clara dos pedidos da loja e dos pagamentos relacionados.

![Novo](../assets/new.svg)<!-- Issue PAY-311 --> [!DNL Payment Services] O oferece preços hierárquicos flexíveis, com base no volume total de processamento, adaptados a qualquer comerciante.

![Novo](../assets/new.svg)<!-- Issue PAY-1443 --> Você pode [personalizar a aparência](payments-options.md) de botões de pagamento PayPal e campos de cartão de crédito para o [!DNL Payment Services] extensão.

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-2473 --> Usar [chaves do Composer incorretas](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-install.html) durante a instalação da extensão impede que o usuário [autenticação](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/connect-auth.html) com o correto `MAGEID`.

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-2474 --> [!DNL Payment Services] relatórios [pode não sincronizar imediatamente](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-report-info-delayed.html).

![Problema conhecido](../assets/bug.svg)<!-- Issue PAY-2475 --> Seu [Conta de sandbox do PayPal](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/payments/payservices-paypal-acct.html) para [!DNL Payment Services] não pode ser verificado se você criar essa conta durante a integração.
