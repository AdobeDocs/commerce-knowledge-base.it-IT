---
title: "MDVA-28661: problema con la gestione degli utenti aziendali durante la modifica delle e-mail di amministrazione"
description: La patch di MDVA-28861 risolve il problema relativo all'errore restituito dagli utenti durante la modifica dell'e-mail di amministrazione. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. L'ID della patch è MDVA-28861.
exl-id: 2d6691e5-baaf-4cef-ae7e-2b6ccc7f2cd3
feature: Admin Workspace, Communications, Companies
role: Admin
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# MDVA-28661: problema relativo alla gestione degli utenti aziendali durante la modifica dell&#39;e-mail di amministrazione

La patch di MDVA-28861 risolve il problema relativo all&#39;errore restituito dagli utenti durante la modifica dell&#39;e-mail di amministrazione. Questa patch è disponibile quando [Strumento Patch di qualità (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. L&#39;ID della patch è MDVA-28861.

## Prodotti e versioni interessati

**La patch viene creata per la versione Adobe Commerce:**

Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure da 2.3.0 a 2.4.1 (inclusa 2.3.5-p1) con estensione B2B

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiorna la `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]: pagina Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Dopo aver modificato **Amministratore società** e-mail, viene restituito un errore e il **Utenti società** non viene visualizzato.

<u>Passaggi da riprodurre</u>:

1. Abilitare la funzionalità aziendale (ulteriori informazioni in [Installare B2B: abilitare le funzioni B2B in Commerce Admin](https://devdocs.magento.com/extensions/b2b/#enable-b2b-features-in-magento-admin) nella documentazione per gli sviluppatori e crea una nuova azienda con due utenti (un amministratore e due utenti), il tutto con indirizzi e-mail.
1. Vai a **Amministratore Commerce** > **Clienti** > **Aziende** e apri l&#39;account aziendale.
1. Apri **Amministratore società** e cambia amministratore con il primo utente, anche cambiando il **Amministratore società** invia un messaggio e-mail al primo utente.
1. Vai al front-end di Adobe Commerce e accedi come primo utente.
1. Vai a **Utenti società** sezione.

<u>Risultati previsti</u>:

Il **Utenti società** L’elenco deve essere visualizzato come previsto.

<u>Risultati effettivi</u>:

Il **Utenti società** L&#39;elenco non viene visualizzato e viene visualizzato un errore simile al seguente:

```bash
No such entity with id = 2
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise [Guida all&#39;aggiornamento del software > Applicazione delle patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull’infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [Rilasciato lo strumento Quality Patches: un nuovo strumento per rendere autonome le patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella nostra knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.

Per ulteriori informazioni sulle funzionalità aziendali B2B, consulta questi articoli nella documentazione per gli sviluppatori:

* [Guida per gli sviluppatori B2B](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [Gestire i ruoli aziendali](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Riferimento ai percorsi di configurazione dell’estensione Adobe Commerce Enterprise B2B](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
