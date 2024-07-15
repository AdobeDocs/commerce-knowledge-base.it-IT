---
title: "MDVA-35312: una richiesta GraphQL vuota genera un errore 500, non 200 OK"
description: La patch MDVA-35312 risolve il problema che causa la generazione del codice di risposta di errore 500 da parte di una richiesta GraphQL vuota. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. L'ID della patch è MDVA-35312. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: 345fdbd4-8a43-4aab-a318-72792c8a7a78
feature: GraphQL
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# MDVA-35312: una richiesta GraphQL vuota genera un errore 500 diverso da 200 OK

La patch MDVA-35312 risolve il problema che causa la generazione del codice di risposta di errore 500 da parte di una richiesta GraphQL vuota. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.18. L&#39;ID della patch è MDVA-35312. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione del Magento:**

Adobe Commerce sull’infrastruttura cloud 2.4.2

**Compatibile con le versioni di Magento:**

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.4.1-p1-2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Una richiesta GraphQL vuota genera il codice di risposta di errore 500 invece del codice 200.

<u>Passaggi da riprodurre</u>:

Invia una richiesta GraphQL, ad esempio:

```curl
curl -i -X OPTIONS http://inv.test/graphql
```

<u>Risultati previsti</u>:

Risposta: *200 OK*.

<u>Risultati effettivi</u>:

Risposta: *Errore interno del server HTTP/1.1 500*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
