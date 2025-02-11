---
title: Aggiornamento di sicurezza disponibile per Adobe Commerce - [!DNL APSB25-08]
promoted: true
description: Applicare una patch isolata per correggere [!DNL critical, important, and moderate vulnerabilities] sia per Adobe Commerce Magenti Open Source che per le versioni 2.4.7-beta1, 2.4.7-p3, 2.4.6-p8, 2.4.5-p10, 2.4.4-p11 e precedenti.
feature: Compliance, Security
role: Developer
source-git-commit: 45c6486dea10b37aa8114467bbd7be0c7f9f86f6
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# Aggiornamento di sicurezza disponibile per Adobe Commerce - [!DNL APSB25-08]

L’11 febbraio 2025, Adobe ha rilasciato un aggiornamento della sicurezza regolarmente pianificato per Adobe Commerce e Magento Open Source. Questo aggiornamento risolve [[!DNL critical, important] e  [!DNL moderate]](https://helpx.adobe.com/security/severity-ratings.html) vulnerabilità. Il successo dello sfruttamento di queste vulnerabilità potrebbe portare all’esecuzione arbitraria del codice, al bypass della funzione di sicurezza e all’escalation dei privilegi. Ulteriori informazioni sono disponibili nel [Bollettino sulla sicurezza di Adobe ([!DNL APSB25-08]) qui](https://helpx.adobe.com/security/products/magento/apsb25-08.html).

>[!NOTE]
>
>**Per garantire che la correzione per [!DNL CVE-2025-24434], indicata nel bollettino sulla sicurezza riportato sopra, possa essere applicata il più rapidamente possibile, Adobe ha inoltre rilasciato una patch isolata che risolve [!DNL CVE-2025-24434]. Questo consente ai commercianti di applicare la correzione in isolamento con meno rischi di ritardo a causa di potenziali problemi di integrazione.**

**Applica gli ultimi aggiornamenti di sicurezza il prima possibile. In caso contrario, si sarà vulnerabili a questi problemi di sicurezza e Adobe disporrà di mezzi limitati per contribuire a risolvere ulteriormente il problema.**

>[!NOTE]
>
>In caso di problemi durante l&#39;applicazione della patch di sicurezza o della patch isolata, contattare il supporto tecnico.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud, Adobe Commerce on-premise e Magento Open Source:

* 2.4.7-beta1 e versioni precedenti
* 2.4.7-p3 e versioni precedenti
* 2.4.6-p8 e versioni precedenti
* 2.4.5-p10 e versioni precedenti
* 2.4.4-p11 e versioni precedenti

## Soluzione per il software on-premise Adobe Commerce on Cloud e Adobe Commerce

Per risolvere la vulnerabilità dei prodotti e delle versioni interessati, è necessario applicare la patch isolata [!DNL CVE-2025-24434].

## Dettagli patch isolata

Usare la seguente patch isolata collegata:

[vuln-28982-composer-patch.zip](assets/vuln-28982-composer-patch.zip)

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
