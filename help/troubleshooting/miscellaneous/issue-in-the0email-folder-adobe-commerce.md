---
title: Il problema di autorizzazione della cartella var/export Adobe Commerce su cloud
description: Questo articolo fornisce una soluzione a un problema che impediva l’esportazione dei dati di prodotto a causa di un problema di autorizzazioni dei file sul server nella cartella "var/export/email". I sintomi includono esportazioni di prodotti e cataloghi non disponibili nell’interfaccia utente, ma visibili quando si utilizza SSH.
exl-id: 68120d3b-f5df-43a5-91f6-2ec519cc25ac
feature: Cloud, Communications, Data Import/Export, Paas, Roles/Permissions
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Il problema di autorizzazione della cartella var/export Adobe Commerce su cloud

Questo articolo fornisce una soluzione a un problema che impedisce l&#39;esportazione dei dati di prodotto a causa di un problema di autorizzazioni dei file sul server nella cartella `var/export/email`. I sintomi includono esportazioni di prodotti e cataloghi non disponibili nell’interfaccia utente, ma visibili quando si utilizza SSH.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud, 2.3.0-2.3.7-p2, 2.4.0-2.4.3-p1

## Problema

Impossibile esportare i file nella cartella `var/export/email` o `var/export/archive`.
La distribuzione non è riuscita a causa delle autorizzazioni su `var/export/email` o `var/export/email/archive` perché la cartella di archivio viene creata tramite e-mail e se eseguo solo l&#39;esportazione/e-mail a volte c&#39;è ancora un problema), a parte l&#39;aggiunta di qualcosa all&#39;account per la sottocartella `var/export/email/archive`.

<u>Passaggi da riprodurre</u>:

In Amministrazione, vai a **Sistema** > *Trasferimento dati* > **Esporta**.
Selezionare i file CSV da salvare nella cartella `var/export/`.

<u>Risultato previsto</u>:

I file CSV sono visibili e possono essere esportati.

<u>Risultato effettivo</u>:

I file CSV non sono visibili. Viene inoltre visualizzato un messaggio di autorizzazione negata: *RecursiveDirectoryIterator::__costrutto(/app/id progetto>/var/export/email): impossibile aprire dir: autorizzazione negata*

Viene visualizzato lo stesso messaggio per tutti i tipi di esportazione: Advanced Pricing, Customer Finances, Customer Main File e Customer Addresses.

## Causa

La causa è una cartella creata all&#39;interno di `/var` con autorizzazioni imperfette: `d-wxrwsr-T`. Il bit permanente T significa che gli utenti possono eliminare solo i file di loro proprietà, ma l&#39;eseguibile mancante significa che non possono creare file nella directory.

Ciò viene spesso notato quando il sistema crea una cartella denominata `export`, che contiene una cartella denominata `email`, che contiene una cartella denominata `archive`.

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

* [Esporta](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/data-transfer/data-export) nella guida utente.
