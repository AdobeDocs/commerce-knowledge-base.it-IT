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

La patch di MDVA-28861 risolve il problema relativo all&#39;errore restituito dagli utenti durante la modifica dell&#39;e-mail di amministrazione. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.5. L&#39;ID della patch è MDVA-28861.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure da 2.3.0 a 2.4.1 (inclusa 2.3.5-p1) con estensione B2B

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Dopo aver modificato l&#39;indirizzo e-mail dell&#39;**Amministratore società**, viene restituito un errore e l&#39;elenco degli **Utenti società** non viene visualizzato.

<u>Passaggi da riprodurre</u>:

1. Abilitare la funzionalità aziendale (ulteriori informazioni su questo argomento in [Installare le funzionalità B2B: abilitare le funzionalità B2B in Commerce Admin](https://devdocs.magento.com/extensions/b2b/#enable-b2b-features-in-magento-admin) nella documentazione per gli sviluppatori e creare una nuova società con due utenti, un amministratore e due utenti, il tutto con indirizzi e-mail).
1. Vai a **Amministratore Commerce** > **Clienti** > **Aziende** e apri il tuo account aziendale.
1. Apri la scheda **Amministratore società** e cambia amministratore con il primo utente, cambiando anche l&#39;e-mail di **Amministratore società** con l&#39;e-mail del primo utente.
1. Vai al front-end di Adobe Commerce e accedi come primo utente.
1. Vai alla sezione **Utenti società**.

<u>Risultati previsti</u>:

L&#39;elenco **Utenti società** deve essere visualizzato come previsto.

<u>Risultati effettivi</u>:

L&#39;elenco **Utenti società** non viene visualizzato e viene visualizzato un errore simile al seguente:

```bash
No such entity with id = 2
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [Guida all&#39;aggiornamento software > Applicazione di patch](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) nella documentazione per gli sviluppatori.
* Adobe Commerce sull&#39;infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://devdocs.magento.com/cloud/project/project-patch.html) nella documentazione per gli sviluppatori.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) nella knowledge base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Quality Patches ](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) nella nostra knowledge base di supporto.

Per informazioni sulle altre patch disponibili in QPT, consulta [Patch disponibili in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) nella documentazione per gli sviluppatori.

Per ulteriori informazioni sulle funzionalità aziendali B2B, consulta questi articoli nella documentazione per gli sviluppatori:

* [Guida per gli sviluppatori B2B](https://devdocs.magento.com/guides/v2.4/b2b/bk-b2b.html)
* [Gestione ruoli società](https://devdocs.magento.com/guides/v2.4/b2b/roles.html)
* [Riferimento dei percorsi di configurazione dell&#39;estensione Adobe Commerce Enterprise B2B](https://devdocs.magento.com/guides/v2.4/config-guide/prod/config-reference-b2b.html)
