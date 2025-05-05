---
title: "ACSD-56635: i clienti importati vengono duplicati quando la condivisione account è impostata su [!DNL Global]"
description: Applica la patch ACSD-56635 per risolvere il problema Adobe Commerce, in cui il cliente importato viene duplicato con lo stesso indirizzo e-mail quando l'importazione viene utilizzata con la condivisione dell'account impostata su [!DNL Global].
feature: Customers, Attributes
role: Admin, Developer
exl-id: abd542a1-6764-4385-97a6-b46015363b42
source-git-commit: 880fc679afc853b514fddda56e570fe1a279a3d9
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-56635: i clienti importati vengono duplicati con lo stesso indirizzo e-mail quando la condivisione account è impostata su [!DNL Global]

La patch ACSD-56635 risolve il problema relativo alla duplicazione del cliente importato con lo stesso indirizzo e-mail quando l&#39;importazione viene utilizzata con la condivisione account impostata su [!DNL Global]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48. L’ID della patch è ACSD-56635. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I clienti importati vengono duplicati con lo stesso indirizzo e-mail quando la condivisione account è impostata su [!DNL Global].

<u>Passaggi da riprodurre</u>:

1. In Adobe Commerce (2.4-development b2b) **[!UICONTROL Admin]**, accedere a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Customer Configuration]** > **[!UICONTROL Account Sharing Options]**.
1. Impostare *[!UICONTROL Share Customer Accounts]* su *[!DNL Global]*.
1. Creazione di più siti Web e store:

   * ws1 > s11, s12 > sw111, sw122
   * ws2 > s21, s22 > sw211, sw212

1. Crea un nuovo cliente nel *sito Web principale* dall&#39;amministratore con indirizzo e-mail utilizzato come <adb@yormail.com>.
1. In **[!UICONTROL Admin]**, passa a **[!UICONTROL System]** > **[!UICONTROL Import]**.
1. Seleziona **[!UICONTROL Customer Entity Type]** come *[!UICONTROL Customers Main File]*.
1. Utilizzare lo stesso indirizzo di posta elettronica di <adb@yormail.com> in un sito Web diverso, ad esempio ws1. Consulta il file CSV di esempio customer.csv fornito di seguito.
1. Completare l&#39;importazione per visualizzare il nuovo utente creato nel sito Web *ws1* con lo stesso indirizzo di posta elettronica.

contenuto customer.csv:

```
email,_website,_store,confirmation,created_at,created_in,disable_auto_group_change,dob,firstname,gender,group_id,lastname,middlename,password_hash,prefix,rp_token,rp_token_created_at,store_id,suffix,taxvat,updated_at,website_id,password
adb@yopmail.com,ws1,sv111,,09/01/24 12:49,Default Store View,0,,newjon,,1,newDoe,,d708be3fe0fe0120840e8b13c8faae97424252c6374227ff59c05814f1aecd79:mgLqkqgTwLPLlCljzvF8hp67fNOOvOZb:1,,07e71459c137f4da15292134ff459cba,30/10/15 12:49,1,,,09/01/24 12:49,1,
```

<u>Risultati previsti</u>:

Il cliente importato con lo stesso indirizzo e-mail viene aggiornato invece di essere duplicato.

<u>Risultati effettivi</u>:

I clienti duplicati vengono creati con lo stesso indirizzo e-mail quando si utilizza l’importazione clienti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
