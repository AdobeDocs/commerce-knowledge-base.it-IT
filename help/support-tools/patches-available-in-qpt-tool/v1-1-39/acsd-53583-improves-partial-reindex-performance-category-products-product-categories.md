---
title: '"ACSD-53583: migliorare le prestazioni di reindicizzazione parziale per [!UICONTROL Category Products] e [!UICONTROL Product Categories] indicizzatori'''
description: Applicare la patch ACSD-53585 per migliorare le prestazioni di reindicizzazione parziale per gli indici Categoria prodotti e Categoria prodotti.
feature: Products, Categories
role: Admin, Developer
exl-id: 1c8f7df3-379f-42d6-8b41-286d34f725d2
source-git-commit: 29c2918ccae6404f6ae87d360ac16b149de5dd0d
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-53583: Migliorare le prestazioni di reindicizzazione parziale per gli indicizzatori di categorie e prodotti

La patch ACSD-53583 migliora le prestazioni di reindicizzazione parziale di *Categoria Prodotti* e *Categorie di prodotti* indici. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.39. L’ID della patch è ACSD-53583. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p3
* Non compatibile con [!DNL Live Search] modulo. Per applicare questa patch a [!DNL Live Search] richiedere una patch ACSD-55719 aggiuntiva.

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La reindicizzazione parziale richiede più tempo della reindicizzazione completa.

<u>Passaggi da riprodurre</u>:

1. Imposta tutti gli indici su *Aggiorna per pianificazione*.
1. Generare dati con [!DNL Performance Toolkit] (profilo medio).
1. Apporta modifiche a tutti i prodotti e a tutte le categorie in modo che si trovino nel backlog dell’indice e che tutti gli indici siano inattivi.
1. Esegui reindicizzazione parziale per *Categoria Prodotti* e *Categorie di prodotti* indici.

<u>Risultati previsti</u>:

La reindicizzazione parziale viene chiamata una volta per prodotto e richiede quasi lo stesso tempo della reindicizzazione completa, perché tutti i prodotti e le categorie sono stati modificati.

<u>Risultati effettivi</u>:

La reindicizzazione parziale viene chiamata molte volte per prodotto e richiede più tempo della reindicizzazione completa.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
