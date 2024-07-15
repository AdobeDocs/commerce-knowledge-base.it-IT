---
title: "ACSD-54106: Rettifica ordinamento caratteri accentati turchi nella categoria di prodotto"
description: Applica la patch ACSD-54106 per risolvere il problema di Adobe Commerce per cui l’ordinamento dei prodotti di categoria in base al nome per i caratteri accentati turchi non è corretto.
feature: Categories, Products, Search
role: Admin
exl-id: 80386ded-4ada-4822-b073-f477ca123093
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# ACSD-54106: Rettifica ordinamento caratteri accentati turchi nella categoria di prodotto

La patch ACSD-54106 risolve il problema per cui l’ordinamento dei prodotti di categoria in base al nome per i caratteri accentati turchi non è corretto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39. L’ID della patch è ACSD-54106. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.4-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’ordinamento dei prodotti all’interno delle categorie per nome non è corretto per i caratteri accentati turchi.

<u>Passaggi da riprodurre</u>:

1. Accedi al pannello di amministrazione.
1. Crea prodotti semplici denominati come segue e assegnali a qualsiasi categoria:

* Nome A
* Nome Ç
* Nome D
* Nome del file di testo
* Nome M
* Nome Ö
* Nome Ü
* Nome Y
* Nome Z

1. Passa alla vetrina e accedi alla categoria contenente i prodotti.
1. Modificare l&#39;ordinamento in *[!UICONTROL By Name]*.

<u>Risultati previsti</u>:

I prodotti vengono ordinati correttamente nel seguente ordine:

* Nome A
* Nome Ç
* Nome D
* Nome del file di testo
* Nome M
* Nome Ö
* Nome Ü
* Nome Y
* Nome Z

<u>Risultati effettivi</u>:

I prodotti vengono ordinati in modo errato nel seguente ordine:

* Nome A
* Nome D
* Nome M
* Nome Y
* Nome Z
* Nome Ç
* Nome Ö
* Nome Ü
* Nome del file di testo

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
