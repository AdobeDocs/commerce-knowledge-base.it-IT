---
title: Aggiornamento di sicurezza disponibile per Adobe Commerce - [!DNL APSB24-73]
promoted: true
description: Applica una patch isolata per correggere [!DNL critical, important, and moderate vulnerabilities] le istanze di Adobe Commerce 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10 e delle versioni precedenti che eseguono solo il modulo [!DNL B2B] .
feature: Compliance, Security
role: Developer
source-git-commit: 694cb7519733e950b55006866e585097bc2429f4
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Aggiornamento di sicurezza disponibile per Adobe Commerce - [!DNL APSB24-73]

L’8 ottobre 2024, Adobe ha rilasciato un aggiornamento della sicurezza pianificato regolarmente per Adobe Commerce e [!DNL Adobe Commerce Webhooks Plugin].
Questo aggiornamento risolve [[!DNL critical, important] e  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html) vulnerabilità. Un corretto sfruttamento potrebbe causare l’esecuzione arbitraria del codice, la lettura arbitraria del file system, il bypass delle funzionalità di sicurezza e l’escalation dei privilegi. Il bollettino è [Adobe Security Bulletin ([!DNL APSB24-73])](https://helpx.adobe.com/security/products/magento/apsb24-73.html).

>[!NOTE]
>
>**[!DNL CVE-2024-45115], elencato nel bollettino sulla sicurezza precedente, è applicabile solo quando si utilizza il modulo [!DNL B2B].** Per garantire che la correzione per questa vulnerabilità possa essere applicata il più rapidamente possibile, Adobe ha anche rilasciato una patch isolata che risolve [!DNL CVE-2024-45115].

**Applica gli ultimi aggiornamenti di sicurezza il prima possibile. In caso contrario, si sarà vulnerabili a questi problemi di sicurezza e Adobe disporrà di mezzi limitati per contribuire a risolvere il problema.**

>[!NOTE]
>
>In caso di problemi durante l&#39;applicazione della patch di sicurezza o della patch isolata, contattare il supporto tecnico.

## Prodotti e versioni interessati

Adobe Commerce su Cloud e Adobe Commerce on-premise:

* 2.4.7-p2 e versioni precedenti
* 2.4.6-p7 e versioni precedenti
* 2.4.5-p9 e versioni precedenti
* 2.4.4-p10 e versioni precedenti

B2B:

* 1.4.2-p2 e versioni precedenti
* 1.3.5-p7 e versioni precedenti
* 1.3.4-p9 e versioni precedenti
* 1.3.3-p10 e versioni precedenti


## Soluzione per il software on-premise Adobe Commerce on Cloud e Adobe Commerce

Per risolvere la vulnerabilità dei prodotti e delle versioni interessati, è necessario applicare la patch isolata [!DNL CVE-2024-45115].

## Dettagli patch isolata

Usare la seguente patch isolata collegata:

[vuln-26510-composer-patch.zip](assets/vuln-26510-composer-patch.zip)

## Come applicare il cerotto isolato

Decomprimi il file e vedi [Come applicare una patch del compositore fornita da Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) nella Knowledge Base di supporto per le istruzioni.

## Solo per gli esercenti di Adobe Commerce on Cloud: come stabilire se le patch isolate sono state applicate

Considerando che non è possibile verificare facilmente se il problema è stato corretto, è possibile verificare se la patch isolata [!DNL CVE-2024-45115] è stata applicata correttamente.

<u>A tale scopo, eseguire la procedura seguente, utilizzando il file `VULN-27015-2.4.7_COMPOSER.patch` **come esempio**</u>:

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

* [Bollettino sulla sicurezza di Adobe ([!DNL APSB24-73])](https://helpx.adobe.com/security/products/magento/apsb24-73.html)
