---
title: "Patch MDVA-32739: vecchie e-mail inviate quando è abilitato l’invio asincrono"
description: La patch MDVA-32739 risolve il problema che, se si abilita [asynchronous email notifications](https://devdocs.magento.com/guides/v2.4/performance-best-practices/configuration.html#asynchronous-email-notifications), vengono inviate e-mail di vendita precedenti. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.2.
exl-id: 8cf4ef8a-f2f2-47fb-9f69-0eedcc10ba8b
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# Patch MDVA-32739: vecchie e-mail inviate quando è abilitato l’invio asincrono

La patch di MDVA-32739 risolve il problema per cui l&#39;attivazione di [notifiche e-mail asincrone](https://devdocs.magento.com/guides/v2.4/performance-best-practices/configuration.html#asynchronous-email-notifications) invia vecchie e-mail di vendita. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.12. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.3.5-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.4.1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Disattiva l’invio asincrono di e-mail.
1. Crea un ordine e assicurati che l’invio dell’e-mail non riesca.
1. Abilita invio asincrono.

<u>Risultati previsti</u>:

Le e-mail vengono inviate solo per ordini, spedizioni, fatture e note di accredito creati dopo l’ultimo aggiornamento asincrono dell’invio.

<u>Risultati effettivi</u>:

La vecchia e-mail verrà inviata tramite il cronjob.

## Correzione

Con la correzione inclusa nella patch, Adobe Commerce selezionerà gli ordini creati dopo l’ultima esecuzione del metodo di invio asincrono e invierà l’e-mail per tali ordini.

Per impostazione predefinita, viene selezionato con uno scostamento di -1 giorno.

È possibile modificare questo valore (ad esempio a -2 giorni) modificando `di.xml`.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta le [patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
