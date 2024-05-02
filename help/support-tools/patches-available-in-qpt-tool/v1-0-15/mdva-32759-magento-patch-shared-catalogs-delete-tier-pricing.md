---
title: "Patch MDVA-32759: i cataloghi condivisi eliminano i prezzi del livello"
description: La patch MDVA-32759 risolve il problema relativo all'eliminazione dei prezzi dei livelli esistenti nei cataloghi condivisi.
exl-id: c6192d2f-cd25-483e-ba69-01ca62996faf
feature: B2B, Catalog Management
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Patch MDVA-32759: cataloghi condivisi, eliminazione dei prezzi di livello

La patch MDVA-32759 risolve il problema relativo all&#39;eliminazione dei prezzi dei livelli esistenti nei cataloghi condivisi.

Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.4-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Prerequisiti</u>:

Installare Adobe Commerce con B2B, **Caratteristiche B2B** abilitato.

<u>Passaggi da riprodurre</u>:

1. Vai a **Archivi > Configurazione > Funzioni B2B > Abilita società** e **Catalogo condiviso**.
1. Esegui `bin/magento cron:run`.
1. Crea un prodotto semplice, fai clic su **Advanced Pricing**, e aggiungi **Prezzo catalogo e livello**, quindi salvarlo.
1. Vai a **Catalogo > Catalogo condiviso > Imposta determinazione prezzi e struttura**, fai clic su **Configura** e dal menu a discesa, deseleziona tutte le opzioni e salva.
1. Esegui `bin/magento cron:run`.
1. Apri il prodotto creato in precedenza e controlla i prezzi avanzati.

<u>Risultati previsti</u>:

I prezzi di livello non devono essere rimossi dai prodotti dopo aver rimosso tutti i prodotti dal catalogo condiviso pubblico, come previsto.

<u>Risultati effettivi</u>:

I prezzi dei livelli vengono rimossi dopo la rimozione di tutti i prodotti dal catalogo condiviso pubblico.


## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
