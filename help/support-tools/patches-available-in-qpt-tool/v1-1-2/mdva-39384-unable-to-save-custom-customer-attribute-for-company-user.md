---
title: "MDVA-39384: impossibile salvare l'attributo cliente personalizzato per l'utente della società"
description: La patch MDVA-39384 risolve il problema che impedisce il salvataggio dell'attributo cliente personalizzato per un utente aziendale. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. L'ID della patch è MDVA-39384. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: b9864ca6-307b-4649-b764-4512abc503d3
feature: Attributes, B2B, Companies
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# MDVA-39384: impossibile salvare l&#39;attributo cliente personalizzato per l&#39;utente della società

La patch MDVA-39384 risolve il problema che impedisce il salvataggio dell&#39;attributo cliente personalizzato per un utente aziendale. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. L&#39;ID della patch è MDVA-39384. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.1 - 2.3.6, 2.4.1 - 2.4.3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’attributo cliente personalizzato per un utente della società non viene salvato.

<u>Prerequisiti</u>:

I moduli B2B sono installati.

<u>Passaggi da riprodurre</u>:

1. Vai a **Archivi** > Impostazioni > **Configurazione** > **Caratteristiche B2B** e imposta **Abilita società** su Sì.
1. Creare un attributo cliente personalizzato:
   * Valori obbligatori: sì (facoltativo, abilitarlo in modo da visualizzare l’errore di convalida).
   * Mostra su Storefront: sì.
   * Forms da utilizzare in: tutto disponibile nell’elenco.
1. Crea una società e accedi come amministratore della società.
1. Passa alla struttura aziendale nel tuo account.
1. Fai clic sul collegamento **Aggiungi utente**.
1. Compila il modulo con l’attributo personalizzato.
1. Fai clic su **Salva**.

<u>Risultati previsti</u>:

I valori degli attributi personalizzati vengono salvati con il nuovo utente aziendale.

<u>Risultati effettivi</u>:

I valori degli attributi personalizzati NON vengono salvati con il nuovo utente aziendale.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
