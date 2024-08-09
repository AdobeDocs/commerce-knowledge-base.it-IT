---
title: Knowledge Base di supporto Adobe Commerce
description: Tutto ciò che è necessario sapere per risolvere i problemi e gestire il Commerce Store.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: cfbe281941fbdc3e6fe7ee36385dc6732b46da26
workflow-type: tm+mt
source-wordcount: '1395'
ht-degree: 0%

---

# Knowledge Base di supporto Adobe Commerce

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

>[!NOTE]
>
>Per archiviare un nuovo ticket, accedi al [Centro assistenza Adobe Commerce](https://support.magento.com/) e segui i passaggi descritti in [Invia un ticket di supporto](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket).
>
>Se non trovi l&#39;opzione per inviare un ticket, consulta la sezione *[Invia un collegamento per il ticket non visualizzato](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#no-submit-link)* nella [Guida utente del Centro assistenza](/help/help-center-guide/help-center/magento-help-center-user-guide.md).

## Novità

<table style="width:100%">
  <tr>
    <th style="width:70%">Descrizione</th>
    <th style="width:15%">Tipo</th>
    <th style="width:15%">Data</th>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/the-magento-cloud-cli-doesnt-show-an-active-environment">L'interfaccia della riga di comando <code>Magento-cloud</code> non mostra un ambiente attivo:</a> Sono presenti diversi ambienti attivi e si sta tentando di interagire con un ambiente eseguendo un comando CLI (strumento da riga di comando) Magento-cloud. Tuttavia, la richiesta di scegliere l’ambiente desiderato non elenca questo ambiente.
    </td>
    <td>Nuovo articolo</td>
    <td>30 luglio 2024</td>
  </tr>

<td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-obtain-and-apply-security-patches">Come ottenere e applicare una patch di sicurezza:</a> In questo articolo vengono fornite istruzioni su come ottenere e applicare una patch di sicurezza rilasciata, ma le istruzioni non sono disponibili.  
    </td>
    <td>Nuovo articolo</td>
    <td>30 luglio 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/elasticsearch/falling-back-to-elasticsearch7-when-search-engine-set-to-opensearch">Ripristino di Elasticsearch7 quando il motore di ricerca è impostato su Opensearch:</a> Questo articolo fornisce una soluzione al problema quando si verifica un errore di ripristino di Elasticsearch7 quando il motore di ricerca è impostato su OpenSearch in Adobe Commerce. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-failed-there-are-no-commands-defined-in-the-cache-namespace-error">Distribuzione non riuscita: nessun comando definito nell'errore dello spazio dei nomi 'cache':</a> Questo articolo fornisce una soluzione al problema quando la distribuzione non riesce e uno degli errori visualizzati nel registro è <em>Nessun comando definito nello spazio dei nomi "cache"</em>. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-55566-mergecart-mutation-fails-with-an-internal-server-error-in-graphql-response">ACSD-55566: la mutazione <code>mergeCart</code> non riesce con un errore interno del server nella risposta di GraphQL:</a> La patch ACSD-55566 risolve il problema se la mutazione <code>mergeCart</code> non riesce con un errore interno del server nella risposta di GraphQL. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48.  
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56546-configurable-and-bundle-products-display-as-out-of-stock-on-the-storefront">ACSD-56546: i prodotti configurabili e del bundle vengono visualizzati come esauriti nella vetrina:</a> La patch ACSD-56546 risolve il problema relativo alla visualizzazione esaurita dei prodotti configurabili e del bundle nella vetrina. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48.  
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57565-the-order-dashboard-displays-incorrect-order-information">ACSD-57565: nel dashboard degli ordini vengono visualizzate informazioni di ordine non corrette:</a> La patch ACSD-57565 risolve il problema relativo alla visualizzazione di informazioni di ordine non corrette nel dashboard degli ordini fino all'aggiornamento del periodo di tempo. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57394-incorrect-product-sorting-by-multiple-sort-fields-in-graphql">ACSD-57394: ordinamento dei prodotti non corretto in base a più attributi di ordinamento in GraphQL:</a> La patch ACSD-57394 risolve il problema relativo all'ordinamento errato dei prodotti quando si utilizzano più attributi di ordinamento in GraphQL. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57854-graphql-response-contains-disabled-categories-that-should-not-be-listed-in-the-category-aggregations">ACSD-57854: la risposta di GraphQL contiene categorie disabilitate che non devono essere elencate nelle aggregazioni di categorie:</a> La patch di ACSD-57854 risolve il problema relativo al fatto che la risposta di GraphQL contiene categorie disabilitate che non dovrebbero essere elencate nelle aggregazioni di categorie. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-57074-yes-no-custom-attribute-does-not-work-with-indexing">ACSD-57074: l'attributo personalizzato Sì/No con prefisso <code>price_*</code> nell'attributo <code>attribute_code</code> non funziona con l'indicizzazione:</a> La patch ACSD-57074 risolve il problema se l'attributo personalizzato <em>Sì/No</em> con prefisso <code>price_*</code> nell'attributo <code>attribute_code</code> non funziona con l'indicizzazione. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-55241-used-and-times-used-attributes-display-incorrect-values-for-generated-coupons">ACSD-55241: gli attributi Used e Times Used visualizzano valori non corretti per i coupon generati:</a> La patch ACSD-55241 risolve il problema relativo alla visualizzazione di valori non corretti per i coupon generati da parte degli attributi Used e Times Used. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-56760-admin-user-is-restricted-to-a-specific-website-and-is-unable-to-sort-or-add-new-products">ACSD-56760: l'utente amministratore è limitato a un sito Web specifico e non è in grado di ordinare o aggiungere nuovi prodotti:</a> La patch ACSD-56760 risolve il problema che impedisce all'utente amministratore limitato a un sito Web specifico di ordinare o aggiungere nuovi prodotti all'interno di una categoria nel caso in cui l'archivio Web disponga di una categoria radice propria. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56635-imported-customers-are-duplicated-with-the-same-email-address">ACSD-56635: i clienti importati vengono duplicati con lo stesso indirizzo e-mail quando la condivisione account è impostata su Globale:</a> La patch ACSD-56635 risolve il problema relativo alla duplicazione del cliente importato con lo stesso indirizzo e-mail quando l'importazione viene utilizzata con la condivisione account impostata su Globale. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57315-new-transaction-created-in-paypal-payflow-pro-each-time-the-fetch-button-is-clicked">ACSD-57315: viene creata una nuova transazione in PayPal Payflow Pro ogni volta che si fa clic sul pulsante di recupero:</a> La patch ACSD-57315 risolve il problema relativo alla creazione di una nuova transazione in PayPal Payflow Pro ogni volta che si fa clic sul pulsante di recupero nella schermata Visualizza transazione in Admin. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-56741-database-setup-upgrade-error-with-custom-mysql-trigger">ACSD-56741: risoluzione dei problemi relativi agli errori di installazione del database con trigger MySQL personalizzati:</a> La patch ACSD-56741 risolve il problema relativo alla visualizzazione di un messaggio di errore <em>Il tentativo di accedere all'offset dell'array su un valore di tipo null</em> è avvenuto durante <code>setup:upgrade</code> a causa di un trigger MySQL personalizzato nel database non correlato all'indicizzazione e a MView. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-58008-editing-the-end-date-as-empty-causes-the-schedule-update-to-disappear">ACSD-58008: la modifica della data di fine come vuota fa scomparire l'aggiornamento della pianificazione:</a> La patch ACSD-58008 risolve il problema se la modifica della data di fine come vuota fa scomparire l'aggiornamento della pianificazione. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-48/acsd-57337-admin-user-with-access-restrictions-can-see-companies">ACSD-57337: l'utente amministratore con restrizioni di accesso può visualizzare tutte le società nella griglia Società:</a> La patch ACSD-57337 risolve il problema che un utente amministratore con restrizioni di accesso a siti Web specifici può visualizzare le società da tutti i siti Web nella griglia Società. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.48. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/deployment/deployment-failed-with-correct-access-key-env-composer-auth">La distribuzione non riesce con le chiavi di accesso corrette in <code>env:COMPOSER_AUTH</code> o <code>auth.json</code>:</a> Questo articolo fornisce una soluzione al problema quando la distribuzione non riesce con un errore come quello nel registro di distribuzione. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-bypass-waf-for-graphql-requests">Ignorare WAF per le richieste GraphQL:</a> In questo articolo viene illustrato come ignorare le richieste WAF per GraphQL quando Fastly WAF blocca le richieste GraphQL. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/email-stating-that-export-storage-is-almost-full">Messaggio di posta elettronica che indica che l'archivio di esportazione è quasi pieno:</a> In questo articolo viene fornita una soluzione per il problema in cui si riceve un messaggio di posta elettronica che indica che l'archivio di esportazione è quasi pieno. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/upgrade-mariadb-10-4-to-10-5-for-magento-commerce-cloud">Aggiornamento di MariaDB da 10.4 a 10.5 per Adobe Commerce sul cloud:</a> Questo articolo spiega come effettuare l'aggiornamento da MariaDB 10.4 a 10.5 per continuare a utilizzare Adobe Commerce sull'infrastruttura cloud. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/revised-patches-for-google-maps-access-loss-on-all-adobe-commerce-versions">Patch riviste per la perdita dell'accesso a Google Maps su tutte le versioni di Adobe Commerce:</a> Questo articolo fornisce una correzione per gli esercenti di Adobe Commerce che non sono compatibili con le versioni recenti di Google Maps della versione 3.54+. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/security-update-available-for-adobe-commerce-apsb24-40-revised-to-include-isolated-patch-for-cve-2024-34102">Aggiornamento di sicurezza disponibile per Adobe Commerce - APSB24-40:</a> Questo articolo condivide un aggiornamento relativo a CVE-2024-34102. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/poor-performance-in-integration-environments">Prestazioni insoddisfacenti negli ambienti di integrazione:</a> Questo articolo fornisce una soluzione al problema relativo alle prestazioni insoddisfacenti degli ambienti di integrazione Pro e degli ambienti di staging Starter. 
    </td>
    <td>Nuovo articolo </td>
    <td>30 luglio 2024</td>
 </tr>
</table>

## Articoli più richiesti

* [Passaggio a OpenSearch per Adobe Commerce su Cloud 2.4.4](/help/announcements/adobe-commerce-announcements/switching-to-opensearch-for-adobe-commerce-on-cloud-2-4-4.md)
* [Vulnerabilità di Apache log4j2 in Adobe Commerce](/help/announcements/adobe-commerce-announcements/apache-log4j2-adobe-commerce.md)
* [Aggiornamenti di sicurezza disponibili per Adobe Commerce APSB22-12](/help/troubleshooting/known-issues-patches-attached/0-day-vulnerability-patch.md)
* [Identificare e misurare le interruzioni per l’infrastruttura cloud di Adobe Commerce](/help/how-to/general/how-to-identify-outages.md)
* [Visualizzazione del livello vCPU dell’ambiente nel cluster in Adobe Commerce](/help/how-to/general/check-vcpu-using-observation-for-adobe-commerce.md)
* [Adobe Commerce sull’infrastruttura cloud: calcolo dell’allocazione della CPU](/help/how-to/general/magento-commerce-cloud-cpu-allocation-calculation.md)
* [Adobe Commerce su infrastruttura cloud: verifica la configurazione della CPU dell’host](/help/how-to/general/magento-commerce-cloud-check-hosts-cpu-configuration.md)
