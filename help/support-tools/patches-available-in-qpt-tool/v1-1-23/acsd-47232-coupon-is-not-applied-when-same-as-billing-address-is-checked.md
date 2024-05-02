---
title: "ACSD-47232: la cedola non viene applicata quando [!UICONTROL Same as Billing Address] è selezionato"
description: Applica la patch ACSD-47232 per risolvere il problema di Adobe Commerce in cui il coupon non viene applicato quando [!UICONTROL Same as Billing Address] è selezionato.
exl-id: 29b95a0b-8792-4830-a1e5-ce977f8453ec
feature: Orders, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-47232: la cedola non viene applicata quando [!UICONTROL Same as Billing Address] è selezionato

La patch ACSD-47232 risolve il problema se il coupon non viene applicato quando **[!UICONTROL Same as Billing Address]** è selezionato. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.23. L’ID della patch è ACSD-47232. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il coupon non viene applicato quando **[!UICONTROL Same as Billing Address]** è selezionato.

<u>Passaggi da riprodurre</u>:

1. Installa Adobe Commerce.
1. Creare un prodotto semplice con peso = *8*.
1. Crea un nuovo cliente con indirizzo di fatturazione e spedizione predefinito.
1. Crea una regola di prezzo del carrello con un coupon.
   * In entrata **[!UICONTROL Conditions]** sezioni, aggiungere *Peso totale uguale o superiore a 5*
1. Prova a creare un nuovo ordine in [!UICONTROL Commerce] Amministratore
   * Utilizza il cliente appena creato
   * Aggiungi un prodotto
   * Prova ad applicare il coupon

<u>Risultati previsti</u>:

Coupon applicato.

<u>Risultati effettivi</u>:

Viene visualizzato un errore simile al seguente: *Codice coupon 123 non valido. Verifica il codice e riprova.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
