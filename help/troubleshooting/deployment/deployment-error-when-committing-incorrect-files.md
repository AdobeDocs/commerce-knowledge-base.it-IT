---
title: Errori di distribuzione durante il commit di file non corretti
description: Questo articolo fornisce una soluzione per il problema che si verifica quando si verificano errori di distribuzione causati da commit non corretti nell’archivio di file/cartelle che non avrebbero dovuto essere aggiunti.
feature: Deploy
role: Developer
exl-id: c795f9d5-7171-4846-b99f-c018f1d2bf12
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 0%

---

# Errori di distribuzione durante il commit di file non corretti

Questo articolo fornisce una correzione del problema che si verifica quando si verificano errori di distribuzione causati da commit non corretti nell’archivio di file/cartelle che non avrebbero dovuto essere aggiunti.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud (tutte le versioni)

## Problema

Si verificano errori di distribuzione quando si esegue il commit nel repository di file/cartelle. Ad esempio, il seguente errore è causato da un tentativo di connessione al database quando non è attualmente disponibile durante il [Fase di build](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#build-phase):

```SQL
SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          SQLSTATE[HY000] [2002] php_network_getaddresses: getaddrinfo for database.i  
          nternal failed: Name or service not known                                    
                                                                                       
        
        In Abstract.php line 124:
                                                                                       
          PDO::__construct(): php_network_getaddresses: getaddrinfo for database.inte  
          rnal failed: Name or service not known       
```

## Causa

Alcuni file o cartelle non devono essere salvati nell’archivio, in quanto causano un’interruzione nel [flusso di lavoro di distribuzione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html).

## Soluzione

Rimuovi questi file/cartelle dal tuo archivio se sono presenti:

* `app/etc/env.php`
* `pub/media/catalog`
* `vendor`
