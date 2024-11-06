---
title: "ACSD-46674: opzioni personalizzate del tipo di immagine visualizzata come HTML nelle e-mail dei clienti"
description: Applica la patch ACSD-46674 per risolvere il problema di Adobe Commerce, in cui le opzioni personalizzate del tipo di immagine vengono visualizzate come HTML nelle e-mail dei clienti.
exl-id: b4941dd0-bb3a-4805-9631-1d256a92f461
feature: Communications, Personalization
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-46674: opzioni personalizzate del tipo di immagine visualizzata come HTML nelle e-mail dei clienti

La patch ACSD-46674 risolve il problema della visualizzazione delle opzioni personalizzate di un tipo di immagine come HTML nelle e-mail dei clienti. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.21. L’ID della patch è ACSD-46674. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le opzioni personalizzate di un tipo di immagine vengono visualizzate come HTML nelle e-mail dei clienti.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto con un’opzione personalizzata.
   * Tipo di opzione: *File*
   * Estensioni file compatibili: *png, jpg, gif*
   * Richiesto: *Sì*
1. Effettua un ordine per questo prodotto con un’immagine caricata come opzione personalizzata.
1. Creare una fattura per l&#39;ordine creato nel passaggio 2.
1. Creare una nota di credito.
1. Controlla tutte le e-mail di conferma.

<u>Risultati previsti</u>:

Le e-mail di conferma mostrano l’immagine caricata.

<u>Risultati effettivi</u>:

Le e-mail di conferma contengono un codice HTML normale invece dell’immagine dell’opzione personalizzata del prodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tools] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per l&#39;esecuzione automatica di patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in [!DNL QPT], fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
