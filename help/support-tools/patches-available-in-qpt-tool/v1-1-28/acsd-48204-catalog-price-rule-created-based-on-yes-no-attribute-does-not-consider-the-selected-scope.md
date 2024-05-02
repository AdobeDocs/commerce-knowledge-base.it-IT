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

# ACSD-48204: regola prezzo catalogo creata in base a *Sì/No* l&#39;attributo non considera l&#39;ambito selezionato

La patch ACSD-48204 risolve il problema in cui la regola del prezzo di catalogo creata in base a *Sì/No* l&#39;attributo non considera l&#39;ambito selezionato. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.28. L’ID della patch è ACSD-48204. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Regola prezzo catalogo creata in base a *Sì/No* l&#39;attributo non considera l&#39;ambito selezionato.

<u>Passaggi da riprodurre</u>:

1. Crea due siti Web (predefinito e W2).
1. Crea un attributo di prodotto di *Sì/No* tipo.
   * Imposta [!UICONTROL Default value] = [!UICONTROL No]
   * [!UICONTROL Scope] = [!UICONTROL Website]
   * [!UICONTROL Use for Promo Rule Conditions] = [!UICONTROL Yes]
1. Crea un prodotto configurabile in base a qualsiasi attributo con due varianti (V1 e V2).
   * Aggiungi il *Sì/No* attributo per il set di attributi delle varianti configurabili
   * Per una delle varianti (V1), imposta il valore su *[!UICONTROL Yes]* sul sito Web non predefinito (W2)
1. Creare una regola di catalogo:
   * Applicato a entrambi i siti Web
   * Condizione: *Sì/No* il valore dell&#39;attributo è *[!UICONTROL Yes]*
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

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
