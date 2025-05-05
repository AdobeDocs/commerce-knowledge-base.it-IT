---
title: 'MDVA-43726: la regola del prezzo di catalogo non viene applicata dopo la reindicizzazione parziale'
description: La patch MDVA-43726 risolve il problema che impedisce l'applicazione della regola del prezzo di catalogo basata sulla corrispondenza degli attributi a livello di archivio dopo la reindicizzazione parziale. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L'ID della patch è MDVA-43726. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 70e7e1d2-e601-4fed-9274-a1a619de29e1
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-43726: la regola del prezzo di catalogo non viene applicata dopo la reindicizzazione parziale

La patch MDVA-43726 risolve il problema che impedisce l&#39;applicazione della regola del prezzo di catalogo basata sulla corrispondenza degli attributi a livello di archivio dopo la reindicizzazione parziale. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L&#39;ID della patch è MDVA-43726. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La regola del prezzo di catalogo basata sulla corrispondenza degli attributi a livello di negozio non viene applicata dopo una reindicizzazione parziale.

<u>Passaggi da riprodurre</u>:

1. Imposta la modalità di indicizzazione in modo che venga eseguita secondo pianificazione.
1. Crea due attributi di prodotto configurabili. Ad esempio: Colore (campione visivo) e Dimensione (campione di testo).
1. Crea un prodotto configurabile utilizzando entrambi gli attributi creati nel passaggio 2.
1. Dopo aver creato i prodotti, crea un attributo di tipo **Sì/No** e rendilo visibile nelle condizioni della regola.
1. Aggiungi questo attributo al set di attributi predefinito.
1. Creare una regola del prezzo di catalogo da applicare quando questo attributo è impostato su **Sì**.
1. Apri uno dei semplici prodotti relativi al prodotto configurabile.
1. Modificare l&#39;ambito per archiviare la visualizzazione e aggiornare il valore dell&#39;attributo in **Yes**.
1. Esegui `CRON` e controlla il prezzo sul front-end.
1. Esegui una reindicizzazione completa. Di nuovo, controlla il prezzo sul front-end.
1. Aggiorna la categoria di prodotto configurabile.
1. Esegui `CRON` e controlla di nuovo il prezzo sul front-end.

<u>Risultati previsti</u>:

La regola di catalogo si applica correttamente senza una reindicizzazione completa utilizzando gli indicizzatori incrementali.

<u>Risultati effettivi</u>:

La regola del catalogo non si applica senza eseguire una reindicizzazione completa.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
