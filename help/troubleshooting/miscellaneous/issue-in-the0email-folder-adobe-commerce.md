---
title: Il problema di autorizzazione della cartella var/export Adobe Commerce su cloud
description: Questo articolo fornisce una soluzione a un problema che impediva l’esportazione dei dati di prodotto a causa di un problema di autorizzazioni dei file sul server nella cartella "var/export/email". I sintomi includono esportazioni di prodotti e cataloghi non disponibili nell’interfaccia utente, ma visibili quando si utilizza SSH.
exl-id: 68120d3b-f5df-43a5-91f6-2ec519cc25ac
feature: Cloud, Communications, Data Import/Export, Paas, Roles/Permissions
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Il problema di autorizzazione della cartella var/export Adobe Commerce su cloud

Questo articolo fornisce una soluzione a un problema che impediva l’esportazione dei dati di prodotto a causa di un problema di autorizzazioni dei file sul server in `var/export/email` cartella. I sintomi includono esportazioni di prodotti e cataloghi non disponibili nell’interfaccia utente, ma visibili quando si utilizza SSH.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Problema

Non è possibile esportare file in `var/export/email` o `var/export/archive` cartella.
Distribuzione non riuscita a causa di autorizzazioni su `var/export/email` o `var/export/email/archive` perché la cartella di archivio viene creata in e-mail e se eseguo solo l’esportazione/e-mail a volte c’è ancora un problema), oltre ad aggiungere qualcosa all’account per la sottocartella `var/export/email/archive`.

<u>Passaggi da riprodurre</u>:

In Admin (Amministrazione), vai a **Sistema** > *Trasferimento dati* > **Esporta**.
Seleziona i file CSV da salvare nel `var/export/` cartella.

<u>Risultato previsto</u>:

I file CSV sono visibili e possono essere esportati.

<u>Risultato effettivo</u>:

I file CSV non sono visibili. Viene inoltre visualizzato un messaggio di autorizzazione negata: *RecursiveDirectoryIterator::__costrutto(/app/project id>/var/export/email): impossibile aprire dir: autorizzazione negata*

Viene visualizzato lo stesso messaggio per tutti i tipi di esportazione: Advanced Pricing, Customer Finances, Customer Main File e Customer Addresses.

## Causa

La causa è una cartella creata all’interno di `/var` che ha autorizzazioni imperfette: `d-wxrwsr-T`. Il bit permanente T significa che gli utenti possono eliminare solo i file di loro proprietà, ma l&#39;eseguibile mancante significa che non possono creare file nella directory.

Questo si nota spesso quando il sistema crea una cartella denominata `export`, che contiene una cartella denominata `email`, che contiene una cartella denominata `archive`.

Per verificare se la directory dispone di queste autorizzazioni non configurate correttamente, eseguire il comando seguente in CLI/Terminal:

`ls -ld var/export/`

Se le autorizzazioni non sono configurate correttamente, l’output sarà:

`d-wxrwsr-T 3 web web 4096 Aug 15 19:12 var/export/`


## Soluzione

Per risolvere questo problema, aggiorna le autorizzazioni delle cartelle a 777 e quindi tutti i file in modo ricorsivo, eseguendo i seguenti comandi:

```bash
chmod 777 var/export/
chmod 777 var/export/email/
chmod 777 var/export/email/archive/
chmod 777 -R var/export/
```

## Lettura correlata

* [Esporta](https://docs.magento.com/user-guide/system/data-export.html) nella guida utente.
