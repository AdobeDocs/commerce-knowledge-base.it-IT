---
title: "ACSD-54018: problema di prestazioni con l’elenco dei prodotti del widget catalogo"
description: Applica la patch ACSD-54018 per risolvere il problema di Adobe Commerce, in cui la pagina viene caricata lentamente quando si aggiunge un elenco di prodotti widget di catalogo con tipo di attributo e condizione booleano.
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 9f20484d-58c7-49d8-87df-1eeb84bee6fe
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '441'
ht-degree: 0%

---

# ACSD-54018: Problema di prestazioni con l’elenco dei prodotti del widget catalogo

La patch ACSD-54018 risolve il problema relativo al caricamento lento della pagina quando si aggiunge un elenco di prodotti widget di catalogo con tipo di attributo e condizione booleano. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.38. L’ID della patch è ACSD-54018. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La pagina viene caricata lentamente quando si aggiunge un elenco di prodotti widget di catalogo con tipo di attributo e condizione booleano.

<u>Passaggi da riprodurre</u>:

1. Genera 100.000 prodotti.
1. Creare un attributo booleano con ambito impostato su [!UICONTROL Store View].
1. Assegna un attributo a tutte le serie di attributi.
   * Assegna il valore dell’attributo *Sì* a tutti i prodotti.
1. Ora vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e selezionare tutti i 100.000 prodotti.
   * Scegli **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**.
   * Imposta l’attributo bool su *Sì* e salvalo.
   * Se hai eseguito la disconnessione in questo passaggio, controlla *Note*.
1. Vai a CLI ed esegui `php bin/magento queue:con:start product_action_attribute.update`.
   * Assicurati che gli attributi di tutti i prodotti siano aggiornati.
1. Ora vai a **[!UICONTROL Content]** > **[!UICONTROL Pages]** e crea una nuova pagina.
1. Apri **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**.
1. Scegli *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*.
1. Imposta la condizione *[!UICONTROL Created attribute]* a *[!UICONTROL Yes]* e salvalo.
1. Vai al front-end e apri la pagina creata.
1. Disattiva la cache full-page e blocca la cache HTML.
1. Controlla la velocità di caricamento della pagina.
1. Ricarica la pagina alcune volte e calcola il tempo medio di caricamento.

<u>Risultati previsti</u>:

La pagina viene caricata rapidamente.

<u>Risultati effettivi</u>:

Il caricamento della pagina richiede 5-10 secondi.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
