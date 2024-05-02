---
title: "ACSD-52219: risoluzione del problema di filtro delle griglie di amministrazione nel passaggio alla visualizzazione segnalibro"
description: Applica la patch ACSD-52219 per risolvere il problema di Adobe Commerce, in cui i filtri salvati delle griglie di amministrazione non funzionano come previsto quando si passa di frequente da una visualizzazione di segnalibro all’altra.
feature: Admin Workspace
role: Admin
exl-id: e8333ee7-28a8-4457-aeff-6828f8ca9412
source-git-commit: dccb8dde1666fa0c72c7c94cd94c82daddaadc54
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# ACSD-52219: risoluzione del problema di filtro delle griglie di amministrazione nel passaggio alla visualizzazione segnalibro

La patch ACSD-52219 risolve il problema relativo al mancato funzionamento dei filtri salvati dalle griglie di amministrazione quando si passa di frequente da una visualizzazione all&#39;altra. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.39. L’ID della patch è ACSD-52219. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si passa spesso da una visualizzazione all&#39;altra, i filtri salvati nelle griglie di amministrazione non funzionano come previsto.

<u>Passaggi da riprodurre</u>:

1. Accedere a [!DNL Sales Order] nell’Admin.
1. Crea da due a tre filtri.
1. Verificare le impostazioni del filtro cambiando le visualizzazioni per assicurarsi che vengano salvate con precisione.
1. Passare a Filter1 o Filter2.
1. Aggiorna la pagina per aggiornare i dati visualizzati.
1. Passa a una visualizzazione diversa e osserva che i filtri rimangono invariati.
1. Nella vista predefinita vengono ora visualizzati i risultati filtrati, anche se non è stato impostato alcun filtro specifico.

<u>Risultati previsti</u>:

I filtri non vengono scambiati e mantengono lo stato originale.

<u>Risultati effettivi</u>:

Quando si modifica una vista, i filtri si mescolano e la vista corretta non viene salvata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
