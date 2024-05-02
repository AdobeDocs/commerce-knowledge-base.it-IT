---
title: "ACSD-52815: il campo di input per il campo della quantità dell’origine non predefinita supporta solo un massimo di 6 cifre"
description: Applicare la patch ACSD-52815 per risolvere il problema di prestazioni di Adobe Commerce, in cui il campo di input per il campo quantità di una sorgente non predefinita supporta solo fino a 6 cifre, a differenza di 8 per una scorta predefinita.
feature: Inventory, Products
role: Admin
exl-id: 44fda5ef-cb8a-481a-9112-f36d886ae3db
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-52815: il campo di input per il campo della quantità di origine non predefinita supporta solo un massimo di 6 cifre

La patch ACSD-52815 risolve il problema per cui il campo di immissione per il campo quantità di una sorgente non predefinita supporta solo fino a 6 cifre, a differenza di 8 per una scorta predefinita. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-52815. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il campo di input per il campo quantità di un&#39;origine non predefinita supporta solo fino a 6 cifre, a differenza di 8 per un titolo predefinito.

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo stock e una nuova origine.
1. Crea un prodotto con il nuovo stock di origine impostato su 123.
1. Controllare la quantità vendibile (123).
1. Aggiorna la quantità di origine in 12345678.
1. Verifica nuovamente la quantità vendibile.

<u>Risultati previsti</u>:

La quantità di vendita mostra l&#39;importo corretto.

<u>Risultati effettivi</u>:

La quantità vendibile è 999999,9999.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
