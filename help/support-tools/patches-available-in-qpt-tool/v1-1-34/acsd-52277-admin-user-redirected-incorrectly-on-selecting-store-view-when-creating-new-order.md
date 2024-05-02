---
title: "ACSD-52277: l’utente amministratore non è stato reindirizzato correttamente quando ha selezionato la vista store durante la creazione di un nuovo ordine"
description: Applica la patch ACSD-52277 per risolvere il problema di Adobe Commerce, se un utente amministratore non viene reindirizzato correttamente, dopo aver selezionato la vista Store durante la creazione di un nuovo ordine in Admin.
exl-id: 6f0b86ae-f6f1-44cf-aef5-64def5f14824
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-52277: l’utente amministratore non è stato reindirizzato correttamente quando ha selezionato la vista store durante la creazione di un nuovo ordine

La patch ACSD-52277 risolve il problema relativo a un utente amministratore che non viene reindirizzato correttamente dopo aver selezionato la vista Store durante la creazione di un nuovo ordine in Admin. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.34. L’ID della patch è ACSD-52277. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4, 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un utente amministratore non viene reindirizzato correttamente dopo aver selezionato la vista store durante la creazione di un nuovo ordine.

<u>Passaggi da riprodurre</u>

1. Installa un’istanza pulita.
1. Crea un prodotto.
1. Crea un sito web aggiuntivo, uno store e due visualizzazioni store.
1. Crea un ordine da Amministratore selezionando *visualizzazione store 1*.

<u>Risultati previsti</u>:

L’utente viene reindirizzato alla pagina dell’ordine.

<u>Risultati effettivi</u>:

L’utente non viene reindirizzato alla pagina dell’ordine dopo aver selezionato la vista Store.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
