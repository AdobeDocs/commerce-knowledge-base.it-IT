---
title: "ACSD-53378: esperienza di pagamento migliorata per i clienti con rubriche estese"
description: Applica la patch ACSD-53378 per risolvere il problema Adobe Commerce in presenza di problemi di prestazioni causati da grandi volumi di indirizzi dei clienti.
feature: Customers, Checkout
role: Admin
exl-id: 561462fd-844b-40e0-9ccd-25f7aa9be161
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-53378: esperienza di pagamento migliorata per i clienti con rubriche estese

La patch ACSD-53378 risolve il problema in presenza di problemi di prestazioni causati da grandi volumi di indirizzi dei clienti. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.40. L’ID della patch è ACSD-53378. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le prestazioni di Adobe Commerce diventano molto lente se un cliente ha un numero elevato di indirizzi.

Se l’opzione di configurazione *[!UICONTROL Enable search address]* in **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** è attivato, la rubrica del cliente non verrà più elaborata completamente. Il numero di indirizzi cliente elaborati è determinato dall’impostazione *[!UICONTROL Customer Addresses Limit]* in  **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice da Admin.
1. Creare un cliente con un&#39;ampia rubrica contenente 1000 indirizzi.
1. Passa al front-end e aggiungi il prodotto al carrello.
1. Apri la pagina del carrello.

<u>Risultati previsti</u>:

Il conteggio degli indirizzi del cliente non ha alcun impatto sul tempo di risposta.

<u>Risultati effettivi</u>:

Il caricamento della pagina del carrello richiede molto tempo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
