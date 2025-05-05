---
title: 'MDVA-39605: valore TTL della cache Redis (data di scadenza) errato'
description: La patch MDVA-39605 risolve il problema in cui il valore TTL (data di scadenza) della cache Redis è errato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L'ID della patch è MDVA-39605. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 7283838b-702d-4ddc-aa03-829dbf5aa91f
feature: Cache, Console, Services
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---

# MDVA-39605: valore TTL della cache Redis (data di scadenza) errato

La patch MDVA-39605 risolve il problema in cui il valore TTL (data di scadenza) della cache Redis è errato. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L&#39;ID della patch è MDVA-39605. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il valore TTL (data di scadenza) della cache Redis non è corretto.

<u>Passaggi da riprodurre</u>:

Per testare la correzione, svuota la cache e apri un prodotto configurabile nella vetrina. Quindi apri un terminale (console) e segui i passaggi seguenti:

1. Eseguire il comando: `redis-cli`.
1. Esegui `KEYS "*PRICE"` (dovrebbe essere presente una sola chiave nel risultato, ad esempio `zc:ti:e54_PRICE`). Copiate la chiave.
1. Esegui `SMEMBERS` seguito dalla chiave del passaggio precedente (ad esempio, `SMEMBERS zc:ti:e54_PRICE`). Copia qualsiasi chiave dal risultato (ad esempio, e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421).
1. Eseguire `KEYS "*<key>"` con il nome della chiave del passaggio precedente per ottenere il nome completo della chiave, ad esempio `KEYS "*e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421"`. Il risultato deve contenere una sola chiave (ad esempio, `zc:k:e54_4E67B390D5C28FC7C3D9BB0D37AB3F7B5E576421`). Come si può notare, il nome completo della chiave è semplicemente il nome della chiave con prefisso &quot;`zc:k:`&quot;. Ora copia il nome completo della chiave.
1. Eseguire `HGETALL` seguito dal nome completo della chiave del passaggio 4 per verificare il valore. Il valore deve contenere dati serializzati dei prodotti associati di un prodotto configurabile correlato.
1. Eseguire `TTL` seguito dal nome completo della chiave del passaggio 4 per verificare se la chiave ha una scadenza. Il risultato deve essere diverso da **-1** e **-2** e deve essere approssimativamente 2592000 (30 giorni). Anche se la scadenza impostata nel codice è un anno, la libreria Redis utilizzata in Adobe Commerce ha un limite massimo di scadenza difficile di 2592000.

<u>Risultati previsti</u>:

Il limite di scadenza è 2592000s

<u>Risultati effettivi</u>:

Il limite di scadenza è impostato su **-1** o **-2**.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
