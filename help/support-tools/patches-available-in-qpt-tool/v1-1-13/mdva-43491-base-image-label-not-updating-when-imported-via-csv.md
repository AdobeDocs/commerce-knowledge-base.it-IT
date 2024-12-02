---
title: 'MDVA-43491: l''etichetta dell''immagine di base non viene aggiornata se importata tramite CSV'
description: La patch MDVA-43491 risolve il problema per cui la "base_image_label" non viene aggiornata quando viene importata tramite un file CSV per un sito web multi-store. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L'ID della patch è MDVA-43491. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: d744423a-f582-4410-8d66-861229cce1b5
feature: Data Import/Export
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# MDVA-43491: l&#39;etichetta dell&#39;immagine di base non viene aggiornata se importata tramite CSV

La patch MDVA-43491 risolve il problema per cui `base_image_label` non viene aggiornato quando viene importato tramite un file CSV per un sito Web multi-store. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.13. L&#39;ID della patch è MDVA-43491. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.5 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

`base_image_label` non viene aggiornato se importato utilizzando un file CSV per un sito Web multischermo.

<u>Prerequisiti</u>:

Uno o più siti Web, archivi e visualizzazioni dello store non predefiniti esistenti.

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo prodotto.

   * Carica un’immagine.
   * Assegna il prodotto ai nuovi siti Web creati.

1. Esporta il prodotto come file CSV.
1. Aggiorna `base_image_label` per ogni visualizzazione archivio duplicando la riga predefinita del file CSV.
1. Importa il file CSV. Le etichette di ogni archivio verranno aggiornate correttamente, che possono essere verificate nella scheda **Immagini e video** nella pagina di modifica del prodotto.
1. Esporta nuovamente il file CSV e aggiorna la colonna `base_image_label` con valori diversi.
1. Importa di nuovo il file CSV.
1. Apri il prodotto in Admin e controlla se l’etichetta è stata aggiornata per ogni visualizzazione store.

<u>Risultati previsti</u>:

Il testo alternativo (etichetta immagine) viene aggiornato con il valore specifico per lo store in base al file CSV.

<u>Risultati effettivi</u>:

Testo alternativo (etichetta immagine) non aggiornato con il valore `base_image_label` nel file CSV.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella documentazione per gli sviluppatori.
