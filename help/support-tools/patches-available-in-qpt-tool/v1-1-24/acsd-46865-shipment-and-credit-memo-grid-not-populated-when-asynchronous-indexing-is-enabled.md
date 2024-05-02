---
title: '"ACSD-46865: [!UICONTROL shipment] e [!UICONTROL credit memo] non popolato quando [!UICONTROL asynchronous indexing] è abilitato'''
description: Applicare la patch ACSD-46865 per risolvere il problema Adobe Commerce in cui [!UICONTROL shipment] e [!UICONTROL credit memo] le griglie non vengono compilate quando [!UICONTROL asynchronous indexing] è abilitato.
exl-id: 056177a8-42f0-4138-8c04-5b037d25dfd0
feature: Cache, Orders, Returns, Shipping/Delivery
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# ACSD-46865 [!UICONTROL shipment] e [!UICONTROL credit memo] non popolato quando [!UICONTROL asynchronous indexing] è abilitato

La patch ACSD-46865 risolve il problema dove [!UICONTROL shipment] e [!UICONTROL credit memo] le griglie non vengono compilate quando [!UICONTROL asynchronous indexing] è abilitato. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.24. L’ID della patch è ACSD-46865. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!UICONTROL Shipment] e [!UICONTROL credit memo] le griglie non vengono compilate quando [!UICONTROL asynchronous indexing] è abilitato.

<u>Passaggi da riprodurre</u>:

1. In [!DNL Commerce] Amministratore, vai a **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL Grid Settings]** > **[!UICONTROL Asynchronous indexing Enable]** = *SÌ*.
2. Vai di nuovo a **[!UICONTROL Set Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoices]** > **[!UICONTROL Shipments]** > **[!UICONTROL Credit Memos Archiving]** > **[!UICONTROL Enable Archiving]** = *[!UICONTROL YES]*.
3. Pulizia cache di configurazione.
4. Effettuare un nuovo ordine per un prodotto semplice.
5. Esegui cron.
6. Apri l’ordine in [!UICONTROL Commerce] Amministratore da **[!UICONTROL Sales]** > **[!UICONTROL Orders]** e generare una fattura e una nota di accredito.
7. Sposta l&#39;ordine in [!UICONTROL Archive].
8. Crea un altro ordine per un prodotto semplice.
9. Esegui cron.
10. Passare al nuovo ordine e generare una nuova spedizione, una fattura e una nota di accredito.
11. Esegui cron.
12. Controlla la [!UICONTROL shipments], [!UICONTROL invoices], e [!UICONTROL credit memo] griglie nell&#39;amministratore.

<u>Risultati previsti</u>:

Nuovo [!UICONTROL shipment], [!UICONTROL invoice] e [!UICONTROL credit memo] vengono visualizzati.

<u>Risultati effettivi</u>:

Nuovo [!UICONTROL shipment], [!UICONTROL invoice], e [!UICONTROL credit memo] non sono visualizzati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
