---
title: Rimuovi dal database i tentativi di accesso non riusciti
description: Questo articolo spiega come rimuovere le credenziali di accesso non riuscite preesistenti da Adobe Commerce on-premise e Adobe Commerce sul database dell’infrastruttura cloud. Per le versioni 2.2.10+ e 2.3.3+, è necessario eseguire solo lo script allegato. Per le versioni precedenti 2.3.0-2.3.2-p2, è necessario applicare una patch per interrompere la registrazione ed eseguire lo script allegato per rimuovere le credenziali di accesso non riuscite preesistenti.
exl-id: 0d7e3674-3563-414f-86a2-297eb8104099
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '673'
ht-degree: 0%

---

# Rimuovi dal database i tentativi di accesso non riusciti

>[!NOTE]
>
>Questo articolo è stato aggiornato il 13 aprile 2020 con un nuovo script denominato DB\_CLEANUP\_SCRIPT\_v2. Utilizza lo script DB\_CLEANUP\_SCRIPT\_v2 allegato per cancellare i dati di accesso non riusciti preesistenti in tabelle aggiuntive. È necessario utilizzare DB\_CLEANUP\_SCRIPT\_v2, anche se in precedenza è stato eseguito DB\_CLEANUP\_SCRIPT\_v1 per garantire la pulizia di tabelle aggiuntive.

Questo articolo spiega come rimuovere le credenziali di accesso non riuscite preesistenti da Adobe Commerce on-premise e Adobe Commerce sul database dell’infrastruttura cloud. Per le versioni 2.2.10+ e 2.3.3+, è necessario eseguire solo lo script allegato. Per le versioni precedenti 2.3.0-2.3.2-p2, è necessario applicare una patch per interrompere la registrazione ed eseguire lo script allegato per rimuovere le credenziali di accesso non riuscite preesistenti.

## **Prodotti e versioni interessati**

* Questo problema riguarda Magento Open Source, Adobe Commerce on-premise e Adobe Commerce on cloud infrastructure 2.2.x, 2.3.x e versioni precedenti.
* Le distribuzioni di Adobe Commerce 1.x non sono interessate.

## Problema

Nel 2019 è stato segnalato un bug ad Adobe Commerce che consentiva di registrare i tentativi di accesso non riusciti in un database in Adobe Commerce 2.3.x e 2.2.x. In risposta, Adobe Commerce ha incluso una correzione per questo problema in Adobe Commerce 2.3.3 e 2.2.10 (rilasciati a ottobre 2019). Anche se la correzione di tale bug ha interrotto la registrazione dei tentativi di accesso non riusciti, le informazioni raccolte prima dell’aggiornamento a queste versioni correnti potrebbero ancora esistere. Questa correzione più recente cancella le informazioni sui tentativi di accesso precedentemente registrati, se presenti.   CVE-2019-8118 è descritto e monitorato in [Vulnerabilità ed esposizioni comuni](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-8118).

## Soluzione

Se devi utilizzare lo script allegato e la patch, o solo lo script, dipende dalla versione di Adobe Commerce in uso:

**Adobe Commerce e versioni di Magento Open Source 2.3.0-2.3.2-p2**

Per queste versioni è necessario applicare la patch ed eseguire lo script di pulizia del database associato per terminare la registrazione continua ed eliminare i registri.

1. Eseguire la patch del compositore per interrompere la registrazione. Questa patch è allegata all’articolo. Per scaricarlo, scorri verso il basso fino alla fine dell&#39;articolo e fai clic sul nome del file, oppure sul seguente collegamento [CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip). Per istruzioni su come applicare la patch, vedere [Come applicare una patch del compositore fornita da Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.

1. Ora esegui lo script per pulire il database dai tentativi di accesso non riusciti preesistenti. Questo script è allegato all’articolo. Per scaricarlo, scorrere verso il basso fino alla fine dell&#39;articolo e fare clic sul nome del file oppure sul seguente collegamento [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip).

Fare riferimento alla sezione [**Come eseguire lo script**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) per le istruzioni.

**Adobe Commerce e Magento Open Source versioni 2.3.3 e successive/2.2.10 e successive**<br>
Solo per queste versioni, esegui lo script seguente per cancellare i vecchi registri (la registrazione è stata terminata in precedenza per queste versioni tramite una correzione rilasciata a ottobre 2019). Questo script è allegato all’articolo. Per scaricarlo, scorrere verso il basso fino alla fine dell&#39;articolo e fare clic sul nome del file oppure sul seguente collegamento [DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip).

Per istruzioni, fare riferimento alla sezione [**Come eseguire lo script**](/help/troubleshooting/known-issues-patches-attached/remove-failed-login-attempts-from-the-database.md#run_script) nella Knowledge Base di supporto.

**Come eseguire lo script**

Per eseguire lo script, attenersi alle istruzioni riportate di seguito.

1. Posiziona `DB_CLEANUP_SCRIPT_v2.php` nella directory principale dell&#39;installazione di Adobe Commerce o di Magento Open Source (nella stessa directory dell&#39;app che contiene `app/bootstrap.php`).
1. Eseguire questo comando nel terminale `php DB_CLEANUP_SCRIPT_v2.php`. Verrà avviato il processo di pulizia del database.

Se riscontri problemi durante l&#39;esecuzione dello script, [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) o inviaci un&#39;e-mail all&#39;indirizzo [security@magento.com](mailto:security@magento.com).

**File allegati**

[CLEANUP\_PATCH\_COMPOSER\_2.3.2.patch](assets/CLEANUP_PATCH_COMPOSER_2.3.2.patch.zip)

[DB\_CLEANUP\_SCRIPT\_v2.php](assets/DB_CLEANUP_SCRIPT_v2.php.zip)
