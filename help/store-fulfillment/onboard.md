---
title: Integrado "[!DNL Store Fulfillment]"
description: Conecte sua instância do Commerce à [!DNL Store Fulfillment Manager] concluindo algumas etapas de integração.
role: User, Admin
level: Intermediate
source-git-commit: 1333b18f610a12c8b7b0eb66a123f6b3bc8130aa
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 1%

---


# Cumprimento da loja integrada pela Walmart Technologies

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

## Pré-requisitos

* **Informações da conta comercial**-Download e instalação [!DNL Channel Manager] exige um [Conta comercial](https://docs.magento.com/user-guide/magento/magento-account.html){target=&quot;_blank&quot;}. Você precisa de uma ID de conta e credenciais com acesso de Proprietário ou Administrador ao [!DNL Adobe Commerce] ou [!DNL Magento Open Source] instância.

* Para [!DNL Adobe Commerce] em projetos de infraestrutura em nuvem, os instaladores de software devem ter o seguinte acesso ao [!DNL Commerce] instância:

   * Acesso de superusuário ao projeto do Cloud
   * Acesso do administrador a um ambiente específico
   * Um [!DNL Adobe Commerce] ou [!DNL Magento Open Source] conta com permissões para acessar o repositório do Composer

      Consulte [Gerenciar o acesso do usuário](https://devdocs.magento.com/cloud/project/user-admin.html).

* **Acesso ao arquivo de software Store Fulfillment by Walmart Technologies para instalar a solução Store Fulfillment em sua instância do Adobe Commerce**-Seu representante de conta do cliente pode fornecer acesso ao arquivo de instalação da extensão.

* **Experiência usando o Composer e a[!DNL Commerce CLI]** -Consulte [Instalação geral da CLI](https://devdocs.magento.com/extensions/install/){target=&quot;_blank&quot;} para obter informações sobre o uso dessas ferramentas para instalar e gerenciar extensões no [!DNL Adobe Commerce] e [!DNL Magento Open Source] plataformas.

* [!DNL Inventory Management] extensão para Adobe Commerce e Magento Open Source

   É necessário ter a extensão Inventory management instalada e ativada na instância do Adobe Commerce e do Magento Open Source. Normalmente, essa extensão é instalada e ativada por padrão no Adobe Commerce e Magento Open Source 2.3.x e posterior. Para obter mais informações, consulte [Instalar o Inventory management](https://devdocs.magento.com/extensions/inventory-management/) na documentação do desenvolvedor do Adobe Commerce.

## Requisitos

A solução Store Fulfillment está disponível para clientes do Adobe Commerce e Magento Open Source. Você deve atender aos seguintes requisitos de sistema e de negócios para instalar, implantar e usar a solução.

### Requisitos do sistema

A extensão Store Fulfillment by Walmart Technologies foi testada para compatibilidade com as seguintes versões de software.

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

* Negócios com base nos EUA

* Varejistas B2C, fabricantes de CPG que vendem D2C ou distribuidores que vendem D2C ou a pequenas empresas

* Pelo menos um armazém físico

* Gerencie o inventário de produtos com o Inventory management for Commerce (era MSI)

* Capacidade de sindicalizar inventário de merchant

* Armazene a disponibilidade do Wi-Fi em todos os locais que oferecem suporte à solução de disponibilização da loja

* Os associados de armazenamento e depósito têm acesso a dispositivos móveis iOS ou Android durante seus turnos, pessoais ou fornecidos pelo comerciante

* Os produtos gerenciados por meio da solução Store Fulfillment devem ter atributos de produto que incluam um produto SKU ou UPC.

### Plataformas compatíveis

* Adobe Commerce on Cloud (ECE) : 2.4.x
* Adobe Commerce nas instalações (EE) : 2.4.x
* Magento Open Source 2.4.x
