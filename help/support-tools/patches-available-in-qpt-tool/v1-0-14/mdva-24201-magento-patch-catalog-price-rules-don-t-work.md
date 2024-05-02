---
title: "MDVA-24201: le regole del prezzo di catalogo non funzionano"
description: La patch MDVA-24201 risolve il problema in cui le regole attive dei prezzi di catalogo nel database non vengono applicate sul front-end.
exl-id: ae541c40-403a-46e9-a486-2a1e8991f05a
feature: Catalog Management, Categories, Marketing Tools, Orders, Price Rules
role: Admin
source-git-commit: ce81fc35cc5b7477fc5b3cd5f36a4ff65280e6a0
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# MDVA-24201: le regole del prezzo di catalogo non funzionano

La patch MDVA-24201 risolve il problema in cui le regole attive dei prezzi di catalogo nel database non vengono applicate sul front-end.

Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.14. Il problema è stato risolto nella versione 2.3.5 di Adobe Commerce.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud 2.3.3

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.0 - 2.3.4-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Prerequisito</u>:

Installa una nuova istanza di Magento con dati di esempio.

<u>Passaggi da riprodurre</u>:

1. Accedi a **Pannello di amministrazione** > **Marketing** > **Regola prezzo catalogo** > **Aggiungi nuova regola**, effettua le seguenti impostazioni:
   1. Imposta il **Nome regola**.
   1. Imposta **Attivo** = *No.*
   1. Imposta condizioni: **Categoria** = *4*. (Esempio: Bagagli)
   1. Imposta azioni:
      1. Imposta **Applica come**   **percentuale dell&#39;originale**.
      1. Imposta **Importo sconto** = *10*.
      1. Salvare e quindi continuare la modifica.
   1. Fai clic su **Pianifica nuovo aggiornamento**:
      * Imposta il **Nome regola**.
      * Imposta **Attivo** = *Sì*.
      * Salva.
1. Vai al backend ed esegui:

   `php    bin/magento cron:run`

<u>Risultati previsti</u>:

I prezzi dei prodotti della categoria 4 &quot;Borse&quot; dovrebbero essere ridotti del 10% rispetto al prezzo iniziale, come previsto dalla regola del prezzo di catalogo.

<u>Risultati effettivi</u>:

Non si verificano modifiche del prezzo anche se la regola del prezzo di catalogo è attiva.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sezione.
