---
title: "ACSD-49480: le regole successive non funzionano"
description: Applicare la patch ACSD-49480 per risolvere il problema Adobe Commerce in cui [!UICONTROL Cart Price Rule - Discard Subsequent Rules] non funziona come previsto.
exl-id: 8d306a9e-ed1a-4295-8130-81700cbf31a6
feature: Price Rules
role: Admin
source-git-commit: 7718a835e343ae7da9ff79f690503b4ee1d140fc
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# ACSD-49480 [!UICONTROL Cart Price Rule - Discard Subsequent Rules] non funziona come previsto

La patch ACSD-49480 risolve il problema in cui [!UICONTROL Cart Price Rule - Discard Subsequent Rules] non funziona come previsto. Questa patch è disponibile quando [!DNL Quality Patches Tool (QPT)] 1.1.32. L’ID della patch è ACSD-49480. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!UICONTROL Cart Price Rule - Discard Subsequent Rules] non funziona come previsto.

<u>Passaggi da riprodurre</u>:

1. Creare un **[!UICONTROL Cart Price Rule]** con un codice coupon (denominalo come *TEST*) che offre uno sconto di $10 al *ID prodotto 1* nel **[!UICONTROL Actions]** scheda con [!UICONTROL Discard Subsequent Rules] imposta su *[!UICONTROL Yes]* e [!UICONTROL Priority] imposta su *1*.
1. Crea un altro **[!UICONTROL Cart Price Rule]** senza un codice coupon che dà uno sconto di $5 a *ID prodotto 2* nel **[!UICONTROL Actions]** scheda con [!UICONTROL Priority] imposta su *2*. Supponiamo che si tratti di una vendita globale per *ID prodotto 2*.
1. Vai al sito front-end e aggiungi *ID prodotto 1* e *ID prodotto 2* nel carrello.
1. Applica *TEST* codice coupon.

<u>Risultati previsti</u>

* *Sconto 1* viene applicato a *ID prodotto 1*.
* *Sconto 2* viene applicato a *ID prodotto 2*.

<u>Risultati effettivi</u>

* Solo *Sconto 1* viene applicato a *ID prodotto 1*.
* *Sconto 2* non è applicato a *ID prodotto 2*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
