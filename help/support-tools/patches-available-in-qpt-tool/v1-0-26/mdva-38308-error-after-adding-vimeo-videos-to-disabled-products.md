---
title: "MDVA-38308: errore dopo l’aggiunta di video Vimeo a prodotti disabilitati"
description: "La patch di qualità MDVA-38308 per Adobe Commerce risolve il problema se gli utenti ricevono il messaggio di errore: *Nota: indice non definito: estensione in /lib/internal/Magento/Framework/File/Uploader.php alla riga 806,* quando si aggiungono video Vimeo a prodotti disabilitati. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26. L'ID della patch è MDVA-38308. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.4."
exl-id: ed5fb9ec-c465-4bb9-8a29-4d5e4bd4c867
feature: Products
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# MDVA-38308: errore dopo l&#39;aggiunta di video Vimeo a prodotti disabilitati

La patch di qualità MDVA-38308 per Adobe Commerce risolve il problema relativo al messaggio di errore: *Avviso: indice non definito: estensione in /lib/internal/Magento/Framework/File/Uploader.php alla riga 806,* quando si aggiungono video Vimeo a prodotti disabilitati. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.26. L&#39;ID della patch è MDVA-38308. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
Adobe Commerce sull’infrastruttura cloud 2.4.1-p1, 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**
Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.5 - 2.3.6-p1, 2.4.0 - 2.4.1-p1, 2.4.2 - 2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si aggiungono video Vimeo a prodotti disabilitati, viene visualizzato il seguente messaggio di errore: *Avviso: Indice non definito: estensione in /lib/internal/Magento/Framework/File/Uploader.php alla riga 806*

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Disattiva il prodotto creato.
1. Prova ad aggiungere un video Vimeo al prodotto disabilitato.

<u>Risultati previsti</u>:

Il video viene aggiunto senza errori.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore:
*Avviso: indice non definito: estensione in /lib/internal/Magento/Framework/File/Uploader.php alla riga 806*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html)
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html)

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità nella nostra knowledge base di supporto, consulta:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md)
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md)

Per informazioni sulle altre patch disponibili nello strumento QPT, consulta la sezione [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) nella nostra knowledge base di supporto.
