---
title: Aggiornamento di sicurezza disponibile per Adobe Commerce - [!DNL APSB25-08]
promoted: true
description: Applica una patch isolata per correggere [!DNL critical, important, and moderate vulnerabilities] per Adobe Commerce 2.4.8-beta1, 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11 e versioni precedenti.
feature: Compliance, Security
role: Developer
exl-id: 567e6ad2-704e-461f-a54d-75f6bd96e996
source-git-commit: aba9548c0b5a06ffd0cddce630e53e5664bb9aac
workflow-type: tm+mt
source-wordcount: '508'
ht-degree: 0%

---

# Aggiornamento di sicurezza disponibile per Adobe Commerce - [!DNL APSB25-08]

L’11 febbraio 2025, Adobe ha rilasciato un aggiornamento sulla sicurezza regolarmente pianificato per Adobe Commerce e Magento Open Source. Questo aggiornamento risolve [[!DNL critical, important] e  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html) vulnerabilità. Il successo dello sfruttamento di queste vulnerabilità potrebbe portare all’esecuzione arbitraria del codice, al bypass della funzione di sicurezza e all’escalation dei privilegi. Ulteriori informazioni sono disponibili nel [Bollettino sulla sicurezza di Adobe ([!DNL APSB25-08]) qui](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

>[!NOTE]
>
>**Per garantire che la correzione per [!DNL CVE-2025-24434], indicata nel bollettino sulla sicurezza riportato sopra, possa essere applicata il più rapidamente possibile, Adobe ha inoltre rilasciato una patch isolata che risolve [!DNL CVE-2025-24434]. Questo consente ai commercianti di applicare la correzione in isolamento con meno rischi di ritardo a causa di potenziali problemi di integrazione.**

**Applica gli ultimi aggiornamenti di sicurezza il prima possibile. In caso contrario, si sarà vulnerabili a questi problemi di sicurezza e Adobe disporrà di mezzi limitati per contribuire a risolvere ulteriormente il problema.**

>[!NOTE]
>
>In caso di problemi durante l&#39;applicazione della patch di sicurezza o della patch isolata, contattare il supporto tecnico.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud, Adobe Commerce on-premise e Magento Open Source:

* 2.4.8-beta1 e versioni precedenti
* 2.4.7-p3 e versioni precedenti
* 2.4.6-p8 e versioni precedenti
* 2.4.5-p10 e versioni precedenti
* 2.4.4-p11 e versioni precedenti

## Soluzione per Adobe Commerce on Cloud, Adobe Commerce on-premise e software Magento Open Source

>[!NOTE]
>
>Questo problema è stato risolto con l&#39;[ultimo aggiornamento di patch cloud](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest). Il tentativo di applicare la patch isolata quando la correzione è già in atto dall’aggiornamento di Cloud-patches può causare errori di installazione.

Per risolvere la vulnerabilità dei prodotti e delle versioni interessati, è necessario applicare la patch isolata [!DNL CVE-2025-24434], a seconda della versione di Adobe Commerce/Magento Open Source in uso.

## Dettagli patch isolata

Utilizza le seguenti patch isolate allegate, a seconda della versione di Adobe Commerce/Magento Open Source in uso:

### Per la versione 2.4.8-beta1:

* [vuln-28982-2-4-8x-v2-composer-patch.zip](assets/vuln-28982-2-4-8x-v2-composer-patch.zip)

### Per le versioni 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3:

* [vuln-28982-2-4-7x-v2-composer-patch.zip](assets/vuln-28982-2-4-7x-v2-composer-patch.zip)

### Per le versioni 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8:

* [vuln-28982-2-4-6x-v2-composer-patch.zip](assets/vuln-28982-2-4-6x-v2-composer-patch.zip)

### Per le versioni 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10:

* [vuln-28982-2-4-5x-v2-composer-patch.zip](assets/vuln-28982-2-4-5x-v2-composer-patch.zip)

### Per le versioni 2.4.4, 2.4.4-p1,, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11:

* [vuln-28982-2-4-4x-v2-composer-patch.zip](assets/vuln-28982-2-4-4x-v2-composer-patch.zip)


## Come applicare il cerotto isolato

Decomprimi il file e vedi [Come applicare una patch del compositore fornita da Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) nella Knowledge Base di supporto per le istruzioni.

## Solo per gli esercenti di Adobe Commerce on Cloud: come stabilire se le patch isolate sono state applicate

Considerando che non è possibile verificare facilmente se il problema è stato corretto, è possibile verificare se la patch isolata [!DNL CVE-2025-24434] è stata applicata correttamente.

>[!NOTE]
>
><u>A tale scopo, eseguire la procedura seguente, utilizzando il file `VULN-27015-2.4.7_COMPOSER.patch` **come esempio**</u>:

1. [Installare lo strumento Patch di qualità](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html).
1. Esegui il comando:<br>
   ![cve-2024-34102-tell-if-patch-apply-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Dovresti visualizzare un output simile a questo, dove VULN-27015 restituisce lo stato *Applicato*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->

## Aggiornamenti di sicurezza

Aggiornamenti di sicurezza disponibili per Adobe Commerce:

* [Bollettino sulla sicurezza di Adobe ([!DNL APSB25-08])](https://helpx.adobe.com/security/products/magento/apsb25-08.html)
* [Aggiornamenti alla sicurezza più recenti disponibili per Adobe Commerce](https://helpx.adobe.com/security/products/magento.html)
