---
title: "ACSD-53722: il prezzo delle opzioni di prodotto in bundle cambia a $0"
description: Applica la patch ACSD-53722 per risolvere il problema di Adobe Commerce, in cui il prezzo delle opzioni del prodotto in bundle cambia a $ 0 quando diventano attivi aggiornamenti pianificati per ambiti diversi.
feature: Products
role: Admin, Developer
exl-id: da4c25ac-78bc-4d4e-a55e-826924a099e9
source-git-commit: e587b70a270bca624fb60a1b0940c05221da3aef
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---

# ACSD-53722: il prezzo delle opzioni di prodotto in bundle cambia a $0

La patch ACSD-53722 risolve il problema in cui il prezzo delle opzioni del prodotto in bundle cambia a $ 0 quando diventano attivi aggiornamenti pianificati per ambiti diversi. Questa patch è disponibile quando [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.41. L’ID della patch è ACSD-53722. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prezzo delle opzioni di prodotto in bundle cambia a $0 quando diventano attivi aggiornamenti pianificati per ambiti diversi.

<u>Passaggi da riprodurre</u>:

1. Creare due siti Web, A e B.
1. Imposta configurazione in **[!UICONTROL Catalog]** > **[!UICONTROL Price]** > **[!UICONTROL Catalog Price Scope]** = **[!UICONTROL Website]**.
1. Crea un prodotto in bundle con un prezzo fisso sui siti Web A e B:

   * Prezzo del prodotto nel pacchetto = fisso = *0*

1. Aggiungi un prodotto semplice come opzione a discesa per il bundle. Imposta i prezzi seguenti:

   * All store views price inside bundled option = prodotto semplice *120*
   * Sito web del prodotto semplice Un prezzo all&#39;interno dell&#39;opzione in bundle = *130*
   * Sito web del prodotto semplice B prezzo all&#39;interno opzione in bundle = *140*

1. Pianifica un aggiornamento per disabilitare il prodotto in bundle sul sito Web A.

<u>Risultati previsti</u>:

L’aggiornamento pianificato per il sito web A non influisce sul prezzo del sito web B.

<u>Risultati effettivi</u>:

Dopo l’aggiornamento pianificato, il prezzo dell’opzione del prodotto nel pacchetto sul sito web B viene modificato in **$ 0**.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nel [!DNL Quality Patches Tool] guida.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida di Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], consulta:

* [[!DNL Quality Patches Tool] rilasciato: un nuovo strumento per applicare patch di qualità self-service](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: cerca le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nel [!DNL Quality Patches Tool] guida.
