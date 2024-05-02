---
title: "Patch MDVA-33482: calcolo errato delle imposte nella nota di accredito"
description: La patch di MDVA-33482 risolve il problema dell'errato calcolo dell'imposta nelle note di credito.
exl-id: 80740e6f-2b6c-4770-9a1a-58ba68a1b28f
feature: Orders, Returns, Taxes
role: Admin
source-git-commit: 0ffa6d63f7046048f7e8f0e9fab1ee1869c98e93
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Patch MDVA-33482: calcolo errato delle imposte nella nota di accredito

La patch MDVA-33482 risolve il problema relativo al calcolo errato dell&#39;imposta nelle note di accredito quando non viene applicata alcuna commissione di adeguamento o rimborso di adeguamento.

Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching.html#mqp) 1.0.15. Il problema è pianificato per la risoluzione in Adobe Commerce versione 2.4.3.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud 2.4.0

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.3.5 - 2.4.2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Configura **Imposte**.
1. Crea un ordine utilizzando due prodotti nel backend utilizzando qualsiasi metodo di pagamento online (Esempio: [!DNL PayPal Payment Pro]). Assicurati che le imposte vengano applicate a tutti i prodotti.
1. Creare due fatture per l&#39;ordine.
1. Creare una nota di accredito a fronte di una delle fatture. Si noti che la soluzione non è applicabile se si prevede di applicare una commissione di adeguamento o un rimborso di adeguamento.
1. Controllare i totali delle note di accredito.

<u>Risultati previsti</u>:

Nella nota di accredito è presente solo un importo di imposta parzialmente fatturato, come previsto.

<u>Risultati effettivi</u>:

Nella nota di accredito viene visualizzato l&#39;intero importo dell&#39;imposta.

## Applicare la patch

Per applicare singole patch, utilizzare i seguenti collegamenti, a seconda del prodotto Adobe Commerce:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili nello strumento QPT, consultare [Patch disponibili nello strumento QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-QPT-tool-) sezione.
