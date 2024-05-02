---
title: "ACSD-49970: gestione errata degli errori GraphQL"
description: Applica la patch ACSD-49970 per risolvere il problema Adobe Commerce in caso di gestione errata degli errori GraphQL quando [!UICONTROL New Relic Reporting] è acceso.
exl-id: 70acade5-02a5-4769-86e2-5c566b2af709
feature: GraphQL, Observability
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# ACSD-49970: gestione errata degli errori GraphQL

La patch ACSD-49970 risolve il problema relativo alla gestione errata degli errori di GraphQL quando *[!UICONTROL New Relic Reporting]* è acceso. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29. L’ID della patch è ACSD-49970. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

`GraphQLOperationNames` non viene gestita correttamente se il `logDataHelper` contiene o meno questa chiave.

<u>Passaggi da riprodurre</u>:

1. Esegui `bin/magento deploy:mode:set developer`.
1. Accedi all’amministratore.
1. Abilita **[!UICONTROL New Relic Integration]** da **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL New Relic Reporting]**
(Nota: anche se viene visualizzato un errore che indica che [!DNL New Relic] non è disponibile, la configurazione viene salvata).
1. Esegui questo *GraphQL* mutazione in `http://yourMagentoDomain/graphql` dal *[!DNL Altair]* client o qualsiasi altro client o tramite cURL.

   ```GraphQL
   mutation {
       createEmptyCart
   }
   ```

   (Nota: impostare **[!UICONTROL Header]** a [!UICONTROL Content-Currency:CA] prima di eseguirlo).

   ```cURL
   curl --location 'http://yourMagentoDomain/graphql' \--header 'Content-Currency: CA' \--header 'Content-Type: application/json' \--header 'Cookie: PHPSESSID=b5147f63fe5014ea523f262946; private_content_version=8d53dfda210a6e9bc46f4e4a01ffd6c5' \--data '{"query":"mutation {\r\n  createEmptyCart\r\n}","variables":{}}'
   ```

<u>Risultati previsti</u>:

Non esiste *Eccezione 500* nei registri, `GraphQLOperationNames` la chiave viene gestita correttamente.

<u>Risultati effettivi</u>:

È presente un *Eccezione 500* nei registri, `GraphQLOperationNames` la chiave non viene gestita correttamente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
