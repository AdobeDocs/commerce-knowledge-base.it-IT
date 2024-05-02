---
title: "MDVA-37874: sconto fisso non applicato all’intero carrello"
description: La patch MDVA-37874 risolve il problema quando l'**importo di sconto fisso** per l'intero carrello viene erroneamente applicato a un prodotto bundle contenente più di un'opzione. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.24. L'ID della patch è MDVA-37874. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.
exl-id: a1c414f0-b654-4b18-b502-47351513ddfa
feature: Orders, Personalization, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# MDVA-37874: sconto fisso non applicato all&#39;intero carrello

La patch MDVA-37874 risolve il problema quando **importo sconto fisso** per l’intero carrello viene erroneamente applicato a un pacchetto di prodotti contenente più di un’opzione. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.24. L&#39;ID della patch è MDVA-37874. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

* La patch è stata progettata per Adobe Commerce sull’infrastruttura cloud 2.4.2
* La patch è compatibile anche con Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.3.6-2.3.7 e 2.4.1-2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema


<u>Passaggi da riprodurre</u>:

1. Creare una regola del carrello con un **importo sconto fisso** per tutto il carrello.
1. Aggiungi un prodotto bundle al carrello (il prodotto bundle deve contenere diverse opzioni selezionate).
1. Vai alla pagina del carrello e controlla lo sconto.


<u>Risultati previsti</u>:

L&#39;importo dello sconto fisso viene applicato all&#39;intero carrello, come previsto.

<u>Risultati effettivi</u>:

L&#39;importo dello sconto fisso viene applicato solo a una parte del carrello.


## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti, a seconda del prodotto Adobe Commerce:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
