---
title: "MDVA-34474: l’aggiornamento dell’elenco delle richieste di acquisto API restituisce un errore"
description: La patch MDVA-34474 risolve il problema che causa l'errore di aggiunta di un prodotto all'elenco delle richieste di acquisto tramite API. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L'ID della patch è MDVA-34474. Il problema è stato risolto in Adobe Commerce 2.4.3.
exl-id: dc39c4f7-417c-45ea-914c-32f7305527da
feature: REST, B2B
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 0%

---

# MDVA-34474: l&#39;aggiornamento dell&#39;elenco delle richieste API genera un errore

La patch MDVA-34474 risolve il problema che causa l&#39;errore di aggiunta di un prodotto all&#39;elenco delle richieste di acquisto tramite API. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.19. L&#39;ID della patch è MDVA-34474. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce sull’infrastruttura cloud 2.4.0

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud 2.3.0 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’aggiunta di un prodotto all’elenco delle richieste di acquisto tramite API genera un errore.

<u>Passaggi da riprodurre</u>:

1. Attiva elenco richieste in Amministratore (**Negozi** > **Configurazione** > **Generale** > **Caratteristiche B2B** > **Abilita elenco richieste di acquisto** = *Sì*).
1. Crea un cliente.
1. Crea un nuovo elenco di richieste per questa chiamata di invio cliente ```json    POST rest/all/V1/requisition_lists``` con il payload json allegato.

<u>Risultati previsti</u>:

Nessun errore e l’elenco viene creato.

<u>Risultati effettivi</u>:

Errore 400.

```json
{"message":"Could not save Requisition List"}
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
