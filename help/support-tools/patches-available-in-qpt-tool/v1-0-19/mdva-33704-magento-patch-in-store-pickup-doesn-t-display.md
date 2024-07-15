---
title: "Patch MDVA-33704: prelievo in-store non visualizzato"
description: La patch MDVA-33704 risolve il problema per cui i prodotti con opzione di prelievo in-store non vengono visualizzati come metodo di spedizione.
exl-id: 2c5c7627-5d2e-44d2-9579-314dbd31ee8b
feature: Shipping/Delivery
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Patch MDVA-33704: prelievo in-store non visualizzato

La patch MDVA-33704 risolve il problema per cui i prodotti con opzione di prelievo in-store non vengono visualizzati come metodo di spedizione.

Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L&#39;ID della patch è MDVA-33704. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce su infrastruttura cloud 2.4.0-p1

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.4.0-2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Prerequisito</u>:<br>

**Prelievo nell&#39;archivio** abilitato

<u>Passaggi da riprodurre</u>:

1. Aggiungi un prodotto al carrello.
1. Vai a Pagamento.
1. Aggiungi le informazioni sulla spedizione e scegli un metodo di spedizione diverso dal prelievo in-store.
1. Selezionare **Procedi al pagamento**, ma non passare alla pagina di pagamento.
1. Torna invece alla sezione **Contatti e spedizione**.
1. Seleziona **Ritiro**.
1. Seleziona **Archivio** e **Fai clic per il pagamento**.
1. L&#39;indirizzo di spedizione viene inserito automaticamente come indirizzo di fatturazione.
1. Aggiorna la pagina Web.

<u>Risultati previsti</u>:

L’opzione di prelievo in-store verrà visualizzata come metodo di spedizione, come previsto.

<u>Risultati effettivi</u>:

L&#39;opzione di prelievo in-store non viene visualizzata come metodo di spedizione.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
