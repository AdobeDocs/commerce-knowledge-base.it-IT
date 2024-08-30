---
title: "ACSD-58446: l’eliminazione di un team con utenti o team secondari tramite GraphQL genera un messaggio di errore non informativo"
description: Applica la patch ACSD-58446 per risolvere il problema di Adobe Commerce, in cui l’eliminazione di un team con utenti o team secondari tramite GraphQL restituisce un messaggio di errore non informativo non coerente con l’interfaccia utente.
feature: Product, GraphQL, Company
role: Admin, Developer
source-git-commit: ab290f7c5b052aa220b3ef003febd9afc1cfdf00
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# ACSD-58446: l’eliminazione di un team con utenti o team secondari tramite GraphQL genera un messaggio di errore non informativo

La patch ACSD-58446 risolve il problema Adobe Commerce, in cui l’eliminazione di un team con utenti o team secondari tramite GraphQL restituisce un messaggio di errore non informativo non coerente con l’interfaccia utente. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.49. L’ID della patch è ACSD-58446. Il problema è pianificato per essere risolto in Adobe Commerce B2B 1.5.1

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p4

**Compatibile con le versioni Adobe Commerce e Magento Open Source:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’eliminazione di un team con utenti o team secondari tramite GraphQL restituisce un messaggio di errore non informativo non coerente con l’interfaccia utente.

## Condizioni preliminari:

Moduli B2B installati.

<u>Passaggi da riprodurre</u>:

1. Abilitare la funzionalità *[!UICONTROL Company]*.
1. Crea un nuovo account aziendale.
1. Accedi a **[!UICONTROL Admin]** e attiva l&#39;account aziendale.
1. Controlla l’e-mail e imposta una password per il nuovo account aziendale.
1. Crea un nuovo team per l’azienda.
1. Accedi come **[!UICONTROL company user]** sul front-end e aggiungi **[!UICONTROL new user]** per il team creato.
1. Accedi a **[!UICONTROL Admin]**, disabilita l&#39;utente della società e imposta *[!UICONTROL Customer Active]* = *No*
1. Assicurati di eliminare il team creato tramite GraphQL.

   ```
   mutation {
     deleteCompanyTeam(
       id: "MQ=="
     ) {
       success
     }
   }
   ```

<u>Risultati previsti</u>:

Viene restituito un messaggio di errore informativo coerente con l’interfaccia utente.

<u>Risultati effettivi</u>:

Viene restituito un messaggio generico di errore interno del server.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
