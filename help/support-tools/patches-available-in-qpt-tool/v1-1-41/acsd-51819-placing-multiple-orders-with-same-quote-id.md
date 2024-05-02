---
title: "ACSD-51819: inserimento di più ordini con un ID di virgoletta singola"
description: Applica la patch ACSD-51819 per risolvere il problema di Adobe Commerce, in cui è possibile effettuare più ordini con lo stesso ID preventivo.
feature: Orders, Checkout
role: Admin, Developer
exl-id: f217de21-2914-4b84-b596-e9e763669941
source-git-commit: 6fa7182a807147a00ad750966cd839ec18ffe0c7
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51819: inserimento di più ordini con un ID preventivo singolo

La patch ACSD-51819 risolve il problema che consente di inoltrare più ordini con lo stesso ID preventivo. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41. L’ID della patch è ACSD-51819. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

È possibile inserire più ordini con lo stesso ID preventivo.

<u>Passaggi da riprodurre</u>:

1. Accedi come utente.
1. Aggiungi gli oggetti al carrello e procedi al pagamento.
1. Scegli qualsiasi metodo di pagamento ma non fare clic sul pulsante **[!UICONTROL Place Order]** pulsante.
1. Accedi allo stesso account in un altro browser.
1. Procedi al pagamento con gli stessi elementi senza fare clic sul pulsante **[!UICONTROL Place Order]** pulsante.
1. Fai clic sul pulsante **[!UICONTROL Place Order]** in entrambi i sistemi contemporaneamente.
1. Convalida gli ordini effettuati in entrambi i browser.

<u>Risultati previsti</u>:

Viene elaborato correttamente solo il primo ordine proveniente da un browser.

<u>Risultati effettivi</u>:

In entrambi i browser sono stati inseriti gli ordini.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
