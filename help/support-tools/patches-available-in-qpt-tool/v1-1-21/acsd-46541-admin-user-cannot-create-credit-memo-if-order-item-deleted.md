---
title: "ACSD-46541: un utente amministratore non può creare una nota di credito se viene eliminato un articolo dell’ordine"
description: Applica la patch ACSD-46541 per risolvere il problema di Adobe Commerce, per cui una volta eliminato un prodotto non è più possibile creare una nota di credito nell’amministratore Adobe Commerce.
exl-id: ff3f8f21-76c1-41b5-bf02-349403a46fc1
feature: Admin Workspace, Orders, Returns
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-46541: un utente amministratore non può creare una nota di credito se viene eliminato un articolo dell&#39;ordine

La patch ACSD-46541 risolve il problema che impediva a un utente amministratore di creare una nota di credito in caso di eliminazione di una voce dell&#39;ordine. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21. L’ID della patch è ACSD-46541. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.3-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Una volta eliminato un prodotto, non è più possibile creare una nota di credito in Commerce Admin.

<u>Passaggi da riprodurre</u>:

1. Accedi all’amministratore di Commerce.
1. Crea un ordine.
1. Fattura l&#39;ordine.
1. Elimina il prodotto dall’ordine.
1. Fai clic sul pulsante **[!UICONTROL Credit Memo]** nella pagina di modifica dell’ordine.
1. Fai clic su **[!UICONTROL Refund Offline]** per creare una nota di credito.

<u>Risultati previsti</u>:

Creazione della nota di credito completata.

<u>Risultati effettivi</u>:

Il _Impossibile trovare i seguenti prodotti con SKU richiesti: SKU001_ viene visualizzato un errore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
