---
title: 'MDVA-42645: l''amministratore non può rimborsare i punti premio per il credito dell''archivio disabilitato'
description: La patch MDVA-42645 risolve il problema per cui l'amministratore non può rimborsare i punti premio se la funzionalità di credito all'archivio è disabilitata. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L'ID della patch è MDVA-42645. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 8e8f8c07-c1a2-4031-a2fb-cb737165dc2c
feature: Admin Workspace, Orders, Rewards, Returns
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 0%

---

# MDVA-42645: l&#39;amministratore non può rimborsare i punti premio per il credito dell&#39;archivio disabilitato

La patch MDVA-42645 risolve il problema per cui l&#39;amministratore non può rimborsare i punti premio se la funzionalità di credito all&#39;archivio è disabilitata. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.12. L&#39;ID della patch è MDVA-42645. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;amministratore non può rimborsare i punti premio se la funzionalità di credito dell&#39;archivio è disabilitata.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Crea un nuovo account cliente e aggiungi alcuni punti premio.
1. Disattiva la funzionalità di credito dello store andando in **Store** > Impostazioni > **Configurazione** > **Cliente** > **Configurazione cliente** > **Opzioni di credito dello store**.
1. Accedi come cliente a cui sono assegnati i punti premio.
1. Aggiungi un prodotto al carrello e passa a pagamento.
1. Utilizza i punti premio nella sezione pagamento e inserisci l’ordine.
1. Aprire l&#39;ordine nell&#39;amministratore e fatturarlo.
1. Fare clic sul collegamento **Nota di credito** per creare una nuova nota di credito.
1. Selezionare l&#39;opzione Rimborsa punti premio nella parte inferiore e fare clic su **Rimborso non in linea**.

<u>Risultati previsti</u>:

* Creazione della nota di credito completata.
* I punti premio vengono rimborsati correttamente.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente messaggio di errore: *Non è possibile utilizzare un credito per l&#39;archivio superiore all&#39;importo dell&#39;ordine.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/usage) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella documentazione per gli sviluppatori.
