---
title: "ACSD-42807: il simbolo di valuta personalizzato non viene visualizzato nella vetrina"
description: La patch ACSD-42807 risolve il problema se il simbolo di valuta personalizzato non viene visualizzato nella vetrina. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17. L’ID della patch è ACSD-42807. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
exl-id: 21bd17b4-d9d8-4c40-8f89-d6f7b930b475
feature: Storefront
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-42807: il simbolo di valuta personalizzato non viene visualizzato nella vetrina

La patch ACSD-42807 risolve il problema se il simbolo di valuta personalizzato non viene visualizzato nella vetrina. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.17. L’ID della patch è ACSD-42807. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il simbolo di valuta personalizzato non viene visualizzato nella vetrina.

<u>Passaggi da riprodurre</u>:

1. Vai a **Store** > **Impostazioni** > **Configurazioni** > **Generale** > **Impostazione valuta** e seleziona una valuta personalizzata. Ad esempio, **Peso messicano**.
1. Vai a **Store** > **Impostazioni** > **Configurazioni** > **Generale** > **Opzioni internazionali** e seleziona **Spagnolo (Messico)**.
1. Vai a **Store** > **Simboli di valuta** e configura il simbolo di valuta in **MX$**.
1. Controlla il simbolo di valuta sul front-end.

<u>Risultati previsti</u>:

Il simbolo di valuta predefinito è &quot;MX$&quot; con valuta impostata come &quot;Peso messicano&quot; e lingua impostata come &quot;Spagnolo (Messico)&quot;.

<u>Risultati effettivi</u>:

Il simbolo di valuta predefinito è &quot;$&quot;.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
