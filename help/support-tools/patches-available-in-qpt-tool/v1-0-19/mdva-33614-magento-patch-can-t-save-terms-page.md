---
title: "Patch MDVA-33614: impossibile salvare la pagina Condizioni"
description: "La patch di MDVA-33614 risolve il problema dell'impossibilità di salvare le modifiche nella pagina Termini, perché Page Builder genera il seguente errore: *Si è verificato un errore durante l'avvio di Page Builder. Contattare il supporto tecnico*. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L'ID della patch è MDVA-33614. Il problema è stato risolto in Adobe Commerce 2.4.2."
exl-id: d9b287bb-eab4-4c33-b725-ae0074962447
feature: Tools and External Services
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%

---

# Patch MDVA-33614: impossibile salvare la pagina Condizioni

La patch di MDVA-33614 risolve il problema dell&#39;impossibilità di salvare le modifiche nella pagina Condizioni, perché Page Builder genera il seguente errore: *Si è verificato un errore durante l&#39;avvio di Page Builder. Contattare il supporto tecnico*. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L&#39;ID della patch è MDVA-33614. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce sull&#39;infrastruttura cloud 2.4.1

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Non è possibile salvare le modifiche apportate alla pagina Condizioni perché Page Builder genera un errore.

<u>Passaggi da riprodurre</u>:

1. In Amministrazione Commerce, vai a **CONTENUTO** > Elementi > **Pagine**.
1. Selezionare la pagina Condizioni.
1. Fai clic su **Modifica**.
1. Apporta una modifica e fai clic su **Salva**.

<u>Risultato previsto</u>:

La pagina viene salvata senza errori.

<u>Risultato effettivo</u>:

Viene visualizzato il seguente errore: *Si è verificato un errore durante l&#39;avvio di Page Builder. Contattare il supporto tecnico*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, fare riferimento alla sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-).
