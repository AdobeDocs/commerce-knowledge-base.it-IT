---
title: Il CAPTCHA di Adobe Commerce 2.3.6 e 2.4.1 nel checkout non funziona
description: Questo articolo fornisce una patch per il problema in cui la funzione CAPTCHA per il pagamento non funziona come previsto nella pagina Inserisci ordine quando si utilizzano fornitori di pagamenti di terze parti come Paypal Express, Payflow Pro o CyberSource in Adobe Commerce.
exl-id: 46ab7f4d-ee0a-4cc1-96cc-6eb408319e9c
feature: Checkout, Orders
role: Developer
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 0%

---

# Il CAPTCHA di Adobe Commerce 2.3.6 e 2.4.1 nel checkout non funziona

Questo articolo fornisce una patch per il problema in cui la funzione CAPTCHA per il pagamento non funziona come previsto nella pagina Inserisci ordine quando si utilizzano fornitori di pagamenti di terze parti come Paypal Express, Payflow Pro o CyberSource in Adobe Commerce.

Questo problema noto è menzionato nella documentazione per gli sviluppatori:

<u>Per Adobe Commerce 2.3.6</u>:

* [Note sulla versione di Adobe Commerce 2.3.6: problemi noti](https://devdocs.magento.com/guides/v2.3/release-notes/commerce-2-3-6.html#known-issues)
* [Note sulla versione del Magento Open Source 2.3.6: problemi noti](https://devdocs.magento.com/guides/v2.3/release-notes/open-source-2-3-6.html#known-issues)

<u>Per Adobe Commerce 2.4.1</u>:

* [Note sulla versione di Adobe Commerce 2.4.1: problemi noti](https://devdocs.magento.com/guides/v2.4/release-notes/commerce-2-4-1.html#known-issues)
* [Note sulla versione del Magento Open Source 2.4.1: problemi noti](https://devdocs.magento.com/guides/v2.4/release-notes/open-source-2-4-1.html#known-issues)

## Prodotti e versioni interessati

* Adobe Commerce (tutti i metodi di implementazione) 2.3.6 e 2.4.1
* Magenti Open Source 2.3.6 e 2.4.1

## Problema

<u>Passaggi da riprodurre</u>

1. Imposta almeno uno di questi metodi di pagamento in Commerce: Paypal Express, Payflow Pro o CyberSource.
1. Vai a **Amministratore > Archivi > Configurazione > Clienti > Configurazione cliente > CAPTCHA** .
   * Imposta **Abilita CAPTCHA su Storefront** = *Sì*.
   * Seleziona in **Forms** : *Ordine di estrazione/inserimento* , *Accesso* e *Password dimenticata*.
   * Imposta **Modalità di visualizzazione** = *Dopo il numero di tentativi di accesso* (per visualizzare l&#39;impostazione **Numero di tentativi di accesso non riusciti**).
   * Imposta **Numero di tentativi non riusciti di accesso** = *0* (per far funzionare captcha continuamente).
1. Sul front-end, aggiungi un prodotto al carrello e prova a effettuare il pagamento.
1. Nella pagina Informazioni sul pagamento, inserisci captcha e prova a effettuare il pagamento con Paypal Express, Payflow Pro o CyberSource.

<u>Risultato previsto:</u>

La funzione CAPTCHA funziona come previsto.

<u>Risultato effettivo:</u>

Viene visualizzato il messaggio di errore: *Specifica il codice CAPTCHA e riprova.*

## Soluzione

Applica una delle patch seguenti a seconda che ti trovi su Adobe Commerce on-premise/Adobe Commerce on cloud infrastructure/Magento Open Source 2.3.6 o 2.4.1.

## Patch

Le patch sono allegate a questo articolo, disponibili per il download nei formati `.composer` e `.git`.

Per scaricare una patch, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic su uno dei seguenti collegamenti:

<u>Per Adobe Commerce on-premise/Adobe Commerce su infrastruttura cloud/Magento Open Source 2.3.6</u>:

* [Patch per compositore MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Patch Git MDVA-33093\_\_\_\_2\_3\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_3_x-p1__CAPTCHA_GIT.patch.zip)

<u>Per Adobe Commerce on-premise/Adobe Commerce su infrastruttura cloud/Magento Open Source 2.4.1</u>:

* [Patch per compositore MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_COMPOSER.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_COMPOSER.patch.zip)
* [Patch Git MDVA-33093\_\_\_\_2\_4\_x-p1\_\_CAPTCHA\_GIT.patch](assets/MDVA-33093____2_4_x-p1__CAPTCHA_GIT.patch.zip)

Queste patch non sono compatibili con altre versioni ed edizioni di Adobe Commerce o di Magento Open Source.

## Come applicare il cerotto

<u>Correzione compositore</u>

Consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto per istruzioni sulla patch del compositore.

<u>Patch Git</u>

Consulta la documentazione per gli sviluppatori [Applicazione delle patch: patch personalizzate](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#custom-patches) per le istruzioni sulle patch Git per Adobe Commerce/Magento Open Source.
