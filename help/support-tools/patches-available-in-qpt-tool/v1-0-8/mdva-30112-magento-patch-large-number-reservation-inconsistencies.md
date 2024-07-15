---
title: "MDVA-30112: incongruenze nelle prenotazioni di un numero elevato"
description: La patch MDVA-30112 risolve il problema relativo a un numero inaspettatamente elevato di [incoerenze di prenotazione](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) nella tabella "inventory_booking". Le incoerenze nelle prenotazioni includono gli ordini aperti non registrati e gli ordini completi non registrati. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Il problema è stato risolto nella versione 2.4.2 di Adobe Commerce.
exl-id: db74fb61-dfeb-4e99-8513-d36fd68d2267
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# MDVA-30112: numerose incoerenze nelle prenotazioni

La patch MDVA-30112 risolve il problema relativo a un numero inaspettatamente elevato di [incoerenze nelle prenotazioni](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#what-causes-reservation-inconsistencies) nella tabella `inventory_reservation`. Le incoerenze nelle prenotazioni includono gli ordini aperti non registrati e gli ordini completi non registrati. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.8. Il problema è stato risolto nella versione 2.4.2 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.3.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.4 - 2.3.5-p2, 2.4.0 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il valore [bunch-size](https://devdocs.magento.com/guides/v2.4/inventory/inventory-cli-reference.html#list-inconsistencies-command) è il valore per il numero di ordini da caricare contemporaneamente. Se il numero di ordini è superiore a questo valore, Adobe Commerce considera incongruenze gli ordini con stato In sospeso.

>[!NOTE]
>
>È disponibile una patch MDVA-33281 che risolve altri tre problemi di incoerenza dell&#39;inventario. Ciò include un errore irreversibile PHP durante l&#39;esecuzione di `bin/magento inventory:reservation:list-inconsistencies` nella CLI. Un altro problema che viene risolto è la presenza di dati duplicati nell’elenco delle incoerenze. Inoltre, l’emissione in cui una prenotazione viene creata prima dell’ordine effettuato (realizzazione precedente basata sulla prenotazione dopo l’ordine effettuato). Per la soluzione, fare riferimento a [MDVA-33281: inventory inconsistency issues](/help/support-tools/patches-available-in-qpt-tool/v1-0-14/mdva-33281-magento-patch-inventory-inconsistency-issues.md) nella knowledge base di supporto.

<u>Prerequisiti</u>:

Eseguire il comando seguente nella CLI per elencare le incoerenze delle prenotazioni nella tabella `inventory_reservation`:

```
magento inventory:reservation:list-inconsistencies
```

Si verifica un numero inaspettatamente elevato di incoerenze nella prenotazione e/o il comando non viene mai completato.

<u>Passaggi da riprodurre</u>:

1. Eseguire il comando seguente in CLI per risolvere le incoerenze:

   ```
   bin/magento inventory:reservation:list-inconsistencies -r | bin/magento inventory:reservation:create-compensations
   ```

1. Effettuare tre ordini:
   * Assegna a ciascuno un singolo prodotto.
   * Utilizzare il metodo di pagamento con assegno o vaglia postale, in modo che lo stato dell&#39;ordine sia &quot;in sospeso&quot;.
1. È possibile visualizzare tre record con quantità -1 nella tabella `inventory_reservation`. Eseguire il comando seguente nella CLI per visualizzare eventuali incoerenze:

   ```
   bin/magento inventory:reservation:list-inconsistencies
   ```

   Questo non restituisce alcun risultato, il che è corretto.

1. Esegui il comando seguente in CLI:

   ```
   Execute bin/magento inventory:reservation:list-inconsistencies      --bunch-size 1
   ```

   Vedete che gli ordini di stato &quot;in sospeso&quot; sono mostrati come incongruenze.

1. Esegui il comando seguente in CLI:

   ```
   bin/magento inventory:reservation:list-inconsistencies      -r --bunch-size 1 | bin/magento inventory:reservation:create-compensations
   ```

<u>Risultati previsti</u>:

Adobe Commerce non deve risolvere le incoerenze degli ordini di stato &quot;in sospeso&quot;. È necessario risolvere le incoerenze delle scorte per gli ordini con stato &quot;completato&quot;, &quot;chiuso&quot; e &quot;annullato&quot;.

<u>Risultati effettivi</u>:

Se gli ordini sono superiori al valore specificato per la dimensione del gruppo, Adobe Commerce considera gli ordini con stato &quot;in sospeso&quot; come incoerenze e aggiunge più record di risoluzione delle incoerenze per lo stesso ordine.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
