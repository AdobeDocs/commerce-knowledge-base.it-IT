---
title: 'ACSD-56616: visualizzazione in vetrina dei prodotti in bundle durante una semplice carenza di scorte'
description: Applica la patch ACSD-56616 per risolvere il problema di Adobe Commerce, in cui i prodotti in bundle vengono visualizzati in modo imprevisto sulla vetrina quando tutti i prodotti semplici associati sono esauriti.
feature: Products
role: Admin, Developer
exl-id: 6cf8e15d-38a5-42b6-aee7-67410b501404
source-git-commit: a28257f55abf21cddec9b415e7e8858df33647be
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# ACSD-56616: visualizzazione in vetrina dei prodotti in bundle durante una semplice carenza di scorte.

La patch ACSD-56616 risolve il problema della visualizzazione imprevista dei prodotti in bundle nella vetrina quando tutti i prodotti semplici associati sono esauriti. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.45. L’ID della patch è ACSD-56616. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Visualizzazione errata della vetrina dei prodotti in bundle durante una semplice carenza di scorte.

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo sito web/store/vetrina.
1. Crea una nuova origine.
1. Create un nuovo magazzino e assegnatelo al sito Web appena creato.
1. Configura gli indicizzatori da aggiornare secondo pianificazione.
1. Generare due prodotti semplici, S1 (qtà = 1) e S2 (qtà = 1), e assegnarli al nuovo magazzino e al nuovo sito Web.
1. Crea il prodotto *bundled1* e associalo al nuovo sito Web, inserendolo nella categoria *CAT*.
1. Definisci due opzioni a discesa richieste e collega il prodotto semplice *S1* all&#39;opzione1 e *S2* all&#39;opzione2.
1. Salva i prodotti.
1. Passa a **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** e abilita *Aggiungi codice archivio all&#39;URL* = *Sì*.
1. Apri la vetrina e acquista il prodotto in bundle.
1. Esegui cron due volte.
1. Torna alla categoria *CAT*.

<u>Risultati previsti</u>:

Il prodotto *bundle1* è esaurito.

<u>Risultati effettivi</u>:

Il prodotto *bundle1* è visibile con prezzo = *$0*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
