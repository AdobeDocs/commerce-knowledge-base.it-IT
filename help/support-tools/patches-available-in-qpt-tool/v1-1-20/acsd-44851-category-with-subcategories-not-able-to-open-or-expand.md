---
title: 'ACSD-44851: categoria con sottocategorie non in grado di aprire o espandere'
description: Questo articolo fornisce una soluzione al problema che impedisce all’utente di aprire o espandere una categoria con sottocategorie.
exl-id: 46ad9f9d-ed66-44df-b66d-ab9ff3923c36
feature: Categories
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-44851: categoria con sottocategorie non in grado di aprire o espandere

La patch ACSD-44851 risolve il problema se l’utente non è in grado di aprire o espandere una categoria con sottocategorie. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.20. L’ID della patch è ACSD-44851. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente non è in grado di aprire o espandere una categoria con sottocategorie.

<u>Passaggi da riprodurre</u>:

1. In Adobe Commerce Admin, crea una struttura ad albero con due categorie principali e alcune sottocategorie per ciascuna.
1. Apri la visualizzazione/emulatore mobile o riduci la larghezza della finestra finché il layout non diventa mobile.
1. Apri il menu principale del catalogo.
1. Prova ad espandere le categorie principali.
1. Prova ad aprire la categoria.

<u>Risultati previsti</u>:

Il menu è accessibile.

<u>Risultati effettivi</u>:

Il secondo livello del menu mobile non si apre.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Strumenti patch di qualità > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) nella guida dello strumento Patch di qualità.

* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/support-tools/patches/check-patch-for-magento-issue-with-magento-quality-patches.html?lang=it) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, vedere [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida dello strumento Patch di qualità.
