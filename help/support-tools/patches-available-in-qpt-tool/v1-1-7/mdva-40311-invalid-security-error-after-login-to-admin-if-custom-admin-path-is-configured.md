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

La patch di MDVA-40311 risolve il problema relativo al messaggio di errore ricevuto dall&#39;utente amministratore: *Protezione o chiave del modulo non valida. Aggiornare la pagina* dopo aver effettuato l&#39;accesso all&#39;amministratore se il percorso di amministrazione personalizzato è configurato e la chiave segreta è abilitata. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.7. L&#39;ID della patch è MDVA-40311. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;utente amministratore riceve un messaggio di errore: *Sicurezza o chiave modulo non valida. Aggiornare la pagina* dopo aver effettuato l&#39;accesso all&#39;amministratore se il percorso di amministrazione personalizzato è configurato e la chiave segreta è abilitata.

<u>Passaggi da riprodurre</u>:

* Accedi come utente amministratore utilizzando un nome utente e una password validi.

<u>Risultati previsti</u>:

L’utente è in grado di accedere senza alcun messaggio di errore.

<u>Risultati effettivi</u>:

*Chiave modulo o protezione non valida. Aggiorna il messaggio di errore della pagina*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
