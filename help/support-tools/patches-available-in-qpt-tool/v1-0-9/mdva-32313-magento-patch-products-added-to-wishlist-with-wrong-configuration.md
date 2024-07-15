---
title: "Patch MDVA-32313: prodotti aggiunti alla lista dei desideri con configurazione errata"
description: La patch MDVA-32313 risolve il problema che impediva l'aggiunta corretta dei prodotti configurabili alla lista dei desideri, poiché le configurazioni assegnate non sono corrette quando vengono aggiunti alla lista dei desideri. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10. Il problema è stato risolto nella versione 2.4.2 di Adobe Commerce.
exl-id: e7ac5ef5-1389-4108-b2bc-73d43eb3e7ca
feature: Configuration, Products
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '447'
ht-degree: 0%

---

# Patch MDVA-32313: prodotti aggiunti alla lista dei desideri con configurazione errata

La patch MDVA-32313 risolve il problema che impediva l&#39;aggiunta corretta dei prodotti configurabili alla lista dei desideri, poiché le configurazioni assegnate non sono corrette quando vengono aggiunti alla lista dei desideri. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.10. Il problema è stato risolto nella versione 2.4.2 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.0

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.3.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Crea un cliente.
1. Accedi all’account del cliente.
1. Passare alla pagina **Elenco prodotti**.
1. Scegli un prodotto configurabile (esempio: *configurabile\_1* ) e seleziona le opzioni di colore e dimensione preferite nella pagina **Elenco prodotti** (**Non aprire la pagina del prodotto.**).
1. Fai clic sull&#39;icona della lista dei desideri di un altro prodotto configurabile (Esempio: *configurabile\_2*) nella stessa pagina senza selezionare opzioni di colore/dimensione.

<u>Risultati previsti</u>:

Il prodotto *configurable\_2* viene aggiunto alla lista dei desideri senza le opzioni selezionate, come previsto.

<u>Risultati effettivi</u>:

Il prodotto *configurable\_2* aggiunto alla lista dei desideri con la configurazione del prodotto *configurable\_1*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta le [patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
