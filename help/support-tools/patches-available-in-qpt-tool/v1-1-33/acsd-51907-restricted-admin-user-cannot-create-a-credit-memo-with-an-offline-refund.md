---
title: 'ACSD-51907: l''utente amministratore con restrizioni non può creare una nota di credito per il rimborso offline'
description: Applica la patch ACSD-51907 per risolvere il problema di Adobe Commerce, per cui l’utente amministratore con restrizioni non può creare una nota di credito con rimborso offline.
exl-id: 564e8524-f2dc-453c-be78-a920fbd47d71
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-51907: l&#39;utente amministratore con restrizioni non può creare una nota di credito per il rimborso offline

La patch ACSD-51907 risolve il problema di prestazioni che impediva all&#39;utente amministratore con restrizioni di creare una nota di credito con rimborso offline. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.33. L’ID della patch è ACSD-51907. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un utente amministratore con restrizioni non può creare una nota di credito con un rimborso offline.

<u>Passaggi da riprodurre</u>:

1. Crea un **cliente** nel sito Web predefinito.
1. Crea **nuovo sito Web** con *archivio* e *visualizzazione archivio* correlati.
1. Imposta il sito Web predefinito sul nuovo sito Web, cancella le cache.
1. Cambia configurazione cliente: **Amministratore** > **Archivio** > **Configurazione** > **Clienti** > **Configurazione cliente** > **Condividi account cliente = Globale**.
1. Crea un nuovo ruolo utente amministratore con l&#39;ambito del ruolo impostato sul nuovo sito Web creato *(solo accesso ai dati di vendita)* in **Amministratore** > **Sistema** > **Autorizzazioni**.
1. Crea un nuovo account amministratore con questo ruolo.
1. Crea un nuovo ordine utilizzando il metodo di pagamento online *(ad esempio, Auth.net o PayPal)*.
1. Accedi come utente amministratore con restrizioni.
1. Vai a **Vendite** > **Ordini** > quindi a **pagina di visualizzazione ordini**.
1. Creare una fattura.
1. Passare alla scheda Fatture.
1. Fare clic su **Fattura**.
1. Fai clic su **[!UICONTROL Credit Memo]**.
1. Selezionare la casella di controllo **[!UICONTROL Refund to Store Credit]**, impostare il campo di testo accanto al valore *1*.
1. Fare clic sul pulsante **[!UICONTROL Refund Offline]**.

<u>Risultati previsti</u>:

La nota di credito viene creata e *$1* viene rimborsato al credito dell&#39;archivio.

<u>Risultati effettivi</u>:

Viene visualizzato il messaggio di errore *Sono necessarie altre autorizzazioni per visualizzare questo elemento*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
