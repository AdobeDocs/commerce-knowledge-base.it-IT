---
title: Informazioni sulla scadenza del certificato SSL personalizzato
description: Questo articolo fornisce una soluzione per i casi in cui un certificato SSL personalizzato è stato aggiornato con un certificato SSL fornito dall’Adobe.
exl-id: cc968bae-f742-449b-b291-bc121ec45935
feature: Support
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Informazioni sulla scadenza del certificato SSL personalizzato

Questo articolo fornisce una soluzione per i casi in cui un certificato SSL personalizzato è stato aggiornato con un certificato SSL fornito dall’Adobe.

## Prodotti e versioni interessati

Adobe Commerce sull&#39;infrastruttura cloud, [tutte le versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Adobe Commerce aggiorna automaticamente i certificati SSL 30 giorni prima della scadenza. Questa automazione non verifica se il certificato sostituito è un SSL interno o un SSL di terze parti personalizzato e lo sostituirà con un SSL interno valido al rilevamento della scadenza. Questo può causare confusione per i proprietari e gli operatori del sito che prevedono di avere il certificato personalizzato sul sito, nonché il rischio di altri problemi di funzionalità, tra cui, ma non solo, un’interruzione del sito.

<u>Passaggi da riprodurre</u>

1. Certificato SSL personalizzato installato per il sito Web.
1. L’automazione rileva che il certificato SSL personalizzato scade dopo 30 giorni.
1. Adobe Commerce sostituisce automaticamente il certificato personalizzato con il nostro certificato interno.

<u>Risultati previsti</u>

Adobe Commerce ignora i certificati personalizzati quando esegue l’aggiornamento automatico del certificato SSL.

<u>Risultati effettivi</u>

Adobe Commerce aggiorna qualsiasi certificato entro 30 giorni dalla scadenza.

## Soluzione

Quando un esercente sceglie di utilizzare il proprio certificato SSL personalizzato, questo deve essere aggiornato più di 30 giorni prima della scadenza del certificato per garantire che non venga sostituito da un certificato SSL interno di Adobe Commerce.

Se ti trovi in una situazione in cui il tuo SSL personalizzato è stato sostituito dal nostro SSL interno e desideri sostituirlo con il certificato SSL personalizzato aggiornato, [invia una richiesta di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) con il percorso in cui hai caricato i nuovi file del certificato. Includi la data di inizio del nuovo SSL. Una volta ottenute queste informazioni, possiamo procedere con l’installazione del nuovo certificato SSL.

## Lettura correlata

* [Certificati SSL (TLS) per il Magento Commerce Cloud: FAQ](/help/how-to/general/ssl-tls-certificates-for-magento-commerce-cloud-faq.md) nella Knowledge Base di supporto.
* [Riferimento agli strumenti della riga di comando: magento-cloud certiified:add](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/dev-tools/cloud-cli/cloud-cli-reference#certificateadd) nella documentazione per gli sviluppatori.
* [Elenco di controllo di Launch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/checklist)nella documentazione per gli sviluppatori.
* [Accedere allo strumento di analisi per l&#39;intero sito](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access#step-2-access-site-wide-analysis-tool) nella guida utente.
