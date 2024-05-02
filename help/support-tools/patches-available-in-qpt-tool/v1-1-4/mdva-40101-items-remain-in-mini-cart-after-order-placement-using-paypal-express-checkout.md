---
title: "MDVA-40101: gli oggetti rimangono mini-cart dopo il posizionamento dell'ordine PayPal Express Checkout"
description: La patch MDVA-40101 risolve il problema che impedisce la rimozione degli articoli dal mini-carrello dopo il corretto inserimento dell'ordine tramite PayPal Express Checkout. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4. L'ID della patch è MDVA-40101. Il problema è stato risolto in Adobe Commerce 2.4.0.
exl-id: d640dfcd-6fb6-4cc6-8817-3ae19aa59bed
feature: Checkout, Orders, Payments, Shopping Cart
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# MDVA-40101: Gli oggetti rimangono mini-cart dopo il posizionamento dell&#39;ordine PayPal Express Checkout

La patch MDVA-40101 risolve il problema che impedisce la rimozione degli articoli dal mini-carrello dopo il corretto inserimento dell&#39;ordine tramite PayPal Express Checkout. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.1.4. L&#39;ID della patch è MDVA-40101. Il problema è stato risolto in Adobe Commerce 2.4.0.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.7

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.2 - 2.3.7-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli oggetti rimangono nel mini-carrello anche dopo un ordine effettuato con successo utilizzando PayPal Express Checkout.

<u>Passaggi da riprodurre</u>:

Effettuare un ordine utilizzando PayPal Express Checkout in modalità Incognito in un browser.

<u>Risultati previsti</u>:

Il mini-carrello deve essere vuoto dopo il completamento dell’ordine.

<u>Risultati effettivi</u>:

* La pagina di successo mostra un mini-carrello vuoto.
* Tutte le altre pagine mostrano il mini-carrello con gli articoli acquistati.
* Facendo clic sul collegamento del carrello, si viene reindirizzati a una pagina vuota del carrello.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
