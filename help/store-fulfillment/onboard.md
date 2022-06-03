---
title: Visão geral da integração
description: '"Conecte seu [!DNL Commerce] à [!DNL Store Fulfillment Manager] concluindo algumas etapas de integração."'
role: User, Admin
level: Intermediate
exl-id: f8e403ac-9bbd-4ea2-b209-9b1a8d1e32a2
source-git-commit: 26d0ddbcbe648b336d527788668caef1f8e688ed
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Visão geral da integração

Cumprimento da loja integrada instalando a extensão na instância do Commerce e configurando as conexões da API. Essas conexões permitem a comunicação e a sincronização de dados entre a instância do Commerce, os sistemas de terceiros para o gerenciamento de inventário e o aplicativo Store Assist.

Após concluir a integração, configure e gerencie a solução no Administrador do Commerce

![[!DNL Store Fulfillment Service] configuração na visualização Administração](assets/store-fulfillment-admin-home.png)

## Visão geral da integração

1. Instale a extensão Store Fulfillment by Walmart Technologies para Adobe Commerce.

1. No Administrador, ative a solução e complete a configuração geral da integração, seus recursos ativos e preencha o formulário de entrada de integração para se conectar aos serviços de cumprimento.

1. Configure os métodos de delivery.

1. Configure as fontes como suas lojas físicas e os produtos no catálogo.

1. Selecione e configure os modelos de email para gerenciar a comunicação com o cliente para compras online, compras na loja (BOPIS) de transações.

1. Crie usuários e funções para o aplicativo Store Assist.

1. Configure os agendamentos para processos em segundo plano para sincronizar dados com o serviço de cumprimento.

## Requisitos

Você deve atender aos seguintes requisitos para instalar, implantar e usar a solução do .

* **Informações da conta comercial**-Instalação [!DNL Channel Manager] exige um [Conta comercial](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}. Você precisa de uma ID de conta e credenciais com acesso de Proprietário ou Administrador ao [!DNL Adobe Commerce] instância.

* Para [!DNL Adobe Commerce] em projetos de infraestrutura em nuvem, os instaladores de software devem ter acesso de administrador ao projeto do Cloud. Consulte [Gerenciar o acesso do usuário](https://devdocs.magento.com/cloud/project/user-admin.html).

* **Acesso ao arquivo de software Loja da Walmart Technologies (arquivo .zip) para instalar a solução Store Fulfillment**-Durante o processo de integração e ativação, o representante da conta do cliente fornecerá acesso de download ao arquivo de instalação.

* **Experiência usando o Composer e a[!DNL Commerce CLI]**—Consulte [Instalação geral da CLI](https://devdocs.magento.com/extensions/install/){target=&quot;_blank&quot;} para obter informações sobre o uso dessas ferramentas para instalar e gerenciar extensões no [!DNL Adobe Commerce] e [!DNL Magento Open Source] plataformas.

* [!DNL Inventory Management] extensão para Adobe Commerce e Magento Open Source

   É necessário ter a extensão Inventory management instalada e ativada na instância do Adobe Commerce e do Magento Open Source. Normalmente, essa extensão é instalada e ativada por padrão no Adobe Commerce 2.3.x e posterior. Para obter mais informações, consulte [Instalar o Inventory management](https://devdocs.magento.com/extensions/inventory-management/) na documentação do desenvolvedor do Adobe Commerce.

## Requisitos da plataforma e da versão

O [!DNL Store Fulfillment] A solução está disponível para clientes da Adobe Commerce nas seguintes plataformas.

* Adobe Commerce on cloud Infrastructure (ECE)
* Adobe Commerce nas instalações (EE)

A solução Store Fulfillment é compatível com as seguintes versões de software.

**Compatibilidade de software**

| **Software** | **Versão mínima** | **Versão máxima** |
|----------------|---------------------|---------------------|
| Adobe Commerce | 2.4.0 | 2.4.4 |
| Composer | 1.x | 2.x |
| MariaDB | 10,2 | 10,4 |
| MySQL | 5,7 | 8,0 |
| PHP | 7,4 | 8,1 |

Para saber mais sobre os requisitos, consulte a Adobe Commerce [Requisitos do sistema](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) na documentação do Desenvolvedor.

### Requisitos de empresa

Sua empresa deve atender aos seguintes critérios mínimos para implementar a solução de fornecimento de armazenamento.

* Somente para empresas com base nos EUA

* Varejistas B2C, fabricantes de CPG que vendem D2C ou distribuidores que vendem D2C ou a pequenas empresas

* Pelo menos um armazém físico

* Gerencie o inventário de produtos com o Inventory management for Adobe Commerce (era MSI)

* Capacidade de sindicalizar inventário de merchant

* Armazene a disponibilidade do Wi-Fi em todos os locais que oferecem suporte à solução de disponibilização da loja

* Os associados de armazenamento e depósito têm acesso a dispositivos móveis iOS ou Android durante seus turnos, pessoais ou fornecidos pelo comerciante

* Os produtos gerenciados por meio da solução Store Fulfillment devem ter atributos de produto que incluam um código de produto SKU ou UPC
