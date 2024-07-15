---
title: "MDVA-36424: le immagini allegate al generatore di pagine scompaiono al momento del salvataggio"
description: La patch MDVA-36424 risolve il problema che causa la scomparsa delle immagini allegate agli elementi Page Builder quando la categoria viene salvata per la seconda volta in più siti Web, con l'URL di base del sito Web predefinito diverso da quello dell'amministratore. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21. L'ID della patch è MDVA-36424. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: ae15db2d-0d9f-48c1-87e4-61da1558a57c
feature: Categories, Page Builder
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 0%

---

# MDVA-36424: le immagini allegate al generatore di pagine scompaiono al momento del salvataggio

La patch MDVA-36424 risolve il problema che causa la scomparsa delle immagini allegate agli elementi Page Builder quando la categoria viene salvata per la seconda volta in più siti Web, con l&#39;URL di base del sito Web predefinito diverso da quello dell&#39;amministratore. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.21. L&#39;ID della patch è MDVA-36424. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.6

**Compatibile con le versioni di Magento:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.5 - 2.4.1-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le immagini multimediali allegate agli elementi del generatore di pagine non vengono salvate se l’URL di base del back-end è diverso dall’URL di base della vetrina.

<u>Passaggi da riprodurre</u>:

1. Creare un secondo sito Web - sito Web2.
1. Imposta un URL di base diverso per il sito web2 (l’URL di base utilizzato nell’amministratore deve essere diverso dal secondo sito web).
1. Imposta il secondo sito Web come sito Web predefinito (**Archivi** > *Impostazioni* > **Tutti gli archivi** > Seleziona il secondo sito Web > Imposta come *Predefinito*).
1. Passa alla pagina categoria nel backend e passa a una vista di modifica delle categorie.
1. Passa a **Contenuto** > *Descrizione*.
1. Aggiungi una colonna al contenuto e imposta un’immagine di sfondo utilizzando la galleria di file multimediali.
1. Salva la categoria.
1. Vai di nuovo a **Contenuto** > *Descrizione*; l&#39;immagine salvata verrà visualizzata correttamente.
1. Salva di nuovo la categoria.
1. Vai a **Contenuto** > *Descrizione*.

<u>Risultati previsti</u>:

L’immagine non viene rimossa durante il salvataggio della categoria.

<u>Risultati effettivi</u>:

L’immagine viene rimossa dopo un secondo salvataggio della categoria.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
