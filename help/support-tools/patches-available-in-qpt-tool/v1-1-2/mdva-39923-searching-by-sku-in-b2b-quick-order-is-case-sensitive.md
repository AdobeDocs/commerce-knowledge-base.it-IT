---
title: "MDVA-39923: la funzionalità di ricerca per SKU nella gestione degli ordini rapidi B2B distingue tra maiuscole e minuscole"
description: La patch MDVA-39923 risolve il problema relativo all'errore che si verifica quando i clienti cercano l'ordine in base allo SKU nella funzionalità di ordinamento rapido B2B utilizzando un caso diverso da quello con cui viene salvato il nome. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. L'ID della patch è MDVA-39923. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
exl-id: 52e435df-28a7-49be-a257-7e5801601d57
feature: B2B, Catalog Management, Orders, Search
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '488'
ht-degree: 0%

---

# MDVA-39923: la funzionalità di ricerca per SKU nella gestione degli ordini rapidi B2B distingue tra maiuscole e minuscole

La patch MDVA-39923 risolve il problema relativo all&#39;errore che si verifica quando i clienti cercano l&#39;ordine in base allo SKU nella funzionalità di ordinamento rapido B2B utilizzando un caso diverso da quello con cui viene salvato il nome. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.2. L&#39;ID della patch è MDVA-39923. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.1-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La ricerca per SKU nella funzionalità di ordinamento rapido B2B distingue tra maiuscole e minuscole e mostra un errore quando si utilizza una maiuscola diversa da quella con cui viene salvato lo SKU.

<u>Prerequisiti</u>:

I moduli B2B sono installati.

<u>Passaggi da riprodurre</u>:

1. Accedi all&#39;amministratore e vai a **Archivi** > **Configurazione** > **B2B**.
1. Abilita **Catalogo condiviso** e **Ordine rapido**.
1. Crea un prodotto con SKU maiuscola, ad esempio TEST20-1234
1. Assegna il prodotto creato al **catalogo condiviso**.
1. Accedi come cliente e fai clic su **Ordine rapido**.
1. Immetti lo SKU in minuscolo, ad esempio test20-1234.

<u>Risultati previsti</u>:

Il prodotto deve essere disponibile indipendentemente dal caso utilizzato.

<u>Risultati effettivi</u>:

Ricevuto il seguente messaggio di errore: *1 prodotto/i richiede/richiedono attenzione*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
