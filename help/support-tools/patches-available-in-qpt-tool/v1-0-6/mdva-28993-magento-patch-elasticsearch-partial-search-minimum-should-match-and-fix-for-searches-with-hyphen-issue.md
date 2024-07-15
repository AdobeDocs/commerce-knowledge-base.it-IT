---
title: '''MDVA-28993: Elasticsearch di ricerca parziale, "minimum should match" e correzione per "searches with hyphen" issue"'
description: La patch MDVA-28993 implementa la funzionalità "Minimum should match" (Minimo deve corrispondere) e la ricerca parziale per il motore di Elasticsearch, e risolve i problemi con i trattini nelle query di ricerca. La patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6.
exl-id: 2af0f950-284b-42f2-9660-8aafce4b04d7
feature: Search, Services
role: Admin
source-git-commit: 6f4d6382cbdb7bedddcc3f264fbf6ef997729323
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-28993: Elasticsearch di ricerca parziale, &quot;minimum should match&quot; (il valore minimo deve corrispondere) e correzione per il problema &quot;searches with hyphen&quot; (ricerche con trattino)

La patch MDVA-28993 implementa la funzionalità &quot;Minimum should match&quot; (Minimo deve corrispondere) e la ricerca parziale per il motore di Elasticsearch, e risolve i problemi con i trattini nelle query di ricerca. La patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) v.1.0.6.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce sull&#39;infrastruttura cloud 2.3.4

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce on-premise/ Adobe Commerce on cloud infrastructure 2.3.4-2.3.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.


## Problema

Quando si utilizza l&#39;Elasticsearch 6 per la ricerca di SKU che contiene un trattino (-), la ricerca restituisce troppi risultati.

<u>Passaggi da riprodurre:</u>

1. Vai alla vetrina.

1. Nella barra di ricerca immettere una stringa contenente un trattino, ad esempio &quot;WS-M-Blue&quot;.

<u>Risultato previsto:</u>

Restituisce solo WS-M-Blue.

<u>Risultato effettivo:</u>

Restituisce tutti gli SKU che iniziano con &quot;WS&quot;.

## Dettagli patch

La patch MDVA-28993 contiene le correzioni e i miglioramenti seguenti:

* implementa la nuova funzionalità &quot;Minimum should match&quot; (Minimo deve corrispondere) e la ricerca parziale di un motore di Elasticsearch. Per informazioni sulla configurazione, consulta [Configurazione della ricerca nel catalogo](https://docs.magento.com/user-guide/catalog/search-configuration.html#step-4-configure-minimum-terms-to-match) nella guida utente.
* ricerca parziale di Elasticsearch
* risolve il problema &quot;ricerche con trattino&quot; descritto in precedenza.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
