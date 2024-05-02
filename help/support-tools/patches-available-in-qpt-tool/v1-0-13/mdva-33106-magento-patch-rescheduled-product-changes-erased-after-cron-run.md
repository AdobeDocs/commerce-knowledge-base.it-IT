---
title: "Patch MDVA-33106: le modifiche del prodotto ripianificate vengono cancellate dopo l'esecuzione del cron"
description: La patch MDVA-33106 risolve il problema relativo alla cancellazione delle modifiche al prodotto riprogrammate dopo il cron
exl-id: be32982c-796c-4069-ad70-37b5124ffb56
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Patch MDVA-33106: le modifiche del prodotto ripianificate vengono cancellate dopo l&#39;esecuzione del cron

La patch MDVA-33106 risolve il problema relativo alla cancellazione delle modifiche al prodotto riprogrammate dopo il cron

```bash
bin/magento cron:run
```

viene eseguito. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. In Commerce Admin, vai a **Catalogo** > **Prodotti** e fai clic su modifica. Osserva **Prezzo** valore, ad esempio *9,99*.
1. Clic **Pianifica nuovo aggiornamento** e inserire i dettagli:
   * Il nome dell&#39;aggiornamento non è importante.
   * Imposta una data futura, +1 anno per la data di inizio e la data di fine.
   * Imposta prezzo su *1,99*.
   * Salva le modifiche.
1. Vai alla dashboard di staging del contenuto e seleziona la vista a griglia per vedere se la corrispondenza pianificata qui sopra è valida.
1. Seleziona Modifica azione accanto all’aggiornamento pianificato. I dati devono comunque corrispondere a quelli riportati sopra.
1. Modifica la data pianificata con un valore più vicino. Invece di +1 anno da ora, modificalo in + 1 settimana o + 1 mese.
1. Salva le modifiche e controlla se le date sono aggiornate nel dashboard di staging.
1. Attendere l&#39;esecuzione di un processo cron.
1. Fai clic di nuovo su Modifica nella modifica pianificata e controlla il prezzo.

<u>Risultati previsti</u>:

Il prezzo è 1,99.

<u>Risultati effettivi</u>:

Il prezzo è 9,99.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
