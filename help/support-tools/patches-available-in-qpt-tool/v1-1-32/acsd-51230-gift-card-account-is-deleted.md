---
title: "ACSD-51230: l’account della gift card viene eliminato"
description: Applicare la patch ACSD-51230 per risolvere il problema Adobe Commerce in cui il conto gift card viene eliminato quando il rimborso parziale di un prodotto semplice viene elaborato da un ordine.
exl-id: 4322a175-3641-468a-8a0f-fcbad90c758f
feature: Customer Service, Gift, Marketing Tools
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-51230: l&#39;account della gift card viene eliminato

La patch ACSD-51230 risolve il problema della cancellazione del conto gift card quando il rimborso parziale di un prodotto semplice viene elaborato da un ordine. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.32. L’ID della patch è ACSD-51230. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il conto gift card viene eliminato quando il rimborso parziale di un prodotto semplice viene elaborato da un ordine.

<u>Passaggi da riprodurre</u>:

1. Crea un ordine con un *Biglietto regalo* e un *prodotto semplice* (ad esempio, *add: SKU: GI000XX000XXX, SKU: PC046CP042076*) - (funziona qualsiasi metodo di pagamento e spedizione).
1. Fattura l&#39;ordine.
1. Vai a **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. Viene creato un account per la gift card.
1. Ora vai a **[!UICONTROL Order]** e creare un **[!UICONTROL Credit Memo]**.
1. Modifica la quantità per *Biglietto regalo* su 0 e aggiornarlo. Verrà creato un rimborso parziale per *prodotto semplice*.
1. Fai clic su **[!UICONTROL Refund]**.
1. Ora aggiorna il **[!UICONTROL Marketing]** > **[!UICONTROL Gift Card accounts]**. L’account appena creato viene eliminato.

<u>Risultati previsti</u>

L&#39;account gift card è disponibile per l&#39;uso in quanto il rimborso non è stato creato per la gift card.

<u>Risultati effettivi</u>

Il conto gift card viene eliminato e la gift card non viene rimborsata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
