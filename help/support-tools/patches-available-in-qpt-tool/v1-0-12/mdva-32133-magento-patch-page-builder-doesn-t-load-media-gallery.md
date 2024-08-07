---
title: "Patch MDVA-32133: il generatore di pagine non carica la raccolta multimediale"
description: La patch MDVA-32133 risolve il problema relativo al mancato caricamento di Media Gallery. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.3.
exl-id: c0ce799d-b452-4044-9635-4218db3904ef
feature: CMS, Media, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Patch MDVA-32133: il generatore di pagine non carica la raccolta multimediale

La patch MDVA-32133 risolve il problema relativo al mancato caricamento di Media Gallery. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.0

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.4.0 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

È stato risolto il problema che causava il caricamento molto lento o nullo della cronologia degli ordini.

<u>Passaggi da riprodurre</u>:

1. Modifica la pagina cms selezionata.
1. Espandi Contenuto e fai clic su **Modifica con Page Builder**.
1. Espandere Media. Trascina e rilascia l’immagine nell’area Riga.
1. Fare clic su **Seleziona dalla raccolta**.
1. È possibile disconnettersi e quindi accedere tramite un&#39;altra finestra.

<u>Risultati previsti</u>:

La raccolta multimediale è caricata.

<u>Risultati effettivi</u>:

Raccolta multimediale non caricata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta le [patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
