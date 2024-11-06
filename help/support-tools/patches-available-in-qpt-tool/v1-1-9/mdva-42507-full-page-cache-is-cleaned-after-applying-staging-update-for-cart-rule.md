---
title: "MDVA-42507: la cache a pagina intera viene pulita dopo l’applicazione dell’aggiornamento di staging per la regola del carrello"
description: La patch MDVA-42507 risolve il problema relativo alla pulizia della cache dell'intera pagina dopo l'applicazione dell'aggiornamento di staging per la regola del carrello. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. L'ID della patch è MDVA-42507. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 9303d488-428b-4565-b9ea-469c34856dce
feature: Cache, Categories, Orders, Shopping Cart, Staging
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-42507: la cache a pagina intera viene pulita dopo l&#39;applicazione dell&#39;aggiornamento di staging per la regola del carrello

La patch MDVA-42507 risolve il problema relativo alla pulizia della cache dell&#39;intera pagina dopo l&#39;applicazione dell&#39;aggiornamento di staging per la regola del carrello. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.9. L&#39;ID della patch è MDVA-42507. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La cache a pagina intera viene pulita dopo l’applicazione dell’aggiornamento di staging per la regola del carrello.

<u>Passaggi da riprodurre</u>:

1. Attiva modalità sviluppatore.
1. Apri diverse pagine di prodotti e categorie e verifica (tramite intestazioni) che siano state caricate dalla cache.
1. Applica qualsiasi aggiornamento di staging per la regola del carrello.
1. Verifica se le pagine delle categorie e dei prodotti sono ancora caricate dalla cache.

<u>Risultati previsti</u>:

La cache a pagina intera NON viene pulita dopo l’applicazione dell’aggiornamento di staging per la regola del carrello.

<u>Risultati effettivi</u>:

La cache a pagina intera viene pulita dopo l’applicazione dell’aggiornamento di staging per la regola del carrello.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella documentazione per gli sviluppatori.
