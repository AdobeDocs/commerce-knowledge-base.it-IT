---
title: Knowledge Base di supporto Adobe Commerce
description: Tutto ciò che è necessario sapere per risolvere i problemi e gestire il Commerce Store.
exl-id: feacf38f-2803-4170-a64f-5d7c4567432d
feature: Support
role: Admin
source-git-commit: 95509b717d41436b68ad94c3c28ac72e1887fdfc
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 1%

---

# Knowledge Base di supporto Adobe Commerce

![Home page della Knowledge Base](../help/assets/knowledge-base-home-page-cover.jpg){width="100%"}

Le informazioni contenute in questa Knowledge Base sono complementari a [Adobe Commerce Developer Documentation](https://developer.adobe.com/commerce/docs), [Adobe Commerce Merchant Guide](https://experienceleague.adobe.com/docs/commerce-admin/user-guides/home.html) e ad altre pubblicazioni Adobe Commerce. Descrive la risoluzione dei problemi e le best practice, gli annunci host, le risposte alle domande frequenti ed evidenzia scenari specifici che non sono stati menzionati (per qualsiasi motivo) nella documentazione ufficiale.

## Cosa c&#39;è nella Knowledge Base?

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
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/how-to/how-to-update-the-cloud-account-profile">Come aggiornare il profilo dell'account cloud:</a> In questo articolo vengono illustrati i passaggi per la modifica del profilo nell'account cloud.
    </td>
    <td>Nuovo articolo</td>
    <td>22 aprile 2024</td>
  </tr>

<td>
    <a href = "https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/admin-create-order-page-in-csp-restricted-mode">Risoluzione dei problemi relativi alla creazione della pagina dell'ordine in modalità CSP con restrizioni:</a> Questo articolo fornisce spiegazioni e correzioni per i problemi di Adobe Commerce 2.4.7 durante la creazione di un ordine sul lato Amministratore quando la modalità con restrizioni CSP è <em>Abilitata</em>.  
    </td>
    <td>Nuovo articolo</td>
    <td>22 aprile 2024</td>
  </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/payments/storefront-checkout-page-in-csp-restricted-mode">Risoluzione dei problemi relativi alla pagina di estrazione della vetrina in modalità CSP con restrizioni:</a> Questo articolo fornisce spiegazioni e correzioni per i problemi di Adobe Commerce 2.4.7 durante la visualizzazione della pagina di estrazione in modalità CSP con restrizioni, con <em>"Rifiuto dell'esecuzione dello script in linea a causa della violazione della seguente direttiva Content Security Policy: messaggio di errore "script-src ..."</em> nel registro della console del browser. 
    </td>
    <td>Nuovo articolo </td>
    <td>22 aprile 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-46/acsd-54656-invisible-recaptcha-fails-during-checkout-preventing-order-placement">ACSD-54656: reCAPTCHA invisibile non funziona durante l'estrazione impedendo il posizionamento dell'ordine:</a> La patch ACSD-54656 risolve il problema relativo al funzionamento non corretto di reCAPTCHA invisibile durante l'estrazione, che impedisce il posizionamento di un ordine. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.46. 
    </td>
    <td>Nuovo articolo </td>
    <td>22 aprile 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-46/acsd-46767-category-page-caches-invalidate-when-the-stock-quantity-changes">ACSD-46767: le cache della pagina Categoria annullano la validità quando cambia la quantità di magazzino:</a> La patch ACSD-46767 risolve il problema che causa l'annullamento della validità della pagina Categoria quando cambia la quantità di magazzino, anche se il prodotto è ancora in magazzino. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.46.  
    </td>
    <td>Nuovo articolo </td>
    <td>22 aprile 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-45/acsd-56415-performance-of-partial-price-indexing-is-slowed-down-due-to-a-delete-query">ACSD-56415: le prestazioni dell'indicizzazione parziale dei prezzi sono rallentate a causa di una query DELETE:</a> La patch ACSD-56415 risolve il problema relativo al rallentamento delle prestazioni dell'indicizzazione parziale dei prezzi dovuto a una query DELETE quando il database dispone di molti indici parziali dei dati dei prezzi. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.45.  
    </td>
    <td>Nuovo articolo </td>
    <td>22 aprile 2024</td>
 </tr>

<tr>
    <td>
    <a href="https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/support-tools/patches/v1-1-47/acsd-56858-role-permissions-display-issue-in-b2b-company-admin-panel">ACSD-56858: discrepanza nelle autorizzazioni del ruolo nell'amministratore società B2B:</a> La patch ACSD-56858 risolve il problema relativo alla visualizzazione errata delle autorizzazioni del ruolo per un amministratore società con restrizioni nell'ambiente B2B. Questa patch è disponibile quando è installato <a href="https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html">[!DNL Quality Patches Tool (QPT)]</a> 1.1.47. 
    </td>
    <td>Nuovo articolo </td>
    <td>22 aprile 2024</td>
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
