---
title: Il pannello di navigazione superiore non si carica nella vetrina
description: Questo articolo fornisce soluzioni di configurazione per i problemi ESI (Varnish Edge Side Includes), in cui il contenuto di determinate pagine, in genere il pannello di navigazione superiore, non viene visualizzato nella vetrina se si utilizza Varnish per la memorizzazione in cache.
exl-id: e7f9b773-1a2d-4c3b-9e1f-a1781fbc898c
feature: Categories, Site Navigation, Storefront, Variables
role: Admin
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# Il pannello di navigazione superiore non si carica nella vetrina

Questo articolo fornisce soluzioni di configurazione per i problemi ESI (Varnish Edge Side Includes), in cui il contenuto di determinate pagine, in genere il pannello di navigazione superiore, non viene visualizzato nella vetrina se si utilizza Varnish per la memorizzazione in cache.

## Prodotti e versioni interessati

* Adobe Commerce 2.X.X
* Tutte le versioni di vernice

## Problema

<u>Prerequisiti</u>:

Installa e configura la vernice per il tuo store Adobe Commerce.

<u>Passaggi da riprodurre</u>:

1. Vai alla vetrina.
1. Sfoglia le pagine del Negozio.

<u>Risultati previsti</u>:

Tutto il contenuto e tutti i blocchi di pagina vengono caricati correttamente.

<u>Risultati effettivi</u>:

Tieni presente che alcuni blocchi di contenuto, come il pannello di navigazione superiore con categorie, non vengono caricati. Viene invece visualizzato uno spazio vuoto.

## Causa

I possibili motivi del problema sono i seguenti:

* I tag ESI includono vengono generati con il protocollo di accesso HTTPS, mentre Varish funziona solo con HTTP.
* La vernice non elabora ESI in JSON.
* Le intestazioni di risposta sono troppo grandi per Vernice e non possono essere elaborate.

## Soluzione

Per risolvere i problemi, è necessario eseguire una configurazione aggiuntiva di Vernice e riavviare Vernice.

1. In qualità di utente con privilegi di `root`, apri il file di configurazione Vanish in un editor di testo. Per informazioni sulla posizione del file per sistemi operativi diversi, vedere [Modificare la configurazione del sistema di Microsoft ](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/config-varnish-server) nella documentazione per gli sviluppatori.
1. In `DAEMON_OPTS variable`, aggiungere `-p feature=+esi_ignore_https`, `-p  feature=+esi_ignore_other_elements`, `-p  feature=+esi_disable_xml_check`. Questo dovrebbe essere:

   ```bash
   DAEMON_OPTS="-a :6081 \    -p feature=+esi_ignore_other_elements \    -p feature=+esi_disable_xml_check \    -p feature=+esi_ignore_https \    -T localhost:6082 \    -f /etc/varnish/default.vcl \    -S /etc/varnish/secret \    -s malloc,256m"
   ```

1. Salva le modifiche e esci dall’editor di testo.
1. Nel file di configurazione VCL, aumentare le intestazioni di risposta aumentando i valori di questi parametri: `http_resp_hdr_len`, `http_resp_size`, `workspace_backend`. Assicurati che gli ultimi due abbiano valori simili.
1. Quando si modifica questa impostazione, è necessario eseguire `service varnish restart` per rendere effettive le modifiche.

## Lettura correlata

* [Configura Microsoft e il tuo server Web](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/cache/config-varnish-server) nella documentazione per gli sviluppatori.
* [Documentazione vernice](https://varnish-cache.org/docs/5.1/reference/index.html)
