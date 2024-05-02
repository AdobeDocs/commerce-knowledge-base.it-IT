---
title: '"ACSD-52606: messaggio di errore visualizzato quando l’utente fa clic su "Notifica ordine pronto per il ritiro""'
description: Applica la patch ACSD-52606 per risolvere il problema di Adobe Commerce che causa la visualizzazione di un messaggio di errore quando l’utente fa clic su **[!UICONTROL Notify Order is Ready for Pickup]**.
feature: Orders, User Account
role: Admin, Developer
exl-id: c3e69eb1-90bf-46cf-9b53-110e40e0c3c1
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-52606: messaggio di errore visualizzato quando l’utente fa clic su &quot;Notify Order is Ready for Pickup&quot; (Notifica ordine pronto per il prelievo)

La patch ACSD-52606 risolve il problema relativo a un messaggio di errore *Il tuo ordine non è pronto per il ritiro* viene visualizzato quando l’utente fa clic su **[!UICONTROL Notify Order is Ready for Pickup]**. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.37. L’ID della patch è ACSD-52606. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un messaggio di errore *Il tuo ordine non è pronto per il ritiro* viene visualizzato sullo schermo quando l’utente fa clic su **[!UICONTROL Notify Order is Ready for Pickup]**.

<u>Prerequisiti</u>:

I moduli di inventario sono installati.

<u>Passaggi da riprodurre</u>:

1. Installa nuova istanza.
1. Create una nuova origine e un nuovo materiale.
1. Assegna la nuova origine al sito Web predefinito.
1. Abilitare la posizione di prelievo per l&#39;origine appena creata.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]** e abilita **[!UICONTROL In-Store Delivery]**.
1. Creare un *In magazzino* prodotto semplice con *QTÀ=0* per tutti gli stock e *[!UICONTROL Manage Stock = No]* e assegnarlo a entrambe le origini.
1. Crea un ordine dal front-end con il prodotto creato nel passaggio precedente, scegliendo *[!UICONTROL In-Store Pickup]* come metodo di consegna.
1. In Amministratore, vai a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice that order]**.
1. Clic **[!UICONTROL Notify order is ready for pickup]**.

<u>Risultati previsti</u>:

La notifica viene inviata senza errori.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente messaggio di errore: *Il tuo ordine non è pronto per il ritiro*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
