---
title: "ACSD-49839: la struttura e i prezzi del catalogo condiviso generano un errore"
description: Applica la patch ACSD-49839 per risolvere il problema di Adobe Commerce, a causa del quale la struttura e i prezzi del catalogo condiviso generano un errore nell’amministratore quando i prodotti presentano virgolette singole o doppie in SKU.
exl-id: 4c477ae8-602b-452e-83f0-b72a29547ef9
feature: Admin Workspace, Catalog Management, Categories
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-49839: la struttura e i prezzi del catalogo condiviso genera un errore

La patch ACSD-49839 risolve il problema relativo alla struttura e ai prezzi del catalogo condiviso genera un errore nell’amministratore quando i prodotti presentano virgolette singole o doppie in SKU. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.29. L’ID della patch è ACSD-49839. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La struttura e il prezzo del catalogo condiviso genera un errore nell’amministratore quando i prodotti presentano virgolette singole o doppie in SKU.

<u>Passaggi da riprodurre</u>:

1. Imposta alcuni SKU del prodotto con un carattere speciale, ad esempio virgolette doppie come:
   *[Prodotto&quot;12, Prodotto&quot;14, Prodotto&quot;15]*.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Add Shared Catalog]** (ad esempio,*[Test catalogo condiviso]*).
1. Assegna tutto **[!UICONTROL Products and Categories]** > **[!UICONTROL Generate Catalog]** > **[!UICONTROL Save]**.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Test Shared Catalog]** > **[!UICONTROL Action]** > **[!UICONTROL Set Pricing and Structure]**.
1. Contrassegna *[!UICONTROL Root Catalog]* per selezionare tutte le categorie e i prodotti.
1. Osserva le richieste dell’AJAX nel pannello di rete.

<u>Risultati previsti</u>:

La struttura e il prezzo del catalogo condiviso non genera un errore nell’amministratore quando i prodotti presentano virgolette singole o doppie in SKU.

<u>Risultati effettivi</u>:

La struttura e i prezzi del catalogo condiviso generano un errore nell’amministratore quando i prodotti presentano virgolette singole o doppie in SKU.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
