---
title: Knowledge Base di supporto Adobe Commerce
description: Tutto ciò che è necessario sapere per risolvere i problemi e gestire il Commerce Store.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 607b835da518536196654734f62d78d095099476
workflow-type: tm+mt
source-wordcount: '1615'
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
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25075">Strumento di analisi della sicurezza restituisce "Impossibile determinare se il server utilizza 2FA":</a> Per risolvere l'errore, verificare se il modulo <code>Magento_TwoFactorAuth</code> è stato disabilitato. Per superare il controllo, in generale, deve essere abilitato.
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60632-address-saved-on-every-order-attempt">ACSD-60632: Indirizzo salvato con ogni tentativo di ordine:</a> La patch ACSD-60632 risolve il problema relativo al salvataggio di un nuovo indirizzo con ogni tentativo di inserimento dell'ordine, indipendentemente dal fatto che l'ordine sia stato creato correttamente o meno. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.51.
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60326-graphql-query-error-customer-return-status">ACSD-60326: la query GraphQL sullo stato delle restituzioni cliente restituisce un errore:</a> La patch ACSD-60326 risolve il problema relativo a un errore nella query GraphQL per lo stato delle restituzioni cliente. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.51.
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59925-sorting-items-in-media-gallery">ACSD-59925: Ordinamento degli elementi nella Raccolta multimediale in base alla posizione in GraphQL:</a> La patch ACSD-59925 risolve il problema relativo agli elementi nella Raccolta multimediale che non sono ordinati in base alla posizione, causando un ordine di visualizzazione errato. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-61322-products-not-assigned-to-shared-catalogue">ACSD-61322: i prodotti non assegnati al catalogo condiviso sono inclusi in XML Sitemap:</a> La patch ACSD-61322 risolve il problema per cui prodotti/categorie non assegnati al catalogo condiviso per il gruppo predefinito (Generale) sono ancora inclusi in XML Sitemap. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-60590-optimized-bestseller-report-generation">ACSD-60590: miglioramento delle prestazioni della generazione di report giornalieri aggregati Bestsellers:</a> La patch ACSD-60590 risolve il problema relativo alla generazione di report giornalieri aggregati Bestsellers richiede molto tempo per un volume elevato di ordini effettuati. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-52/acsd-59865-cart-price-rule-fix-for-insufficient-quantity-issue">ACSD-59865: la regola prezzo carrello non annulla le regole precedenti a causa di una quantità di prodotto insufficiente:</a> La patch ACSD-59865 risolve il problema per cui il valore del <em>passaggio quantità sconto</em> in <em>Sconto importo fisso</em>, <em>Sconto prezzo prodotto</em> e <em>Acquista X ottieni Y</em> Regole prezzo carrello non annulla più l'azione delle regole precedenti. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.52.
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/known-issues-patches-attached/error-when-filtering-orders-in-admin">Errore durante il filtraggio degli ordini in Admin:</a> Questo articolo fornisce una patch per il problema di Adobe Commerce in cui si verifica un errore durante il tentativo di filtrare gli ordini in Admin per data, visualizzando il messaggio: <em>Violazione del vincolo di integrità: 1052 Colonna 'created_at' in cui la clausola è ambigua</em>.
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-25030">Adobe Commerce: problemi in linea di JavaScript nella pagina di estrazione in modalità limitata CSP (Content Security Policy):</a> Questo articolo fornisce spiegazioni dettagliate e soluzioni per i problemi riscontrati con JavaScript personalizzato aggiunto tramite Adobe Commerce Admin e Google Tag Manager in Adobe Commerce 2.4.7 durante l'estrazione quando è abilitata la modalità limitata CSP <strong>.</strong>
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-61195-empty-cart-on-final-graphql-page">ACSD-61195: la richiesta Cart GraphQL non restituisce gli elementi nella pagina finale:</a> La patch ACSD-61195 risolve il problema per cui non viene restituito alcun elemento del carrello nell'ultima pagina della richiesta Cart GraphQL. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.51.
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-59514-forms-in-admin-with-page-builder-throw-error-in-browser-console">ACSD-59514: Forms in Admin con Page Builder genera un errore nella console del browser:</a> La patch ACSD-59514 risolve il problema relativo alla generazione dell'errore da parte dei moduli in Admin con Page Builder <em>Il rendering di Page Builder è durato 5 secondi senza rilasciare blocchi</em> nella console del browser dopo l'invio del modulo e non è possibile salvare le modifiche. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.50.
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-51/acsd-60538-if-product-is-disabled-attributes-dont-show">ACSD-60538: gli attributi non vengono visualizzati correttamente se il prodotto è disabilitato in <em>Tutte le visualizzazioni dello store</em>:</a> La patch ACSD-60538 risolve il problema per cui se un prodotto è disabilitato in <em>Tutte le visualizzazioni dello store</em> e abilitato solo in ambiti specifici di visualizzazione dello store, gli attributi del prodotto non vengono visualizzati correttamente nella risposta di GraphQL, causando una visualizzazione non corretta del prodotto. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.51.
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-50/acsd-58352-return-attribute-labels-for-the-default-store-are-returned-via-graphql-api">ACSD-58352: le etichette degli attributi restituite per l'archivio predefinito vengono restituite tramite API GraphQL:</a> La patch ACSD-58352 risolve il problema relativo alla restituzione delle etichette degli attributi per l'archivio predefinito tramite API GraphQL quando nell'intestazione della richiesta è specificata una visualizzazione dell'archivio non predefinita. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.50.
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-24983">Il menu a discesa <em>Switch Accounts</em> non è presente nel tuo account:</a> Questo articolo fornisce una soluzione al problema di Adobe Commerce, in cui il menu a discesa <em>Switch Accounts</em> non è presente nel tuo account e hai perso l'accesso per inviare i ticket per conto del commerciante.
    </td>
    <td>Nuovo articolo</td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>  
    <td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-56979-product-images-removed-after-staging-update-deleted">ACSD-56979: immagini del prodotto rimosse dopo l'eliminazione dell'aggiornamento dello staging:</a> La patch ACSD-56979 risolve il problema relativo alla rimozione delle immagini del prodotto dopo l'eliminazione di un aggiornamento dello staging. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.49.  
    </td>
    <td>Nuovo articolo</td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-48210-store-view-specific-scope-attribute-overrides-global-values">ACSD-48210: gli attributi di ambito specifici della visualizzazione archivio sovrascrivono i valori globali:</a> La patch ACSD-48210 risolve il problema per cui quando si aggiorna un attributo <em>Ambito sito Web</em> all'interno di una visualizzazione archivio specifica, i valori degli attributi nell'ambito globale vengono sostituiti. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.50. 
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-59280-fix-for-reflection-union-type-error">ACSD-59280: Errore ReflectionUnionType::getName() nelle installazioni 2.4.4-pX:</a> La patch ACSD-59280 risolve il problema relativo alla chiamata al metodo non definito <code>ReflectionUnionType::getName()</code> durante l'installazione delle versioni 2.4.4-pX. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.50. 
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-54887-customer-shopping-cart-gets-cleared-after-session-expiry">ACSD-54887: il carrello acquisti del cliente viene cancellato dopo la scadenza della sessione del cliente:</a> La patch ACSD-54887 risolve il problema relativo alla cancellazione del carrello acquisti del cliente dopo la scadenza della sessione del cliente con <em>Carrello acquisti persistente</em> abilitato. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.50. 
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-60303-admin-order-placement-fix">ACSD-60303: il problema di posizionamento dell'ordine amministratore è stato risolto con la minimizzazione HTML abilitata:</a> La patch ACSD-60303 risolve il problema che impedisce di effettuare un ordine da amministratore se la minimizzazione HTML è abilitata. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.50. 
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57045-url-rewrites-cause-infinite-page-looping-after-website-root-unchecked-hierarchy">ACSD-57045: le riscritture URL causano un ciclo di pagine infinito dopo la deselezione di <em>Directory principale sito Web</em> dalla gerarchia:</a> La patch ACSD-57045 risolve il problema relativo alle riscritture URL, che causano un ciclo di pagine infinito dopo la deselezione di <em>Directory principale sito Web</em> dalla gerarchia. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.49.
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/ascd-58446-deleting-a-team-with-child-users-or-teams-via-graphql-gives-an-uninformative-error-message">ACSD-58446: l'eliminazione di un team con utenti o team secondari tramite GraphQL genera un messaggio di errore non informativo:</a> La patch ACSD-58446 risolve il problema di Adobe Commerce, in cui l'eliminazione di un team con utenti o team secondari tramite GraphQL restituisce un messaggio di errore non informativo non coerente con l'interfaccia utente. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.49. 
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-58375-wrong-youtube-api-key-configuration-causes-an-error-when-adding-a-youtube-video-at-the-store-view-level">ACSD-58735: la chiave API YouTube non è configurata correttamente causa un errore durante l'aggiunta di video a livello di visualizzazione archivio:</a> La patch ACSD-58735 risolve il problema se la configurazione errata della chiave API YouTube causa un errore durante l'aggiunta di un video YouTube a livello di visualizzazione archivio. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.49. 
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-49/acsd-57086-orders-placed-from-non-default-websites-with-terms-conditions-processed-incorrectly">ACSD-57086: gli ordini provenienti da siti Web non predefiniti con termini e condizioni abilitati non vengono elaborati correttamente:</a> La patch ACSD-57086 risolve il problema relativo agli ordini provenienti da siti Web non predefiniti con termini e condizioni abilitati non vengono elaborati correttamente. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.49. 
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58141-phpsessid-regenerates-on-post-requests-for-logged-in-customers-with-l2-redis-cache-enabled">ACSD-58141: PHPSESSID viene rigenerato nelle richieste POST per i clienti connessi se la cache L2 Redis è abilitata:</a> La patch ACSD-58141 risolve il problema in cui PHPSESSID viene rigenerato nelle richieste POST per un cliente connesso se la cache L2 Redis è abilitata e il cliente viene aggiornato dall'amministratore. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.50. 
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58790-fixes-pinch-to-zoom-functionality-on-the-product-detail-page-images-in-mobile-view-on-chrome">ACSD-58790: Corregge la funzionalità di zoom sulle immagini della pagina dei dettagli del prodotto nella visualizzazione per dispositivi mobili su Chrome:</a> La patch ACSD-58790 risolve il problema di Adobe Commerce, in cui l'immagine nella visualizzazione per dispositivi mobili su Chrome non veniva ingrandita come previsto. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.50. 
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-50/acsd-58442-fixes-issue-devices-768px-mobile-view-instead-desktop">ACSD-58442: è stato risolto il problema che causava il caricamento di menu e intestazioni nella visualizzazione per dispositivi mobili non desktop nei dispositivi con larghezza di 768 px:</a> La patch ACSD-58442 risolve il problema Adobe Commerce, che causava il caricamento di menu e intestazioni in una visualizzazione per dispositivi mobili anziché desktop nei dispositivi con larghezza di 768 px. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.50.
    </td>
    <td>Nuovo articolo </td>
    <td>17 ottobre 2024</td>
  </tr>
</table>
