---
title: Variabile di incremento auto_increment del database impostata su "3" Adobe Commerce nell’architettura cloud pro
description: Questo è il comportamento previsto per le soluzioni di architettura Pro di Adobe Commerce su infrastruttura cloud a causa dell'architettura a 3 nodi e non può essere modificato.
exl-id: ea478cbc-2dc2-41c9-8ea7-7e2f308e5948
feature: Cloud
source-git-commit: 83b21845cd306336e1cb193a9541478c8a38eea8
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Variabile di incremento auto_increment del database impostata su &quot;3&quot; Adobe Commerce nell’architettura cloud pro

Questo è il comportamento previsto per le soluzioni di architettura Pro di Adobe Commerce su infrastruttura cloud a causa dell&#39;architettura a 3 nodi e non può essere modificato.

Viene utilizzato il cluster di database Galera, un cluster di database con un database MySQL MariaDB per nodo con un&#39;impostazione di incremento automatico di tre per gli ID univoci in ogni database.

<u>Perché l’ID di incremento utilizzato nei cluster Pro non viene sempre separato/incrementato di 3?</u>

L’ID di incremento utilizzato nei cluster non sempre viene separato/incrementato di 3 a causa del modo in cui funziona Galera.

Ognuno dei tre server gestisce il proprio spazio ID e l&#39;incremento utilizzato dipende dal server di database principale MySQL (a seconda del carico relativo), quindi dalle differenze.
Se si esegue SSH su ciascun nodo e si esegue la connessione all&#39;istanza locale di MySQL in esecuzione su tale nodo utilizzando la porta 3307 (anziché essere proxy alla porta &quot;main&quot; sulla porta standard 3306), verrà visualizzata la seguente immagine:

![auto_increment](assets/auto_increment_id.png)

Ad esempio, se l’elemento principale selezionato è il nodo 1 in cui `auto_increment_offset = 1`, l’ID viene incrementato di 1. Quindi, se viene selezionato un nuovo nodo principale in un secondo momento, ad esempio il nodo 3 in cui `auto_increment_offset = 3`, verrebbe incrementato di 3.

## Collegamenti utili

Consulta nella documentazione per gli sviluppatori:

* [Cloud per Adobe Commerce > Architettura Pro > Backup e disaster recovery](https://devdocs.magento.com/cloud/architecture/pro-architecture.html#backup-and-disaster-recovery)
* [Cloud for Adobe Commerce > Installa prerequisiti: database](https://devdocs.magento.com/cloud/before/before-workspace-magento-prereqs.html#database)
