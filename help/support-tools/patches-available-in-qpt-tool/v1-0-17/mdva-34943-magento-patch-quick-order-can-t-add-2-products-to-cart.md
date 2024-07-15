---
title: "MDVA-34943: l'ordine rapido non può aggiungere più di 2 prodotti al carrello"
description: La patch MDVA-34943 risolve il problema che impedisce a un ordine rapido di aggiungere due o più prodotti al carrello. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17. Il problema è stato risolto nella versione 2.4.2 di Adobe Commerce.
exl-id: fcff6a78-fe00-4352-b0bc-149bd411d999
feature: Orders, Products, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '584'
ht-degree: 0%

---

# MDVA-34943: l&#39;ordine rapido non può aggiungere più di 2 prodotti al carrello

La patch MDVA-34943 risolve il problema che impedisce a un ordine rapido di aggiungere due o più prodotti al carrello. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.17. Il problema è stato risolto nella versione 2.4.2 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.0-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.4.1-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti non possono aggiungere due o più prodotti al carrello in ordine rapido.

<u>Prerequisiti</u>:

Adobe Commerce con prodotti semplici.

<u>Passaggi da riprodurre</u>:

1. Vai a **Ordine rapido** sullo Storefront (senza aver effettuato l&#39;accesso).
1. Immettere uno SKU valido, fare clic sul prodotto visualizzato nel campo di completamento automatico e impostare **Quantità** = *1*.
1. Immettere lo stesso SKU valido, ma modificare le lettere maiuscole del primo carattere (cambiando le lettere maiuscole in minuscole o cambiando le lettere minuscole in maiuscole) e fare clic sul prodotto visualizzato nel campo di completamento automatico e impostare **Quantità** = *1*.
1. Immetti un `random_sting_value` per **SKU** e imposta **Quantità** = *1*.
1. Imposta **SKU** = *123123123* e **Quantità** = *1*.
1. Elimina tutto tranne la prima voce aggiunta alla pagina **Ordine rapido**.
1. Immetti il primo SKU (simile al passaggio 2 di cui sopra) nel campo **Immettere più SKU** e fai clic su **Aggiungi all&#39;elenco**.
1. Ciò determina una quantità di 2 per il primo SKU e una riga per `random_sting_value`.
1. Per eseguire ulteriori test, aggiorna la pagina.
1. Questo non comporta alcun SKU per l’ordine rapido, come previsto.
1. Immetti un `random_sting_value2` nel campo **Immettere più SKU** e fai clic su **Aggiungi all&#39;elenco**.
1. Ciò comporta due SKU validi da prima e un `random_sting_value2`.

<u>Risultati previsti</u>:

È possibile aggiungere al carrello due o più prodotti, come previsto.

<u>Risultati effettivi</u>:

Quando viene reindirizzato alla pagina **Carrello**, il primo prodotto aggiunto viene visualizzato normalmente, ma per il secondo prodotto e tutti i prodotti successivi aggiunti al carrello viene visualizzato il messaggio di errore &quot;*1 prodotto richiede attenzione*&quot;. Il secondo o gli altri prodotti saranno elencati nella sezione **Product Requirement** della pagina **Cart**.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
