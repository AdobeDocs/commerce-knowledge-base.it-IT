---
title: 'MDVA-35092: errore Vimeo: "Video non trovato"'
description: '''La patch MDVA-35092 risolve il problema relativo alla visualizzazione dell''errore: *"Video not Found"*. Questo messaggio di errore viene visualizzato quando immetti un video Vimeo utilizzando l’interfaccia nativa Aggiungi video nell’amministratore di prodotto di Adobe Commerce. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17. Il problema è stato risolto in Adobe Commerce 2.4.3."'
exl-id: bc0952d9-1ea4-417c-926c-96875984d82c
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '426'
ht-degree: 0%

---

# MDVA-35092: errore Vimeo: &quot;Video non trovato&quot;

La patch MDVA-35092 risolve il problema relativo alla visualizzazione dell&#39;errore: *&quot;Video non trovato&quot;*. Questo messaggio di errore viene visualizzato quando immetti un video Vimeo utilizzando l’interfaccia nativa Aggiungi video nell’amministratore di prodotto di Adobe Commerce. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.5 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’API semplice di Vimeo smette di funzionare come previsto.

<u>Passaggi da riprodurre</u>:

1. Accedi all’amministratore.
1. Per modificare un prodotto esistente, vai a **CATALOGO** > **Prodotti** > **Modifica**, o per creare un nuovo prodotto, vai a **CATALOGO** > **Prodotti** > **Modifica** > **Aggiungi prodotto**.
1. Fai clic su **Immagini E Video** nella pagina Prodotto.
1. Clic **Aggiungi video** e aggiungi l’URL di un video Vimeo. Clic **Salva**.

<u>Risultati previsti</u>:

Il nuovo video viene trovato e salvato.

<u>Risultati effettivi</u>:

Errore: *&quot;Video non trovato&quot;* viene visualizzato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
