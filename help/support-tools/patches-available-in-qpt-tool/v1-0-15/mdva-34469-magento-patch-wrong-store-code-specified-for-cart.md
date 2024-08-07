---
title: "MDVA-34469: il codice dell'archivio specificato per il carrello non è corretto"
description: "La patch MDVA-34469 risolve il problema relativo al messaggio di errore: *Codice di archiviazione errato specificato per il carrello* quando si aggiunge un prodotto al carrello dopo il passaggio da una visualizzazione all'altra. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15. L'ID della patch è MDVA-34469. Il problema è stato risolto in Adobe Commerce 2.4.2."
exl-id: 35d4f120-7fcf-4996-8b23-aca99cfc18ac
feature: Orders, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# MDVA-34469: specificato codice archivio errato per il carrello

La patch MDVA-34469 risolve il problema relativo al messaggio di errore: *Codice archivio errato specificato per il carrello* quando si aggiunge un prodotto al carrello dopo il passaggio da una visualizzazione all&#39;altra. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15. L&#39;ID della patch è MDVA-34469. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.4.1 - 2.4.1-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;utente visualizza un errore di query del carrello, *&quot;Codice archivio errato specificato per il carrello&quot;*, durante il tentativo di cambiare le visualizzazioni dell&#39;archivio.

<u>Prerequisiti</u>:

* Adobe Commerce 2.4.0.
* È configurato un singolo sito web con un singolo store e due visualizzazioni dello store.
* Viene creato un account cliente.

<u>Passaggi da riprodurre</u>:

1. Il backend di Adobe Commerce è configurato per avere due visualizzazioni store (con codici store: default, second).
1. L’utente crea un carrello utilizzando il codice store predefinito.
1. L&#39;utente tenta di recuperare questo carrello utilizzando il secondo codice store nell&#39;intestazione della richiesta `Store`.

<u>Risultati previsti</u>:

Il carrello viene visualizzato perché il passaggio dall&#39;archivio (invio del nuovo codice nell&#39;intestazione della richiesta `Store`) associa il carrello all&#39;archivio richiesto.

<u>Risultati effettivi</u>:

La query del carrello restituisce un errore e il carrello non viene visualizzato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
