---
title: Pagamento cybersource da parte dell’amministratore e front su domini diversi non elaborato
description: Questo articolo fornisce una patch per la limitazione nota di Adobe Commerce 2.3.0 correlata all’impossibilità di elaborare i pagamenti Cybersource sia da storefront che dall’amministratore Commerce, se si trovano su domini diversi.
exl-id: 948d5907-70bd-4890-bc8a-23e04b116018
feature: Admin Workspace, Orders, Payments
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '579'
ht-degree: 0%
---
# Pagamento cybersource da parte dell’amministratore e front su domini diversi non elaborato

Questo articolo fornisce una patch per la limitazione nota di Adobe Commerce 2.3.0 correlata all’impossibilità di elaborare i pagamenti Cybersource sia da storefront che dall’amministratore Commerce, se si trovano su domini diversi.

>[!NOTE]
>
>L’integrazione del pagamento core Adobe Commerce Cybersource è obsoleta a partire dalla versione 2.3.3 e verrà completamente rimossa nella versione 2.4.0. Utilizza invece l&#39;[estensione ufficiale](https://marketplace.magento.com/cybersource-global-payment-management.html) da Marketplace.

## Problema

La precedente implementazione dell’integrazione di Cybersource consentiva l’elaborazione di pagamenti da un solo dominio. Di conseguenza, se la vetrina Adobe Commerce si trova su un dominio diverso da quello dell&#39;amministratore Commerce, viene visualizzato il seguente errore quando si tenta di effettuare un ordine utilizzando Cybersource nell&#39;amministratore: &quot; *Caricamento negato da X-Frame-Options: https://%your\_domain%/cybersource/SilentOrder/TokenResponse/ non consente il frame tra origini.* ..&quot;

<u>Passaggi da riprodurre</u>:

1. Imposta l’amministratore su un sottodominio diverso.
1. Configura Cybersource per l&#39;archivio in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Metodi di pagamento** > **CyberSource**.
1. Vai a **Vendite** > **Ordini**.
1. Crea nuovo ordine.
1. Crea nuovo cliente.
1. Immettere i dettagli del cliente.
1. Inserire i dettagli dell&#39;ordine (prodotti, metodo di spedizione).
1. Seleziona Cybersource come metodo di pagamento.
1. Invia ordine.

<u>Risultato previsto</u>: l&#39;ordine è stato effettuato senza problemi.

<u>Risultato effettivo</u>: nella pagina Ordine viene visualizzata un&#39;icona di caricamento, ma l&#39;ordine non viene mai inserito. L’errore viene visualizzato nella console.

## Soluzione

La patch allegata fornisce il miglioramento per l’integrazione con Cybersource. Dopo aver applicato la patch, è necessario creare un altro profilo con Cybersource per l&#39;elaborazione dei pagamenti in Admin e aggiungere le credenziali richieste nella configurazione Cybersource in Commerce Admin in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Metodi di pagamento** > **CyberSource**.

>[!NOTE]
>
>Questo miglioramento è incluso nelle infrastrutture Adobe Commerce on-premise e cloud 2.2.9 e 2.3.1.

## Patch

A questo articolo sono allegate diverse patch, diverse patch per versioni diverse. Per scaricare una patch, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

* [Scarica MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch](assets/MDVA-5914_EE_2.1.9_COMPOSER_v3.patch.zip)
* [Scarica MDVA-8609\_EE\_2.2\_COMPOSER\_v2.patch](assets/MDVA-8609_EE_2.2.2_COMPOSER_v2.patch.zip)
* [Scarica MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch](assets/MDVA-12964_EE_2.2.5_COMPOSER_v1.patch.zip)
* [Scarica MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch](assets/MDVA-16643_EE_2.3.0_COMPOSER_v1.patch.zip)

## Versioni compatibili di Adobe Commerce

Le patch sono state create per una particolare versione indicata nel nome del file di patch. MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch è stato creato per Adobe Commerce 2.1.9 ed è la patch migliore da utilizzare per questa versione.

Le patch sono compatibili anche con le seguenti versioni:

* Adobe Commerce on-premise 2.1.3-2.1.17; Adobe Commerce on cloud infrastructure 2.1.5-2.12 (MDVA-5914\_EE\_2.1.9\_COMPOSER\_v3.patch)
* Adobe Commerce on-premise 2.2.0-2.2.3; Adobe Commerce on cloud infrastructure 2.2.0-2.2.3 (MDVA-8609\_EE\_2.2\_COMPOSER\_v2.patch)
* Adobe Commerce on-premise 2.2.4-2.2.7; Adobe Commerce on cloud infrastructure 2.2.4-2.2.7 (MDVA-12964\_EE\_2.2.5\_COMPOSER\_v1.patch)
* Adobe Commerce on-premise 2.2.8, 2.3.0; Adobe Commerce on cloud infrastructure 2.3.0 (MDVA-16643\_EE\_2.3.0\_COMPOSER\_v1.patch)

## Come applicare una patch

Per istruzioni, vedere [Come applicare una patch del compositore fornita da Adobe](https://experienceleague.adobe.com/it/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/how-to-apply-a-composer-patch-provided-by-magento) nella Knowledge Base di supporto.

## File allegati
