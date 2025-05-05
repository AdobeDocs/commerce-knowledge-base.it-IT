---
title: "ACSD-57337: l’utente amministratore con restrizioni di accesso poteva visualizzare tutte le aziende nella griglia *Aziende*"
description: Applica la patch ACSD-57337 per risolvere il problema Adobe Commerce, in cui un utente amministratore con restrizioni di accesso a siti web specifici può visualizzare le aziende da tutti i siti web nella griglia *Aziende*.
feature: Companies, B2B, Configuration
role: Admin, Developer
exl-id: e49289a1-fe86-42b7-8d93-71f35b5e318d
source-git-commit: 33a9cb0227b318a0fff135621ecd6642f2fa827a
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-57337: l&#39;utente amministratore con restrizioni di accesso poteva visualizzare tutte le società nella griglia *Società*

La patch ACSD-57337 risolve il problema per cui un utente amministratore con restrizioni di accesso a siti Web specifici può visualizzare le società di tutti i siti Web nella griglia *Aziende*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.48. L’ID della patch è ACSD-57337. Il problema è pianificato per essere risolto in Adobe Commerce 2.5.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un utente amministratore con restrizioni di accesso a siti Web specifici potrebbe visualizzare le società da tutti i siti Web nella griglia *Aziende*.

<u>Passaggi da riprodurre</u>:

1. Crea un altro sito web, store e storeview.
1. Crea alcune aziende assegnate a siti Web diversi.
1. Crea un ruolo utente amministratore e imposta l’ambito del ruolo sul sito web creato.
1. Crea un amministratore e assegnalo al ruolo creato.
1. Accedi con un nuovo amministratore.
1. Apri **[!UICONTROL Customers]** > **[!UICONTROL Companies]** e osserva l&#39;elenco delle aziende.

<u>Risultati previsti</u>:

Le aziende che sono state assegnate al sito Web aggiuntivo sono visibili nella griglia *Aziende*.

<u>Risultati effettivi</u>:

Tutte le aziende sono visibili nella griglia *Aziende*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
