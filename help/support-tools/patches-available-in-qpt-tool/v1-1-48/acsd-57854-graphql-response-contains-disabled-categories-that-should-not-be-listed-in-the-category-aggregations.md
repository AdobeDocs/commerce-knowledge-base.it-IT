---
title: 'ACSD-57854: la risposta *GraphQL* contiene categorie disabilitate che non devono essere elencate nelle aggregazioni di categorie'
description: Applica la patch ACSD-57854 per risolvere il problema Adobe Commerce, se la risposta *GraphQL* contiene categorie disabilitate che non dovrebbero essere elencate nelle aggregazioni di categorie.
feature: GraphQL
role: Admin, Developer
exl-id: b6130a0f-57bc-4719-99f2-beb630c463c7
source-git-commit: ea6f23a7ce599e24c6b683f82cf08b72b2506020
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57854: la risposta di *GraphQL* contiene categorie disabilitate che non devono essere elencate nelle aggregazioni di categorie

La patch ACSD-57854 risolve il problema per cui la risposta *GraphQL* contiene categorie disabilitate che non dovrebbero essere elencate nelle aggregazioni di categorie. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.48. L’ID della patch è ACSD-57854. Il problema è pianificato per essere risolto in Adobe Commerce 2.5.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La risposta di *GraphQL* contiene categorie disabilitate che non dovrebbero essere elencate nelle aggregazioni di categorie.

<u>Passaggi da riprodurre</u>:

1. Crea due categorie.
1. Crea un prodotto (Prodotto di Adobe di test) e assegna il prodotto a entrambe le categorie.
1. Disattiva una delle categorie create.
1. Utilizza i prodotti *GraphQL* per eseguire ricerche nel prodotto.
1. Controlla l&#39;elenco delle categorie di prodotti nella risposta *GraphQL*.

<u>Risultati previsti</u>:

Le categorie disabilitate non sono elencate nella risposta di *GraphQL*.

<u>Risultati effettivi</u>:

Le categorie disabilitate sono elencate nella risposta di aggregazione di categorie *GraphQL*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
