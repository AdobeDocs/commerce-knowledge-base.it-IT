---
title: "ACSD-55231: errore SKU non trovato durante l’utilizzo della funzionalità di ordine rapido"
description: Applica la patch ACSD-55231 per risolvere il problema di Adobe Commerce, se viene visualizzato l’errore *"Lo SKU non è stato trovato nel catalogo"* quando si tenta di aggiungere un prodotto al carrello utilizzando la funzionalità di ordine rapido.
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: 463c2c07-39ec-4b03-81f7-ec2f71f5af76
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 0%

---

# ACSD-55231: errore SKU non trovato durante l’utilizzo della funzionalità di ordine rapido

La patch ACSD-55231 risolve il problema relativo alla *&#39;Impossibile trovare lo SKU nel catalogo&#39;* errore durante il tentativo di aggiungere un prodotto al carrello utilizzando la funzionalità ordine rapido. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44. L’ID della patch è ACSD-55231. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Recupero *&#39;impossibile trovare lo SKU nel catalogo&#39;* errore durante la ricerca di prodotti da aggiungere al carrello utilizzando la funzionalità ordine rapido.

<u>Passaggi da riprodurre</u>:

1. Installare Adobe Commerce con moduli B2B.
1. Accedi a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** e imposta:
   * **[!UICONTROL Enable company]**: *Sì*
   * **[!UICONTROL Enable Shared Catalog]**: *Sì*
   * **[!UICONTROL Enable Quick Order]**: *Sì*
1. Salva la configurazione precedente.
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** e crea un nuovo catalogo condiviso.
1. Accedi a **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** e creare un nuovo cliente:
   * Nel campo gruppo, scegli il catalogo condiviso creato di recente e imposta *[!UICONTROL Allow remote shopping assistance]* a *Sì*.
1. Generare un prodotto semplice con SKU *p12*, associarlo alla categoria *c1* e quindi optare per il catalogo condiviso appena creato nel [!UICONTROL Product in Shared Catalog] sezione.
1. Esegui:

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. Aggiorna la pagina di amministrazione.
1. Accedi a **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** e modificare il cliente creato in precedenza.
1. Clic **[!UICONTROL Login as customer]**.
1. Vai a **[!UICONTROL Quick order]**.
1. Cerca in *p12* SKU e fai clic sul pulsante **[!UICONTROL Product Suggestion]**.
1. Aggiungi questo prodotto al carrello e ordina.
1. Torna a **[!UICONTROL Quick Order]**, cerca SKU *p12* e fai clic su **[!UICONTROL Product Suggestion]**.

<u>Risultati previsti</u>:

Puoi aggiungere il prodotto al carrello utilizzando la funzionalità di ordine rapido.

<u>Risultati effettivi</u>:

Non è possibile aggiungere il prodotto al carrello utilizzando la funzionalità di ordine rapido e ottenere *&#39;Impossibile trovare lo SKU nel catalogo&#39;* durante la ricerca dello SKU del prodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
