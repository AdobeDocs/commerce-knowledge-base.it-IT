---
title: "ACSD-51036: le condizioni di concorrenza durante le chiamate API REST simultanee determinano una sovrascrittura dello stato di spedizione"
description: Applica la patch ACSD-51036 per risolvere il problema Adobe Commerce in presenza di race condition durante le chiamate REST API simultanee, causando la sovrascrittura dello stato di spedizione nella tabella articoli ordinati.
exl-id: 12d90de7-fe5c-4fcc-b84a-d420dcd871ca
feature: REST, Orders, Shipping/Delivery
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-51036: le condizioni di gara durante le chiamate API REST simultanee determinano una sovrascrittura dello stato di spedizione nella tabella degli articoli ordinati

La patch ACSD-51036 risolve il problema in cui le race condition durante le chiamate API REST simultanee determinano una sovrascrittura dello stato di spedizione nella tabella articoli ordinati. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.31. L’ID della patch è ACSD-51036. Tieni presente che il problema è risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le condizioni di concorrenza durante le chiamate API REST simultanee determinano una sovrascrittura dello stato di spedizione nella tabella articoli ordinati.

<u>Passaggi da riprodurre</u>:

1. Crea un ordine con due elementi.
1. Voce fattura A.
1. Inviare contemporaneamente una richiesta di rimborso per l&#39;articolo A tramite API REST mentre si invia una richiesta di spedizione per l&#39;articolo B.
1. Vai all’ordine in **[!UICONTROL Admin Panel]**.

<u>Risultati previsti</u>

*[!UICONTROL Shipped 1]* deve essere presente lo stato per l&#39;articolo B nel *[!UICONTROL Items]* tavolo ordinato.

<u>Risultati effettivi</u>

*[!UICONTROL Shipped 1]* lo stato non è presente per l&#39;articolo B nel *[!UICONTROL Items]* tavolo ordinato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
