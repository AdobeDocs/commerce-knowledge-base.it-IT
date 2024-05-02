---
title: Se si rimuove l’entità correlata dall’aggiornamento dello staging, viene eliminata
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.3 relativo all’entità (categoria, pagina CMS, ecc.) che viene rimossa quando viene eliminato il relativo aggiornamento della pianificazione.
exl-id: 91138ac1-916e-4dd1-bad5-892524fdd9e1
feature: CMS, Cache, Categories, Staging
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# Se si rimuove l’entità correlata dall’aggiornamento dello staging, viene eliminata

Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.3 relativo all’entità (categoria, pagina CMS, ecc.) che viene rimossa quando viene eliminato il relativo aggiornamento della pianificazione.

>[!NOTE]
>
>Il problema è stato risolto in Adobe Commerce 2.2.6.

## Problema

Quando si elimina un aggiornamento della pianificazione attivo tra la data di inizio e la data di fine, viene eliminata anche l&#39;entità correlata (categoria, sottocategoria, pagina CMS).

<u>Passaggi da riprodurre (con categorie)</u>:

1. Accedi all’amministratore di Commerce.
1. Crea una nuova sottocategoria in **Catalogo** > **Categorie**.
1. Crea un nuovo aggiornamento di staging con l&#39;ora di inizio e di fine.
1. Attendi che venga applicato l’aggiornamento, ovvero l’ora di inizio.
1. Elimina l’aggiornamento utilizzando **Visualizza/Modifica** collegamento.

<u>Risultati previsti</u>:

L’aggiornamento viene eliminato e la sottocategoria esiste ancora nell’amministratore.

<u>Risultati effettivi</u>:

L’aggiornamento e la sottocategoria vengono eliminati.

## Soluzione

Applicare la patch fornita in questo articolo e pulire la cache in esecuzione

```bash
bin/magento
  cache:clean
```

## Patch

Le patch sono allegate a questo articolo. Per scaricare una patch, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file o sul collegamento corrispondente:

* [Scarica MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-11059_EE_2.2.3_COMPOSER_v1.patch.zip)
* [Scarica MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch](assets/MDVA-23505_EE_2.2.4_COMPOSER_v1.patch.zip)
* [Scarica MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch](assets/MDVA-12158_EE_2.2.5_COMPOSER_v2.patch.zip)

### Versioni compatibili di Adobe Commerce:

Le patch sono state create per:

* MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch creata per Adobe Commerce (tutti i metodi di distribuzione) 2.2.3
* MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch creata per Adobe Commerce (tutti i metodi di distribuzione) 2.2.4
* MDVA-12158\_EE\_2.2.5\_COMPOSER\_v2.patch creata per Adobe Commerce (tutti i metodi di distribuzione) 2.2.5

La patch MDVA-11059\_EE\_2.2.3\_COMPOSER\_v1.patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce on-premise 2.2.0-2.2.2
* Adobe Commerce sull’infrastruttura cloud 2.2.0-2.2.3

La patch MDVA-23505\_EE\_2.2.4\_COMPOSER\_v1.patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce on-premise 2.1.0-2.1.18, 2.2.0-2.2.3
* Adobe Commerce sull’infrastruttura cloud 2.1.0-2.1.18, 2.2.0-2.2.3

La patch MDVA-23505\_EE\_2.2.5\_COMPOSER\_v1.patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce sull’infrastruttura cloud 2.2.5

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita da Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) per istruzioni.

## File allegati
