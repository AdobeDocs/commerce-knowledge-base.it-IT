---
title: Adobe Commerce Recommendations per le vulnerabilità PHP
description: Il 3 settembre, il Multi-State Information Sharing and Analysis Center (MS-ISAC) ha emesso un avviso relativo a più vulnerabilità che potrebbero consentire l'esecuzione arbitraria del codice e una raccomandazione che tutti i siti che utilizzano PHP dovrebbero aggiornare alla versione più recente PHP ASAP ([full alert is available here](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).
exl-id: 0bc7caab-0b89-463a-a7f2-a7c92df9f84e
feature: Compliance, Recommendations
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 0%

---

# Adobe Commerce Recommendations per le vulnerabilità PHP

Il 3 settembre, il Multi-State Information Sharing and Analysis Center (MS-ISAC) ha emesso un avviso relativo a più vulnerabilità che potrebbero consentire l&#39;esecuzione arbitraria del codice e un consiglio che tutti i siti che utilizzano PHP devono aggiornare alla versione PHP più recente ASAP ([avviso completo è disponibile qui](https://www.cisecurity.org/advisory/multiple-vulnerabilities-in-php-could-allow-for-arbitrary-code-execution_2019-087/)).

>[!WARNING]
>
>Sull’infrastruttura cloud Adobe Commerce on, tieni presente che gli aggiornamenti dei servizi non possono essere inviati all’ambiente di produzione senza un preavviso di 48 ore lavorative al nostro team di infrastruttura. Ciò è necessario in quanto è necessario disporre di un tecnico del supporto dell&#39;infrastruttura per aggiornare la configurazione entro l&#39;intervallo di tempo desiderato, riducendo al minimo i tempi di inattività dell&#39;ambiente di produzione. Quindi, 48 ore prima del momento in cui le modifiche devono essere in produzione [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) specificando l&#39;aggiornamento del servizio richiesto e indicando l&#39;ora in cui desideri avviare il processo di aggiornamento.

Continua a leggere per conoscere l’impatto e i passaggi per i siti Adobe Commerce:

**Adobe Commerce ospitato sul nostro prodotto cloud**

Se utilizzi Adobe Commerce su un’infrastruttura cloud, ti preghiamo di collaborare con il team tecnologico per ridistribuire Adobe Commerce a partire da qualsiasi momento\* per sfruttare i vantaggi dell’aggiornamento. Consigliamo ai commercianti di completare la reinstallazione entro il 30 settembre per evitare problemi di conformità PCI che potrebbero diventare effettivi a seguito di queste vulnerabilità alla fine del mese.

Note aggiuntive sulla ridistribuzione del sito Cloud per questo aggiornamento:

* Se il tuo sito utilizza ancora PHP versione 7.0, dovrai prima effettuare l’aggiornamento a una versione PHP supportata per poter usufruire di questi aggiornamenti di sicurezza.
* Per 2.1.x/2.2.x, ulteriori informazioni sull&#39;aggiornamento del PHP sono disponibili [qui](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html).

\* *Le versioni precedenti di questo articolo e della nostra messaggistica indicavano il 19 settembre, ma i nostri team hanno terminato il lavoro prima del previsto.*

**Adobe Commerce su tutte le altre soluzioni di hosting**

Poiché Adobe Commerce si affida a PHP, consigliamo a tutti i commercianti che utilizzano Adobe Commerce di rivedere con il proprio provider gli aggiornamenti necessari per PHP. Consigliamo inoltre ai commercianti di completare questa revisione e gli eventuali aggiornamenti entro il 30 settembre per evitare problemi di conformità PCI che potrebbero diventare effettivi a seguito di queste vulnerabilità alla fine del mese.

Tieni presente alcuni dettagli aggiuntivi per Adobe Commerce su altre soluzioni di hosting:

* Le versioni Adobe Commerce 2.0 o 1.x che utilizzano versioni PHP precedenti alla 7.1 o successive non dispongono di patch PHP ufficiale. Il percorso consigliato consiste nell&#39;aggiornare PHP a una versione PHP supportata.

In base all’avviso, le patch consigliate per questa vulnerabilità includono:

* PHP 7.1: [https://www.php.net/ChangeLog-7.php\#7.1.32](https://www.php.net/ChangeLog-7.php#7.1.32)
* PHP 7.2: [https://www.php.net/ChangeLog-7.php\#7.2.22](https://www.php.net/ChangeLog-7.php#7.2.22)
* PHP 7.3: [https://www.php.net/ChangeLog-7.php\#7.3.9](https://www.php.net/ChangeLog-7.php#7.3.9)

Per ulteriori informazioni su PHP e sulle versioni recenti, visitare il sito di [PHP](https://www.php.net/). Se hai domande o desideri ulteriori informazioni sulle best practice per la sicurezza, consulta la [Guida alle best practice per la sicurezza](https://www.adobe.com/content/dam/cc/en/security/pdfs/Adobe-Magento-Commerce-Best-Practices-Guide.pdf).
