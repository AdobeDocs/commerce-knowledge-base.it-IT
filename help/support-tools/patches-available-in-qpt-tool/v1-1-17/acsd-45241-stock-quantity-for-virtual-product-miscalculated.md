---
title: "ACSD-45241: calcolo errato della quantità di scorte del prodotto virtuale"
description: La patch ACSD-45241 risolve il problema relativo al calcolo errato della quantità di scorte del prodotto virtuale dopo la creazione di una nota di credito. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17. L’ID della patch è ACSD-45241. Il problema è stato risolto in Adobe Commerce 2.4.4.
exl-id: 4be97da9-d399-419a-816e-cf65f15cc3be
feature: Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# ACSD-45241: calcolo errato della quantità di scorte del prodotto virtuale

La patch ACSD-45241 risolve il problema relativo al calcolo errato della quantità di scorte del prodotto virtuale dopo la creazione di una nota di credito. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17. L’ID della patch è ACSD-45241. Il problema è stato risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.5 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La quantità di magazzino per un prodotto virtuale viene calcolata in modo errato dopo la creazione di una nota di credito.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto configurabile con un prodotto virtuale come prodotto secondario in Commerce Admin.
1. Assicurati che entrambi i prodotti creati nel passaggio 1 siano in magazzino.
1. Contrassegna la quantità per il prodotto virtuale creato nel passaggio 1 come 100 e mantieni la quantità vendibile come 100.
1. Aggiungi il prodotto al carrello.
1. Effettuare un ordine con il prodotto virtuale creato nel primo passaggio.
1. Mantenere lo stato dell&#39;ordine come &quot;In sospeso&quot;. Non è necessario elaborare il pagamento.
1. Record `order_created` creato in `inventory_reservation`. La quantità del prodotto virtuale è pari a 100 con la quantità vendibile pari a 99.
1. Apri l&#39;ordine e passa a **Fattura** > **Invia fattura**.
1. Record `invoice_created` creato in `inventory_reservation`. La quantità di prodotto virtuale è ora 99 e anche la quantità vendibile è 99.
1. Creare una nota di credito senza selezionare **Torna al magazzino**.

<u>Risultati previsti</u>:

Nessun nuovo record creato in `inventory_reservation` e la quantità di scorte per il prodotto virtuale rimane invariata.

<u>Risultati effettivi</u>:

Un record `creditmemo_created` viene creato in `inventory_reservation` e la quantità di scorte di prodotto virtuale viene adeguata a 98 con la quantità vendibile pari a 99.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
