---
title: "ACSD-53643: l’ordine presenta un totale errato al momento dell’inserimento di un ordine fornitore"
description: Applicare la patch ACSD-53643 per risolvere il problema Adobe Commerce in cui l'ordine presenta un totale errato quando si effettua un ordine con prodotti disabilitati o esauriti.
feature: B2B
role: Admin, Developer
exl-id: 9843e07a-8a17-401e-98bc-559df5148d34
source-git-commit: 2356ac10b05ae9f38e5c0ca90d9156b0fc405718
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# ACSD-53643: l’ordine presenta un totale errato al momento del posizionamento di un ordine fornitore

La patch ACSD-53643 risolve il problema relativo a un totale non corretto dell&#39;ordine quando si effettua un ordine di acquisto con prodotti disabilitati o esauriti. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41. L’ID della patch è ACSD-53643. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il totale dell’ordine non è corretto quando si effettua un ordine di acquisto con prodotti disabilitati o esauriti.

<u>Passaggi da riprodurre</u>:

1. Installa *[!UICONTROL B2B]* e *[!UICONTROL Inventory]*.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B]** e imposta **[!UICONTROL Company]** = *Sì* e **[!UICONTROL Purchase Order]** = *Sì*.
1. Cancella la cache di configurazione.
1. Crea una nuova società, attivala e abilita *[!UICONTROL Purchase order]* per l&#39;azienda.
1. Crea un nuovo utente per l’azienda.
1. Creare un *Regola di approvazione* per approvare tutti gli ordini superiori a *1 USD* dall’amministratore della società.
1. Crea un’origine aggiuntiva.
1. Accedi come nuovo utente aziendale.
1. Aggiungi due prodotti al carrello e invia un ordine di acquisto.
1. Disattiva il secondo prodotto.
1. Accedi come amministratore della società.
1. Aprire l&#39;ordine di acquisto e verificare che l&#39;ordine di acquisto contenga entrambi i prodotti e che il totale sia relativo a entrambi.
1. Approva l&#39;ordine fornitore.
1. Effettua l’ordine.
1. Apri i dettagli dell’ordine.

<u>Risultati previsti</u>:

* Impossibile effettuare l&#39;ordine anche se un prodotto nell&#39;ordine è *disabilitato* o *esaurito*.
* *[!UICONTROL Place Order]* è nascosto.

<u>Risultati effettivi</u>:

L&#39;ordine inoltrato contiene solo il primo prodotto attivo, ma il totale dell&#39;ordine viene calcolato per entrambi i prodotti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
