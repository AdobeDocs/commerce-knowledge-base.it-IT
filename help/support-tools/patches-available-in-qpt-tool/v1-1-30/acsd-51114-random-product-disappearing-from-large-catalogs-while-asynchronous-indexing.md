---
title: "ACSD-51114: i prodotti casuali scompaiono da cataloghi di grandi dimensioni quando è abilitata l’indicizzazione asincrona"
description: Applica la patch ACSD-51114 per risolvere il problema di Adobe Commerce. I prodotti Random scompaiono dai cataloghi di grandi dimensioni quando è abilitata l’indicizzazione asincrona.
exl-id: 6ea7de32-1d30-4c4a-af6e-6a0931396846
feature: Catalog Management, Categories, Products
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-51114: i prodotti casuali scompaiono dai cataloghi di grandi dimensioni quando è abilitata l’indicizzazione asincrona

>[!NOTE]
>
>Questa patch è obsoleta.

La patch ACSD-51114 risolve il problema Prodotti casuali scomparsi da cataloghi di grandi dimensioni quando l’indicizzazione asincrona è abilitata. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.30. L’ID della patch è ACSD-51114. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]:Pagina Cerca patch].Utilizzare l&#39;ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti casuali scompaiono dai cataloghi di grandi dimensioni quando è abilitata l’indicizzazione asincrona.

<u>Passaggi da riprodurre</u>:

1. Crea un set di 10 prodotti.
1. Imposta tutti gli indicizzatori su **[!UICONTROL Update on Save]** modalità.
1. Crea una categoria e assegna a essa tutti i prodotti.
1. Disattiva tutti i prodotti.
1. Apri la categoria e verifica che non vi siano prodotti.
1. Imposta tutti gli indicizzatori su **[!UICONTROL Update on Schedule]** modalità.
1. Imposta il `DEFAULT_BATCH_SIZE` a 2 pollici  `lib/internal/Magento/Framework/Mview/View.php#L31`.
1. Abilitare i prodotti nell&#39;ordine seguente: 1°, 9°, 2°, 5°, 10°, 3°.
1. Esegui il comando cron.
1. Apri nuovamente la categoria.

<u>Risultati previsti</u>:

Vengono visualizzati tutti i prodotti abilitati.

<u>Risultati effettivi</u>:

Tutti i prodotti abilitati non vengono visualizzati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
