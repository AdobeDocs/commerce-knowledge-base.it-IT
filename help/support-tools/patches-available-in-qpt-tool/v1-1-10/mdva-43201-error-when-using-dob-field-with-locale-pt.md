---
title: 'MDVA-43201: errore durante l''utilizzo di un campo DOB con PT delle impostazioni internazionali'
description: La patch MDVA-43201 risolve il problema relativo all'errore che si verifica quando si utilizza l'attributo DOB del cliente nel modulo di registrazione per le impostazioni locali portoghesi. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. L'ID della patch è MDVA-43201. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 02979378-adc1-4a1a-93bf-a35ad50e6b80
feature: B2B, Cache
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-43201: errore durante l&#39;utilizzo di un campo DOB con PT delle impostazioni internazionali

La patch MDVA-43201 risolve il problema relativo all&#39;errore che si verifica quando si utilizza l&#39;attributo DOB del cliente nel modulo di registrazione per le impostazioni locali portoghesi. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.10. L&#39;ID della patch è MDVA-43201. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando l&#39;attributo del cliente DOB viene aggiunto al modulo di registrazione del cliente per le impostazioni locali portoghesi, il modulo restituisce l&#39;errore *L&#39;argomento 1 passato a iterator_to_array() deve implementare l&#39;interfaccia viaggiabile, null specificato*.

<u>Prerequisiti</u>:

I moduli B2B sono installati.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione > **Archivi** > **Configurazione** > **Generale** > **Opzioni internazionali**, imposta la lingua su **Portoghese (Portogallo)** e fai clic su **Salva**.
1. Reindicizzare e cancellare la cache.
1. Vai a **Archivi** > **Attributo** > **Cliente**.
1. Aprire l&#39;attributo del cliente DOB e impostare **Show on Storefront** su **Yes**.
1. Seleziona tutto da **Modulo da utilizzare in**.
1. Salva l’attributo.
1. Vai alla pagina Crea nuovo account nel front-end.

<u>Risultati previsti</u>:

Il modulo di registrazione cliente per l’archivio portoghese non fornisce alcun errore quando si aggiunge l’attributo DOB.

<u>Risultati effettivi</u>:

Il modulo di registrazione cliente per l’archivio portoghese restituisce un errore quando si aggiunge l’attributo DOB.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella documentazione per gli sviluppatori.
