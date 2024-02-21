---
title: Registros de perfil
description: Saiba quais dados um registro de perfil captura.
role: Admin, Developer
feature: Personalization, Integration, Eventing
source-git-commit: 655b5d18a4fb77232523c9c18a9fb362de93c70a
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# [!DNL Data Connection] Registros de perfil (Beta)

>[!NOTE]
>
>Esse recurso está na versão beta. Se você quiser participar do programa beta, envie uma solicitação para [dataconnection@adobe.com](mailto:dataconnection@adobe.com).

A tabela a seguir descreve os dados de registro do perfil do Commerce que estão disponíveis quando você instala o [!DNL Data Connection] extensão. Os dados nos registros de perfil são enviados para a Adobe Experience Platform.

## Registro de perfil

As atualizações de registro de perfil estão disponíveis no Experience Platform quando um novo perfil é criado, atualizado ou excluído.

### Dados coletados do registro do perfil

A seguir estão os dados capturados para um registro de perfil.

| Campo | Descrição |
|---|---|
| `channel` | Contém informações sobre a fonte de dados. Ambos `_id` e `_type` contain [valores com namespace](https://experienceleague.adobe.com/docs/experience-platform/xdm/schema/namespaces.html). |
| `channel._id` | O identificador exclusivo do canal, como `"https://ns.adobe.com/xdm/channels/web"`. |
| `channel._type` | Identifica a origem dos dados do canal, como `"https://ns.adobe.com/xdm/channel-types/web"`. |
| `person` | Contém informações sobre o cliente. |
| `person.name` | Contém informações sobre o nome do cliente. |
| `person.name.firstName` | Contém o nome do cliente. |
| `person.name.lastName` | Contém o sobrenome do cliente. |
| `person.birthDate` | Data de nascimento do comprador. |
| `personalEmail` | Um endereço de email pessoal. |
| `personalEmail.address` | O endereço técnico, por exemplo, `name@domain.com` como geralmente definido em RFC2822 e padrões subsequentes. |
| `userAccount` | Indica detalhes de fidelidade, preferências, processos de logon e outras preferências de conta. |
| `userAccount.startDate` | A data em que o perfil foi criado pela primeira vez. |

>[!NOTE]
>
>Cada registro de perfil também inclui a variável [`identityMap`](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/identitymap.html) que inclui o endereço de email do comprador, quando disponível, e a ECID.

Saiba como [criar um esquema específico de registro de perfil](profile-data.md) que podem assimilar os dados dos registros do perfil.
