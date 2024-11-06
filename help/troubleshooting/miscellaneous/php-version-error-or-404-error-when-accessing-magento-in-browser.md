---
title: Errore di versione PHP o errore 404 durante l’accesso ad Adobe Commerce nel browser
description: Questo articolo fornisce soluzioni per i problemi in cui non è possibile accedere all’istanza di Adobe Commerce in un browser web e si verifica l’errore 404 o l’errore "versione PHP non supportata".
exl-id: 6cfdeaae-5e52-411c-9006-5af8a467873a
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Errore di versione PHP o errore 404 durante l’accesso ad Adobe Commerce nel browser

Questo articolo fornisce soluzioni per i problemi in cui non è possibile accedere all’istanza di Adobe Commerce in un browser web e si verifica l’errore 404 o l’errore &quot;versione PHP non supportata&quot;.

## Prodotti e versioni interessati:

* Adobe Commerce 2.3.x

## Problema: versione PHP non supportata

Il seguente messaggio viene visualizzato quando tenti di accedere ad Adobe Commerce storefront o Commerce Admin:

`Magento supports PHP 7.1.3 or later. Please read Magento System Requirements.`

### Soluzione

Provare a eseguire le operazioni seguenti:

* Aggiornare PHP alla versione 7.3. Per ulteriori informazioni, consulta [Requisiti dello stack di tecnologia Adobe Commerce 2.3](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/system-requirements) nella documentazione per gli sviluppatori.
* Riavvia Apache, poiché potrebbe non utilizzare la stessa versione PHP presente nel file system. Per riavviare Apache, usa i seguenti comandi:
   * Ubuntu: `service apache2 restart`
   * CentOS: `service httpd restart`

## Problema: errore 404

Quando tenti di accedere alla vetrina Adobe Commerce o all’amministrazione di Commerce, viene visualizzato un errore 404 (Non trovato).

### Soluzione

Provare a eseguire le operazioni seguenti:

* Assicurarsi che [Le riscritture del server Apache](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/web-server/apache) siano abilitate. Se le riscritture del server Apache non sono impostate correttamente, i file statici non vengono serviti dalla posizione corretta.
* Potrebbe essersi verificato un problema con l&#39;URL di base immesso durante l&#39;installazione. L&#39;URL di base viene specificato come valore di `--base-url=` durante l&#39;installazione di Adobe Commerce dalla riga di comando o come valore del campo **Indirizzo archivio** nella pagina Configurazione Web del programma di installazione Web. L&#39;URL di base *must* inizia con lo schema (ad esempio `http://` ) e termina con una barra finale (/). Esegui di nuovo il programma di installazione con un valore valido e prova ad accedere in seguito ad Adobe Commerce.
