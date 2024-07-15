---
title: Sito non accessibile a causa del cloaking dell'origine
description: Questo articolo fornisce una soluzione per i casi in cui l’amministratore e/o la gestione temporanea dell’infrastruttura cloud di Adobe Commerce su cloud o la vetrina del sito di produzione non sono accessibili.
exl-id: 4412d744-3066-4f78-bc45-8149614ce455
feature: Products
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '216'
ht-degree: 0%

---

# Sito non accessibile a causa del cloaking dell&#39;origine

Questo articolo fornisce una soluzione per i casi in cui l’amministratore e/o la gestione temporanea dell’infrastruttura cloud di Adobe Commerce su cloud o la vetrina del sito di produzione non sono accessibili.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.3.x, 2.4.x

## Problema

https:&#x200B;//mydomain.com.c.&lt;projectid>.magento.cloud/ non è più accessibile.

<u>Passaggi da riprodurre:</u>

1. Accedi al progetto.
1. Fare clic su **Progetto di Access** per visualizzare un elenco di URL e SSH.

<u>Risultati effettivi:</u>

Impossibile caricare la pagina con il seguente errore:

*NET::ERR\_CERT\_INVALID* *Avviso TLS, certificato non valido (554):*

<u>Risultati previsti:</u>

Pagina caricata correttamente.

## Causa

Il cloaking dell&#39;origine è stato abilitato, pertanto l&#39;origine non è più accessibile direttamente.

Il cloaking dell’origine è una funzione di sicurezza che consente ad Adobe Commerce di bloccare qualsiasi traffico non Fastly diretto all’infrastruttura cloud (origine) per prevenire gli attacchi DDoS.

## Soluzione

* Se il sito cloud è attivo, passa a https://mydomain.com/.
* Se disponi di un sito attivo (non cloud) che utilizza il dominio https://mydomain.com/, configura un sottodominio `mcprod.mydomain.com` e aggiorna **URL di base** in *https://mcprod.mydomain.com*, quindi [punta il DNS a Fastly](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#update-dns-configuration-with-development-settings).

## Lettura correlata

[Domande frequenti sull&#39;abilitazione del cloaking dell&#39;origine rapida](/help/faq/general/fastly-origin-cloaking-enablement-faq.md) nella knowledge base di supporto.
