---
title: "ACSD-52398: la quantità richiesta non è disponibile quando si tenta di aggiornare la quantità del prodotto nel bundle"
description: Applica la patch ACSD-52398 per risolvere il problema di Adobe Commerce per cui la quantità richiesta non è disponibile quando si tenta di aggiornare la quantità di un prodotto nel carrello nella vetrina.
feature: Shopping Cart, Quotes, Products
role: Admin
exl-id: 7b7f06ac-7913-4603-992a-a5620045d828
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# ACSD-52398: la quantità richiesta non è disponibile quando si tenta di aggiornare la quantità del prodotto nel pacchetto

La patch ACSD-52398 risolve il problema se la quantità richiesta non è disponibile quando si tenta di aggiornare la quantità di un prodotto nel carrello nella vetrina. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-52398. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La quantità richiesta non è disponibile quando si tenta di aggiornare la quantità di un prodotto nel carrello nella vetrina.

<u>Passaggi da riprodurre</u>:

1. Creare due prodotti semplici con quantità *1* e *10*.
1. Crea un prodotto in bundle utilizzando i prodotti semplici.
1. Aggiungi il prodotto nel carrello.
1. Modifica il prodotto e prova ad aggiornare la quantità a *3* per l&#39;opzione in cui sono disponibili *10* elementi.

<u>Risultati previsti</u>:

Nessun errore. La quantità è stata aggiornata correttamente poiché per questa opzione sono disponibili *10* elementi.

<u>Risultati effettivi</u>:

Viene generato il seguente errore: *La quantità richiesta non è disponibile*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
