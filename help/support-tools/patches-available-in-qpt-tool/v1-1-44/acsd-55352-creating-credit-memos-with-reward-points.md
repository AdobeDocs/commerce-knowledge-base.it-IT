---
title: "ACSD-55352: Creazione di note di credito con punti premio"
description: Applicare la patch ACSD-55352 per risolvere il problema di Adobe Commerce, in cui dopo aver creato una nota di credito parziale con i punti premio del cliente, lo stato dell'ordine cambia in *chiuso* e le opzioni della nota di credito scompaiono dalla pagina dell'ordine amministratore.
feature: Checkout, Orders
role: Admin, Developer
exl-id: 33ceb2e9-3cd5-4472-941a-e06c5c534f4a
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# ACSD-55352: Creazione di note di credito con punti premio

La patch ACSD-55352 risolve il problema per cui dopo aver creato una nota di credito parziale con i punti premio del cliente, lo stato dell&#39;ordine cambia in *chiuso* Le opzioni della nota di accredito e scompaiono dalla pagina ordine amministratore. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.44. L’ID della patch è ACSD-55352. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Dopo aver creato una nota di credito parziale con punti premio cliente, lo stato dell&#39;ordine cambia in *chiuso* Le opzioni della nota di accredito e scompaiono dalla pagina ordine amministratore.

<u>Passaggi da riprodurre</u>:

1. Accedi ad Adobe Commerce Admin.
2. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Other Setting]** > **[!UICONTROL Reward Exchange Rates]** > **[!UICONTROL Add New Rate]**.
3. Aggiungi due tassi:
   * *[!UICONTROL First]*:
      * *[!UICONTROL Direction]* = *Punti a valuta*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
   * *[!UICONTROL Second]*:
      * *[!UICONTROL Direction]* = *Valuta in punti*
      * *[!UICONTROL Rate]* = *100*
      * *[!UICONTROL Upper Boundary]* = *100*
4. Creare un prodotto semplice con il prezzo di *$ 100* e con *Qtà* : *100*.
5. Crea un cliente dalla vetrina.
6. Vai di nuovo al backend: **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** > **[!UICONTROL Edit]** > **[!UICONTROL Reward Points]** > **[!UICONTROL Update Points]** > Aggiungi *100* e salvare il cliente.
7. Vai alla vetrina e accedi come cliente creato in precedenza.
8. Aggiungi il prodotto al carrello con *Qtà* : *10*.
9. Vai a **[!UICONTROL Checkout]** e utilizza il *100* ricompensa i punti quando richiesto e inserisci l&#39;ordine.
10. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Invoice]** e spedisci quell&#39;ordine.
11. Vai a [!UICONTROL Credit Memo] e aggiorna *Qtà da rimborsare* a *8*.
12. Seleziona la **[!UICONTROL Refund Reward Points]** e fai clic su **[!UICONTROL Refund offline]**.
13. Provare a rimborsare gli altri due prodotti rimanenti dall&#39;ordine utilizzando [!UICONTROL Credit Memo].

<u>Risultati previsti</u>:

* L’Amministratore crea [!UICONTROL Credit Memo] per restituire i due prodotti rimanenti.
* Lo stato dell’ordine è *Completato*.

<u>Risultati effettivi</u>:

* Impossibile creare altro [!UICONTROL Credit Memo].
* Lo stato dell’ordine è *Chiuso*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
