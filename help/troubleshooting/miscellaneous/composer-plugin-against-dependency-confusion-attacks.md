---
title: Plug-in del compositore contro gli attacchi di confusione delle dipendenze
description: Questo articolo fornisce informazioni sul plug-in del compositore rilasciato per gli attacchi Dependency Confusion e raccomandazioni su come evitare l’errore. Il plug-in Composer è stato introdotto insieme alla versione 2.4.3 di Adobe Commerce per proteggere i commercianti di Adobe Commerce dagli attacchi di Dependency Confusion.
exl-id: 42543043-cf60-4431-80e9-866771c5c87b
feature: Observability
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# Plug-in del compositore contro gli attacchi di confusione delle dipendenze

Questo articolo fornisce informazioni sul plug-in del compositore rilasciato per gli attacchi Dependency Confusion e raccomandazioni su come evitare l’errore. Il plug-in Composer è stato introdotto insieme alla versione 2.4.3 di Adobe Commerce per proteggere i commercianti di Adobe Commerce dagli attacchi di Dependency Confusion.

## Prodotti e versioni interessati

* Adobe Commerce 2.4.3 e versioni future (tutti i metodi di distribuzione)

## Problema

Un potenziale caso di attacco di dipendenza attiva confusa viene rilevato attraverso almeno una delle dipendenze dirette o indirette definite in `composer.json` dal plug-in compositore `magento/composer-dependency-version-audit-plugin` durante l&#39;installazione/aggiornamento del compositore.

<u>Passaggi da riprodurre</u>:

Quando si installa/aggiorna il compositore, il plugin del compositore interrompe il processo se rileva un potenziale attacco di confusione della dipendenza. In tal caso, l&#39;installazione o l&#39;aggiornamento del compositore non riuscirà e verrà visualizzato un messaggio di errore simile al seguente:

*```Higher matching version x.x.x of package/name was found in public repository packagist.org than x.x.x in private.repo. Public package might've been taken over by a malicious entity; please investigate and update package requirement to match the version from the private repository.```*

## Causa

L&#39;attacco Dependency Confusion permette di eseguire in remoto codice arbitrario su un server ingannando un manager di dipendenza (ad esempio, il Compositore di PHP) per scaricare un pacchetto dannoso da una fonte pubblica invece del pacchetto originale da un archivio privato.

Un attacco di questo tipo può anche non essere rilevato se l&#39;autore dell&#39;attacco è in grado di mantenere la funzionalità del pacchetto originale.

Gli aggressori possono sfruttare questa vulnerabilità se un pacchetto è disponibile solo tramite archivi privati, ma non è registrato in quello pubblico. L’autore dell’attacco carica quindi un pacchetto con lo stesso nome nell’archivio pubblico e gli assegna una versione superiore a quella disponibile privatamente. Il manager delle dipendenze confronta quindi le versioni dei pacchetti disponibili sia privatamente che pubblicamente e sceglie la più alta dall’archivio pubblico. Il codice dannoso scaricato dal manager delle dipendenze verrà quindi eseguito con gli stessi privilegi del codice dell&#39;applicazione.

## Soluzione

### Recommendations agli esercenti

* Considera seriamente il messaggio di errore visualizzato quando il plug-in interrompe l’installazione o l’aggiornamento del compositore e, se riconosci il pacchetto potenzialmente compromesso, contatta lo sviluppatore dell’estensione.
* È comunque possibile installare Adobe Commerce con la versione sicura del pacchetto dal Marketplace o da un altro archivio privato attendibile.
* Modifica la versione del pacchetto richiesta nel file compositore.json con la versione esatta trovata nel Marketplace per procedere con l’installazione o l’aggiornamento del compositore.

### Aspettative degli sviluppatori di estensioni

* Non c’è modo di sapere con certezza se il pacchetto di un plug-in, se proveniente da un archivio pubblico, sia stato compromesso o meno. Il plug-in rileva quando una versione pubblica di un pacchetto in packagist.org ha una versione più alta di quella disponibile da un archivio privato come [repo.magento.com](https://repo.magento.com). Consigliamo vivamente agli sviluppatori di estensioni di evitare tali situazioni e di non pubblicare versioni più recenti pubblicamente di quelle disponibili tramite [repo.magento.com](https://repo.magento.com).
* Adobe Commerce è consapevole del fatto che il processo di revisione del Marketplace può ritardare la disponibilità del rilascio delle estensioni, ma il processo serve a mantenere i commercianti al sicuro e ad aiutare gli sviluppatori di estensioni a trovare errori accidentali che potrebbero aver saltato.
