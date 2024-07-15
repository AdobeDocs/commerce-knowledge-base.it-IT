---
title: "MDVA-28191: nessun metodo di pagamento per un sito Web in Amministrazione - Crea nuovo ordine"
description: La patch MDVA-28191 risolve il problema relativo al mancato caricamento di un metodo di pagamento nell'Admin **Create New Order** per un sito Web, anche se i metodi di pagamento potrebbero essere visualizzati per altri siti Web.  Questa patch è disponibile quando è installato lo strumento [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versione 1.0.5.
exl-id: 42169743-4f09-4f0a-aadd-931cccc9b467
feature: Admin Workspace, Orders, Payments
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28191: nessun metodo di pagamento per un sito Web in Amministrazione - Crea nuovo ordine

La patch di MDVA-28191 risolve il problema relativo al mancato caricamento di un metodo di pagamento nell&#39;Admin **Create New Order** per un sito Web, anche se i metodi di pagamento potrebbero essere visualizzati per altri siti Web.  Questa patch è disponibile quando è installato lo strumento [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) versione 1.0.5.

## Prodotti e versioni interessati

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud da 2.3.3 a 2.4.1 (inclusa 2.3.5-p1).

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Durante la creazione di un ordine dal backend Adobe Commerce crea due virgolette, una è inattiva e l’altra è attiva. Ma la sessione contiene l&#39;ID preventivo inattivo.

<u>Passaggi da riprodurre</u>

1. Vai a **Pannello di amministrazione** > **Vendite** > **Ordini** e fai clic sul pulsante **Crea nuovo ordine**.
1. Scegliere il cliente per il quale si desidera creare l&#39;ordine.
1. Se lo store dispone di più visualizzazioni, scegliere la visualizzazione dello store in cui inserire l&#39;ordine nella pagina **Crea nuovo ordine** per l&#39;utente selezionato.
1. Aggiungere prodotti dalla sezione **Attività del cliente** o dal catalogo facendo clic su **Aggiungi prodotti**. Scorri verso il basso la pagina per completare le sezioni seguenti in base alle esigenze dell’ordine:
   * Applica codici coupon
   * Metodo di pagamento
   * Metodo di spedizione
   * Commenti ordine

<u>Risultato previsto:</u>

I metodi di pagamento devono essere caricati nell&#39;amministratore per tutti i siti Web.

<u>Risultato effettivo:</u>

Nessun metodo di pagamento disponibile (non viene visualizzato il messaggio &quot;*Nessuna informazione di pagamento richiesta*&quot;) per questo sito Web, anche se i metodi di pagamento possono essere visualizzati durante la verifica degli ordini per altri siti Web.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
