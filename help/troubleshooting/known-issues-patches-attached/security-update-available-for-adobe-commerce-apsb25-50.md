---
title: Aggiornamento di sicurezza disponibile per Adobe Commerce - [!DNL APSB25-50]
promoted: true
description: Applicare una patch isolata per correggere [!DNL critical and important vulnerabilities] per Adobe Commerce 2.4.8, 2.4.7-p5, 2.4.6-p10, 2.4.5-p12, 2.4.4-p13 e versioni precedenti.
feature: Compliance, Security
role: Developer
source-git-commit: 9df7dee77bec7ffe4323f21e44d555338a0b1934
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Aggiornamento di sicurezza disponibile per Adobe Commerce - [!DNL APSB25-50]

Il 10 giugno 2025 Adobe ha rilasciato un aggiornamento della sicurezza regolarmente pianificato per Adobe Commerce e Magento Open Source. Questo aggiornamento risolve [[!DNL critical] e [!DNL important]](https://helpx.adobe.com/it/security/severity-ratings.html) vulnerabilità. Il successo dello sfruttamento di queste vulnerabilità potrebbe portare al bypass delle funzionalità di sicurezza, all’escalation dei privilegi e all’esecuzione arbitraria del codice.

Ulteriori informazioni sono disponibili nel [Bollettino sulla sicurezza di Adobe ([!DNL APSB25-50]) qui](https://helpx.adobe.com/security/products/magento/apsb25-50.html).

>[!NOTE]
>
>**Per garantire che la correzione per [!DNL CVE-2025-47110] indicata nel bollettino sulla sicurezza di cui sopra possa essere applicata il più rapidamente possibile, Adobe ha inoltre rilasciato una patch isolata che risolve [!DNL CVE-2025-47110]. Questo consente ai commercianti di applicare la correzione in isolamento con meno rischi di ritardo a causa di potenziali problemi di integrazione.**

**Applica gli ultimi aggiornamenti di sicurezza il prima possibile. In caso contrario, si sarà vulnerabili a questi problemi di sicurezza e Adobe disporrà di mezzi limitati per contribuire a risolvere ulteriormente il problema.**

Ulteriori informazioni sul [processo di distribuzione delle patch isolate sono disponibili qui.](https://business.adobe.com/blog/introducing-enhanced-security-patch-deployment-and-communications-in-adobe-commerce)

>[!NOTE]
>
>Per i clienti Adobe Commerce su Managed Services, il Customer Success Engineer può fornire ulteriori indicazioni sull’applicazione della patch.

>[!NOTE]
>
>In caso di problemi durante l&#39;applicazione della patch di sicurezza o della patch isolata, contattare il supporto tecnico.

Come promemoria, puoi trovare [gli aggiornamenti di sicurezza più recenti disponibili per Adobe Commerce qui.](https://helpx.adobe.com/it/security/products/magento.html)

## Prodotti e versioni interessati

Adobe Commerce (tutti i metodi di distribuzione):

* 2.4.8.
* 2.4.7-p5 e versioni precedenti
* 2.4.6-p10 e versioni precedenti
* 2.4.5-p12 e versioni precedenti
* 2.4.4-p13 e versioni precedenti

## Problemi

### I. CVE-2025-47110: XSS memorizzato tramite l’iniezione di modelli lato server in Adobe Commerce 2.4.7-p4

<u>Prodotti e versioni interessati</u>:

Adobe Commerce (tutti i metodi di distribuzione):

* 2.4.8.
* 2.4.7-p5 e versioni precedenti
* 2.4.6-p10 e versioni precedenti
* 2.4.5-p12 e versioni precedenti
* 2.4.4-p13 e versioni precedenti

<u>Soluzione</u>:

Per le versioni di Adobe Commerce:

* 2.4.8.
* 2.4.7, 2.4.7-p1, 2.4.7-p2, 2.4.7-p3, 2.4.7-p4, 2.4.7-p5
* 2.4.6, 2.4.6-p1, 2.4.6-p2, 2.4.6-p3, 2.4.6-p4, 2.4.6-p5, 2.4.6-p6, 2.4.6-p7, 2.4.6-p8, 2.4.6-p10
* 2.4.5, 2.4.5-p1, 2.4.5-p2, 2.4.5-p3, 2.4.5-p4, 2.4.5-p5, 2.4.5-p6, 2.4.5-p7, 2.4.5-p8, 2.4.5-p9, 2.4.5-p10, 2.4.5-p11, 2.4.5-p12
* 2.4.4, 2.4.4-p1, 2.4.4-p2, 2.4.4-p3, 2.4.4-p4, 2.4.4-p5, 2.4.4-p6, 2.4.4-p7, 2.4.4-p8, 2.4.4-p9, 2.4.4-p10, 2.4.4-p11, 2.4.4-p12, 2.4.4-p13

**Applicare la seguente patch isolata o eseguire l&#39;aggiornamento alla patch di sicurezza più recente.**

* **[VULN-31609_2.4.X.patch](assets/VULN-31609_2.4.X_patch.zip)**

### II. VULN-31547: XSS riflesso in marketplace.magento.com + un clic sul problema ATO che influisce sulle istanze IMS

<u>Prodotti e versioni interessati</u>:

Adobe Commerce (tutti i metodi di distribuzione):

* 2.4.8.

<u>Soluzione</u>:

Per le versioni di Adobe Commerce:

* 2.4.8.

**Applicare la seguente patch isolata o eseguire l&#39;aggiornamento alla patch di sicurezza più recente.**

* **[VULN-31547_2.4.8.patch](assets/VULN-31547_2.4.8_patch.zip)**

## Come applicare il cerotto isolato

Decomprimi il file e vedi [Come applicare una patch del compositore fornita da Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=it) nella Knowledge Base di supporto per le istruzioni.

## Solo per gli esercenti di Adobe Commerce on Cloud: come stabilire se le patch isolate sono state applicate

Considerando che non è possibile verificare facilmente se il problema è stato corretto, è possibile verificare se la patch isolata [!DNL CVE-2025-47110] è stata applicata correttamente.

>[!NOTE]
>
><u>A tale scopo, eseguire la procedura seguente, utilizzando il file `VULN-27015-2.4.7_COMPOSER.patch` **come ESEMPIO**</u>:

1. [Installare lo strumento Patch di qualità](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it).
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

* [Bollettino sulla sicurezza di Adobe ([!DNL APSB25-50])](https://helpx.adobe.com/security/products/magento/apsb25-50.html)
* [Aggiornamenti alla sicurezza più recenti disponibili per Adobe Commerce](https://helpx.adobe.com/it/security/products/magento.html)
