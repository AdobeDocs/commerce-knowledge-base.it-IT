---
title: Ordini non visualizzati nella griglia Ordini dell'amministratore
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.1 relativo agli ordini non visualizzati nella griglia Ordini in Commerce Admin.
exl-id: b8376760-6558-41ed-8c6b-51c5759e831a
feature: Admin Workspace, B2B, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# Ordini non visualizzati nella griglia Ordini dell&#39;amministratore

Questo articolo fornisce una patch per il problema noto di Adobe Commerce 2.2.1 relativo agli ordini non visualizzati nella griglia Ordini in Commerce Admin.

## Problema

In Adobe Commerce 2.2.1 con l’estensione B2B installata, gli ordini creati in vetrina da un cliente registrato non vengono visualizzati nell’elenco degli ordini nell’account del cliente in Commerce Admin. Nel registro di debug (`./var/log/debug.log`) viene registrato il seguente errore:

`report.CRITICAL: You cannot define a correlation name ‘company_order’ more than once`

<u>Prerequisiti</u>:

Il catalogo dello store contiene prodotti, non dati di esempio di Adobe Commerce, e l’estensione B2B è installata.

<u>Passaggi da riprodurre</u>:

1. Passa alla vetrina e crea un account cliente.
1. Aggiungi un prodotto al carrello, completa il pagamento e invia un ordine.
1. Accedi all’amministratore.
1. Passa a **Clienti,** quindi scegli **Tutti i clienti**.
1. Per il cliente appena creato, fare clic su **Modifica**.
1. Fai clic su **Ordini** nel pannello a sinistra.

<u>Risultato previsto</u>:

L&#39;ordine inviato di recente è elencato nella griglia.

<u>Risultato effettivo</u>:

La griglia Ordini non viene visualizzata. Viene invece visualizzata una pagina vuota.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[Scarica MDVA-7868\_EE\_2.2.1\_v1\_compositore.patch](assets/MDVA-7868_EE_2.2.1_v1_composer.patch.zip)

### Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce on-premise 2.2.1

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce sull’infrastruttura cloud da 2.2.0 a 2.2.3
* Adobe Commerce on-premise 2.2.0 e da 2.2.2 a 2.2.3

## Come applicare il cerotto

Per istruzioni, consulta [Come applicare una patch del compositore fornita da Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.

## File allegati
