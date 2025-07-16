---
title: Il numero massimo di cookie verrebbe superato dall’errore in Adobe Commerce
description: Scopri come risolvere il problema di Adobe Commerce in cui si verifica un errore che indica il superamento del numero massimo di cookie.
feature: Deploy, Support, Upgrade, Tools and External Services
role: Admin, Developer
exl-id: 5c42ea7a-f023-4d34-8417-bb470efc3b84
source-git-commit: 87e98607ee5e1cc41e4266836fd09531a290725e
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---

# *Il numero massimo di cookie verrebbe superato* errore in Adobe Commerce

In questo articolo vengono fornite patch per risolvere l&#39;errore che indica il superamento del numero massimo di cookie ** in Adobe Commerce.

## Prodotti e versioni interessati

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7, con una delle seguenti patch:

* Patch MDVA-12304 applicata utilizzando [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/release-notes)
* [Aggiornamento sicurezza disponibile per Adobe Commerce - APSB25-08](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27149)
* [Patch cloud per [!DNL Commerce] 1.1.4](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches)

## Problema

A causa di problemi relativi ai cookie in Adobe Commerce, nei registri di errore viene visualizzato il seguente errore:

*rapporto.AVVISO: impossibile inviare il cookie. Il numero massimo di cookie verrebbe superato.*

### Causa

Il problema si verifica perché il numero massimo di cookie consentiti è impostato su *50*.

## Soluzione

1. Rimuovere la patch MDVA-12304 se applicata utilizzando [!DNL Quality Patches Tool (QPT)].

   * Per Adobe Commerce su infrastruttura cloud, rimuovere la patch da `.magento.env.yaml`.
   * Per le installazioni locali di Adobe Commerce, esegui il seguente comando per ripristinare la patch:

     `vendor/bin/magento/quality-patches revert MDVA-12304`

1. Applicare le patch allegate in base alla versione di Adobe Commerce in uso:

   * Per le versioni 2.4.4-p12, 2.4.5-p11, 2.4.6-p9 e 2.4.7-p4, applicare la [patch ACSD-64710](assets/acsd-64710_2.4.5-p11.patch.zip).

   * Per le versioni 2.4.4-p13, 2.4.5-p12, 2.4.6-p10, 2.4.7-p5 e 2.4.8, applicare la [patch ACSD-65562](assets/acsd-65562_2.4.5-p12.patch.zip).

### Lettura correlata

* [Applicare le patch](https://experienceleague.adobe.com/en/docs/commerce-operations/upgrade-guide/patches/apply) nella guida all&#39;aggiornamento di Adobe Commerce
* [Best practice per la distribuzione delle patch di Adobe Commerce su larga scala](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/maintenance/patching-at-scale) nel playbook di implementazione di Adobe Commerce
* [Note sulla versione per Commerce Cloud Tools Suite](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-tools-suite) nella Guida di Commerce su Cloud.
