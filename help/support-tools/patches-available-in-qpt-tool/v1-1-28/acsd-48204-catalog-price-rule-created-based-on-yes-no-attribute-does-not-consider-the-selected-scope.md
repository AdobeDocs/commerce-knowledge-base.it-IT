---
title: "ACSD-48204: la regola del prezzo di catalogo creata in base all’attributo *Sì/No* non considera l’ambito selezionato"
description: Applica la patch ACSD-48204 per risolvere il problema Adobe Commerce per cui la regola del prezzo di catalogo creata in base all’attributo *Sì/No* non considera l’ambito selezionato.
exl-id: 9b0b4d62-c4c5-40d7-a279-52f59ee7ac42
feature: Admin Workspace, Attributes, Catalog Management, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# ACSD-48204: la regola del prezzo del catalogo creata in base all&#39;attributo *Sì/No* non considera l&#39;ambito selezionato

La patch ACSD-48204 risolve il problema per cui la regola del prezzo di catalogo creata in base all&#39;attributo *Sì/No* non considera l&#39;ambito selezionato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28. L’ID della patch è ACSD-48204. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La regola del prezzo di catalogo creata in base all&#39;attributo *Sì/No* non considera l&#39;ambito selezionato.

<u>Passaggi da riprodurre</u>:

1. Crea due siti Web (predefinito e W2).
1. Creare un attributo di prodotto di tipo *Sì/No*.
   * Imposta [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Crea un prodotto configurabile in base a qualsiasi attributo con due varianti (V1 e V2).
   * Aggiungi l&#39;attributo *Sì/No* al set di attributi delle varianti configurabili
   * Per una delle varianti (V1), imposta il valore su *[!UICONTROL Yes]* nel sito Web non predefinito (W2)
1. Creare una regola di catalogo:
   * Applicato a entrambi i siti Web
   * Condizione: *Il valore dell&#39;attributo* è *[!UICONTROL Yes]*
   * Sconto = 50%
1. Apri il prodotto configurabile sul sito Web non predefinito (W2).
1. Verifica che alla variante V1 sia applicato lo sconto del 50%.
1. Apri la variante V1 in Adobe Commerce Admin.
   * Passa al sito Web predefinito
   * Non apportare modifiche e salvare il prodotto
1. Aggiorna la pagina della vetrina del prodotto configurabile.

<u>Risultati previsti</u>:

Alla variante V1 viene ancora applicato lo sconto del 50% in quanto non sono state apportate modifiche.

<u>Risultati effettivi</u>:

Lo sconto scompare.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
