---
title: '"MDVA-40311: errore "Sicurezza o chiave del modulo non valida" dopo l’accesso in Admin se è configurato un percorso di amministrazione personalizzato"'
description: "La patch di MDVA-40311 risolve il problema relativo al messaggio di errore ricevuto dall'utente amministratore: *Protezione o chiave del modulo non valida. Aggiorna la pagina* dopo aver effettuato l’accesso all’amministratore se il percorso di amministrazione personalizzato è configurato e la chiave segreta è abilitata. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7. L'ID della patch è MDVA-40311. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.4."
exl-id: d4562f09-0aed-438e-8c2e-90557aa2f146
feature: Admin Workspace, Compliance, Security
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '469'
ht-degree: 0%

---

# MDVA-40311: errore &quot;Sicurezza o chiave del modulo non valida&quot; dopo l&#39;accesso ad Admin se è configurato un percorso di amministrazione personalizzato

La patch di MDVA-40311 risolve il problema relativo al messaggio di errore ricevuto dall&#39;utente Admin: *Chiave modulo o protezione non valida. Aggiorna la pagina*, dopo l’accesso all’amministratore se il percorso di amministrazione personalizzato è configurato e la chiave segreta è abilitata. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7. L&#39;ID della patch è MDVA-40311. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente amministratore riceve un messaggio di errore: *Chiave modulo o protezione non valida. Aggiorna la pagina*, dopo l’accesso all’amministratore se il percorso di amministrazione personalizzato è configurato e la chiave segreta è abilitata.

<u>Passaggi da riprodurre</u>:

* Accedi come utente amministratore utilizzando un nome utente e una password validi.

<u>Risultati previsti</u>:

L’utente è in grado di accedere senza alcun messaggio di errore.

<u>Risultati effettivi</u>:

*Chiave modulo o protezione non valida. Aggiorna la pagina* viene visualizzato un messaggio di errore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
