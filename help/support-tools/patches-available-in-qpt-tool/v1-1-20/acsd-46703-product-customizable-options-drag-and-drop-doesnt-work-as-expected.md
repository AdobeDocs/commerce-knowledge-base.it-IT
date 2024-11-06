---
title: "ACSD-46703: il trascinamento della personalizzazione del prodotto non funziona"
description: Questo articolo fornisce una soluzione per il problema in cui il trascinamento e il rilascio delle opzioni personalizzabili del prodotto non funzionano come previsto.
exl-id: 49b29495-d225-4f34-ac76-b7294a86aea6
feature: Products
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-46703: il trascinamento della personalizzazione del prodotto non funziona

La patch ACSD-46703 risolve il problema relativo al mancato funzionamento delle opzioni personalizzabili del prodotto (trascinamento della selezione). Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20. L’ID della patch è ACSD-46703. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti non possono trascinare e rilasciare le opzioni personalizzabili da una pagina all’altra.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Aggiungi opzioni personalizzabili al prodotto semplice e assicurati di aggiungere più di 20 opzioni con conseguente impaginazione.
1. Prova a spostare un’opzione personalizzabile (tramite trascinamento) all’interno della stessa pagina.
1. Ora prova a spostare un’opzione personalizzabile dalla pagina 2 alla pagina 1.

<u>Risultati previsti</u>:

* Puoi trascinare le opzioni personalizzabili da una pagina all’altra.
* Puoi ordinare i valori utilizzando la funzionalità di trascinamento della selezione, anche per più pagine.

<u>Risultati effettivi</u>:

Non puoi spostare alcun valore in un’altra pagina utilizzando la funzionalità di trascinamento.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Strumenti patch di qualità > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida dello strumento Patch di qualità.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, vedere [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida dello strumento Patch di qualità.
