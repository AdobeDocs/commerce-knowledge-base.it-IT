---
title: "MDVA-26639: nessun elemento ordine nel modello e-mail di conferma nuovo ordine"
description: La patch di MDVA-26639 risolve il problema quando viene creato un nuovo ordine, gli elementi dell'ordine mancano in un modello di e-mail di conferma.
exl-id: 5d9716ab-6e57-47b0-8b38-ca98a98101e8
feature: Communications, Marketing Tools, Native Luma Frontend Development, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# MDVA-26639: nessun elemento ordine nel modello e-mail di conferma nuovo ordine

La patch di MDVA-26639 risolve il problema quando viene creato un nuovo ordine, gli elementi dell&#39;ordine mancano in un modello di e-mail di conferma.

Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.20. L&#39;ID della patch è MDVA-26639. Il problema è stato risolto in Adobe Commerce 2.3.6.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:** Adobe Commerce sull’infrastruttura cloud 2.3.3-p1

**Compatibile con le versioni di Adobe Commerce:** Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.3.3-p1-2.3.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

<u>Passaggi da riprodurre</u>:

1. Vai a **Negozi** > **Configurazione** > **Vendite** > **E-mail vendite** > **Conferma nuovo ordine** e seleziona **Modello: nuovo ordine di ritiro**.
1. Vai a **Vendite** > **Ordine: selezionare un ordine**, quindi vai a **Informazioni**, e seleziona **Invia messaggio**.

<u>Risultati previsti</u>:

Gli articoli dell’ordine vengono visualizzati come previsto nell’e-mail dell’ordine del cliente.

<u>Risultati effettivi</u>:

Gli articoli dell&#39;ordine non sono presenti nell&#39;e-mail dell&#39;ordine cliente. Lo stesso vale se si crea un nuovo modello e si seleziona un modello Nuovo ordine o Nuovo ordine (Luma).

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento al [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-) sezione.
