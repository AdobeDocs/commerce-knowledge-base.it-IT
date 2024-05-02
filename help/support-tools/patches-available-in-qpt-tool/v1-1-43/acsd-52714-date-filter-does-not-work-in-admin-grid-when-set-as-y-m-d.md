---
title: "ACSD-52714: il filtro data non funziona nella griglia di amministrazione se impostato come y-m-d"
description: Applica la patch ACSD-52714 per risolvere il problema di Adobe Commerce per cui il filtro della data non funziona nella griglia di amministrazione quando il formato della data è impostato come y-m-d.
feature: Attributes
role: Admin, Developer
exl-id: b292ab2c-e12d-40df-a9ad-19f25fbde5a0
source-git-commit: 513cb47c054dbb907810bbdc3d20d2aca9d5e42b
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-52714: il filtro data non funziona nella griglia di amministrazione se impostato come y-m-d

La patch ACSD-52714 risolve il problema relativo al mancato funzionamento del filtro data nella griglia di amministrazione quando il formato data è impostato su y-m-d. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.43. L’ID della patch è ACSD-52714. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il filtro data non funziona nella griglia di amministrazione quando il formato data è impostato su y-m-d.

<u>Passaggi da riprodurre</u>:

1. Installa clean Adobe Commerce.
1. Modifica
   `/app/code/Magento/Customer/view/adminhtml/ui_component/customer_listing.xml`
file e aggiungi
   `<dateFormat>Y-MM-dd</dateFormat>`
a
   `<column name="created_at" class="Magento\Ui\Component\Listing\Columns\Date" component="Magento_Ui/js/grid/columns/date" sortOrder="100">`
sotto il tag
   `<dataType>date</dataType>`

1. Svuota la cache `bin/magento c:f`.
1. Accedi ad Admin e crea un nuovo cliente da **[!UICONTROL Customers]** > **[!UICONTROL All Customers]**.

   * da: data corrente meno 1 giorno
   * a: data corrente

1. Fai clic su **[!UICONTROL Apply Filters]**.

<u>Risultati previsti</u>:

Il filtro data della griglia funziona correttamente, indipendentemente dalle impostazioni internazionali impostate.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente messaggio: *Non è stato trovato alcun record*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
