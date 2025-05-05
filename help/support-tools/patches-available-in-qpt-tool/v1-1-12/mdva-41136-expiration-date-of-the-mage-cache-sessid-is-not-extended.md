---
title: 'MDVA-41136: la data di scadenza di mage-cache-sessid non è estesa'
description: La patch MDVA-41136 risolve il problema per cui la data di scadenza del cookie "mage-cache-sessid" non viene estesa, causando la pulizia dei dati del cliente. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L'ID della patch è MDVA-41136. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 7673d084-1ed2-4f1d-8525-e665b971baf2
feature: Cache
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# MDVA-41136: la data di scadenza di mage-cache-sessid non è estesa

La patch MDVA-41136 risolve il problema che impedisce l&#39;estensione della data di scadenza del cookie `mage-cache-sessid`, causando la pulizia dei dati del cliente. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L&#39;ID della patch è MDVA-41136. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La data di scadenza di `mage-cache-sessid` non è estesa. Verrà eseguita la pulizia dei dati del cliente.

<u>Passaggi da riprodurre</u>:

1. In Amministrazione Commerce, vai a **Archivi** > **Configurazione** > **Web** > **Impostazioni cookie predefinite** > e imposta la **Durata cookie** su 60.
1. Accedi come cliente sulla vetrina.
1. Vai a **Il mio account**.
1. Ricarica la pagina dopo 30 secondi.

<u>Risultati previsti</u>:

Viene visualizzato il nome del cliente nell’intestazione.

<u>Risultati effettivi</u>:

Nome del cliente mancante nell&#39;intestazione e *Messaggio di benvenuto predefinito.* messaggio visualizzato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
