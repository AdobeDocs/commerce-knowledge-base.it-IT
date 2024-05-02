---
title: "ACSD-51907: l’utente amministratore con restrizioni non può creare una nota di credito per il rimborso offline"
description: Applica la patch ACSD-51907 per risolvere il problema di Adobe Commerce, per cui l’utente amministratore con restrizioni non può creare una nota di credito con rimborso offline.
exl-id: 564e8524-f2dc-453c-be78-a920fbd47d71
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-51907: l&#39;utente amministratore con restrizioni non può creare una nota di credito per il rimborso offline

La patch ACSD-51907 risolve il problema di prestazioni che impediva all&#39;utente amministratore con restrizioni di creare una nota di credito con rimborso offline. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.33. L’ID della patch è ACSD-51907. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 &lt; 2.4.3-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un utente amministratore con restrizioni non può creare una nota di credito con un rimborso offline.

<u>Passaggi da riprodurre</u>:

1. Creare un **cliente** nel sito Web predefinito.
1. Crea **nuovo sito web** con relativo *archiviare* e *visualizzazione store*.
1. Imposta il sito Web predefinito sul nuovo sito Web, cancella le cache.
1. Modifica configurazione cliente: **Amministratore** > **Archivia** > **Configurazione** > **Clienti** > **Configurazione cliente** > **Condividi account cliente = Globale**.
1. Crea un nuovo ruolo utente amministratore con l’ambito del ruolo impostato sul nuovo sito web creato *(accesso solo ai dati di vendita)* in **Amministratore** > **Sistema** > **Autorizzazioni**.
1. Crea un nuovo account amministratore con questo ruolo.
1. Crea nuovo ordine utilizzando il metodo di pagamento online *(esempio: Auth.net o PayPal)*.
1. Accedi come utente amministratore con restrizioni.
1. Vai a **Vendite** > **Ordini** > then **pagina di visualizzazione ordine**.
1. Creare una fattura.
1. Passare alla scheda Fatture.
1. Fai clic su **Fattura**.
1. Fai clic su **[!UICONTROL Credit Memo]**.
1. Controlla la **[!UICONTROL Refund to Store Credit]** , impostare il campo di testo accanto alla casella di controllo *1* valore.
1. Fai clic sul pulsante **[!UICONTROL Refund Offline]** pulsante.

<u>Risultati previsti</u>:

Viene creata la nota di credito e *$ 1* viene rimborsato al credito del punto vendita.

<u>Risultati effettivi</u>:

Il messaggio di errore, *Sono necessarie altre autorizzazioni per visualizzare questo elemento* viene visualizzato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
