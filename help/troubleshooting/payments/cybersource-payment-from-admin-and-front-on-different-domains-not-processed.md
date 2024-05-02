---
title: Pagamento cybersource da parte dell’amministratore e front su domini diversi non elaborato
description: Questo articolo fornisce una patch per la limitazione nota di Adobe Commerce 2.3.0 correlata all’impossibilità di elaborare i pagamenti Cybersource sia da storefront che dall’amministratore Commerce, se si trovano su domini diversi.
exl-id: 948d5907-70bd-4890-bc8a-23e04b116018
feature: Admin Workspace, Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Pagamento cybersource da parte dell’amministratore e front su domini diversi non elaborato

Questo articolo fornisce una patch per la limitazione nota di Adobe Commerce 2.3.0 correlata all’impossibilità di elaborare i pagamenti Cybersource sia da storefront che dall’amministratore Commerce, se si trovano su domini diversi.

>[!NOTE]
>
>L’integrazione del pagamento core Adobe Commerce Cybersource è obsoleta a partire dalla versione 2.3.3 e verrà completamente rimossa nella versione 2.4.0. Utilizza il [estensione ufficiale](https://marketplace.magento.com/cybersource-global-payment-management.html) dal marketplace.

## Problema

La precedente implementazione dell’integrazione di Cybersource consentiva l’elaborazione di pagamenti da un solo dominio. Di conseguenza, se la vetrina Adobe Commerce si trova su un dominio diverso da quello dell’amministratore Commerce, viene visualizzato il seguente errore quando si tenta di effettuare un ordine utilizzando Cybersource nell’amministratore: &quot; *Caricamento negato da X-Frame-Options: https://%your\_domain%/cybersource/SilentOrder/TokenResponse/ non consente il frame tra origini.* ...&quot;

<u>Passaggi da riprodurre</u>:

1. Imposta l’amministratore su un sottodominio diverso.
1. Configurare Cybersource per lo store in **Negozi** > Impostazioni > **Configurazione** > **Vendite** > **Metodi di pagamento** > **CyberSource**.
1. Vai a **Vendite** > **Ordini**.
1. Crea nuovo ordine.
1. Crea nuovo cliente.
1. Immettere i dettagli del cliente.
1. Inserire i dettagli dell&#39;ordine (prodotti, metodo di spedizione).
1. Seleziona Cybersource come metodo di pagamento.
1. Invia ordine.

<u>Risultato previsto</u>: l’ordine viene effettuato senza problemi.

<u>Risultato effettivo</u>: la pagina Ordine mostra un’icona di caricamento, ma l’ordine non viene mai effettuato. L’errore viene visualizzato nella console.

## Soluzione

La patch allegata fornisce il miglioramento per l’integrazione con Cybersource. Dopo aver applicato la patch, devi creare un altro profilo con Cybersource per l’elaborazione dei pagamenti in Admin (Amministrazione) e aggiungere le credenziali richieste nella configurazione Cybersource in Commerce Admin (Amministrazione) in **Negozi** > Impostazioni > **Configurazione** > **Vendite** > **Metodi di pagamento** > **CyberSource**.

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

Per istruzioni, consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella nostra knowledge base di supporto.

## File allegati
