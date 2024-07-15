---
title: "Patch MDVA-33281: problemi di incoerenza dell'inventario"
description: La patch MDVA-33281 risolve tre problemi di incoerenza dell'inventario. Fai clic sui problemi collegati nella sezione Problema per visualizzare i passaggi per riprodurre questi errori. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14.
exl-id: adba9728-6e42-467e-943d-cf8af0bec353
feature: Inventory, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# Patch MDVA-33281: problemi di incoerenza dell&#39;inventario

La patch MDVA-33281 risolve tre problemi di incoerenza dell&#39;inventario. Fai clic sui problemi collegati nella sezione Problema per visualizzare i passaggi per riprodurre questi errori. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.14.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.5-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.4 - 2.3.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La patch risolve problemi di incoerenza dell’inventario quali:

* **Errore irreversibile PHP** durante l&#39;esecuzione di `bin/magento inventory:reservation:list-inconsistencies` in CLI a causa di un tipo di parametro SKU non corretto.
* **Dati duplicati** nell&#39;elenco delle incoerenze.
* **La nuova prenotazione** verrà creata prima dell&#39;ordine effettuato (realizzazione precedente basata sulla prenotazione dopo l&#39;ordine effettuato). In caso di errori nell’inserimento dell’ordine, verrà aggiunta una prenotazione aggiuntiva per compensare.

>[!NOTE]
>
>Esiste anche una patch MDVA-30112 che risolve il problema relativo a un numero inaspettatamente elevato di [incoerenze di prenotazione](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) nella documentazione per gli sviluppatori, nella tabella `inventory_reservation`. Per la soluzione, fare riferimento alla [patch di Magento MDVA-30112: numerose incongruenze nelle prenotazioni](/help/support-tools/patches-available-in-qpt-tool/v1-0-8/mdva-30112-magento-patch-large-number-reservation-inconsistencies.md) nella Knowledge Base di supporto.

## Errore irreversibile PHP

<u>Passaggi da riprodurre</u>:

Errore irreversibile PHP durante l&#39;esecuzione di `bin/magento inventory:reservation:list-inconsistencies`.

Per ottenere un elenco di incoerenze nelle prenotazioni, accedi al server di produzione ed esegui il seguente comando nella CLI (-r switch - output non elaborato):

<pre>inventario bin/magento:reservation:elenco-incoerenze -r</pre>

<u>Risultati previsti</u>:

Viene creato l’elenco delle incongruenze nelle prenotazioni. Questi verranno restituiti nel seguente formato

```plaintext
<ORDER_INCREMENT_ID>:<SKU>:<QUANTITY>:<STOCK-ID>
```

<u>Risultati effettivi</u>:

Viene generato l’errore irreversibile PHP.

## Dati duplicati

Dati duplicati in `inventory_reservation table`.

<u>Passaggi da riprodurre</u>:

Per risolvere eventuali incongruenze nelle prenotazioni, eseguire il comando seguente:

<pre>SELEZIONA *, COUNT(*)
FROM inventory_booking
Metadati GROUP BY, SKU, quantità
CON CONTEGGIO(*) &gt; 1</pre>

<u>Risultati previsti</u>:

Nessun duplicato.

<u>Risultati effettivi</u>:

Sono presenti duplicati.

## Nuova prenotazione

<u>Passaggi da riprodurre</u>:

Nuova prenotazione creata prima dell’ordine effettuato:

1. Importa il database.
1. Esegui `bin/magento setup:upgrade` nel terminale.
1. Elencare incoerenze eseguendo `bin/magento inventory:reservation:list-inconsistencies        -i -r` nel terminale.

<u>Risultati previsti</u>:

Nessun loop e risultati molto più rapidi.

<u>Risultati effettivi</u>:

Gli stessi risultati vengono visualizzati in un ciclo infinito oppure il comando non riesce con `memory_limit`, a seconda delle impostazioni di sistema.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta le [patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
