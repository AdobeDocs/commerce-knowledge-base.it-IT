---
title: Aggiornamento di sicurezza disponibile per Adobe Commerce - [!DNL APSB24-61]
promoted: true
description: Applica una patch isolata per correggere [!DNL CVE-2024-39397] le istanze di Adobe Commerce 2.4.7-p2, 2.4.6-p7, 2.4.5-p9, 2.4.4-p10 e versioni precedenti che eseguono solo [!DNL Apache].
feature: Compliance, Security
role: Developer
source-git-commit: 2038e766d65c81172391091a0cdff4abb04e84d5
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# Aggiornamento di sicurezza disponibile per Adobe Commerce - [!DNL APSB24-61]

Il 13 agosto 2024 Adobe ha rilasciato un aggiornamento sulla sicurezza del plug-in Adobe Commerce, Magento Open Source e Adobe Commerce Webhooks.
Questo aggiornamento risolve [[!DNL critical, important] e  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html) vulnerabilità. Un corretto sfruttamento potrebbe causare l’esecuzione arbitraria del codice, la lettura arbitraria del file system, il bypass delle funzionalità di sicurezza e l’escalation dei privilegi. Il bollettino è [Adobe Security Bulletin ([!DNL APSB24-61])](https://helpx.adobe.com/security/products/magento/apsb24-61.html).

>[!NOTE]
>
>**[!DNL CVE-2024-39397]è applicabile solo quando si utilizza il server Web [!DNL Apache].** Per garantire che la correzione per questa vulnerabilità possa essere applicata il più rapidamente possibile, Adobe ha anche rilasciato una patch isolata che risolve [!DNL CVE-2024-39397].

**Applica gli ultimi aggiornamenti di sicurezza il prima possibile. In caso contrario, si sarà vulnerabili a questi problemi di sicurezza e gli Adobi disporranno di mezzi limitati per contribuire a risolvere il problema.**

>[!NOTE]
>
>In caso di problemi durante l&#39;applicazione della patch di sicurezza o della patch isolata, contattare il supporto tecnico.

## Prodotti e versioni interessati

Adobe Commerce su Cloud, Adobe Commerce on-premise e Magento Open Source:

* 2.4.7-p1 e versioni precedenti
* 2.4.6-p6 e versioni precedenti
* 2.4.5-p8 e versioni precedenti
* 2.4.4-p9 e versioni precedenti

## Soluzione per Adobe Commerce on Cloud, software Adobe Commerce on-premise e Magento Open Source

Per risolvere la vulnerabilità dei prodotti e delle versioni interessati, è necessario applicare la patch isolata [!DNL CVE-2024-39397].

## Dettagli patch isolata

Usare la seguente patch isolata collegata:

* [acsd-60551-composer-patch.zip](assets/acsd-60551-composer-patch.zip)

## Come applicare il cerotto isolato

Decomprimi il file e vedi [Come applicare una patch del compositore fornita dall&#39;Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html) nella Knowledge Base di supporto per le istruzioni.

## Solo per gli esercenti di Adobe Commerce on Cloud: come stabilire se le patch isolate sono state applicate

Considerando che non è possibile verificare facilmente se il problema è stato corretto, è possibile verificare se la patch isolata [!DNL CVE-2024-39397] è stata applicata correttamente.

<u>A tale scopo, eseguire la procedura seguente, utilizzando il file `VULN-27015-2.4.7_COMPOSER.patch` come esempio</u>:

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

* [Bollettino sulla sicurezza di Adobe ([!DNL APSB24-61])](https://helpx.adobe.com/security/products/magento/apsb24-61.html)
