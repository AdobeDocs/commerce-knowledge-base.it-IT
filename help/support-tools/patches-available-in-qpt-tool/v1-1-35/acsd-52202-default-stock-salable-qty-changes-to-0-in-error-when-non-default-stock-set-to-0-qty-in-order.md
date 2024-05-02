---
title: "ACSD-52202: la quantità di magazzino vendibile predefinita viene impostata su 0 per errore quando le scorte non predefinite vengono impostate su 0 per ordine"
description: Applicare la patch ACSD-52202 per risolvere il problema di Adobe Commerce in cui una quantità di magazzino predefinita vendibile cambia a 0 per errore quando le scorte non predefinite sono impostate su 0 quantità in un ordine.
feature: Inventory, Products
role: Admin
exl-id: 8a3b5da4-cf16-41c8-b2d5-b740d638c745
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-52202: la quantità di magazzino vendibile predefinita viene impostata su 0 per errore quando le scorte non predefinite vengono impostate su 0 quantità in un ordine

La patch di ACSD-52202 risolve il problema relativo alla modifica della quantità (qtà) di magazzino predefinita su 0 per errore quando la quantità non predefinita è impostata su 0 in un ordine. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-52202. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La quantità di magazzino vendibile predefinita viene impostata su 0 per errore quando le scorte non predefinite vengono impostate su 0 in un ordine.

<u>Passaggi da riprodurre</u>:

1. Accedi a [!DNL Admin].
1. Crea **sito Web2**.
1. Crea personalizzato **source2**.
1. Crea personalizzato **stock2**.
1. Assegna la **source2** e **stock2** a **sito Web1** e l&#39;origine e il materiale di default sul sito Web predefinito.
1. Creare un prodotto semplice e assegnare **qtà** = *10* per origine predefinita e **qtà** = *1* per **source2** sorgente.
1. Effettua un ordine con **qtà** = *1* per **sito Web2**.
1. Creare una fattura e una spedizione.
1. Controlla il prodotto semplice **quantità vendibile**.

<u>Risultati previsti</u>:

Il **quantità vendibile** = *10* per **source2**.

<u>Risultati effettivi</u>:

Il **quantità vendibile** = *0* per entrambe le origini.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
