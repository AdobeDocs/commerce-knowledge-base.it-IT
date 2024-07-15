---
title: "MDVA-30858: report di liquidazione PayPal mancanti"
description: "La patch MDVA-30858 corregge i rapporti di liquidazione PayPal mancanti quando si dispone di più account PayPal. I report devono essere disponibili nella barra laterale di amministrazione &gt; **Reports** &gt; Sales &gt; **PayPal Settlement**. Invece, il messaggio: *Non è stato possibile trovare alcun record.*. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13. Il problema è stato risolto in Adobe Commerce 2.4.2."
exl-id: 268aa74c-5cb5-4653-a6c9-1d4c30167e6a
feature: Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# MDVA-30858: report di liquidazione PayPal mancanti

La patch MDVA-30858 corregge i rapporti di liquidazione PayPal mancanti quando sono presenti più conti PayPal. I report devono essere disponibili nella barra laterale Amministratore > **Report** > Vendite > **Regolamento PayPal**. Il messaggio *Non è stato possibile trovare alcun record.* viene visualizzato. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.13. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.4

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Corregge il problema per cui non sono stati trovati record in **Report** > Vendite > **Regolamento PayPal** quando sono presenti più account PayPal.

<u>Passaggi da riprodurre</u>:

1. Configura i report di liquidazione PayPal.
1. Vai a Amministratore, a **Rapporti** > Vendite > **Liquidazione PayPal**.
1. Per gli aggiornamenti più recenti, fai clic su **Recupera aggiornamenti** in alto a destra.

<u>Risultati previsti</u>:

I report dovrebbero essere visualizzati.

<u>Risultati effettivi</u>:

Nella griglia non viene visualizzato nulla, anche se i rapporti sono disponibili.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
