---
title: Sono stati eliminati più prodotti di quelli avviati durante l’eliminazione di massa in Amministratore
description: Questo articolo fornisce una patch per il problema noto dell’Adobe СCommerce on cloud infrastructure 2.2.3 relativo alla mancata selezione dei record da eliminare quando viene eseguita un’eliminazione in blocco in una griglia nell’amministratore di Commerce.
exl-id: 0bfdc84e-0292-4702-a20e-bdbe67c111a2
feature: Admin Workspace, Products
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# Sono stati eliminati più prodotti di quelli avviati durante l’eliminazione di massa in Amministratore

Questo articolo fornisce una patch per il problema noto dell’Adobe СCommerce on cloud infrastructure 2.2.3 relativo alla mancata selezione dei record da eliminare quando viene eseguita un’eliminazione in blocco in una griglia nell’amministratore di Commerce.

## Problema

In Amministratore, se selezioni i record cliente o client da eliminare, filtra la griglia, quindi seleziona la **Elimina** azione, tutti i record vengono eliminati.

<u>Passaggi da riprodurre</u>:

1. Accedi a **Catalogo** > **Prodotti** in Admin.
1. Seleziona uno o più prodotti.
1. Selezionare Elimina dal menu a discesa Azioni.

<u>Risultati previsti</u>:

Solo i prodotti selezionati vengono eliminati.

<u>Risultati effettivi</u>:

Vengono eliminati anche alcuni altri prodotti.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file o sul seguente collegamento:

[Scarica MDVA-10600\_EE\_2.2.3\_v1.compositore.patch](assets/MDVA-10600_EE_2.2.3_v1.composer.patch.zip)

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce sull’infrastruttura cloud 2.2.3

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce on-premise 2.1.8-2.1.14, 2.2.0-2.2.2 e 2.2.4-2.2.5
* Adobe Commerce sull’infrastruttura cloud 2.2.4-2.2.5

## Come applicare il cerotto

Consulta [Come applicare una patch del compositore fornita da Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) per istruzioni.
