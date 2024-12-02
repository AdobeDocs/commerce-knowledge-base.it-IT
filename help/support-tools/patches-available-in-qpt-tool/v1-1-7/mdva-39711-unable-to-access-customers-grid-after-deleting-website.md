---
title: 'MDVA-39711: impossibile accedere alla griglia clienti dopo l''eliminazione del sito Web'
description: La patch MDVA-39711 risolve il problema che impediva all'utente amministratore di accedere alla griglia dei clienti dopo l'eliminazione del sito Web. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7. L'ID della patch è MDVA-39711. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: 46bef304-9360-4b69-b064-631725de381c
feature: Configuration
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-39711: impossibile accedere alla griglia clienti dopo l&#39;eliminazione del sito Web

La patch MDVA-39711 risolve il problema che impediva all&#39;utente amministratore di accedere alla griglia dei clienti dopo l&#39;eliminazione del sito Web. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7. L&#39;ID della patch è MDVA-39711. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7-p2, 2.3.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente amministratore non può accedere alla griglia dei clienti dopo l’eliminazione del sito web.

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo sito Web, store e visualizzazione store.
1. Crea un nuovo cliente nell’amministratore e associalo al sito web creato.
1. Vai a **Archivi** > **Tutti gli archivi** ed elimina il sito Web creato.
1. Vai a **Clienti** > **Tutti i clienti**.

<u>Risultati previsti</u>:

* Nessun messaggio di errore.
* Tutti i clienti sono visibili nella griglia.

<u>Risultati effettivi</u>:

* L&#39;utente riceve un messaggio di errore: *Impossibile trovare il sito Web con ID 2 richiesto. Verifica il sito Web e riprova*
* Tutti i clienti non vengono visualizzati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella documentazione per gli sviluppatori.
