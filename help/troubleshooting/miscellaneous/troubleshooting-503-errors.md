---
title: Risoluzione dei problemi relativi all'errore 503 causato dalla necessità di modificare le impostazioni predefinite di Vernice
description: In questo articolo vengono fornite soluzioni per la risoluzione dell'errore 503 causato da valori predefiniti non sufficienti per l'archivio.
exl-id: 3f001cc9-b19a-4dee-bff0-fc8ba89e2646
feature: Cache, Categories
role: Admin
source-git-commit: 9c5e993b69a98865a1142110625252da848eae04
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# Risoluzione dei problemi relativi all&#39;errore 503 causato dalla necessità di modificare le impostazioni predefinite di Vernice

In questo articolo vengono fornite soluzioni per la risoluzione dell&#39;errore 503 causato da valori predefiniti non sufficienti per l&#39;archivio.

## Problema

Se la lunghezza dei tag della cache utilizzati da Adobe Commerce supera il valore predefinito di 8192 byte di Varnish, nel browser vengono visualizzati gli errori HTTP 503 (recupero back-end non riuscito). Gli errori potrebbero essere simili ai seguenti: *&quot;Errore 503: recupero back-end non riuscito. Recupero back-end non riuscito&quot;*

## Soluzione

Per risolvere questo problema, aumenta il valore predefinito del `http_resp_hdr_len` parametro nel file di configurazione di Vernice. Il `http_resp_hdr_len` Il parametro specifica la lunghezza massima dell&#39;intestazione *entro* dimensione di risposta predefinita totale di 32768 byte.

>[!NOTE]
>
>Se il `http_resp_hdr_len` supera i 32 K, è necessario anche aumentare le dimensioni di risposta predefinite utilizzando `http_resp_size` parametro.

1. Come utente con `root` , apri il file di configurazione Vanish in un editor di testo:
   * CentOS 6: `/etc/sysconfig/varnish`
   * CentOS 7: `/etc/varnish/varnish.params`
   * Debian: `/etc/default/varnish`
   * Ubuntu: `/etc/default/varnish`
1. Cerca `http_resp_hdr_len` parametro.
1. Se il parametro non esiste, aggiungilo dopo `thread_pool_max` .
1. Imposta `http_resp_hdr_len` a un valore uguale al numero di prodotti della categoria più grande moltiplicato per 21. (Ogni tag di prodotto è lungo circa 21 caratteri).    Ad esempio, l’impostazione del valore su 65536 byte dovrebbe funzionare se la categoria più grande dispone di 3.000 prodotti.    Ad esempio:    ```conf    -p http_resp_hdr_len=65536 \    ```
1. Imposta il `http_resp_size` a un valore che soddisfa l’aumento della lunghezza dell’intestazione di risposta.    Ad esempio, l’utilizzo della somma dell’aumento della lunghezza dell’intestazione e della dimensione della risposta predefinita è un buon punto di partenza (ad esempio, 65536 + 32768 = 98304): `-p http_resp_size=98304`. Di seguito è riportato uno snippet:

   ```
   # DAEMON_OPTS is used by the init script.
   DAEMON_OPTS="-a ${VARNISH_LISTEN_ADDRESS}:${VARNISH_LISTEN_PORT} \
       -f ${VARNISH_VCL_CONF} \
       -T ${VARNISH_ADMIN_LISTEN_ADDRESS}:${VARNISH_ADMIN_LISTEN_PORT} \
       -p thread_pool_min=${VARNISH_MIN_THREADS} \
       -p thread_pool_max=${VARNISH_MAX_THREADS} \
       -p http_resp_hdr_len=65536 \
       -p http_resp_size=98304 \
       -p workspace_backend=98304 \
       -S ${VARNISH_SECRET_FILE} \
       -s ${VARNISH_STORAGE}" \
   ```

## Timeout di verifica stato {#health-check-timeouts}

Se si disattiva la cache mentre Microsoft è configurato come applicazione di caching e Adobe Commerce è in modalità sviluppatore, potrebbe risultare impossibile accedere all’amministratore.

Questa situazione può verificarsi perché il controllo di integrità predefinito presenta un `timeout` valore di 2 secondi. Potrebbero essere necessari più di 2 secondi prima che il controllo di integrità raccolga e unisca le informazioni su ogni richiesta di controllo. Se ciò si verifica in 6 controlli di integrità su 10, il server Adobe Commerce viene considerato non integro. La vernice fornisce contenuti non aggiornati quando il server non è integro.

Poiché si accede ad Admin tramite Microsoft, non è possibile accedere ad Admin per abilitare il caching (a meno che Adobe Commerce non torni integro). Tuttavia, puoi utilizzare il seguente comando per abilitare la cache:

```bash
$ bin/magento cache:enable
```

Per ulteriori informazioni sull&#39;utilizzo della riga di comando, vedere [Introduzione alla configurazione della riga di comando](https://devdocs.magento.com/guides/v2.3/config-guide/cli/config-cli-subcommands.html).
