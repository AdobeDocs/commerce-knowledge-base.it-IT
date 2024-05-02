---
title: "ACSD-50849: l’aggiunta di un nuovo prodotto dopo la cancellazione della cache causa una mancata corrispondenza"
description: Applica la patch ACSD-50849 per risolvere il problema di Adobe Commerce, in cui l’aggiunta di un nuovo prodotto alla categoria dopo la cancellazione della cache determina una mancata corrispondenza tra le posizioni e le selezioni dei prodotti esistenti.
feature: Cache, Categories, Products
role: Admin
exl-id: 3c797bf4-45da-4500-8c06-8c1007249738
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-50849: l’aggiunta di un nuovo prodotto dopo aver cancellato la cache causa una mancata corrispondenza

La patch ACSD-50849 risolve il problema che, quando si aggiunge un nuovo prodotto alla categoria dopo aver cancellato la cache, si verifica una mancata corrispondenza tra le posizioni e le selezioni dei prodotti esistenti. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) QPT 1.1.32 è installato. L’ID della patch è ACSD-50849. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’aggiunta di un nuovo prodotto alla categoria dopo la cancellazione della cache determina una mancata corrispondenza tra le posizioni e le selezioni dei prodotti esistenti.

<u>Passaggi da riprodurre</u>:

1. Crea due prodotti.
1. Assegna un prodotto a una categoria.
1. Apri la categoria dall’amministratore.
1. Pulizia della cache `bin/magento cache:flush`.
1. Aggiungi il secondo prodotto alla categoria.

<u>Risultati previsti</u>:

I prodotti esistenti assegnati alla categoria non vengono rimossi automaticamente.

<u>Risultati effettivi</u>:

Il primo prodotto (esistente) viene rimosso automaticamente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
