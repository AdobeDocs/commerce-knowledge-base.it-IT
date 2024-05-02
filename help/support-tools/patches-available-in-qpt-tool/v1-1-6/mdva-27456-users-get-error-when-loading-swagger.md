---
title: "MDVA-27456: gli utenti ricevono un errore durante il caricamento di Swagger"
description: La patch di MDVA-27456 risolve il problema relativo all'errore che si verifica quando si tenta di caricare Swagger. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6. L'ID della patch è MDVA-27456. Il problema è stato risolto in Adobe Commerce 2.3.7.
exl-id: e331595f-a94b-4070-803a-60f559735b29
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# MDVA-27456: errore durante il caricamento di Swagger

La patch di MDVA-27456 risolve il problema relativo all&#39;errore che si verifica quando si tenta di caricare Swagger. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.6. L&#39;ID della patch è MDVA-27456. Il problema è stato risolto in Adobe Commerce 2.3.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.5-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.5 - 2.3.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti ricevono un errore durante il caricamento di Swagger.

<u>Passaggi da riprodurre</u>:

Vai a `../swagger.`

<u>Risultati previsti</u>:

Swagger si carica senza alcun errore.

<u>Risultati effettivi</u>:

Gli utenti ricevono il seguente errore: *Impossibile caricare la definizione dell&#39;API*. Il registro errori contiene:

*report.CRITICAL: ID report: webapi-5ea9c6da19cb1; Messaggio: il tipo di parametro &quot;\DateTime&quot; non è valido. Verifica il parametro e riprova.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
