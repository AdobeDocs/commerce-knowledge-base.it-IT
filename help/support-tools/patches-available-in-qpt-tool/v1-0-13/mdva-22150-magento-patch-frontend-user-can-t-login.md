---
title: "Patch MDVA-22150 Adobe Commerce: l'utente front-end non può accedere"
description: La patch MDVA-22150 risolve il problema quando un utente front-end non riesce ad accedere dopo un acquisto interrotto utilizzando un coupon. Ciò si verifica quando un utente front-end utilizza un codice coupon su un prodotto che è stato disabilitato prima di completare l’acquisto. Di conseguenza, l’utente front-end non può più accedere e riceve un errore 503. Un altro effetto di questo problema è che la capacità di gestire i carrelli dei clienti nell’Amministratore smette di funzionare.
exl-id: 8aabe7b2-4b8a-4339-914e-7131006907b3
feature: Communications
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Patch di MDVA-22150 Adobe Commerce: l&#39;utente front-end non può accedere

La patch MDVA-22150 risolve il problema quando un utente front-end non riesce ad accedere dopo un acquisto interrotto utilizzando un coupon. Ciò si verifica quando un utente front-end utilizza un codice coupon su un prodotto che è stato disabilitato prima di completare l’acquisto. Di conseguenza, l’utente front-end non può più accedere e riceve un errore 503. Un altro effetto di questo problema è che la capacità di gestire i carrelli dei clienti nell’Amministratore smette di funzionare.

Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.13. Il problema è stato risolto nella versione 2.3.4 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch è stata creata per Adobe Commerce versione:** Adobe Commerce sull&#39;infrastruttura cloud 2.3.2

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce su infrastruttura cloud e Adobe Commerce 2.3.1 - 2.3.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre:</u>

1. Accedi all’amministratore e crea un prodotto configurabile.
1. Vai a **Regole carrello** e crea un codice coupon con uno sconto.
1. Crea un account cliente nel front-end.
1. Aggiungi il prodotto al carrello, segui il processo di pagamento e immetti il coupon.
1. Dopo aver inserito il coupon, non inviare l&#39;ordine, ma interromperlo e disconnettersi.
1. Torna all’Amministratore e disabilita l’intero prodotto configurabile.

<u>Risultati previsti:</u>

Il prodotto non viene visualizzato nel carrello della vetrina, né con il messaggio di errore appropriato che indica che è stato disattivato, come previsto.

<u>Risultati effettivi:</u>

* Quando tenti di accedere nuovamente al front-end, sarai bloccato in un ciclo infinito (che alla fine mostrerà un’eccezione dopo un lungo periodo di tempo).
* La possibilità di gestire i carrelli acquisti dei clienti in Admin smette di funzionare.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
