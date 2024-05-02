---
title: "MDVA-35847: il modulo utente della società non funziona"
description: La patch MDVA-35847 risolve il problema del mancato funzionamento del modulo Utente dell'azienda e restituisce un errore 500 sul front-end. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L'ID della patch è MDVA-35847. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.
exl-id: 1a3f4a61-0c21-460a-ae48-e792d03ed805
feature: B2B, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# MDVA-35847: il modulo utente della società non funziona

La patch MDVA-35847 risolve il problema del mancato funzionamento del modulo Utente dell&#39;azienda e restituisce un errore 500 sul front-end. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L&#39;ID della patch è MDVA-35847. Il problema è stato risolto nella versione 2.4.3 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.1-2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Prerequisiti</u>:

Adobe Commerce B2B è installato.

<u>Passaggi da riprodurre</u>:

1. Vai a **Negozi** > **Attributi** > **Cliente** e creare un nuovo attributo cliente personalizzato:

   * Tipo di input = *Data*
   * Mostra su Storefront = *Sì*
   * Ordinamento = *0*
   * Forms da usare in = *Tutti i moduli*

1. Crea una nuova società.
1. Accedi come amministratore aziendale al front-end.
1. Vai alle sezioni Utenti dell’azienda.

<u>Risultati previsti</u>:

Il modulo Utente dell’azienda viene caricato normalmente.

<u>Risultati effettivi</u>:

Il modulo Utente società non viene caricato e viene restituito un errore 500.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
