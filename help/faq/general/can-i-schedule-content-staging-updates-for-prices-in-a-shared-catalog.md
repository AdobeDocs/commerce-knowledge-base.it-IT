---
title: Posso pianificare gli aggiornamenti di Gestione temporanea dei contenuti per i prezzi in un catalogo condiviso?
description: Adobe Commerce non offre la funzionalità di pianificazione di un aggiornamento del prezzo ([Content Staging](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)) per uno o più prodotti in un catalogo condiviso.
exl-id: 5482326f-54c2-4efc-8e5e-6d075ee5be55
feature: Catalog Management, Customer Service
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
subfeature_v2:
  - id: deedbb4d-f1b7-58ea-a34a-de1f481f9d4c
    internal-label: Customer Service
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 0%
---
# Posso pianificare gli aggiornamenti di Gestione temporanea dei contenuti per i prezzi in un catalogo condiviso?

Adobe Commerce non offre la funzionalità di pianificazione di un aggiornamento del prezzo ([Gestione temporanea dei contenuti](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging.html)) per uno o più prodotti in un catalogo condiviso.

Ciò significa che non è possibile pianificare un aggiornamento del prezzo direttamente dal menu **Imposta prezzi e struttura** del pannello di amministrazione di Commerce (in questo menu non è presente il pulsante **Pianifica nuovo aggiornamento**).

È comunque possibile utilizzare metodi alternativi e pianificare un aggiornamento del prezzo per:

* un gruppo di clienti
* il prezzo base del prodotto

## Pianifica aggiornamento prezzo per un gruppo di clienti

1. Avvia [la pianificazione di un nuovo aggiornamento del prodotto](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html).
1. Scorri verso il basso fino al campo **Prezzo** e fai clic su **Determinazione prezzi avanzata**.

   ![advanced_pricing.png](assets/advanced_pricing.png){width="600"}

1. Nella sezione **Prezzo gruppo clienti**, seleziona il gruppo clienti necessario e imposta il prezzo aggiornato.

   ![customer_group_price.png](assets/customer_group_price.png){width="700"}

1. Completa la pianificazione dell’aggiornamento come al solito.

In questo flusso di lavoro, è possibile aggiornare il prezzo solo per un singolo prodotto; l’aggiornamento collettivo del prezzo non è disponibile.

Ricorda: i cataloghi condivisi sfruttano i prezzi dei gruppi di clienti.

**Documentazione correlata**

* [Pianificazione di un aggiornamento (gestione temporanea del contenuto)](https://experienceleague.adobe.com/docs/commerce-admin/content-design/staging/content-staging-scheduled-update.html) nella guida utente.
* [Advanced Pricing](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/pricing/pricing-advanced.html) nella guida utente.

## Pianifica aggiornamento prezzo per il prezzo base

Vedere l&#39;articolo correlato: [In che modo la modifica del prezzo di base influisce sul prezzo del catalogo condiviso?](/help/faq/general/base-price-change-affect-on-shared-catalog-price.md) nella nostra knowledge base di supporto.
