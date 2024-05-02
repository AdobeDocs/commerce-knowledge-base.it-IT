---
title: "ACSD-53118: le regole del carrello con il coupon non funzionano correttamente"
description: Applica la patch ACSD-53118 per risolvere il problema Adobe Commerce in cui la regola del prezzo del carrello viene applicata utilizzando un codice coupon mentre il prodotto nel carrello ha un attributo corrispondente vuoto.
feature: Shopping Cart, Price Rules
role: Admin, Developer
exl-id: a660ddb3-03fc-4460-b2a8-8e851f57e7a9
source-git-commit: 35cd21581ee34a6213be42a79e159439b8856fb6
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-53118: le regole del carrello con il coupon non funzionano correttamente

La patch ACSD-53118 risolve il problema in cui la regola del prezzo del carrello viene applicata utilizzando un codice coupon mentre il prodotto nel carrello ha un attributo corrispondente vuoto. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41. L’ID della patch è ACSD-53118. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La regola del prezzo del carrello viene applicata utilizzando un codice coupon, mentre il prodotto nel carrello ha un attributo corrispondente vuoto.

<u>Passaggi da riprodurre</u>:

1. Creare un attributo di prezzo e aggiungerlo alla serie di attributi. Rendi l’attributo utilizzabile nelle condizioni della regola promozionale.
1. Crea un prodotto e lascia vuoto il nuovo attributo.
1. Crea una regola di prezzo del carrello con un coupon specifico e la seguente condizione:

   * Se un articolo viene TROVATO nel carrello con TUTTE queste condizioni true: Attribute1 è 0.

1. Aggiungi al carrello il prodotto creato nel passaggio 2.
1. Utilizza il codice coupon per la regola del carrello creata nel passaggio 3.

<u>Risultati previsti</u>:

Lo sconto non viene applicato al carrello.

<u>Risultati effettivi</u>:

Lo sconto viene applicato al carrello.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
