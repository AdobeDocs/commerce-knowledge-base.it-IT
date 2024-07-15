---
title: I nuovi ordini vengono inviati all'archivio
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.0 relativo agli ordini appena creati visualizzati nell’archivio anziché nella griglia Ordini in Commerce Admin.
exl-id: 37b70d28-0569-44f2-b677-29b2bde0bc5c
feature: Storage, Data Import/Export
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# I nuovi ordini vengono inviati all&#39;archivio

Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.0 relativo agli ordini appena creati visualizzati nell’archivio anziché nella griglia Ordini in Commerce Admin.

>[!NOTE]
>
>Il problema è stato risolto nella versione 2.2.3 e successive.

## Problema

Quando i clienti inseriscono gli ordini, questi vengono visualizzati nella griglia degli ordini archiviati anziché nella griglia degli ordini regolari.

<u>Passaggi da riprodurre</u>:

1. Aggiungi qualsiasi prodotto al carrello nella vetrina, procedi attraverso il pagamento e ordina.
1. In Amministrazione Commerce, passa a **Vendite** > **Operazioni** > **Ordine**. Visualizzare l&#39;ordine nella griglia.
1. Passa a **Vendite** > **Archivia** > **Ordini**. Visualizzare il nuovo ordine nella griglia.

<u>Risultati previsti</u>:

L&#39;ordine viene visualizzato solo nella griglia Ordini.

<u>Risultati effettivi</u>:

L&#39;ordine viene visualizzato nella griglia Ordini e nella griglia archivio ordini.

## Soluzione

Dopo aver applicato la patch, gli ordini vengono visualizzati nella griglia Ordine come previsto. Tuttavia, è necessario ripristinare manualmente nell’amministratore di Commerce quelli inviati all’archivio prima che la patch venisse applicata.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[Scarica MDVA-8007\_EE\_2.2.0\_v1.compositore.patch](assets/MDVA-8007_EE_2.2.0_v1.composer.patch.zip)

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce 2.2.0

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce on-premise, Adobe Commerce sull’infrastruttura cloud 2.2.1 - 2.2.3

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita da Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.

## Link utili nella guida utente

* [Gestisci ordini archiviati](https://docs.magento.com/user-guide/sales/order-archive.html)

## File allegati
