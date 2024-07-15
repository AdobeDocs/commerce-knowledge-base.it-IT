---
title: Ridistribuzione dell'ambiente non riuscita o server MySQL eliminato
description: In questo articolo viene fornita una soluzione per i problemi di Adobe Commerce (tutti i metodi di distribuzione), in cui l'interruzione dello spazio allocato per MySQL causa errori di distribuzione bloccata o di connessione al database.
exl-id: 2086b45a-0bfe-45cc-bef9-1b6f09ddb70a
feature: Deploy, Services
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# Ridistribuzione dell&#39;ambiente non riuscita o server MySQL eliminato

In questo articolo viene fornita una soluzione per i problemi di Adobe Commerce (tutti i metodi di distribuzione), in cui l&#39;interruzione dello spazio allocato per MySQL causa errori di distribuzione bloccata o di connessione al database.

## Prodotti e versioni interessati

* Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud (tutte le versioni)

## Problema

* Il processo di distribuzione non riesce e viene visualizzato il seguente errore nel registro di distribuzione (riga di comando e registro interfaccia utente): ```bash    Re-deploying environment abcdefghijklm-master-7rqtwti         E: Environment redeployment failed    ```
* Adobe Commerce risponde con un errore 503 e nei registri dell’applicazione viene visualizzato il seguente messaggio di errore:    ```bash    SQLSTATE[HY000] [2006] MySQL server has gone away    ```    e quando si esegue la connessione a un server MySQL viene visualizzato il seguente errore:    ```bash    ERROR 2013 (HY000): Lost connection to MySQL server at 'reading initial communication packet', system error: 0 "Internal error/check (Not system error)"    ```

## Causa

La causa più probabile dei problemi è che lo spazio allocato nel database MySQL è troppo basso. A tale scopo, verificare lo spazio disponibile per MySQL come descritto di seguito.

### Verifica se lo spazio è sufficiente per MySQL

Per tutti gli ambienti dell&#39;architettura del piano Starter di Adobe Commerce su infrastruttura cloud e l&#39;[ambiente di integrazione](/help/announcements/adobe-commerce-announcements/integration-environment-enhancement-request-pro-and-starter.md) dell&#39;architettura del piano Pro di Adobe Commerce su infrastruttura cloud, [SSH nell&#39;ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) ed esegui il comando:

```bash
magento-cloud db:size
```

Per l&#39;ambiente di staging o produzione dell&#39;architettura Pro, [SSH nell&#39;ambiente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/secure-connections.html) ed eseguire `df -h`   Comando `| grep mysql`. Il risultato sarà simile al seguente:

```bash
sxpe7gigd5ok2@i-00baa9e24f31dba41:~$ df -h | grep mysql
/dev/xvdj                            40G  7.4G   32G  19% /data/mysql
```

## Soluzione

### Per risolvere il problema, è necessario allocare più spazio per MySQL.

Per tutti gli ambienti di integrazione dell&#39;architettura Starter e Pro, questa operazione viene eseguita nel file `.magento/services.yaml`, aumentando il parametro `mysql: disk:`. Ad esempio:

```yaml
mysql:
    type: mysql:10.0
    disk: 2048
```

Per ulteriori informazioni, vedere l&#39;articolo [Configurazione del servizio MySQL](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/mysql.html).

Per apportare queste modifiche all&#39;ambiente di staging o produzione dell&#39;architettura Pro, è necessario creare un [ticket di supporto](https://support.magento.com). In genere, tuttavia, non è necessario occuparsi di questo problema in Staging/Produzione dell’architettura Pro, in quanto Adobe Commerce monitora questi parametri per te e ti avvisa e/o intraprende azioni in base al contratto.

### Applicazione delle modifiche

Dopo aver modificato il file `.magento/services.yaml`, è necessario eseguire il commit e inviare le modifiche per applicarle. Il push attiverà il processo di distribuzione.
