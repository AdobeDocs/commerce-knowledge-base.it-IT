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

La patch MDVA-37874 risolve il problema quando l&#39;importo **fisso dello sconto** per l&#39;intero carrello non viene applicato correttamente a un prodotto bundle contenente più di un&#39;opzione. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.24. L&#39;ID della patch è MDVA-37874. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

* La patch è stata progettata per Adobe Commerce sull’infrastruttura cloud 2.4.2
* La patch è compatibile anche con Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.3.6-2.3.7 e 2.4.1-2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema


<u>Passaggi da riprodurre</u>:

1. Crea una regola carrello con **importo sconto fisso** per l&#39;intero carrello.
1. Aggiungi un prodotto bundle al carrello (il prodotto bundle deve contenere diverse opzioni selezionate).
1. Vai alla pagina del carrello e controlla lo sconto.


<u>Risultati previsti</u>:

L&#39;importo dello sconto fisso viene applicato all&#39;intero carrello, come previsto.

<u>Risultati effettivi</u>:

L&#39;importo dello sconto fisso viene applicato solo a una parte del carrello.


## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti, a seconda del prodotto Adobe Commerce:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
