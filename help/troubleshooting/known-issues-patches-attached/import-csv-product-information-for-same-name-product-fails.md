---
title: Importazione delle informazioni sui prodotti CSV per un prodotto con lo stesso nome non riuscita
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.3 relativo agli errori durante il tentativo di importare un file `.csv` con informazioni sui prodotti se sono presenti prodotti con lo stesso nome.
exl-id: 420b0283-455a-4bd5-ba51-18f341ddacd5
feature: Data Import/Export, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# Importazione delle informazioni sui prodotti CSV per un prodotto con lo stesso nome non riuscita

Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.3 relativo agli errori durante il tentativo di importazione di un `.csv` file con informazioni sui prodotti se sono presenti prodotti con lo stesso nome.

## Problema

Quando un `.csv` Se viene importato un file contenente informazioni sui prodotti e sono presenti prodotti con lo stesso nome, viene visualizzato il seguente errore nel passaggio Verifica dati: *&quot;`URL Key XYZ was already generated for an item with the SKU %sku%"`*. Il problema è causato dalla riscrittura degli URL dei prodotti durante l’importazione, anche quando non è presente alcuna colonna per gli URL dei prodotti nel file importato `.csv` file.

<u>Passaggi da riprodurre</u>:

1. Crea due prodotti configurabili con lo stesso nome in Commerce Admin.
1. Creare un `.csv` file per importare i dati per tali prodotti, che dispone ad esempio delle seguenti colonne: `sku` | `product_type` | `name` | `product_websites` | `store_view_code`
1. Vai a **Sistema** > **Trasferimento dati** > **Importa** e seleziona la `.csv` file.
1. Clic **Verifica dati**.

<u>Risultato previsto</u>:

Nessun problema trovato; puoi importare la `.csv` file.

<u>Risultato effettivo</u>:

Viene visualizzato il seguente messaggio di errore: *&quot;La chiave URL XYZ è già stata generata per un elemento con SKU %sku%&quot;*, non è possibile importare il file.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file o sul seguente collegamento:

[Scarica MDVA-12899\_EE\_2.2.3\_COMPOSER\_v2.patch](assets/MDVA-12899_EE_2.2.3_COMPOSER_v2.patch.zip)

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce on-premise 2.2.3

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti edizioni e versioni di Adobe Commerce:

* Adobe Commerce sull’infrastruttura cloud da 2.2.0 a 2.2.7 e 2.3.0
* Adobe Commerce on-premise da 2.2.0 a 2.2.2, da 2.2.4 a 2.2.7 e 2.3.0

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita da Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella knowledge base di supporto per le istruzioni.

## Collegamenti utili

[Applicare patch personalizzate ad Adobe Commerce sull’infrastruttura cloud](https://devdocs.magento.com/guides/v2.3/cloud/project/project-patch.html)

## File allegati
