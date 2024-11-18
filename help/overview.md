---
title: Knowledge Base di supporto Adobe Commerce
description: Tutto ciò che è necessario sapere per risolvere i problemi e gestire il Commerce Store.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 52d07e5a5bb7be492f6799d0e5ad9fd49c3a61ae
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# Knowledge Base di supporto Adobe Commerce

>[!NOTE]
>
>La Knowledge Base di supporto di Adobe Commerce verrà presto ristrutturata e i suoi contenuti verranno spostati in altre posizioni all’interno di Adobe Experience League. Nel frattempo, continueremo a mantenere e aggiornare il contenuto di questa guida.

![Home page della Knowledge Base](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

Le informazioni contenute in questa Knowledge Base sono complementari a [Adobe Commerce Developer Documentation](https://developer.adobe.com/commerce/docs), [Adobe Commerce Merchant Guide](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html) e ad altre pubblicazioni Adobe Commerce. Descrive la risoluzione dei problemi e le best practice, gli annunci host, le risposte alle domande frequenti ed evidenzia scenari specifici che non sono stati menzionati (per qualsiasi motivo) nella documentazione ufficiale.

## Cosa contiene la Knowledge Base?

| CATEGORIA | DESCRIZIONE |
| --- | --- |
| [Strumenti di supporto](/help/support-tools/overview.md) | Migliora la tua esperienza nei negozi di e-commerce con i diversi strumenti di supporto forniti da Adobe Commerce. Forniamo best practice personalizzate, strumenti di diagnostica e monitoraggio e le informazioni più rilevanti sul tuo sito. |
| [Annunci](/help/announcements/overview.md) | Ottieni aggiornamenti importanti dai team di Adobe Commerce. |
| [Risoluzione dei problemi](/help/troubleshooting/overview.md) | Soluzioni e patch self-service dal team di supporto Adobe Commerce. |
| [Guida utente del Centro assistenza](/help/help-center-guide/help-center/magento-help-center-user-guide.md) | Scopri come gestire i ticket di supporto, concedere l’accesso condiviso e sfogliare in modo efficace la Knowledge Base. |
| [Istruzioni](/help/how-to/overview.md) | Ricevi istruzioni dettagliate dal team di supporto Adobe Commerce. |
| [Domande frequenti](/help/faq/overview.md) | Trova le domande frequenti su politiche, strategie e specifiche di Adobe Commerce relative alle funzioni di Adobe Commerce. |

## Novità

<table style="width:100%">
  <tr>
    <th style="width:70%">Descrizione</th>
    <th style="width:15%">Tipo</th>
    <th style="width:15%">Data</th>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25234">Trasferimento della licenza a causa della ristrutturazione:</a> Questo articolo ti aiuterà a cambiare facilmente la proprietà del tuo account Adobe Commerce, inclusi tutti i passaggi essenziali necessari per mantenere i servizi in esecuzione senza intoppi.
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25289">Aggiornamenti di sicurezza disponibili per Adobe Commerce (APSB24-90):</a> Il 12 novembre 2024, Adobe ha rilasciato un aggiornamento di sicurezza per Adobe Commerce (su cloud e on-premise) e le funzionalità di Magento Open Source basate su Commerce Services e distribuite come SaaS (Software as a Service). Questo aggiornamento risolve una vulnerabilità <a href="https://helpx.adobe.com/security/severity-ratings.html">critica</a>. 
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25231">Il proprietario dell'account MageID non è in grado di accedere e inviare un ticket di supporto:</a> Questo articolo risolve il problema di Adobe Commerce, ovvero l'impossibilità di accedere all'account (MageID) all'indirizzo account.magento.com per inviare un ticket di supporto.
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25135">L'estensione OOTB Braintree per Adobe Commerce non supporta i campi Visa 3DS più recenti:</a> Questo articolo spiega come rispettare le nuove normative Visa, in quanto l'estensione Adobe Commerce Braintree preconfigurata non supporta i campi Visa 3DS più recenti.
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-61528-retrieving-roles-using-graphql-returns-no-results">ACSD-61528: il recupero dei ruoli tramite GraphQL non restituisce alcun risultato:</a> La patch ACSD-61528 risolve il problema per cui il recupero dei ruoli dall'amministratore della società tramite GraphQL restituisce sempre un risultato null. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.53.
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-48318-environment-emulation-nesting-error-in-system-log">ACSD-48318: errore di nidificazione emulazione ambiente in system.log:</a> La patch ACSD-48318 risolve il problema relativo a un messaggio di errore <em>main.ERROR:La nidificazione emulazione ambiente non è consentita</em> viene visualizzata in <code>system.log</code> ogni volta che viene inviata un'e-mail di fattura. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.53.
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59366-delete-teams-with-deactivated-users-not-visible-in-the-team-list">ACSD-59366: Eliminare i team con utenti disattivati non visibili nell'elenco dei team:</a> La patch ACSD-59366 risolve il problema relativo all'errore che si verifica quando si tenta di eliminare un team contenente utenti disattivati non visibili nell'elenco dei team. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60234-paypal-shows-an-incorrect-amount-when-discount-is-applied">ACSD-60234: PayPal mostra un importo errato quando viene applicato lo sconto:</a> La patch ACSD-60234 corregge il problema in cui [!DNL PayPal] mostra un importo errato quando lo sconto viene applicato tramite il metodo di pagamento. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.51.
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60673-cart-price-rule-fix-for-multiple-payment-methods-at-checkout">ACSD-60673: problema della regola prezzo carrello risolto per più metodi di pagamento all'acquisto:</a> La patch ACSD-60673 risolve il problema in cui gli sconti di [!UICONTROL Cart Price Rule] che utilizzano una condizione di metodo di pagamento non sono sempre elencati nei totali. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-60584-access-token-created-for-one-website-is-allowed-to-access-information-on-other-websites">ACSD-60584: il token di accesso creato per un sito Web è autorizzato ad accedere alle informazioni su altri siti Web:</a> La patch ACSD-60584 risolve il problema che consente al token di accesso creato per l'utente su un sito Web di accedere o modificare le informazioni del cliente su altri siti Web. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.53.
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60788-fixes-issue-where-custom-scripts-for-google-tag-manager-are-not-executed-due-to-content-security-policy-errors">ACSD-60788: gli script personalizzati per Google Tag Manager non vengono eseguiti a causa di errori dei criteri di sicurezza del contenuto:</a> La patch ACSD-60788 risolve il problema relativo alla mancata esecuzione degli script personalizzati per [!DNL Google Tag Manager] a causa di errori dei criteri di sicurezza del contenuto. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61366-setup-command-fails-with-error">ACSD-61366: il comando <code>bin/magento setup:static-content:deploy --jobs 4</code> rileva più errori di processo con un errore:</a> La patch ACSD-61366 risolve il problema in cui il comando <code>bin/magento setup:static-content:deploy --jobs 4</code> rileva più errori di processo con <em>Port deve essere configurato all'interno dell'errore del parametro host</em>, nonostante sia stata specificata la porta per la connessione DB. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60816-newrelic-browser-monitoring-scripts-injected-by-apm-agent-are-not-compliant-with-csp">ACSD-60816: gli script di monitoraggio del browser New Relic inseriti dall'agente APM non sono conformi a CSP:</a> La patch ACSD-60816 risolve il problema relativo alla mancata conformità degli script di monitoraggio del browser [!DNL New Relic] inseriti dall'agente APM ai criteri sulla sicurezza dei contenuti (CSP). Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.51.
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59952-error-on-deleting-shared-catalog-with-same-group-id-as-another-shared-catalog">ACSD-59952: errore durante l'eliminazione del catalogo condiviso con lo stesso ID gruppo di un altro catalogo condiviso:</a> La patch ACSD-59952 corregge l'errore generato durante l'eliminazione dei cataloghi condivisi con lo stesso <code>customer_group_id</code> di un altro catalogo condiviso. Inoltre, impedisce agli utenti di creare tali cataloghi condivisi. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-59786-graphql-returns-an-error-when-fetching-a-quote-id-for-an-expired-quote">ACSD-59786: GraphQL restituisce un errore durante il recupero di un <code>quote_id</code> per un preventivo scaduto:</a> La patch ACSD-59786 risolve il problema relativo a una query GraphQL che restituisce un errore durante il recupero di un <code>quote_id</code> per un preventivo scaduto. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.51.
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-59967-javascript-error-prevents-google-maps-from-rendering-correctly">ACSD-59967: l'errore JavaScript impedisce il corretto rendering di Google Maps:</a> La patch ACSD-59967 risolve il problema che impedisce il corretto rendering di [!DNL Google Maps] a causa dell'errore JavaScript. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.51.
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-53/acsd-59930-improves-performance-of-company-flows">ACSD-59930: migliora le prestazioni dei flussi aziendali:</a> La patch ACSD-59930 risolve il problema relativo alla visualizzazione di un errore <em>Timeout</em> nel pannello di amministrazione durante la creazione, il salvataggio o l'eliminazione di una società con un amministratore che dispone di più di 1000 indirizzi nella rubrica. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.53.
    </td>
    <td>Nuovo articolo </td>
    <td>14 novembre 2024</td>
  </tr>
</table>
