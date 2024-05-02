---
title: "Patch MDVA-31519: ordine perso dopo il pagamento del guest"
description: La patch MDVA-31519 risolve il problema relativo agli ordini a pagamento mancanti e blocca i timeout di attesa durante il pagamento da parte degli utenti guest.
exl-id: 2b4f9992-d58d-434f-adf8-d8ad8f761755
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Patch MDVA-31519: ordine perso dopo il pagamento del guest

La patch MDVA-31519 risolve il problema relativo agli ordini a pagamento mancanti e blocca i timeout di attesa durante il pagamento da parte degli utenti guest.

Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.5 - 2.3.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Abilita estrazione guest.
1. Crea una regola di prezzo del carrello senza un coupon (Esempio: &quot;Spedizione gratuita superiore all’importo x&quot;).
1. Effettuare una grande quantità di ordini simultanei dei clienti che coinvolgono fornitori di servizi di pagamento API (PSP).

<u>Risultati previsti</u>:

Tutte le transazioni di pagamento a pagamento vengono salvate nel database e visualizzate nell&#39;amministratore, come previsto.

<u>Risultati effettivi</u>:

Solo una piccola parte degli ordini viene salvata nel database, mentre la maggior parte delle informazioni degli ordini viene persa a causa dei timeout di attesa del blocco.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
