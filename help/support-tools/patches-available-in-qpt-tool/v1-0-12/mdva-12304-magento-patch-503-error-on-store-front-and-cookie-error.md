---
title: "MDVA-12304: errore 503 nella parte anteriore dello store e errore cookie"
description: Questa patch di MDVA-12304 Adobe Commerce risolve 503 errori sui fronti degli store, con *Impossibile inviare il cookie. Il numero massimo di cookie verrebbe superato.* messaggio di errore nei registri. Questo è un problema noto di Adobe Commerce 2.2.5. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12.
exl-id: b4b1a2f7-f328-488f-86b8-576b908792fb
feature: Storefront
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# MDVA-12304: errore 503 nella parte anteriore dello store e errore cookie

Questa patch di MDVA-12304 Adobe Commerce risolve 503 errori sui fronti degli store, con *Impossibile inviare il cookie. Il numero massimo di cookie verrebbe superato.* messaggio di errore nei registri. Questo è un problema noto di Adobe Commerce 2.2.5. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12.

## Prodotti e versioni interessati

* **La patch è stata creata per Adobe Commerce versione:** Adobe Commerce on-premise 2.2.5.
* **Compatibile con le versioni di Adobe Commerce:** Adobe Commerce (tutti i metodi di distribuzione) 2.x.x.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I clienti ricevono un errore 503 durante la navigazione nella vetrina. Nel file `var/log/exception.log` è presente il seguente messaggio di errore *Impossibile inviare il cookie. Il numero massimo di cookie verrebbe superato.*

Il problema si verifica perché il limite predefinito dei cookie di Adobe Commerce è impostato su 50 e se il browser del client raggiunge tale limite, Commerce genera un’eccezione. La soluzione fornita nella patch aumenta il limite di cookie a 200.

<u>Passaggi da riprodurre:</u>

L’errore 503 può essere visualizzato in qualsiasi momento quando il cliente tenta di accedere e visualizzare il carrello.

Nel file `var/log/exception.log` è presente il seguente messaggio di errore *Impossibile inviare il cookie. Il numero massimo di cookie verrebbe superato.*

<u>Risultato effettivo:</u> Il cliente non può controllare il carrello né completare l&#39;ordine.

<u>Risultato previsto:</u> il cliente può controllare il carrello e completare l&#39;ordine.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.


## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
