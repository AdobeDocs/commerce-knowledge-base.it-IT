---
title: "ACSD-51041: il completamento dell’indice dei prezzi richiede molto tempo"
description: Applicare la patch ACSD-51041 per risolvere il problema di Adobe Commerce, in cui l'indice dei prezzi richiede molto tempo per essere completato con un set di prodotti molto grande.
exl-id: 442f5eae-ca00-4329-be24-68970624928f
feature: Configuration
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '348'
ht-degree: 0%

---

# ACSD-51041: Il completamento dell’indice dei prezzi richiede molto tempo

La patch ACSD-51041 risolve il problema che richiede molto tempo per il completamento dell&#39;indice dei prezzi con un set di prodotti molto grande. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.32. L’ID della patch è ACSD-51041. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.5-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Con un set di prodotti molto ampio, il completamento dell’indice dei prezzi richiede molto tempo.

<u>Passaggi da riprodurre</u>:

1. Abilita *[!UICONTROL Inventory]* modulo.
1. Avere più origini di magazzino (con una fonte non predefinita che fornisce la maggior parte del magazzino).
1. Generare circa 200.000 prodotti.
1. Eseguire un indice di inventario.

<u>Risultati previsti</u>:

`deleteIndexData` elabora solo gli ID univoci per ottimizzare le prestazioni.

<u>Risultati effettivi</u>:

`deleteIndexData` elabora tutti gli ID, il cui completamento richiede molto tempo.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
