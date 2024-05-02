---
title: "MDVA-36832: immagini duplicate su pagine con larghezza di visualizzazione di 768 px"
description: La patch MDVA-36832 risolve il problema relativo alla duplicazione di immagini su pagine con larghezza di visualizzazione di 768 px. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24. L'ID della patch è MDVA-36832. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 3eb0c11b-d93a-4676-afd1-8f6592c6cd6d
feature: Configuration, Storefront
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-36832: immagini duplicate su pagine con una larghezza di visualizzazione di 768 px

La patch MDVA-36832 risolve il problema relativo alla duplicazione di immagini su pagine con larghezza di visualizzazione di 768 px. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.24. L&#39;ID della patch è MDVA-36832. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Immagini duplicate su pagine con larghezza di visualizzazione di 768 px.

<u>Passaggi da riprodurre:</u>

1. Vai a backend > CONTENUTO > Pagine e modifica qualsiasi pagina.
1. Aggiungi un&#39;immagine alla pagina.
1. Vai a pagina front-end e apri pagina modificata.
1. Apri gli strumenti per sviluppatori in Chrome.
1. Abilita &quot;visualizzazione dispositivo&quot; e seleziona iPad view (Visualizzazione dispositivo) oppure imposta la larghezza della pagina su 768 px.

<u>Risultato effettivo:</u>

L’immagine viene duplicata.

<u>Risultato previsto:</u>

Sulla pagina deve essere visibile una sola immagine aggiunta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
