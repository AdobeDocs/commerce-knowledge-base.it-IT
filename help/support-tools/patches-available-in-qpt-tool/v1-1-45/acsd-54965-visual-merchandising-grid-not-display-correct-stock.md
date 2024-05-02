---
title: '"ACSD-54965: [!UICONTROL Visual Merchandising] la griglia non visualizza il materiale corretto'''
description: Applicare la patch ACSD-54965 per risolvere il problema Adobe Commerce in cui [!UICONTROL Visual Merchandising] la griglia non visualizza il materiale corretto quando un prodotto viene assegnato al materiale personalizzato.
feature: Merchandising, Categories
role: Admin, Developer
exl-id: 13d98f55-ca2c-4064-b66f-ab2cdeb37382
source-git-commit: 4f05117aa42dec1f56e4986ffd22d1a68bf5cea2
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# ACSD-54965 [!UICONTROL Visual Merchandising] la griglia non visualizza il materiale corretto

La patch ACSD-54965 risolve il problema in cui [!UICONTROL Visual Merchandising] la griglia non visualizza il materiale corretto quando un prodotto viene assegnato al materiale personalizzato. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45. L’ID della patch è ACSD-54965. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il [!UICONTROL Visual Merchandising] la griglia non visualizza il materiale corretto quando un prodotto viene assegnato al materiale personalizzato.

<u>Passaggi da riprodurre</u>:

1. Crea una nuova origine.
1. Create un nuovo grezzo.
1. Crea due prodotti:
   * Un solo prodotto con il magazzino personalizzato.
   * Un solo prodotto con le scorte di default.
1. Aggiungi questi prodotti a una categoria.
1. Vai a [!UICONTROL visual Merchandising] griglia (*[!UICONTROL Products in Category]*).

<u>Risultati effettivi</u>:

In *[!UICONTROL All Store Views]* il prodotto con scorte personalizzate non mostra alcuna quantità. È solo quando *[!UICONTROL Default Store View]* è selezionato l&#39;ambito, il magazzino personalizzato mostra la quantità del prodotto.

<u>Risultati previsti</u>:

La griglia mostra tutte le informazioni sulle scorte se l&#39;ambito è *[!UICONTROL All Store Views]*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
