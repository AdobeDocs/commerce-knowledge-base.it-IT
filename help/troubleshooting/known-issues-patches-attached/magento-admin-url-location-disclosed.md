---
title: È stata comunicata la posizione dell’URL dell’amministratore Adobe Commerce
description: Questo articolo fornisce una patch per il problema di sicurezza di Adobe Commerce in cui è possibile divulgare la posizione URL del pannello di amministrazione. Conoscere la posizione dell’URL potrebbe semplificare l’automazione degli attacchi.
exl-id: fe147ad5-6019-46c1-b48c-6b957b6e1582
feature: Admin Workspace
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# È stata comunicata la posizione dell’URL dell’amministratore Adobe Commerce

Questo articolo fornisce una patch per il problema di sicurezza di Adobe Commerce in cui è possibile divulgare la posizione URL del pannello di amministrazione. Conoscere la posizione dell’URL potrebbe semplificare l’automazione degli attacchi.

## Prodotti e versioni interessati

* Adobe Commerce sull’infrastruttura cloud 2.X.X
* Adobe Commerce on-premise 2.X.X
* Magento Open Source 2.X.X

## Problema

È stato rilevato un problema in Magento Open Source e Adobe Commerce che può essere utilizzato per divulgare la posizione dell’URL del pannello di amministrazione. Anche se al momento non c’è motivo di credere che questo problema possa portare direttamente a un compromesso, conoscere la posizione dell’URL potrebbe semplificare l’automazione degli attacchi.

## Soluzione

Per risolvere il problema, applica la patch allegata a questo articolo. Per scaricarlo, fai clic sul seguente collegamento:

* Scarica [PRODSECBUG-2432\_EE\_2.1.17\_compositore.patch](assets/PRODSECBUG-2432_EE_2.1.17_composer.patch.zip) - per le versioni 2.1.13-2.1.17, Adobe Commerce, Magento Open Source
* Scarica [PRODSECBUG-2432\_EE\_2.2.8\_compositore.patch](assets/PRODSECBUG-2432_EE_2.2.8_composer.patch.zip) - per le versioni 2.2.0-2.2.8, tutte le edizioni
* Scarica [PRODSECBUG-2432\_EE\_2.3.1\_compositore.patch](assets/PRODSECBUG-2432_EE_2.3.1_composer.patch.zip) - per le versioni 2.3.0-2.3.1, tutte le edizioni

Se non viene visualizzata una patch per il prodotto o la versione, eseguire l&#39;aggiornamento all&#39;ultima versione di sicurezza, quindi applicare la patch.

Adobe consiglia vivamente di applicare il cerotto il prima possibile, anche se non ha manifestato alcun sintomo di attacco.

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita da Adobe Commerce](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md).

## Altre raccomandazioni per la sicurezza

Adobe consiglia inoltre vivamente ai commercianti di implementare strumenti per proteggere il pannello di amministrazione, tra cui autenticazione a due fattori, VPN, Inserisce nell&#39;elenco Consentiti di IP e altro ancora. Per informazioni dettagliate, consulta i seguenti blog e documentazione:

* [5 Azioni immediate per Protect contro attacchi di forza bruta](https://magento.com/security/best-practices/5-immediate-actions-protect-against-brute-force-attacks)
* [Protect La Password Di Installazione Del Magento Sta Cercando Un Nuovo Aggiornamento](https://magento.com/security/best-practices/protect-your-magento-installation-password-guessing-new-update)
* [Best practice per la sicurezza](https://magento.com/security/best-practices/security-best-practices)
* Aggiunta e configurazione dell&#39;autenticazione a due fattori in Adobe Commerce per [2.4.x](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/2fa/security-two-factor-authentication)
