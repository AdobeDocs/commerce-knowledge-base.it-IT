---
title: '''MDVA-42269: l''utente amministratore non può accedere ad Admin a causa dell''errore "TypeError"'''
description: La patch MDVA-42269 risolve il problema che impediva agli utenti Admin di accedere ad Admin a causa di TypeError. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11.  L'ID della patch è MDVA-42269.  L’ultimo aggiornamento della patch è disponibile in QPT 1.1.15. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
exl-id: 66d744a2-054e-493c-a060-9ed78447e35b
feature: Admin Workspace
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# MDVA-42269: l&#39;utente Admin non può accedere ad Admin a causa dell&#39;errore &quot;TypeError&quot;

La patch MDVA-42269 risolve il problema che impediva agli utenti Admin di accedere ad Admin a causa di TypeError. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.11.  L&#39;ID della patch è MDVA-42269.  L’ultimo aggiornamento della patch è disponibile in QPT 1.1.15. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1, 2.3.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1 - 2.4.3-p2, 2.3.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti Admin non possono accedere ad Admin a causa del seguente errore: *TypeError: strtotime() prevede che il parametro 1 sia una stringa, dato null.*

<u>Passaggi da riprodurre</u>:

Accedi all’amministratore di Commerce.

<u>Risultati previsti</u>:

L’utente amministratore può effettuare l’accesso con il nome utente e la password corretti.

<u>Risultati effettivi</u>:

L’utente amministratore non può effettuare l’accesso. Viene registrato il seguente errore: *TypeError: strtotime() prevede che il parametro 1 sia una stringa, dato null.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
