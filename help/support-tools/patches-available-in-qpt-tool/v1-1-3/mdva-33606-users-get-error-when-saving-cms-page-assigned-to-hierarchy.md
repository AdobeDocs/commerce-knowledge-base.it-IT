---
title: "MDVA-33606: errore durante il salvataggio della pagina CMS assegnata alla gerarchia"
description: La patch di MDVA-33606 risolve il problema relativo all'errore *Unique constraint viola found* (Violazione di vincolo univoca trovata) durante il salvataggio di una pagina CMS assegnata alla struttura gerarchica. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3. L'ID della patch è MDVA-33606. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: cdefece5-6d13-4003-87e9-810c665e940c
feature: CMS
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# MDVA-33606: errore durante il salvataggio della pagina CMS assegnata alla gerarchia

La patch MDVA-33606 risolve il problema relativo agli utenti *Violazione di vincolo univoco trovata* durante il salvataggio di una pagina CMS assegnata alla struttura gerarchica. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.3. L&#39;ID della patch è MDVA-33606. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1-2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si tenta di salvare una pagina CMS assegnata a una struttura gerarchica, viene visualizzato il messaggio di errore seguente: *Violazione di vincolo univoco trovata*.

<u>Passaggi da riprodurre</u>:

1. Crea una nuova pagina CMS. Imposta l&#39;ambito su Tutte le visualizzazioni dello store. Pagina 1 del CMS.
1. Crea una nuova visualizzazione store. Questa è la tua Store View 2.
1. Vai a **Contenuto** > **Gerarchia** > Aggiungere la pagina 1 del CMS alla struttura gerarchica.
1. Modificare l&#39;ambito in Visualizzazione archivio 2.
   * Deselezionare &quot;Use the parent node hierarchy&quot; (Utilizza la gerarchia dei nodi padre).
   * Aggiungi la pagina 1 del CMS a questo ambito e salvalo.
1. Ora modifica l’ambito in Visualizzazione archivio predefinita.
   * Deselezionare &quot;Use the parent node hierarchy&quot; (Utilizza la gerarchia dei nodi padre).
   * Aggiungi la pagina 1 del CMS a questo ambito e salvalo.
1. Vai a **Contenuto** > **Pagine** > **Aggiungi nuova pagina**.
   * Assegna alla pagina il titolo Pagina 2.
   * Nella sezione Pagina nei siti Web, assegna a Tutte le visualizzazioni del Negozio ed entrambe le visualizzazioni del Negozio (Visualizzazione predefinita del Negozio e Visualizzazione del Negozio 2) e fai clic su **Salva pagina**.
1. Nella pagina di modifica del CMS, apri la scheda Gerarchia.
   * Assegna pagina 2 al nodo Visualizzazione archivio 2, al nodo Predefinito e al nodo Tutti i siti Web.

<u>Risultati previsti</u>:

Puoi assegnare la pagina CMS a tutti e tre i nodi senza alcun errore.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore: *Violazione di vincolo univoco trovata*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md).
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md).

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sezione.
