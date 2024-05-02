---
title: Reindirizza HTTP a HTTPS per tutte le pagine su Adobe Commerce nell’infrastruttura cloud (Forza TLS)
description: Attiva la funzionalità **Force TLS** di Fastly nell’amministratore di Commerce per abilitare il reindirizzamento globale da HTTP a HTTPS per tutte le pagine dell’Adobe Commerce nell’archivio dell’infrastruttura cloud.
exl-id: 71667f52-a99a-47a6-99d8-10532364870f
feature: Cache, Cloud
source-git-commit: f11c8944b83e294b61d9547aefc9203af344041d
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# Reindirizza HTTP a HTTPS per tutte le pagine su Adobe Commerce nell’infrastruttura cloud (Forza TLS)

Attiva la Fastly **Forza TLS** nell’amministratore di Commerce per abilitare il reindirizzamento globale da HTTP a HTTPS per tutte le pagine dell’archivio Adobe Commerce nell’infrastruttura cloud.

Questo articolo fornisce informazioni dettagliate [passaggi](#steps): panoramica rapida della funzione Force TLS (Forza TLS), versioni interessate e collegamenti alla relativa documentazione.

## Passaggi {#steps}

### Passaggio 1: configurare URL protetti {#step-1-configure-secure-urls}

In questo passaggio definiamo gli URL sicuri per l’archivio. Se è già stato fatto, vai a [Passaggio 2: abilitare Force TLS (Forza TLS)](#step-2-enable-force-tls).

1. Accedi all’amministratore di Commerce.
1. Accedi a **Negozi** > **Configurazione** > **Generale** > **Web**.
1. Espandi **URL di base (protetto)** sezione.    ![magento-admin_base-urls-secure.png](assets/magento-admin_base-urls-secure.png)
1. In **URL di base sicuro** , specifica l&#39;URL HTTPS dello store.
1. Imposta il **Usa URL protetti in Storefront** e **Utilizzare URL protetti in Admin** impostazioni per **Sì**.    ![magento-admin_base-urls-secure-settings.png](assets/magento-admin_base-urls-secure-settings.png)
1. Clic **Salva configurazione** nell’angolo in alto a destra per applicare le modifiche.

**Documentazione correlata nella nostra guida utente:**   [URL store](https://docs.magento.com/m2/ee/user_guide/stores/store-urls.html).

### Passaggio 2: abilitare Force TLS (Forza TLS) {#step-2-enable-force-tls}

1. In Amministrazione Commerce, passa a **Negozi** > **Configurazione** > **Avanzate** > **Sistema**.
1. Espandi **Cache a pagina intera** , quindi **Configurazione rapida**, quindi **Configurazione avanzata**.
1. Fai clic su **Forza TLS** pulsante.    ![magento-admin_force-tls-button.png](assets/magento-admin_force-tls-button.png)
1. Nella finestra di dialogo visualizzata, fai clic su **Carica**.    ![magento-admin_force-tls-confirm-dialog.png](assets/magento-admin_force-tls-confirmation-dialog.png)
1. Dopo aver chiuso la finestra di dialogo, accertati che lo stato corrente di Force TLS sia visualizzato come **abilitato**.    ![magento-admin_force-tls-enabled.png](assets/magento-admin_force-tls-enabled.png)

**Documentazione Fastly correlata:**   [Forza guida TLS](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md) per Adobe Commerce 2.

## Info Forza TLS

TLS (Transport Layer Security) è un protocollo per connessioni HTTP sicure che sostituisce il suo predecessore meno sicuro, il protocollo SSL (Secure Socket Layer).

La funzionalità Force TLS di Fastly consente di forzare a TLS tutte le richieste non crittografate in entrata per le pagine del sito.

>>
Funziona restituendo un *301 Spostato in modo permanente* risposta a qualsiasi richiesta non crittografata, che reindirizza all’equivalente TLS. Ad esempio, effettuando una richiesta per *http://www.example.com/foo.jpeg* reindirizzerebbe a *https://www.example.com/foo.jpeg*.

[Protezione delle comunicazioni](https://docs.fastly.com/guides/securing-communications/) (Documentazione rapida)

## Versioni interessate

* **Adobe Commerce sull’infrastruttura cloud:**
   * versione: 2.1.4 e successive
   * piani: Adobe Commerce su infrastruttura cloud Architettura del piano iniziale e Adobe Commerce su infrastruttura cloud Architettura del piano Pro (inclusa Pro Legacy)
* **In breve:** 1.2.4.

## Nessuna modifica necessaria in route.yaml

Per abilitare il reindirizzamento da HTTP a HTTPS su **tutto** pagine del negozio, non è necessario aggiungere le pagine al `routes.yaml` file di configurazione: è sufficiente abilitare Force TLS globalmente per l’intero archivio (utilizzando Commerce Admin).

## Documentazione Fastly correlata

* [Forza guida TLS per Adobe Commerce 2](https://github.com/fastly/fastly-magento2/blob/master/Documentation/Guides/FORCE-TLS.md)
* [Forzare un reindirizzamento TLS](https://docs.fastly.com/guides/securing-communications/forcing-a-tls-redirect)
* [Protezione delle comunicazioni](https://docs.fastly.com/guides/securing-communications/)
