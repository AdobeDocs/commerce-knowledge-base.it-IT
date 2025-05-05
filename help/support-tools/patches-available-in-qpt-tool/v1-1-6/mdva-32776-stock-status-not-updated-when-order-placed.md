---
title: 'MDVA-32776: lo stato del magazzino non viene aggiornato con l''inserimento dell''ordine'
description: La patch MDVA-32776 risolve il problema che causa l'aggiornamento dello stato delle scorte quando un ordine viene effettuato ma non spedito. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6. L'ID della patch è MDVA-32776. Il problema è stato risolto in Adobe Commerce 2.4.2.
exl-id: 10e9458f-562a-480b-b813-104a93db4308
feature: Orders
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# MDVA-32776: lo stato del magazzino non viene aggiornato con l&#39;inserimento dell&#39;ordine

La patch MDVA-32776 risolve il problema che causa l&#39;aggiornamento dello stato delle scorte quando un ordine viene effettuato ma non spedito. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.6. L&#39;ID della patch è MDVA-32776. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.0

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.1-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato delle scorte non viene aggiornato quando un ordine viene effettuato ma non spedito.

<u>Prerequisiti</u>:

1. Il modulo Inventario è installato.
1. Visualizza prodotti esauriti è impostato su *Sì*.

   Per impostare, vai a **Archivi** > **Configurazione** > **Catalogo** > **Inventario** > **Visualizza prodotti esauriti** = *Sì*.

<u>Passaggi da riprodurre</u>:

1. Creare due prodotti semplici con qtà = 11 e 22.
1. Crea un prodotto raggruppato utilizzando i prodotti semplici creati nel primo passaggio.
1. Aggiungere prodotti raggruppati al carrello impostando una delle quantità di prodotto su 11 e facendo esaurire l&#39;altro prodotto semplice.
1. Completa il pagamento e fai l’ordine.

<u>Risultati previsti</u>:

I prodotti raggruppati visualizzano le etichette `out-of-stock` quando i prodotti semplici associati esauriscono le scorte.

<u>Risultati effettivi</u>:

1. Il prodotto semplice con qtà = 11 è esaurito.
1. Il prodotto raggruppato non mostra un messaggio *esaurito* per il prodotto con qtà = 11. Tuttavia, l&#39;aggiunta di questo prodotto al carrello restituisce un errore *esaurito*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
