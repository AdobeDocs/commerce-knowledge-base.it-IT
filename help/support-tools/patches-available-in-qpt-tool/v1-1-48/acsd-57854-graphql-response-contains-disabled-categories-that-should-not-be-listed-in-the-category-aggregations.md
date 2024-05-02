---
title: "ACSD-57854: la risposta *GraphQL* contiene categorie disabilitate che non devono essere elencate nelle aggregazioni di categorie"
description: Applica la patch ACSD-57854 per risolvere il problema Adobe Commerce, se la risposta *GraphQL* contiene categorie disabilitate che non dovrebbero essere elencate nelle aggregazioni di categorie.
feature: GraphQL
role: Admin, Developer
exl-id: b6130a0f-57bc-4719-99f2-beb630c463c7
source-git-commit: ea6f23a7ce599e24c6b683f82cf08b72b2506020
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-57854 *GraphQL* la risposta contiene categorie disabilitate che non devono essere elencate nelle aggregazioni di categorie

La patch ACSD-57854 risolve il problema in cui *GraphQL* la risposta contiene categorie disabilitate che non dovrebbero essere elencate nelle aggregazioni di categorie. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.48. L’ID della patch è ACSD-57854. Il problema è pianificato per essere risolto in Adobe Commerce 2.5.0.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

*GraphQL* la risposta contiene categorie disabilitate che non dovrebbero essere elencate nelle aggregazioni di categorie.

<u>Passaggi da riprodurre</u>:

1. Crea due categorie.
1. Crea un prodotto (Prodotto di Adobe di test) e assegna il prodotto a entrambe le categorie.
1. Disattiva una delle categorie create.
1. Utilizzare i prodotti *GraphQL* per eseguire ricerche nel prodotto.
1. Controlla l’elenco delle categorie di prodotti nella sezione *GraphQL* risposta.

<u>Risultati previsti</u>:

Le categorie disabilitate non sono elencate nella *GraphQL* risposta.

<u>Risultati effettivi</u>:

Le categorie disabilitate sono elencate nell&#39;aggregazione di categorie *GraphQL* risposta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
