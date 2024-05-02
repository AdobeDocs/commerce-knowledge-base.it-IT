---
title: "MDVA-42326: i clienti ricevono un errore al momento dell'estrazione dopo il timeout della sessione"
description: La patch di MDVA-42326 risolve il problema relativo all'errore che i clienti ricevono al momento del pagamento dopo il timeout della sessione, anche se il carrello acquisti persistente è abilitato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8. L'ID della patch è MDVA-42326. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: bc9b71de-510d-4c4e-8b0d-9abf9a3e447f
feature: Checkout, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 0%

---

# MDVA-42326: i clienti ricevono un errore al momento dell&#39;estrazione dopo il timeout della sessione

La patch di MDVA-42326 risolve il problema relativo all&#39;errore che i clienti ricevono al momento del pagamento dopo il timeout della sessione, anche se il carrello acquisti persistente è abilitato. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.8. L&#39;ID della patch è MDVA-42326. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I clienti ricevono un errore al momento del pagamento dopo il timeout della sessione, anche se il carrello acquisti persistente è abilitato.

<u>Prerequisiti</u>:

1. Vai a **Config** > **Generale** > **Web** > **Impostazioni predefinite cookie** > **Durata dei cookie** e impostato su **120**.
1. Vai a **Config** > **Clienti** > **Configurazione cliente** > **Opzioni clienti online** e imposta entrambi i valori su **2**.
1. Vai a **Config** > **Clienti** > **Carrello acquisti persistente** e impostato su **Abilita**.
1. Vai a **Config** > **Vendite** > **Metodi di pagamento** e disattivare tutti i metodi di pagamento eccetto **Assegno/vaglia postale** (deve essere attivato).

<u>Passaggi da riprodurre</u>:

1. Accedi come cliente e aggiungi alcuni prodotti al carrello.
1. Controlla il carrello.
1. Attendi due minuti (impostati come condizione preliminare); la sessione dovrebbe scadere.
1. Clic **Vai al pagamento** e non aggiornare la pagina.
1. Effettua il pagamento come ospite, compila l&#39;indirizzo di spedizione e scegli un metodo di spedizione.
1. Clic **Successivo**.
1. Il giorno **Revisione e pagamenti** pagina, fai clic su **Inserisci ordine**. Poiché è consentito un solo metodo di pagamento, il cliente deve poter effettuare l&#39;ordine senza selezionare il metodo di pagamento.

<u>Risultati previsti</u>:

Il cliente deve essere in grado di effettuare l’ordine.

<u>Risultati effettivi</u>:

Il cliente riceve il seguente errore: *Convalida indirizzo non riuscita: il formato dell&#39;e-mail non è corretto*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
