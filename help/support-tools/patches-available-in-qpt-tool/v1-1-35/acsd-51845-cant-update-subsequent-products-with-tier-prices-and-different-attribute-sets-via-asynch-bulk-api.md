---
title: 'ACSD-51845: impossibile aggiornare i prodotti successivi con prezzi di livello e set di attributi diversi tramite massa asincrona [!DNL API]'
description: Applicare la patch ACSD-51845 per risolvere il problema di Adobe Commerce che impedisce l'aggiornamento dei prodotti successivi con prezzi di livello e set di attributi diversi tramite massa asincrona [!DNL REST API].
feature: REST, Products
role: Admin
exl-id: c3fff9f2-30ad-4bcb-945e-e9e0c69630b3
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---

# ACSD-51845: impossibile aggiornare i prodotti successivi con prezzi di livello e set di attributi diversi tramite massa asincrona [!DNL API]

La patch di ACSD-51845 risolve il problema che impediva l&#39;aggiornamento dei prodotti successivi con prezzi di livello e set di attributi diversi tramite massa asincrona [!DNL REST API]. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-51845. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;aggiornamento non riesce per i prodotti successivi con prezzi di livello e set di attributi diversi tramite massa asincrona [!DNL REST API].

<u>Passaggi da riprodurre</u>:

1. Configura [!DNL RabbitMQ].
1. Creare due set di attributi.
1. Crea due **Prodotti semplici**, assegnando ogni prodotto a un set di attributi diverso.
1. Aggiungi un **Prezzo gruppo clienti** per ciascun prodotto.
1. Aggiorna entrambi i prodotti nello stesso aggiornamento collettivo [!DNL API].
1. Verificare che il comando `bin/magento queue:consumers:start async.operations.all` sia in esecuzione.
1. Controllare lo stato [!DNL API] in blocco.

<u>Risultati previsti</u>:

Esecuzione del servizio completata.

<u>Risultati effettivi</u>:

Il sistema restituisce il messaggio di errore: *Impossibile salvare il prodotto. Riprova.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
