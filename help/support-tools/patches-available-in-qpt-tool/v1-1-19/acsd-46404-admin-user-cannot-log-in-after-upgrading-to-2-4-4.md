---
title: "ACSD-46404: l’utente amministratore non può accedere dopo l’aggiornamento alla versione 2.4.4"
description: La patch ACSD-46404 risolve il problema che impediva a un utente amministratore di accedere dopo l’aggiornamento alla versione 2.4.4. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19. L’ID della patch è ACSD-46404. Il problema è stato risolto in Adobe Commerce 2.4.5.
exl-id: 0aebc879-1128-4be2-a6a8-90d5812c7602
feature: Admin Workspace
role: Admin
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '398'
ht-degree: 0%

---

# ACSD-46404: l’utente amministratore non può accedere dopo l’aggiornamento alla versione 2.4.4

La patch ACSD-46404 risolve il problema che impediva a un utente amministratore di accedere dopo l’aggiornamento alla versione 2.4.4. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.1.19. L’ID della patch è ACSD-46404. Il problema è stato risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’utente amministratore non può accedere dopo l’aggiornamento alla versione 2.4.4.

<u>Passaggi da riprodurre</u>:

1. Accedi al pannello di amministrazione
1. Passa a Store > **Impostazioni** > **Configurazione** > **Avanzate** > **Sistema** > **Sicurezza**.
1. Imposta la dimensione massima della sessione in Admin su **0** e salvalo.

<u>Risultati previsti</u>:

L’utente amministratore è in grado di accedere correttamente.

<u>Risultati effettivi</u>:

L’utente amministratore si disconnette e non è in grado di accedere.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.
