---
title: Posso installare applicazioni di terze parti nella mia istanza cloud?
description: No. L’installazione di app di terze parti (come WordPress o Drupal) su Adobe Commerce nei server dell’infrastruttura cloud non è consentita. È necessario ospitare tali applicazioni su server esterni.
exl-id: 3abbe282-2a14-4597-8af8-da1edcbece30
feature: Cloud, Compliance, Install
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Posso installare applicazioni di terze parti nella mia istanza cloud?

No. L’installazione di app di terze parti (come WordPress o Drupal) su Adobe Commerce nei server dell’infrastruttura cloud non è consentita. È necessario ospitare tali applicazioni su server esterni.

## Motivi

### Condizioni del contratto di assistenza

L&#39;edizione [dei termini del contratto di servizio](https://magento.com/legal/terms/cloud-terms) di Adobe Commerce on cloud infrastructure indica all&#39;articolo 18 quanto segue:

> Il Cliente accetta che Adobe Commerce e il Servizio non verranno utilizzati per ospitare altre applicazioni software di terze parti che non dipendono direttamente dal Software.

Essendo una soluzione cloud, Adobe si assume la piena responsabilità della sicurezza del server. Per garantire un’elevata sicurezza, consentiamo di ospitare l’applicazione Adobe Commerce solo sul server cloud dedicato.

### Conformità PCI

In qualità di provider di soluzioni di livello 1 con certificazione PCI, Adobe Commerce sull’infrastruttura cloud deve seguire lo standard PCI Data Security e assicurarsi di:

>... Sviluppo e manutenzione di sistemi e applicazioni sicuri
> ([Approccio di Adobe alla conformità PCI](https://magento.com/pci-compliance) Requisito 6, Mantenere un programma di gestione delle vulnerabilità)

Poiché Adobe non può garantire la conformità PCI delle applicazioni di terze parti, l’installazione di tali app sui server cloud non è consentita.

## Suggerimento: utilizzare estensioni Commerce Marketplace per integrazioni migliori

Per migliorare l&#39;integrazione dell&#39;applicazione Adobe Commerce sull&#39;infrastruttura cloud con le soluzioni di terze parti ospitate su server esterni, ti invitiamo a utilizzare le estensioni [Commerce Marketplace](https://marketplace.magento.com) che potrebbero soddisfare le tue esigenze.
