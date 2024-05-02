---
title: "MDVA-30815: Elasticsearch di risultati di ricerca vuoti"
description: La patch MDVA-30815 risolve il problema relativo alla visualizzazione di una pagina vuota in Elasticsearch quando vengono modificate le opzioni del limitatore dei risultati della ricerca. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Il problema è stato risolto in Adobe Commerce 2.3.5.
exl-id: dbe41a43-e248-407e-8cf9-319ad5843935
feature: Search, Services
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '456'
ht-degree: 0%

---

# MDVA-30815: Elasticsearch di risultati di ricerca vuoti

La patch MDVA-30815 risolve il problema relativo alla visualizzazione di una pagina vuota in Elasticsearch quando vengono modificate le opzioni del limitatore dei risultati della ricerca. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.7. Il problema è stato risolto in Adobe Commerce 2.3.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.3.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.2 - 2.3.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si utilizza Elasticsearch, se si modificano le opzioni del limitatore dei risultati della ricerca, Adobe Commerce visualizza una pagina vuota.

<u>Prerequisiti</u>:

Elasticsearch è **abilitato**. Vai a **NEGOZI** > **Impostazioni** > **Configurazione** > **Catalogo** > **Ricerca nel catalogo**.

<u>Passaggi da riprodurre</u>:

1. Vai al tuo sito.
1. Cerca un prodotto nel campo di ricerca principale.
1. Dopo aver visualizzato le pagine dei risultati della ricerca, fare clic sull&#39;ultima pagina nelle pagine dei risultati della ricerca.
1. Seleziona **Mostra xx per pagina** dall&#39;opzione limiter. Assicurati che questo sia un limite di numeri di risultati di ricerca diverso da quello attualmente configurato.

<u>Risultati previsti</u>:

Nella pagina viene visualizzato il numero configurato di risultati di prodotto.

<u>Risultati effettivi</u>:

Viene visualizzata una pagina vuota. Questo errore può essere visualizzato anche nel `var/report` : *\`&quot;0&quot;:&quot;SQLSTATE\[42000\]: Errore di sintassi o violazione di accesso: 1064 Si è verificato un errore di sintassi SQL. Controllare il manuale corrispondente alla versione del server MySQL per verificare la sintassi corretta da utilizzare accanto a&#39;\`*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
