---
title: "ACSD-46767: [!UICONTROL Category] le cache di pagina invalidano quando cambia la quantità di magazzino"
description: Applicare la patch ACSD-46767 per risolvere il problema Adobe Commerce in cui [!UICONTROL Category] le cache di pagina annullano la validità quando cambia la quantità di magazzino, anche se il prodotto è ancora in magazzino.
feature: Cache, Products, Inventory
role: Admin, Developer
exl-id: 39811c03-8518-4975-a128-31537b4706c0
source-git-commit: b7e2ff7cd259963adb9a113eb8e94acdaa45ba1e
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-46767 [!UICONTROL Category] le cache delle pagine annullano la validità quando cambia la quantità delle scorte

La patch ACSD-46767 risolve il problema in cui [!UICONTROL Category] le cache di pagina annullano la validità quando cambia la quantità di magazzino, anche se il prodotto è ancora in magazzino. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.46. L’ID della patch è ACSD-46767. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!UICONTROL Category] le cache di pagina annullano la validità quando cambia la quantità delle scorte.

<u>Passaggi da riprodurre</u>:

1. Crea alcuni prodotti e aggiungili alla stessa categoria.
1. Apri *[!UICONTROL Category]* nella vetrina per garantire che la pagina sia memorizzata in cache.
1. Effettuare l&#39;ordine con uno dei prodotti della categoria *(la quantità di prodotto è cambiata, ma il prodotto è ancora in magazzino)*.
1. Apri [!UICONTROL Category] di nuovo nella vetrina.

<u>Risultati effettivi</u>:

La pagina non viene caricata dalla cache. Viene rigenerato.

<u>Risultati previsti</u>:

La pagina viene caricata dalla cache.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
