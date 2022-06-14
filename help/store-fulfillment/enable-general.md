---
title: Configuração geral
description: Defina as configurações gerais para ativar [!DNL Store Fulfillment] para sua loja. Defina as configurações de extensão global, as configurações do sistema para registro, sincronização de dados e segurança. Forneça os principais dados para permitir a integração entre o Adobe Commerce e os serviços de fornecimento de armazenamento.
role: User, Admin
level: Intermediate
source-git-commit: 4ea03b3be11056526adc42d875b1e26a24736d15
workflow-type: tm+mt
source-wordcount: '2409'
ht-degree: 0%

---

# Configuração geral

No Administrador de comércio do Adobe, defina as configurações gerais para habilitar o [!DNL Store Fulfillment] serviços para sua loja, defina as configurações da extensão global e forneça os principais dados para a integração definindo o [!UICONTROL Account Credentials].

A integração deve ser conectada ao serviço de Atendimento da loja. Além disso, configure as configurações gerais de Cumprimento da loja para habilitar e personalizar os serviços de Atendimento da loja com base nos recursos e requisitos operacionais da organização.

A configuração geral para [!DNL Store Fulfillment] O inclui as seguintes configurações:

- [Habilitar a extensão](#enable-the-extension)
- [Gerenciar credenciais da conta para se conectar aos serviços de fornecimento de armazenamento](#account-credentials)
- [Configurar o registro](#configure-logging)
- [Definir opções para gerenciar operações de [sincronização de pedidos]](#order-synchronization)
- [Ativar as opções de entrega do Cumprimento da Loja](#enable-store-fullment-shipping-options)
- [Definir configurações de segurança e autenticação para o aplicativo de fornecimento de loja](#store-fulfillment-app)
- [Definir a disponibilidade do método de entrega e a configuração das mensagens](#in-store-delivery-methods)


## Habilitar a extensão

| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enabled]** | Ative ou desative a solução. Quando habilitado, configure e use os recursos de Entrega da loja e estabeleça a conexão entre a loja da Adobe Commerce e os serviços de Entrega da loja. Quando desativado, todos os recursos de Entrega de loja são desativados e não há comunicação entre o Adobe Commerce e os serviços de Entrega de loja. As informações do pedido não podem ser processadas ou recebidas. | Global | Sim |


Para concluir essa configuração, consulte **Armazena → Configuração → Serviços → Armazenar o Cumprimento por Tecnologias Walmart Commerce**.

## Adicionar credenciais de conta



| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Environment]** | Pode selecionar *Sandbox* ou *Produção*:</br> A sandbox se comunica com os serviços de cumprimento em um teste.</br>A produção se comunica com um ambiente vivo. Use **only** em produção.</br>Você recebe um conjunto de credenciais para cada ambiente e pode gerenciar ambos os conjuntos na mesma instalação. </br></br>Salve as credenciais antes de validar a conexão. | Global | Sim |
| **[!UICONTROL API Server URL]** | O URL para o endpoint da API de disponibilização da Loja Walmart. Esse URL deve ser totalmente qualificado e fornecido a você durante o processo de integração. Os clientes do Store Fulfillment recebem sandbox e URL de produção. Certifique-se de copiar/colar o URL completo, incluindo a barra à direita &quot;/&quot;. | Global | Sim |
| **[!UICONTROL Token Auth Server URL]** | O URL para o ponto de extremidade de Autenticação de Cumprimento de Loja Walmart. O valor deve ser o URL totalmente qualificado fornecido a você durante o processo de integração. Você recebe um sandbox e um URL de produção. Certifique-se de copiar/colar o URL completo, incluindo barra à direita `/`&quot;. | Global | Sim |
| **[!UICONTROL Merchant Id]** | Sua ID exclusiva de comerciante (locatário) fornecida a você durante o processo de integração. Sua ID é usada para encaminhar seus pedidos e garante que suas lojas de merchant estejam recebendo esses pedidos. | Global | Sim |
| **[!UICONTROL Consumer Id]** | Sua ID de integração exclusiva. Isso é fornecido a você durante o processo de integração. Não muda. É usado para autenticar todas as comunicações com os serviços de atendimento. | Global | Sim |
| **[!UICONTROL Consumer Secret]** | Sua chave de integração exclusiva. Isso é fornecido a você durante o processo de integração. É usado para autenticar todas as comunicações com os serviços de atendimento. | Global | Sim |

Após configurar as Credenciais da Conta, selecione **[!UICONTROL Validate Credentials]** para verificar e estabelecer uma conexão com o serviço da Web de cumprimento pela primeira vez.

## Configurar o registro

Quando o registro é ativado, o arquivo de log pode expandir rapidamente. Para evitar problemas de tempo de resposta em ambientes de produção, tenha cuidado ao ativar o registro e ative o por um curto período de tempo, quando necessário.

Solicite ao administrador do sistema que configure seus ambientes para permitir o tratamento de exceções, de modo que as exceções relacionadas à API possam ser capturadas pelo firewall ou cache. Você também pode pedir ao administrador do sistema para configurar a rotação de log neste arquivo para minimizar o tamanho.

| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **Modo de depuração** | O Modo de depuração é usado para aumentar a atividade registrada na integração. Quando desativado, nenhuma informação de depuração é registrada. Quando ativado, todas as informações de depuração são registradas em log.</br> Todos os dados registrados podem ser encontrados no arquivo : `var/log/walmart-bopis.log` | Global | Não |

## Gerenciar a sincronização do pedido

Configure as configurações para gerenciar o tratamento de erros para sincronização de pedidos, atributos de catálogo a serem usados para a varredura de código de barras durante a escolha de pedidos e configurar os tamanhos de lote de pedidos para a fila de atendimento da loja.

Você pode visualizar detalhes sobre as operações de sincronização de pedidos no painel Gerenciamento da fila de atendimento da loja no Administrador (
**[!UICONTROL System > Tools > Store Fulfillment Queue]**).

### Gerenciamento de Erros de Sincronização

| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------|
| **Erro Crítico na Tentativa** | Especifica as tentativas de repetição de uma operação de sincronização de registro após ocorrer um erro crítico.</br></br>Erros críticos ocorrem sempre que a integração não obtém uma resposta positiva do serviço de cumprimento. Isso pode ocorrer quando o serviço está inativo ou quando há um erro nos dados do pedido que estão sendo enviados.</br></br>Quando o limite de repetição é atingido, o item permanece em uma fila, mas não é processado novamente. Exibir todos os itens com erros de **[!UICONTROL System → Tools → Store Fulfillment Queue]** Gerenciamento no Administrador. Para solucionar problemas consistentemente de itens com falha, entre em contato com seu Gerente de conta. | Global | Não |
| **Ativar Email de Notificação de Erro** | Ative as notificações de erro para receber um email quando a função [!UICONTROL Retry Critical Error Threshold] é acessado para um pedido. A notificação inclui todos os detalhes disponíveis sobre o erro. | Global | Não |
| **Enviar email de notificação de erro para** | Uma lista delimitada por vírgulas de endereços de email de destinatários para notificações de erro. | Global | Não |
| **Modelo de Email de Exceção de Sincronização de Pedido** | Especifica o template de email usado para notificar os recipients sobre erros de sincronização de pedidos. Um template padrão é fornecido. Ele não oferece suporte à personalização. | Exibição da loja | Não |

### Sincronização de pedidos

| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Barcode Source]** | O atributo de catálogo que armazena o código que pode ser verificado para os itens correspondentes em seus locais do comerciante.</br></br>Se você tiver apenas um local comercial existente, é provável que use códigos UPC, enquanto seu canal de comércio eletrônico identifica produtos por SKU. Se este for o seu cenário, selecione o atributo de catálogo que contém o código UPC.</br></br>Essa configuração garante que os pedidos enviados para seus lojas de merchant listem itens com o identificador correto para que os associados da loja possam verificar os itens com precisão durante o processo de separação.</br></br>Se não tiver certeza, verifique com seus associados de atendimento no departamento de Entrega e Separação para determinar qual atributo deve ser enviado. Talvez seja necessário adicionar o atributo apropriado ao conjunto de atributos do produto Adobe Commerce se o atributo não estiver incluído no banco de dados. | Site | Sim |
| **[!UICONTROL Barcode Type]** | O atributo de catálogo que armazena a fonte do código de barras para os itens correspondentes em seus locais de merchant.</br></br>Essa configuração garante que os pedidos enviados para seus lojas de merchant listem itens com o identificador correto para que os associados da loja possam verificar os itens com precisão durante o processo de separação. As opções incluem - SKU, UPC, GTIN, UPCA, EAN13, UPCE0, DISA, UAB, CODABAR, Preço incorporado na UPC.</br></br>Se não tiver certeza, selecione a opção que mais se assemelha aos valores contidos em [!UICONTROL Barcode Source] atributo. As associações de armazenamento ainda podem corresponder aos itens manualmente da lista de separação. | Site | Sim |
| **[!UICONTROL Max Number of Items]** | O número máximo de itens para enviar da fila de atendimento da loja de uma vez.</br></br>As ordens BOPIS são enviadas ao serviço de atendimento em lotes, em intervalos regulares. Esta configuração permite controlar o tamanho do lote.</br></br>O valor padrão é 100 itens. Dependendo do volume e da capacidade do seu pedido, talvez seja necessário ajustar esse valor para cima ou para baixo. | Global | Não |


## Ativar as opções de entrega do Cumprimento da Loja

Configure as opções de envio da Loja de Atendimento que determinam a disponibilidade das opções de coleta na loja e de entrega doméstica para suas lojas Adobe Commerce.

### Entregar para Armazenamento


| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|---------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable Ship To Store]** | A configuração de entrega para loja aproveita seus recursos existentes de entrega para loja. Se você usar o Inventory management, ou se puder aceitar e atender pedidos em locais do comerciante sem inventário por meio de transferências de inventário de armazenamento para armazenamento, defina essa opção como `Yes`.</br></br>Se não for possível oferecer suporte à opção de entrega para loja ou se não quiser oferecê-la, defina como `No`. Quando desativado, os itens no catálogo com inventário zero de uma loja de merchant ou os itens que estão abaixo dessa localização [!DNL Out of Stock Threshold], não são oferecidas com opções de retirada na loja.</br></br>Esta é uma configuração global que pode ser ajustada por localização do comerciante. | Global | Não |

### Entregar do Armazenamento

| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|-----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable Ship From Store]** | Ativa ou desativa a opção Entrega inicial em suas lojas de merchant. Quando ativadas, as localizações da loja de merchant são consideradas agregadas a outras fontes atribuídas no estoque associado ao seu site.</br></br>Nos serviços padrão da Inventory management, a variável [!DNL Ship from Store] é inerente e não pode ser desativado. Com a solução Store Fulfillment, você tem a opção de ativá-la ou desativá-la.</br></br>Esta é uma configuração global. Também é possível ajustar essa configuração por localização do comerciante e produto. | Global | Não |


## Gerenciar contas e permissões de uso do aplicativo de preenchimento da loja

Defina as configurações para a conta de usuário e a segurança de senha do aplicativo de preenchimento da loja e a autenticação de dois fatores.

### Segurança do aplicativo

| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL User Session Lifetime]** | O período, em segundos, em que uma sessão de usuário associada da loja permanece ativa antes do logout automático. Os valores válidos variam de 60 a 31536000. | Global | Não |
| **[!UICONTROL Maximum Login Failures to Lockout Account]** | Especifica o número de tentativas de logon com falha permitidas antes que um associado de loja seja bloqueado para fora de sua conta.</br></br>Para desativar o bloqueio da conta, defina o valor como 0. | Global | Não |
| **[!UICONTROL Lockout Time (minutes)]** | Número de minutos para bloquear uma conta após uma falha de logon. | Global | Não |
| **[!UICONTROL Force Password Change]** | Determina se é necessária uma alteração da senha do usuário.</br></br>`Yes`: Exigir que o usuário altere sua senha após a configuração da conta.</br>`No`: Recomenda que o usuário altere a senha após a configuração da conta. | Global | Não |
| **Duração da senha** | O número de dias em que uma senha permanece válida antes de uma alteração de senha necessária. Deixe em branco para desativar essa opção. | Global | Não |


### Autenticação de dois fatores

| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **Usuário do APLICATIVO 2FA** | Ative ou desative a autenticação de dois fatores para os associados da loja. Quando ativado, o associado da loja é solicitado a fornecer uma senha única gerada por um provedor de autenticação. | Global | Não |
| **Política APP 2FA** | Define a política de aplicação para autenticação de dois fatores.</br></br>**[!UICONTROL Optional]**: O associado da loja pode ignorar a autenticação de dois fatores se nenhum provedor estiver definido.</br></br>**[!UICONTROL Mandatory]**: O associado da loja é necessário para concluir a autenticação de dois fatores. | Global | Não |
| **Provedores 2FA** | Selecione um ou mais serviços de provedor de autenticação para oferecer associações de loja. Para configurar a autenticação de dois fatores e a autenticação, os associados da loja devem instalar o aplicativo de autenticação de um dos provedores disponíveis instalados em seus dispositivos móveis. | Global | Não |

### Métodos de delivery

A opção Armazenar Cumprimento funciona ao estender o Adobe Commerce nativo [!DNL In-Store Delivery] recursos.
Depois de instalar a extensão, opções adicionais de configuração do administrador estarão disponíveis para métodos de entrega na loja. Configure essas opções adicionais no Administrador selecionando **[!UICONTROL Stores > Configuration > Sales > Delivery Methods > In-Store Pickup]**.

Nas configurações de Atendimento à loja, você pode configurar os seguintes métodos de entrega para pedidos de retirada na loja.

- **Aquisição na loja**—Opções de oferta para entrega na loja durante o processo de finalização Este é o cenário de entrega mais comum para pedidos BOPIS.

- **Coleta de lado**-Ofereça opções para que os clientes estacionem em um local de loja e tenham seu pedido entregue a eles por um associado de loja.

#### Configuração de métodos de delivery

<!---
In-store pickup, says its global setting, but scope is Website.  How do you configure the in-store pickup options at the retail level?
--->

| **Campo** | **Descrição** | **Escopo** | **Obrigatório** |
|-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------|--------------|
| **[!UICONTROL Enable In-Store Pickup]** | Ative ou desative a opção de coleta na loja disponível durante o check-out para clientes que escolhem a retirada da loja. Quando a retirada na loja está desativada, a opção não é exibida.</br></br>Essa configuração global se aplica a todos os locais da loja de varejo. Quando ativado, você pode desativá-lo seletivamente no local da loja de varejo. | Site | Não |
| **Ativar a retirada do lado do cursor** | Ative ou desative a opção de coleta de lado da borda durante o processo de finalização para clientes que escolhem a retirada da loja.</br></br>Essa configuração global se aplica a todos os locais da loja de varejo. Quando ativado, você pode desativá-lo seletivamente no local da loja de varejo. | Site | Não |

Para obter detalhes sobre como personalizar os métodos de entrega em locais selecionados da loja de varejo, consulte **Configuração da loja de varejo**.


#### Configuração do Título do Método de Entrega

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
<td>Especifica o título a ser exibido para a opção Entrega inicial nas áreas de produto, carrinho e check-out. O delivery doméstico refere-se aos recursos de envio padrão da Adobe Commerce, de um depósito, por uma operadora, diretamente para o endereço de envio fornecido pelo cliente.</br></br>Este rótulo não afeta a transportadora selecionada nem os rótulos disponíveis do método de entrega.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Descrição da entrega inicial</strong></td>
<td>Uma descrição opcional que é exibida sempre que o Título da entrega inicial é exibido aos clientes. Na maioria das vezes, a descrição é uma mensagem estática para comunicar suas promessas de delivery. Alguns exemplos:</br><code>Same-day shipping on orders by 4</code></br></br><code>Ships within 2 business days</code></td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Título da retirada da loja</strong></td>
<td>Quando um cliente é apresentado com opções de entrega e a retirada na loja está disponível, esse rótulo é mostrado.</br></br>Você pode personalizar esse rótulo, que é exibido nas áreas de produto, carrinho e check-out.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<td><strong>Descrição da retirada da loja</strong></td>
<td>Sempre que o Título da retirada da loja for exibido, você poderá incluir uma descrição. Essa mensagem estática ajuda a melhorar as comunicações do cliente relacionadas à experiência de retirada da loja. Alguns exemplos:</br></br><code>Get it today for free!</code></br></br><code>Ready for pickup in an hour!</code></td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Título da retirada na loja</strong></td>
<td>Quando a retirada na loja está ativada, esse título é exibido aos clientes como a opção de entrega de retirada da loja. Você pode personalizar seu rótulo.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<tr>
<td><strong>Título da retirada do lado do cursor</strong></td>
<td>Quando a Seleção de lado é ativada, a opção é exibida para os clientes como um tipo de opção de entrega Seleção de loja. Você pode personalizar o rótulo aqui.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Instruções de retirada na loja</strong></td>
<td>Quando um pedido está pronto para ser recebido em suas lojas de varejo, o cliente é notificado por e-mail. Se o cliente tiver selecionado [!DNL In-Store Pickup] durante o checkout, você pode personalizar as instruções de coleta aqui.</br></br>Esta é uma configuração global que se aplica a todos os locais da loja de varejo. Você também pode personalizar as instruções no nível de local da loja de varejo.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Instruções de retirada do lado do cursor</strong></td>
<td>Especifica instruções personalizadas de coleta de ordem para incluir em notificações por email do cliente para ordens de retirada de lado da curva.</br></br>Esta é uma configuração global que se aplica a todos os locais da loja de varejo. Você também pode personalizar as instruções no nível de local da loja de varejo.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Lead Time de retirada estimado</strong></td>
<td>O número de minutos necessários antes que um pedido seja recebido, realizado e pronto para ser selecionado. Essas informações são mostradas ao cliente ao selecionar um local de loja de varejo para a opção de entrega de retirada da loja.</br></br>Esta é uma configuração global e se aplica a todos os locais da loja de varejo. Você também pode personalizar o lead time no nível de local da loja de varejo.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Rótulo de Tempo de Coleta Estimado</strong></td>
<td>Exibe o tempo estimado até que um pedido esteja disponível para retirada do cliente. Essas informações são mostradas aos clientes quando eles selecionam um local de loja de varejo para a opção de entrega de retirada da loja.</br></br>Ao personalizar esse rótulo, você pode usar o código <code>%1</code> para inserir o seu <strong>Lead Time de retirada estimado</strong>.Por exemplo:</br></br><code>Ready for Pickup in %1 minutes.</code></br></br>Esta é uma configuração global que se aplica a todos os locais da loja de varejo. Você também pode personalizar o lead time no nível de local da loja de varejo.</br></br><code>Ready for Pickup in %1 minutes.</code></br></br></td>
<td>Exibição da loja</td>
<td>Não</td>
<tr>
<td><strong>Aviso de isenção de tempo de retirada</strong></td>
<td>O conteúdo exibido na página do produto na dica de ferramenta que lista as horas de armazenamento, feriados, fechamentos inesperados e assim por diante</td>
<td>Exibição da loja
</td>
<td>Não
</td>
</tr>
</tbody></table>

#### Configuração de Títulos de Disponibilidade de Estoque

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
<td><strong>Em estoque</strong></td>
<td>Quando um cliente está usando o localizador de loja de varejo, a disponibilidade do inventário para os itens atuais é mostrada para cada local.</br></br>Você pode personalizar o rótulo de status "em estoque" aqui.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Produto esgotado</strong></td>
<td>Quando um cliente está usando o localizador de loja de varejo, a disponibilidade do inventário para quaisquer itens atuais é mostrada para cada local.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
<tr>
<td><strong>Parcialmente em estoque</strong></td>
<td>Quando um cliente está usando o localizador de loja de varejo, a disponibilidade do inventário para quaisquer itens atuais é mostrada para cada local.</br></br>Você pode personalizar o rótulo de status "parcialmente em estoque" aqui.</td>
<td>Exibição da loja</td>
<td>Não</td>
</tr>
</tbody></table>





