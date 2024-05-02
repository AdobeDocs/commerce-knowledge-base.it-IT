---
title: '"MDVA-44887: errore "SyntaxError non rilevato: const di token imprevisto" nel pannello di amministrazione"'
description: '"La patch di MDVA-44887 risolve il problema che impediva all''utente amministratore di fare clic su un''opzione di menu. Nel pannello di amministrazione viene visualizzato l’errore *Uncatch SyntaxError: Unexpected token const* (Sintassi non rilevata: costo token imprevisto*). Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15. L''ID della patch è MDVA-44887. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5".'
exl-id: 66555e66-49d0-4f80-8f77-84ee107ab12e
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# MDVA-44887: errore &quot;SyntaxError non rilevato: const di token imprevisto&quot; nel pannello di amministrazione

La patch di MDVA-44887 risolve il problema che impediva all&#39;utente amministratore di fare clic su un&#39;opzione di menu. Il *Sintassi non rilevataErrore: numero di token imprevisto* nel pannello di amministrazione. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.15. L&#39;ID della patch è MDVA-44887. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente amministratore non può fare clic su nessuna opzione di menu. Il *Sintassi non rilevataErrore: numero di token imprevisto* nel pannello di amministrazione.

<u>Passaggi da riprodurre</u>:

1. Abilita il bundling JS.
1. Minimizza i file JS.
1. Accedi al pannello di amministrazione di Commerce.

<u>Risultati previsti</u>:

L’utente amministratore non può fare clic su nessuna opzione di menu. Errore nella console del browser: *Sintassi non rilevataErrore: numero di token imprevisto*.

<u>Risultati effettivi</u>:

Il pannello Amministratore è accessibile a un utente amministratore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
