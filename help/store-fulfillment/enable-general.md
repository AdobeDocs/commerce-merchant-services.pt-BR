---
title: Configuração geral
description: Definir configurações gerais para habilitar [!DNL Store Fulfillment] para sua loja. Defina as configurações de extensão global, as configurações do sistema para registro, sincronização de dados e segurança. Forneça os principais dados para habilitar a integração entre o Adobe Commerce e os serviços de Atendimento da loja.
role: User, Admin
level: Intermediate
exl-id: 51dcfc95-3dd6-40d9-bd26-d8409a25f3c8
source-git-commit: e7493618e00e28e2de5043ae2d7e05a81110d8f1
workflow-type: tm+mt
source-wordcount: '2440'
ht-degree: 0%

---

# Serviço de armazenamento e configuração de vendas

Configurar [!DNL Store Fulfillment] do [!DNL Commerce] Admin para habilitar a extensão, especificar configurações de extensão, definir as configurações de segurança para usuários do aplicativo Store Assist e definir opções para métodos de entrega.

>[!IMPORTANT]
>
>A configuração do serviço Store Fulfillment se aplica somente depois que você conecta a instância do Adobe Commerce e a [!DNL Store Fulfillment] aplicativo. Consulte [Conectar Atendimento da Loja](connect-set-up-service.md).

## Gerenciar configurações de Serviços de Atendimento da Loja

Gerenciar configurações para Serviços de Atendimento da Loja do [!DNL Commerce Admin Store Configuration] menu.

- Habilite a extensão, defina as configurações globais e especifique as opções de segurança para conexões de usuário e contas do aplicativo Store Assist selecionando **[!UICONTROL Stores > Configuration > Services > Store Fulfillment by Walmart Commerce Technologies]**.

   ![Configuração de serviços da Loja do Administrador para Atendimento da Loja](assets/store-services-admin-sf-config.png)

- Configurar métodos de delivery selecionando **[!UICONTROL Store > Configuration > Sales > Delivery Methods > In-Store Pickup]**.

   ![Configuração de vendas da Loja do Administrador para Atendimento da Loja](assets/store-sales-admin-sf-deliver-config.png)

## Configurações básicas

<table>
<thead>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descrição</strong></td>
<td><strong>Escopo</strong></td>
<td><strong>Obrigatório</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Price]</strong></td>
<td>O preço que você cobra do cliente pela coleta na loja. O padrão é zero.</td>
<td>Site</td>
<td>Não</td>
</tr>
<tr>
<td><strong>[!UICONTROL Search Radius]</strong></td>
<td>O raio, em quilômetros, a ser usado quando um comprador procurar um local de coleta de loja na finalização da loja. Os resultados da pesquisa retornam apenas armazenamentos localizados no raio de pesquisa especificado.</td>
<td>Site</td>
<td>Não</td>
</tr>
<tr>
<td><strong>[!UICONTROL Displayed error message]</strong></td>
<td>Mensagem que é exibida quando um cliente seleciona a retirada na loja para um item que não está disponível para a retirada na loja. Você pode personalizar o texto padrão, se necessário.
</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
</tbody>
</table>

>[!NOTE]
>
>A variável [!UICONTROL Search Radius] A configuração só será usada se você tiver configurado o [localização de armazenamento e configuração de mapeamento](store-location-map-provider-setup.md) para Adobe Commerce.

## Habilitar a solução Store Fulfillment

Ativar o [!DNL Store Fulfillment] solução para adicionar os recursos de retirada na loja e à beira-mar às experiências de compra e check-out na loja da Adobe Commerce.

<table>
<thead>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descrição</strong></td>
<td><strong>Escopo</strong></td>
<td><strong>Obrigatório</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enabled]</strong></td>
<td>Habilitar ou desabilitar a solução. Quando habilitado, configure e use os recursos de Atendimento da Loja e estabeleça a conexão entre sua loja da Adobe Commerce e [!DNL Store Fulfillment] serviços. Quando desabilitados, todos os recursos de Atendimento da Loja são desabilitados e não há comunicação entre o Adobe Commerce e os serviços de Atendimento da Loja. As informações da ordem não podem ser processadas ou recebidas.</td>
<td>Site</td>
<td>Sim</td>
</tr>
</tbody>
</table>

## Adicionar credenciais da conta

<table>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descrição</strong></td>
<td><strong>Escopo</strong></td>
<td><strong>Obrigatório</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Environment]</strong></td>
<td>Selecione <i>[!UICONTROL Sandbox]</i> ou <i>[!UICONTROL Production]</i><br></br>Selecionar [!UICONTROL Sandbox] permite a comunicação com serviços de fulfillment em um ambiente de teste.<br></br>Selecionar [!UICONTROL Production] permite a comunicação com serviços de fulfillment em um ambiente ativo.<br></br>Você recebe um conjunto de credenciais para cada ambiente e pode gerenciar ambos os conjuntos na mesma instalação. <br></br>Salve as credenciais antes de validar a conexão.</td>
<td>Global</td>
<td>Sim</td>
</tr>
<tr>
<td><strong>[!UICONTROL API Server URL]</strong></td>
<td>O URL para o endpoint da API de Atendimento da Walmart Store. Esse deve ser o URL totalmente qualificado fornecido durante o processo de integração. Os clientes de Atendimento da loja recebem um URL de Sandbox e Produção. Ao adicionar os valores, copie e cole o URL completo, incluindo a barra à direita "/".</td>
<td>Global</td>
<td>Sim</td>
</tr>
<tr>
<td><strong>[!UICONTROL Token Auth Server URL]</strong></td>
<td>O URL para o ponto de extremidade de Autenticação de Abastecimento de Loja Walmart. O valor deve ser o URL totalmente qualificado fornecido durante o processo de integração. Você recebe um URL de sandbox e produção. Ao adicionar os valores, copie e cole o URL completo, incluindo a barra à direita "/".</td>
<td>Global</td>
<td>Sim</td>
</tr>
<tr>
<td><strong>[!UICONTROL Merchant Id]</strong></td>
<td>Sua ID de comerciante (locatário) exclusiva fornecida durante o processo de integração. Essa ID é usada para encaminhar pedidos para garantir que seus armazenamentos de comerciantes os recebam.</td>
<td>Global</td>
<td>Sim</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Id]</strong></td>
<td>A ID de integração exclusiva fornecida durante o processo de integração. Essa ID é usada para autenticar toda a comunicação entre o Adobe Commerce e os serviços de preenchimento de loja</td>
<td>Global</td>
<td>Sim</td>
</tr>
<tr>
<td><strong>[!UICONTROL Consumer Secret]</strong></td>
<td>A chave de integração exclusiva fornecida durante o processo de integração. Essa chave é usada para autenticar toda a comunicação entre o Adobe Commerce e o serviço de preenchimento de loja.</td>
<td>Global</td>
<td>Sim</td>
</tr>
</table>

Após configurar o [!UICONTROL Account Credentials], selecione <strong>[!UICONTROL Validate Credentials]</strong> para verificar e estabelecer uma conexão com o serviço de abastecimento de armazenamento pela primeira vez.

## Configurar registro

Os logs dos serviços de fornecimento de armazenamento estão disponíveis no arquivo de log `var/log/walmart-bopis.log`.

Solicite ao administrador do sistema que configure seus ambientes para permitir o tratamento de exceções para que as exceções relacionadas à API possam ser capturadas por meio do firewall ou do cache.

Como o arquivo de log do aplicativo pode crescer rapidamente, habilite o registro para o aplicativo somente por um curto período quando necessário - por exemplo, ao solucionar problemas de preenchimento de lojas para um [!DNL Commerce] pedido. Essa configuração evita problemas de tempo de resposta em ambientes de produção causados por arquivos de log grandes.

>[!TIP]
>
>Para instalações locais do Adobe Commerce, peça ao administrador do sistema para configurar a rotação de log para o `var/log/walmart-bopis.log` para minimizar o tamanho. Para instalações locais do Adobe Commerce, consulte [Rotação de logs](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/next-steps/configuration.html#server-settings) no _Guia de instalação do Adobe Commerce_. Para projetos de infraestrutura em nuvem do Adobe Commerce, consulte [Exibir e gerenciar logs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html).

<table>
<thead>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descrição</strong></td>
<td><strong>Escopo</strong></td>
<td><strong>Obrigatório</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Debug Mode]</strong></td>
<td>O Modo de depuração é usado para aumentar a atividade registrada na integração. Quando desativado, nenhuma informação de depuração é registrada. Quando ativado, todas as informações de depuração são registradas <br></br>Todos os dados registrados podem ser encontrados no arquivo: <pre>var/log/walmart-bopis.log</pre>
<td>Global</td>
<td>Não</td>
</tr>
</tbody>
</table>

## Gerenciar Sincronização de pedidos

Defina as configurações para gerenciar a manipulação de erros para a sincronização de ordens, os atributos do catálogo a serem usados para a verificação de código de barras durante a separação de ordens e configure os tamanhos do lote de ordens para a fila de atendimento de armazenamento.

Você pode exibir detalhes sobre operações de sincronização de ordens no painel Gerenciamento da Fila de Abastecimento de Loja no Admin (
<strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong>).

### Gerenciamento de Erros de Sincronização

<table>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descrição</strong></td>
<td><strong>Escopo</strong></td>
<td><strong>Obrigatório</strong></td>
</tr>
<tr>
<td><strong>[!UICONTROL Retry Critical Error]</strong></td>
<td>Especifica as tentativas de repetição para uma operação de sincronização de registros após a ocorrência de um erro crítico.<br></br>Erros críticos ocorrem sempre que a integração não obtém uma resposta positiva do serviço de preenchimento. Isso pode ocorrer quando o serviço está inativo ou quando há um erro nos dados do pedido que estão sendo enviados.<br></br>Quando o limite de novas tentativas é atingido, o item permanece em uma fila, mas não é processado novamente. Exibir todos os itens com erros de <strong>[!UICONTROL System > Tools > Store Fulfillment Queue]</strong> Gerenciamento no Administrador. Para solucionar problemas de itens com falha consistente, entre em contato com o Gerente de conta.</td>
<td>Global</td>
<td>Não</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Error Notification Email]</strong></td>
<td>Ativar notificações de erro para receber um email quando a variável [!UICONTROL Retry Critical Error Threshold] é atingido para um pedido. A notificação inclui todos os detalhes disponíveis sobre o erro.</td>
<td>Global</td>
<td>Não</td>
</tr>
<tr>
<td><strong>[!UICONTROL Send Error Notification Email To]</strong></td>
<td>Uma lista delimitada por vírgulas de endereços de email de recipients para notificações de erro.</td>
<td>Global</td>
<td>Não</td>
</tr>
<tr>
<td><strong>[!UICONTROL Order Sync Exception Email Template]</strong></td>
<td>Especifica o modelo de email usado para notificar os destinatários sobre erros de sincronização de pedidos. Um template padrão é fornecido. Ele não oferece suporte à personalização.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
</table>

### Sincronização de pedidos

<table>
<thead>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descrição</strong></td>
<td><strong>Escopo</strong></td>
<td><strong>Obrigatório</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Barcode Source]</strong></td>
<td>O atributo de catálogo que armazena o código digitalizável para itens correspondentes em seus locais de comerciante.<br></br>Se você tiver apenas uma localização de comerciante existente, é provável que você use códigos UPC, enquanto seu canal de comércio eletrônico identifica produtos por SKU. Se esse for o seu cenário, selecione o atributo de catálogo que contém o código UPC.<br></br>Essa configuração garante que as ordens enviadas aos itens da lista de lojas com o identificador correto, para que as associadas de loja possam verificar os itens com precisão durante o processo de separação.<br></br>Se não tiver certeza, verifique com seus associados de preenchimento no departamento de Entrega e Separação para determinar qual atributo deve ser enviado. Talvez seja necessário adicionar o atributo apropriado ao conjunto de atributos do produto Adobe Commerce se o atributo não estiver incluído no banco de dados.</td>
<td>Site</td>
<td>Sim</td>
</tr>
<tr>
<td><strong>[!UICONTROL Barcode Type]</strong></td>
<td>O atributo de catálogo que armazena a origem do código de barras para itens correspondentes em seus locais de comerciante.<br></br>Essa configuração garante que as ordens enviadas aos itens da lista de lojas com o identificador correto, para que as associadas de loja possam verificar os itens com precisão durante o processo de separação. As opções incluem - SKU, UPC, GTIN, UPCA, EAN13, UPCE0, DISA, UAB, CODABAR, Preço incorporado UPC.<br></br>Se não tiver certeza, selecione a opção mais parecida com os valores contidos nas [!UICONTROL Barcode Source] atributo. Os associados da loja ainda podem corresponder itens manualmente em sua lista de separação.</td>
<td>Site</td>
<td>Sim</td>
</tr>
<tr>
<td><strong>[!UICONTROL Max Number of Items]</strong></td>
<td>O número máximo de itens a serem enviados da fila de atendimento de armazenamento de uma vez.<br></br>As ordens de BOPIS são enviadas ao serviço de fulfillment em lotes, em intervalos regulares. Essa configuração permite controlar o tamanho do lote.<br></br>O valor padrão é 100 itens. Dependendo do volume e da capacidade do seu pedido, talvez seja necessário ajustar esse valor para cima ou para baixo.</td>
<td>Global</td>
<td>Não</td>
</tr>
</tbody>
</table>

## Habilitar opções de remessa de Atendimento da Loja

Configure as opções de envio de Store Fulfillment que determinam a disponibilidade das opções de entrega na loja e em casa para suas lojas Adobe Commerce.

### Entregar para armazenamento

<table>
<thead>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descrição</strong></td>
<td><strong>Escopo</strong></td>
<td><strong>Obrigatório</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship To Store]</strong></td>
<td>A configuração de entrega para armazenamento baseia-se nos recursos existentes de entrega para armazenamento. Se você usa o Inventory management, ou se você pode aceitar e atender ordens em locais de comerciantes sem inventário por meio de transferências de inventário de loja para loja, defina esta opção como "Sim".<br></br>Se você não puder suportar a opção entregar para armazenamento ou não quiser oferecê-la, defina como "Não". Quando desabilitados, os itens do catálogo com inventário zero para uma loja de comerciantes ou os itens abaixo desse local [!DNL Out of Stock Threshold], não são oferecidos com opções de coleta na loja.<br></br>Essa é uma configuração global que pode ser ajustada por localização do comerciante.</td>
<td>Global</td>
<td>Não</td>
</tr>
</tbody>
</table>

### Entregar do armazenamento

<table>
<thead>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descrição</strong></td>
<td><strong>Escopo</strong></td>
<td><strong>Obrigatório</strong></td>
</tr>
</thead>
<tbody>
<tr>
<td><strong>[!UICONTROL Enable Ship From Store]</strong></td>
<td>Ativa ou desativa a opção Entrega em casa nas lojas do comerciante. Quando ativado, seus locais de loja de comerciantes são considerados em conjunto com outras fontes atribuídas no estoque associado ao seu site.<br></br>Nos serviços Inventory management padrão, a variável [!DNL Ship from Store] A opção is é inerente e não pode ser desativada. Com a solução Store Fulfillment, você pode ativá-la ou desativá-la.<br></br>Esta é uma configuração global. Você também pode ajustar essa configuração por localização e produto do comerciante.</td>
<td>Global</td>
<td>Não</td>
</tr>
</tbody>
</table>


## Gerenciar contas e permissões de uso do Aplicativo de Atendimento da Loja

Defina as configurações da segurança de senha e conta de usuário do Aplicativo de Abastecimento da Loja e da autenticação de dois fatores.

### Segurança do aplicativo

<table>
<thead>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descrição</strong></td>
<td><strong>Escopo</strong></td>
<td><strong>Obrigatório</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL User Session Lifetime]</strong></td>
<td>O período, em segundos, em que uma sessão de usuário associado de armazenamento permanece ativa antes do logout automático. Os valores válidos variam de 60 a 31536000.</td>
<td>Global</td>
<td>Não</td>
</tr>
<tr>
<td><strong>[!UICONTROL Maximum Login Failures to Lockout Account]</strong></td>
<td>Especifica o número de tentativas de logon com falha permitidas antes que uma associada de armazenamento seja bloqueada de sua conta.<br></br>Para desativar o bloqueio de conta, defina o valor como 0.</td>
<td>Global</td>
<td>Não</td>
</tr>
<tr>
<td><strong>[!UICONTROL Lockout Time (minutes)]</strong></td>
<td>Número de minutos para bloquear uma conta após uma falha de logon.</td>
<td>Global</td>
<td>Não</td>
</tr>
<tr>
<td><strong>[!UICONTROL Force Password Change]</strong></td>
<td><em>[!UICONTROL Yes]</em>: Exigir que o usuário altere a senha após a configuração da conta.<br></br><em>[!UICONTROL No]</em>: recomenda que o usuário altere a senha após a configuração da conta.</td>
<td>Global</td>
<td>Não</td>
</tr>
<tr>
<td><strong>[!UICONTROL Password Lifetime]</strong></td>
<td>O número de dias que uma senha permanece válida antes de uma alteração de senha necessária. Deixe em branco para desativar esta opção.</td>
<td>Global</td>
<td>Não</td>
</tr>
</tbody>
</table>

## Métodos de delivery

O Atendimento da loja funciona estendendo o Adobe Commerce nativo [!DNL In-Store Delivery] recursos. Após instalar a extensão, é possível configurar métodos de entrega na loja usando as seguintes configurações estendidas que são adicionadas ao Administrador.

- **Coleta na loja**—Opções de oferta para entrega na loja durante o processo de finalização Este é o cenário de entrega mais comum para pedidos BOPIS.

- **[!UICONTROL Curbside pick up]**-Oferecer opções para que os clientes estacionem em um local de loja e tenham seu pedido entregue a eles por um associado de loja.

Defina essas configurações no Administrador selecionando <strong>[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]</strong>.

>[!NOTE]
>
>Para obter informações adicionais sobre como configurar as opções de entrega na loja, consulte [Entrega na loja](https://docs.magento.com/user-guide/shipping/shipping-in-store-delivery.html) no _Guia do usuário do Adobe Commerce_.


### Configuração de métodos de entrega

Com o método de entrega na loja, o cliente pode selecionar uma origem a ser usada como um local de retirada durante a finalização da compra.

<table>
<thead>
<tr>
<td><strong>Campo</strong></td>
<td><strong>Descrição</strong></td>
<td><strong>Escopo</strong></td>
<td><strong>Obrigatório</strong></td>
</tr>
 </thead>
 <tbody>
<tr>
<td><strong>[!UICONTROL Enable In-Store Pickup]</strong></td>
<td>Habilite ou desabilite a opção de retirada na loja disponível durante o check-out para clientes que escolhem a retirada da loja. Quando a coleta na loja está desativada, a opção não é exibida.<br></br>Essa configuração global se aplica a todos os locais de lojas de varejo. Quando ativado, você pode desativá-lo seletivamente no local da loja de varejo.</td>
<td>Site</td>
<td>Não</td>
</tr>
<tr>
<td><strong>[!UICONTROL Enable Curbside Pickup]</strong></td>
<td>Habilite ou desabilite a opção de retirada à beira-mar durante o processo de finalização para clientes que escolhem a retirada da loja.<br></br>Essa configuração global se aplica a todos os locais de lojas de varejo. Quando ativado, você pode desativá-lo seletivamente no local da loja de varejo.</td>
<td>Site</td>
<td>Não</td>
</tr>
</tbody>
</table>

### Configuração de título do método de entrega

<table>
<thead>
<tr>
<th><strong>Campo</strong></th>
<th><strong>Descrição</strong></th>
<th><strong>Escopo</strong></th>
<th><strong>Obrigatório</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Título da entrega inicial</strong></td>
<td>Especifica o título a ser exibido para a opção Entrega inicial nas áreas do produto, carrinho e finalização. A entrega em casa refere-se aos recursos de entrega padrão do Adobe Commerce — de um depósito, por uma transportadora ou diretamente para o endereço de entrega fornecido pelo cliente. </br></br>Essa etiqueta não afeta as etiquetas do método de envio da transportadora selecionada.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Descrição da entrega inicial</strong></td>
<td>Uma descrição opcional que é exibida sempre que o Título do delivery inicial é exibido aos clientes. Na maioria das vezes, a descrição é uma mensagem estática para comunicar suas promessas de delivery. Alguns exemplos:</br><code>Same-day shipping on orders by 4</code></br></br><code>Ships within 2 business days</code></td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Título da retirada da loja</strong></td>
<td>Quando uma opção de entrega é apresentada ao cliente e a retirada na loja está disponível, este rótulo é exibido. </br></br>Você pode personalizar este rótulo, que é exibido nas áreas do produto, carrinho e check-out.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<td><strong>Descrição da retirada da loja</strong></td>
<td>Sempre que o Título de retirada da loja for exibido, você poderá incluir uma descrição, se desejar. Esta mensagem estática ajuda a melhorar as comunicações do cliente relacionadas à experiência de retirada da loja. Alguns exemplos:</br></br><code>Get it today for free!</code></br></br><code>Ready for pickup in an hour!</code></td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Título de retirada na loja</strong></td>
<td>Quando a Coleta na loja está ativada, esse título é exibido aos clientes como a opção de entrega Coleta da loja. Você pode personalizar seu rótulo.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<tr>
<td><strong>Título de retirada da borda</strong></td>
<td>Quando a opção Seleção à beira da proibição está ativada, a opção é mostrada aos clientes como um tipo de opção de entrega de Seleção de loja. Você pode personalizar seu rótulo aqui.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Instruções de retirada na loja</strong></td>
<td>Quando um pedido estiver pronto para retirada em suas lojas de varejo, o cliente será notificado por e-mail. Se o cliente selecionou [!DNL In-Store Pickup] durante a finalização da compra, você pode personalizar as instruções de retirada aqui. </br></br>Essa é uma configuração global que se aplica a todos os locais de lojas de varejo. Você também pode personalizar as instruções no nível do local da loja de varejo.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Instruções de retirada da calçada</strong></td>
<td>Especifica instruções personalizadas de retirada de ordem a serem incluídas nas notificações por email do cliente para ordens de retirada na borda. </br></br>Essa é uma configuração global que se aplica a todos os locais de lojas de varejo. Você também pode personalizar as instruções no nível do local da loja de varejo.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Lead Time de Retirada Estimado</strong></td>
<td>O número de minutos necessários antes de um pedido ser recebido, atendido e pronto para ser retirado. Essas informações são mostradas ao cliente ao selecionar um local de loja de varejo para a opção Entrega de retirada da loja. Essa é uma configuração global e se aplica a todos os locais de lojas de varejo. Você também pode personalizar o prazo de entrega no nível de localização da loja de varejo.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Rótulo de tempo estimado de retirada</strong></td>
<td>Exibe o tempo estimado até que um pedido esteja disponível para retirada do cliente. Essas informações são exibidas para os clientes quando eles selecionam um local de loja de varejo para a [!DNL In-Store Pickup] opção de entrega. </br></br>Ao personalizar esse rótulo, você pode usar o código <code>%1</code> para inserir seu <strong>Lead Time de Retirada Estimado</strong>. Por exemplo:</br></br><code>Ready for Pickup in %1 minutes.</code></br></br>Essa é uma configuração global que se aplica a todos os locais de lojas de varejo. Você também pode personalizar o prazo de entrega no nível de localização da loja de varejo.</br></br><code>Ready for Pickup in %1 minutes.</code></br></br></td>
<td>Exibição da loja</td>
<td>Não</td>
<tr>
<td><strong>Aviso de isenção de tempo de retirada</strong></td>
<td>O conteúdo exibido na página do produto na dica de ferramenta que lista horas de armazenamento, feriados, fechamentos inesperados e assim por diante</td>
<td>Exibição da loja
</td>
<td>Não
</td>
</tr>
</tbody></table>

### Configuração dos títulos de disponibilidade do Stock

<table>
<thead>
<tr>
<th><strong>Campo</strong></th>
<th><strong>Descrição</strong></th>
<th><strong>Escopo</strong></th>
<th><strong>Obrigatório</strong></th>
</tr>
</thead>
<tbody><tr>
<td><strong>Em Estoque</strong></td>
<td>Quando um cliente estiver usando o endereço da loja de varejo, a disponibilidade do inventário para os itens atuais é mostrada para cada local. </br></br>É possível personalizar o <em>[!UICONTROL in-stock]</em> rótulo de status aqui.</br></br></td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Sem estoque</strong></td>
<td>Quando um cliente estiver usando o endereço da loja de varejo, a disponibilidade do inventário para qualquer item atual é mostrada para cada local.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Parcialmente em Estoque</strong></td>
<td>Quando um cliente estiver usando o endereço da loja de varejo, a disponibilidade do inventário para quaisquer itens atuais é mostrada para cada local. </br></br>É possível personalizar o <em>[!UICONTROL partially in-stock]</em> rótulo de status aqui.</br></br></td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
</tbody></table>

