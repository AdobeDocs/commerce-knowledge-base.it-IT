---
title: "ACSD-45849: i metadati video vengono persi dopo l’aggiornamento dell’area di gestione temporanea"
description: La patch ACSD-45849 risolve il problema della perdita dei metadati video dopo l’applicazione di un aggiornamento di staging. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18. L’ID della patch è ACSD-45849. Il problema è stato risolto in Adobe Commerce 2.4.4.
exl-id: 071a535d-f96c-4731-a17c-0b7bf8a87372
feature: Staging, Page Content
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 0%

---

# ACSD-45849: i metadati video vengono persi dopo l’aggiornamento dello staging

La patch ACSD-45849 risolve il problema della perdita dei metadati video dopo l’applicazione di un aggiornamento di staging. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.18. L’ID della patch è ACSD-45849. Il problema è stato risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.3-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I metadati video vengono persi dopo l’applicazione di un aggiornamento di staging.

<u>Passaggi da riprodurre</u>:

1. Configurare la chiave API di YouTube in **Amministratore** > **Negozi** > **Configurazione** > **Catalogo** > **Video prodotto**.
1. Crea un prodotto con un video YouTube. L’URL, il titolo e la descrizione sono compilati.
1. Crea un nuovo aggiornamento pianificato per il prodotto con tutti i parametri senza modificare il *Immagini e video* sezione.
1. Fai clic su **Visualizza/Modifica** in Modifiche pianificate.
1. Vai a **Immagini e video** e fai clic sul video.

<u>Risultati previsti</u>:

L’URL, il titolo e la descrizione contengono dati appropriati.

<u>Risultati effettivi</u>:

I campi URL, titolo e descrizione sono vuoti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
