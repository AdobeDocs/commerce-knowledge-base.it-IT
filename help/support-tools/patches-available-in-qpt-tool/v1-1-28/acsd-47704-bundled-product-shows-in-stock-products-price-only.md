---
title: "ACSD-47704: il pacchetto di prodotti mostra il prezzo dei soli prodotti in magazzino"
description: Applica la patch ACSD-47704 per risolvere il problema Adobe Commerce, in cui un prodotto in bundle mostra il prezzo dei soli prodotti in stock.
exl-id: 91fbeaf7-4bc2-49b1-a561-c3e63f193eaa
feature: Admin Workspace, Customer Service, Orders, Products
role: Admin
source-git-commit: 3eeb86c2644f8a04ddcf5e205bc400d2ca9969af
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 0%

---

# ACSD-47704: il pacchetto di prodotti mostra il prezzo dei soli prodotti in magazzino

La patch ACSD-47704 risolve il problema in cui i prezzi dei segmenti dei clienti vengono memorizzati nella cache in modo errato tra i gruppi di clienti. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28. L’ID della patch è ACSD-47704. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prezzo di un prodotto in bundle con Dynamic Pricing abilitato non è corretto in quanto sono inclusi solo gli articoli in stock.

<u>Passaggi da riprodurre</u>:

1. Passa al pannello di amministrazione di Commerce.
1. Vai a **[!UICONTROL CATALOG]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Bundle Product]**.
1. Imposta **[UICONROL Dynamic Price]** a **[!UICONTROL Yes]**.
1. Elementi bundle:
   * Imposta **[!UICONTROL Ship bundle items]** a **[!UICONTROL Together]**
   * Seleziona **[!UICONTROL Add Option]**
      * **[!UICONTROL Title]** = o1
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Casella di controllo Contrassegna come obbligatorio
      * Aggiungi qualsiasi prodotto semplice disponibile; ad esempio, Joust Duffle Bag SKU 24-MB01. Prima di aggiungere il prodotto, annota il suo prezzo - $ 34
   * Quantità predefinita: 1
   * Seleziona **[!UICONTROL Add Option]**
      * **[!UICONTROL Option Title]** = o2
      * **[!UICONTROL Input type]** = **[!UICONTROL Dropdown]**
      * Casella di controllo Contrassegna come obbligatorio
      * Aggiungi qualsiasi prodotto semplice in magazzino, diverso dal prodotto aggiunto nel passaggio precedente; ad esempio - Strive Shoulder Pack 24-MB04. Prima di aggiungere il prodotto, annota il suo prezzo - $ 32
      * Quantità predefinita: 1
1. Salva prodotto.
1. Vai alla vetrina e trova il prodotto creato nei passaggi precedenti. Annota il suo prezzo - $66 (66 = 32 + 34).
Attualmente, il prezzo del prodotto aggregato è pari alla somma dei prezzi delle sue opzioni.
1. Passa al pannello di amministrazione di Commerce. Vai a **[!UICONTROL CATALOG]** > **[!UICONTROL Products]**.
1. Trova uno dei prodotti semplici assegnati come opzione al prodotto bundle in precedenza: SKU 24-MB01 e un prezzo di $ 34.
1. Modificarne la quantità in 0.
1. Salva il prodotto.
1. Vai alla vetrina e trova il prodotto bundle creato nei passaggi precedenti. Annota il suo prezzo - $ 32. In precedenza il prezzo era di 66 dollari, ovvero la somma di 34 dollari da SKU 24-MB01 e 32 dollari da SKU 24-MB04. Ora che il prodotto 24-MB01 è esaurito, il prezzo del bundle è indicato come $32. Si tratta del prezzo dell&#39;altro prodotto, che è un&#39;opzione in stock.

<u>Risultati previsti</u>:

Il prezzo dei prodotti in bundle con Dynamic Pricing abilitato viene calcolato in modo coerente, indipendentemente dal fatto che le opzioni siano disponibili o esaurite.

<u>Risultati effettivi</u>:

Il prezzo del prodotto bundle con Dynamic Pricing abilitato non viene calcolato correttamente. Vengono prese in considerazione solo le opzioni in stock, con un conseguente importo inferiore visualizzato rispetto a quello effettivo quando una delle opzioni è esaurita.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
