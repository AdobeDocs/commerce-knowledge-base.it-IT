---
title: Hotfix per il pacchetto di compatibilità di Adobe Commerce 2.4.7-p4 [!DNL HIPAA] 1.2.0
description: Questo articolo fornisce un hotfix per aggiungere compatibilità per il nuovo  [!DNL HIPAA] pacchetto 1.2.0 con Adobe Commerce on Cloud Infrastructure 2.4.7-p4
feature: Install, Upgrade, Security, Compliance
role: Developer
source-git-commit: 705c43d2328d47fb5f00ae582a2a623ca9f94f70
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Hotfix per pacchetto di compatibilità [!DNL HIPAA] 1.2.0 di Adobe Commerce 2.4.7-p4

Questo articolo fornisce un hotfix per aggiungere compatibilità per il nuovo pacchetto **[!DNL HIPAA]1.2.0** con Adobe Commerce on Cloud Infrastructure 2.4.7-p4.

Il problema verrà risolto nella versione 2.4.7-p5.

## Versioni e prodotti interessati

Adobe Commerce sull’infrastruttura cloud 2.4.7-p4 e versioni precedenti

## Prerequisiti

* Adobe ha eseguito il provisioning del tuo account Adobe Commerce per accedere all&#39;estensione **[!DNL HIPAA Ready]**. Consulta [[!DNL HIPAA] preparazione su Adobe Commerce](https://experienceleague.adobe.com/it/docs/commerce-admin/start/compliance/hipaa-ready-service/overview) per ulteriori dettagli nella **Guida introduttiva di Adobe Commerce**.
* Accedi a [repo.magento.com](https://repo.magento.com) per installare l&#39;estensione. Per generare le chiavi e ottenere i diritti necessari, vedere [Ottenere le chiavi di autenticazione](https://experienceleague.adobe.com/it/docs/commerce-operations/installation-guide/prerequisites/authentication-keys) nella **Guida all&#39;installazione di Adobe Commerce**.

## Problema

Il pacchetto [!DNL HIPAA] 1.1.0 non è compatibile con la versione 2.4.7x di Adobe Commerce.

## Soluzione

Tramite questo hotfix, i commercianti che eseguono Adobe Commerce sull&#39;infrastruttura cloud 2.4.7-p4 potranno utilizzare il pacchetto [!DNL HIPAA] 1.2.0.

>[!NOTE]
>
>**[!DNL HIPAA]1.2.0 è compatibile solo con Adobe Commerce 2.4.7-p5. Se si desidera aggiungere la compatibilità con [!DNL HIPAA] 1.2.0 ad Adobe Commerce 2.4.7-p4, installare la patch fornita.<br><u>Se non usi Adobe Commerce 2.4.7-p4, devi prima eseguire l&#39;aggiornamento ad Adobe Commerce 2.4.7-p4 per usare questa patch</u>.**

Per risolvere il problema relativo all’infrastruttura Adobe Commerce on Cloud 2.4.7-p4, è necessario applicare la patch:

[ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip](assets/ac-13382--patch-for-hipaa-2-4-7-p4-composer-patch.zip)

## Come applicare il cerotto

Decomprimi il file e vedi [Come applicare una patch del compositore fornita da Adobe](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-apply-a-composer-patch-provided-by-magento.html?lang=it) nella Knowledge Base di supporto per le istruzioni.

## Solo per gli esercenti di Adobe Commerce on Cloud: come stabilire se la patch è stata applicata

Considerando che non è possibile verificare facilmente se il problema è stato corretto, è possibile verificare se la patch è stata applicata correttamente.

>[!NOTE]
>
><u>Per eseguire questa operazione, eseguire la procedura seguente, utilizzando il file `VULN-27015-2.4.7_COMPOSER.patch` **come esempio**</u>:

1. [Installare lo strumento Patch di qualità](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it).
1. Esegui il comando:<br>
   ![cve-2024-34102-tell-if-patch-apply-code](assets/cve-2024-34102-tell-if-patch-applied-code.png)
1. Dovresti visualizzare un output simile a questo, **<u>dove l&#39;esempio utilizzato qui, VULN-27015</u>**, restituisce lo stato *Applicato*:

   ```bash
   ║ Id            │ Title                                                        │ Category        │ Origin                 │ Status      │ Details                                          ║ ║ N/A           │ ../m2-hotfixes/VULN-27015-2.4.7_COMPOSER_patch.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                
   ```

<!-- For Step 2:
     ```bash
    vendor/bin/magento-patches -n status |grep "27015\|Status"
     ```
-->
