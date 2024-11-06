---
title: "MDVA-39482: il prodotto esaurisce le scorte se viene importato con la quantità '0' con ordini inevasi abilitati"
description: MDVA-39482 risolve il problema relativo all'esaurimento delle scorte del prodotto importato con quantità pari a "0" quando MSI e gli ordini inevasi sono attivati e la soglia delle scorte esaurite è impostata su un valore meno. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4. L'ID della patch è MDVA-39482. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 2caf461c-993d-48b3-bc47-3fa1d014deaf
feature: Data Import/Export, Orders, Products
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-39482: il prodotto esaurisce le scorte se viene importato con la quantità &#39;0&#39; con ordini inevasi abilitati

MDVA-39482 risolve il problema relativo all&#39;esaurimento delle scorte del prodotto importato con quantità pari a &quot;0&quot; quando MSI e gli ordini inevasi sono attivati e la soglia delle scorte esaurite è impostata su un valore meno. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/overview) 1.1.4. L&#39;ID della patch è MDVA-39482. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.1-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.6 - 2.3.7-p2, 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se viene importata con una quantità pari a &quot;0&quot;, il prodotto esaurisce le scorte quando MSI e gli ordini inevasi sono abilitati e la soglia delle scorte esaurite è impostata su un valore meno.

<u>Prerequisiti</u>:

1. È necessario installare MSI e i dati di esempio.
1. Vai a **Archivi** > **Configurazioni** > **Catalogo** > **Inventario**:
   * Imposta ordini arretrati su &quot;Consenti quantità inferiore a 0&quot;
   * Imposta soglia esaurita su &quot;-10&quot;

<u>Passaggi da riprodurre</u>:

1. Assicurati che lo SKU sia **In magazzino** e abbia una quantità di **24-MB01**.
1. Importa il file CSV delle origini Stock. Accertatevi di selezionare &quot;Origini magazzino&quot; in Tipo entità:

   ```code panel
   sku,qty,out_of_stock_qty
   24-MB01,0,-10
   ```

1. Controllare lo stato delle scorte del prodotto dopo l&#39;importazione delle origini delle scorte.

<u>Risultati previsti</u>:

24-MB01 è **Disponibile** in Storefront.

<u>Risultati effettivi</u>:

24-MB01 è **esaurito** in Storefront.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
