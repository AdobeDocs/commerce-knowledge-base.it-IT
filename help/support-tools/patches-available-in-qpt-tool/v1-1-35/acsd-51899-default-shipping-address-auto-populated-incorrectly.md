---
title: 'ACSD-51899: l''indirizzo di spedizione predefinito non viene compilato correttamente automaticamente'
description: Applica la patch ACSD-51899 per risolvere il problema di Adobe Commerce, in cui l’indirizzo di spedizione predefinito viene popolato automaticamente con un indirizzo errato.
feature: Checkout
role: Admin
exl-id: 67100fcd-e98f-4740-8f1f-fcc820f4c75d
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# ACSD-51899: l&#39;indirizzo di spedizione predefinito non viene compilato correttamente automaticamente

La patch ACSD-51899 risolve il problema relativo alla compilazione automatica dell&#39;indirizzo di spedizione predefinito con un indirizzo errato. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-51899. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;indirizzo di spedizione predefinito è compilato automaticamente con un indirizzo errato

<u>Passaggi da riprodurre</u>:

1. Abilita **Prelievo in negozio** nel metodo di spedizione.
1. Crea *stock* e *source*.
1. Crea il prodotto e assegnalo all’origine.
1. Aggiungi un prodotto al carrello.
1. Fai clic su **Procedi all&#39;estrazione** dal mini-carrello.
1. Immetti l&#39;indirizzo e-mail di prova e seleziona **Scegli nello store**.
1. Fare clic sul pulsante **Seleziona archivio** e selezionare un percorso di archivio da cui scegliere.
1. Fai clic sul pulsante **avanti**.
1. Passare alla **home page** facendo clic sul logo dello store.
1. Apri il **mini carrello**.
1. Fare clic sul collegamento ipertestuale inferiore denominato **Visualizza e modifica carrello**.
1. Fai clic su **Procedi all&#39;estrazione**.
1. Fai clic sul pulsante di spedizione nella pagina di spedizione.

<u>Risultati previsti</u>

Il campo dell&#39;indirizzo di spedizione rimane vuoto ad eccezione di *Paese, Regione e CAP*.

<u>Risultati effettivi</u>

Dopo l&#39;aggiornamento della pagina, l&#39;indirizzo di spedizione predefinito viene compilato automaticamente con *indirizzo di prelievo in-store*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
