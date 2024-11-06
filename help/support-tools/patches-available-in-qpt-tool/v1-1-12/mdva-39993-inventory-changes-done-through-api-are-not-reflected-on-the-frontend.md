---
title: "MDVA-39993: le modifiche dell’inventario eseguite tramite API non vengono riportate nella vetrina"
description: La patch MDVA-39993 risolve il problema che impedisce che le modifiche di inventario eseguite tramite API vengano riportate nella vetrina. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L'ID della patch è MDVA-39993. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 2d49b9b7-8a70-44f3-80bf-4460bb2e61d5
feature: REST, Inventory, Orders, Storefront
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---

# MDVA-39993: le modifiche dell&#39;inventario eseguite tramite API non vengono riportate nella vetrina

La patch MDVA-39993 risolve il problema che impedisce che le modifiche di inventario eseguite tramite API vengano riportate nella vetrina. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L&#39;ID della patch è MDVA-39993. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.5 - 2.3.7-p2 e 2.4.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le modifiche di inventario eseguite tramite API non vengono riportate nella pagina del prodotto di vetrina.

<u>Prerequisiti</u>:

Moduli inventario installati.

<u>Passaggi da riprodurre</u>:

1. Verificare che la coda sia impostata per l&#39;esecuzione con cron e che cron sia installato e in esecuzione.
1. Creare un prodotto configurabile (COC001), con due colori (nero e rosso) e due dimensioni (M e L).
1. Creare un&#39;opzione esaurita (COC001-Red-M).
1. Carica la pagina del prodotto configurabile nella vetrina e prova a fare clic su ciascun colore. Quando fai clic su **Rosso**, la dimensione **M** deve essere cancellata perché è esaurita.
1. Prepara COC001-Red-M in stock utilizzando il seguente endpoint API e il payload:

   ```json
   POST http://{domain}/rest/V1/inventory/source-items
   
   {
     "sourceItems": [
       {
         "sku": "COC001-Red-M",
         "source_code": "default",
         "quantity": 1000,
         "status": 1
       }
     ]
   }
   ```

1. Controlla questo semplice prodotto dal backend e verifica che sia aggiornato a In Stock.
1. Carica il prodotto configurabile dal front-end e fai clic su ciascun colore. Osserva le dimensioni **M** quando fai clic su **Rosso**.

<u>Risultati previsti</u>:

L’opzione COC001-Red-M non viene eliminata perché è stata aggiornata a In Stock tramite API.

<u>Risultati effettivi</u>:

L&#39;opzione COC001-Red-M è ancora eliminata, anche se è in magazzino.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella documentazione per gli sviluppatori.
