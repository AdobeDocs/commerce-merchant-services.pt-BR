---
title: Lidar com restrições de cookies
description: Saiba como as recomendações de produto lidam com restrições de cookies.
source-git-commit: 81ab2e22b0ec81e97d27ee135c88b50731a3986d
workflow-type: tm+mt
source-wordcount: '170'
ht-degree: 0%

---

# Lidar com restrições de cookies

O Adobe Commerce e o Magento Open Source pedem consentimento antes que os dados sejam armazenados em cookies do navegador. Para obter mais informações, consulte [Modo de restrição de cookie](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/privacy/compliance-cookie-law.html).

Ao implantar o `magento/product-recommendations` para produção, ele começa a coletar eventos de interação do comprador na loja. Como os dados desses eventos podem ser armazenados em cookies do navegador ou no armazenamento local, o recurso suporta o modo de restrição de cookies não coletando eventos até que o comprador tenha dado consentimento de cookie.

Isso pode não funcionar com soluções de consentimento de cookies de terceiros. É responsabilidade de cada comerciante garantir que a coleta de dados não ocorra antes de o consentimento do cookie ser dado, como geralmente é exigido por lei. Se você gerencia o consentimento do cookie com código personalizado, é possível usar um cookie de não rastreamento chamado `mg_dnt` para restringir a coleta de dados.

- Nome do cookie:

   ```text
   `const DNT_COOKIE = "mg_dnt";`
   ```

- Defina o cookie do not track para desativar a coleta de dados:

   ```text
   `$.mage.cookies.set(DNT_COOKIE, true);`
   ```

- Para limpar o cookie quando o usuário tiver aceitado cookies:

   ```text
   `$.mage.cookies.clear(DNT_COOKIE);`
   ```
