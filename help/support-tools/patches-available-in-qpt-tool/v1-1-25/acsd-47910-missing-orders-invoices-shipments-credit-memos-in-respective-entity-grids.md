---
title: "ACSD-47910: ordini, fatture, spedizioni e note di accredito mancanti nelle rispettive griglie entità"
description: Applicare la patch ACSD-47910 per risolvere il problema Adobe Commerce in presenza di ordini, fatture, spedizioni e note di accredito mancanti nelle rispettive griglie entità.
exl-id: 4eb897ec-16e4-420e-89a6-c8f7c8740303
feature: Admin Workspace, Invoices, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---

# ACSD-47910: ordini, fatture, spedizioni e note di accredito mancanti nelle rispettive griglie entità

La patch ACSD-47910 risolve il problema relativo a ordini, fatture, spedizioni e note di accredito mancanti nelle rispettive griglie entità. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.25. L’ID della patch è ACSD-47910. La versione in cui verrà risolto il problema non è ancora disponibile.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p1

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Ordini, fatture, spedizioni e note di accredito mancanti nelle rispettive griglie entità.

<u>Passaggi da riprodurre</u>:

1. Abilita **[!UICONTROL Asynchronous indexing]** a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]**.
1. Effettuare due ordini.
1. Esegui la cron per sincronizzare questi ordini con la griglia.
1. Aprire uno degli ordini e prepararlo per la fatturazione. NON INVIARE ANCORA LA FATTURA.
1. Crea un nuovo ordine pronto per essere inserito sul front-end. NON FARE ANCORA CLIC SUL PULSANTE INSERISCI ORDINE.
1. Aggiungi un `sleep(30)` nel `foreach` a `NotSyncedDataProvider::L43`.
1. Esegui `bin/magento cron:run`.
1. Ora inserisci il nuovo ordine.
1. Fattura l&#39;ordine precedente.
1. Esegui di nuovo il cron in attesa della sincronizzazione del nuovo ordine.
1. Vai alla griglia dell’ordine nell’amministratore.

<u>Risultati previsti</u>:

Il nuovo ordine dovrebbe essere visualizzato nella griglia dell&#39;ordine.

<u>Risultati effettivi</u>:

L&#39;aggiornamento dell&#39;ordine precedente è stato sincronizzato con la griglia (**[!UICONTROL status: Processing]**). Il nuovo ordine non viene mai visualizzato sulla griglia.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
