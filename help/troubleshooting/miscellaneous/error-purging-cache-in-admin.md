---
title: Errore durante la rimozione della cache in Commerce Admin
description: "Questo articolo spiega come identificare la causa di un messaggio di errore che si verifica quando si elimina la cache in Commerce Admin. Quando tenti di eliminare la cache tramite l’amministratore, ricevi il seguente messaggio:"
exl-id: aa414e04-bc6d-46bd-b98f-0446b97bda14
feature: Admin Workspace, Cache
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 0%

---

# Errore durante la rimozione della cache in Commerce Admin

Questo articolo spiega come identificare la causa di un messaggio di errore che si verifica durante l’eliminazione della cache in Commerce Admin. Quando tenti di eliminare la cache tramite l’amministratore, ricevi il seguente messaggio:
Impossibile eliminare il file */app/project-id/pub/media/catalog/product/cache/directory/filename&quot;. Avviso!unlink(/app/project id/pub/media/catalog/product/cache/directory/filename): file o directory non esistente*

## Prodotti e versioni interessati

Adobe Commerce (tutti i metodi di implementazione) 2.3.0-2.3.7, 2.4.0-2.4.2-p1

## Problema

Quando tenti di eliminare la cache tramite l’amministratore, ricevi un messaggio di errore.

<u>Passaggi da riprodurre:</u>

1. In Amministrazione, vai a **Sistema** > **Strumenti** > **Gestione cache**.
1. Seleziona una delle opzioni per cancellare il caching.

<u>Risultato previsto:</u>

La cache di Adobe Commerce è stata svuotata senza errori.

<u>Risultato effettivo:</u>

Viene visualizzato l&#39;errore &quot;Impossibile eliminare il file&quot;.

## Causa

L&#39;errore è correlato a un ritardo tra il momento in cui è stata avviata l&#39;operazione di pulizia della cache e il momento in cui è stato segnalato il completamento.

## Soluzione

1. Conferma che i file menzionati nell’errore non siano presenti sul server (verificando che l’eliminazione della cache sia avvenuta correttamente):

```bash
ls -la pub/media/catalog/product/cache/directory/filename
```

Se viene visualizzato il seguente output:

```bash
ls: cannot access 'pub/media/catalog/product/cache/directory/filename/': No such file or directory
```

si è tentato di cancellare i file quando l&#39;operazione era già stata completata. Non si tratta di un bug, ma di un problema di concorrenza nei messaggi che dovrebbe verificarsi a volte. Nessun problema da risolvere.
Tuttavia, se l&#39;output mostra che i file sono ancora nella cache, è necessario [inviare un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket).

## Lettura correlata

* [Gestione della cache](https://docs.magento.com/user-guide/system/cache-management.html) nella documentazione per gli sviluppatori.
