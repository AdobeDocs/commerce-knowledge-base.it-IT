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

La patch MDVA-28191 risolve il problema relativo al mancato caricamento di un metodo di pagamento nell&#39;Admin **Crea nuovo ordine** per un sito web, anche se i metodi di pagamento possono essere visualizzati per altri siti web.  Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) è installata la versione dello strumento 1.0.5.

## Prodotti e versioni interessati

Adobe Commerce on-premise e Adobe Commerce sull’infrastruttura cloud da 2.3.3 a 2.4.1 (inclusa 2.3.5-p1).

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Durante la creazione di un ordine dal backend Adobe Commerce crea due virgolette, una è inattiva e l’altra è attiva. Ma la sessione contiene l&#39;ID preventivo inattivo.

<u>Passaggi da riprodurre</u>

1. Vai a **Pannello di amministrazione** > **Vendite** > **Ordini** e fai clic su **Crea nuovo ordine** pulsante.
1. Scegliere il cliente per il quale si desidera creare l&#39;ordine.
1. Se il tuo Negozio ha più visualizzazioni, scegli la visualizzazione del Negozio in cui deve essere effettuato l’ordine, sulla **Crea nuovo ordine** per l&#39;utente selezionato.
1. Aggiungi prodotti da **Attività del cliente** o dal catalogo facendo clic su **Aggiungi prodotti**. Scorri verso il basso la pagina per completare le sezioni seguenti in base alle esigenze dell’ordine:
   * Applica codici coupon
   * Metodo di pagamento
   * Metodo di spedizione
   * Commenti ordine

<u>Risultato previsto:</u>

I metodi di pagamento devono essere caricati nell&#39;amministratore per tutti i siti Web.

<u>Risultato effettivo:</u>

Nessun metodo di pagamento disponibile (né il messaggio è &quot;*Nessuna informazione di pagamento richiesta*&quot;) per questo sito web, anche se i metodi di pagamento possono mostrare quando si verificano gli ordini per altri siti web.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
