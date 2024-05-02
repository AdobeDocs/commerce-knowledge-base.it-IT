---
title: '"ACSD-51294: prezzo, quantità, imposta, spedizione, ricavi inviati come stringa a [!DNL Google Analytics] e GTM'''
description: Applica la patch ACSD-51294 per risolvere il problema Adobe Commerce, in cui prezzo, quantità, imposta, spedizione e ricavi vengono inviati come stringa a [!DNL Google Analytics] e GTM.
feature: Orders, Shipping/Delivery, Variables
role: Admin
exl-id: 159e1e98-0def-4b20-901d-f5f58c3ead7c
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '346'
ht-degree: 0%

---

# ACSD-51294: prezzo, quantità, imposta, spedizione, ricavi inviati come stringa a [!DNL Google Analytics] e GTM

La patch ACSD-51294 risolve il problema per cui prezzo, quantità, imposta, spedizione e ricavi vengono inviati come stringa a [!DNL Google Analytics] e GTM. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.32. L’ID della patch è ACSD-51294. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Prezzo, quantità, imposta, spedizione e ricavi vengono inviati come stringa a [!DNL Google Analytics] e GTM.

<u>Passaggi da riprodurre</u>:

1. Configura [!DNL Google Tag Manager] passando a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]** > **[!UICONTROL Google GTag]** > **[!UICONTROL Google Analytics4]**.
2. Crea un prodotto semplice.
3. Completa il pagamento con quel prodotto.
4. Controlla la `dataLayer` Variabile JavaScript nella pagina di completamento dell’estrazione.

<u>Risultati previsti</u>

I valori di prezzo e quantità sono numerici.

<u>Risultati effettivi</u>

I valori di prezzo e quantità sono stringa.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) nel [!DNL Quality Patches Tool] guida.
