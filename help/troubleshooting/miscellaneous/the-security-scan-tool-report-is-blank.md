---
title: Il report dello strumento Security Scan è vuoto
description: Questo articolo corregge il problema relativo alla visualizzazione di una pagina vuota al posto del rapporto effettivo da parte dello strumento Security Scan. Per risolvere il problema, potrebbe essere necessario aggiungere gli IP utilizzati dallo strumento all’Elenco Consentiti del firewall
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%
---
# Il report dello strumento Security Scan è vuoto

Questo articolo corregge il problema relativo alla visualizzazione di una pagina vuota al posto del rapporto effettivo da parte dello strumento Security Scan. Per risolvere il problema, potrebbe essere necessario aggiungere gli IP utilizzati dallo strumento all’Elenco Consentiti del firewall

## Prodotti e versioni interessati:

* Adobe Commerce (tutti i metodi di distribuzione) e Magento Open Source, Tutte le versioni

## Problema

<u>Passaggi da riprodurre</u>:

1. Configurare lo strumento Security Scan per controllare il sito Web, come descritto in [Security Scan](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/security/security-scan) nella guida utente.
1. Nella colonna Azioni selezionare **Esegui analisi**.

<u>Risultati previsti</u>:

Visualizza la notifica di completamento del rapporto e la possibilità di aprirlo.

<u>Risultati effettivi</u>:

Nessuna notifica e nessun rapporto disponibile.

## Causa

È possibile che il problema si verifichi perché lo strumento Security Scan non è riuscito a raggiungere il sito Web. Ciò significa che il sito Web non è accessibile o che lo strumento Security Scan è bloccato.

## Soluzione

Prova ad aprire il tuo sito web.

* Se la pagina viene caricata correttamente, potrebbe essere necessario aggiungere gli IP utilizzati dagli strumenti Security Scan Tools al Inserisco nell&#39;elenco Consentiti di analisi del firewall. Sono utilizzati i seguenti IP: 52.87.98.44, 34.196.167.176, 3.218.25.102 alle porte 80 e 443.
* Se il sito non viene caricato e restituisce il messaggio *&quot;Si è verificato un errore durante l&#39;elaborazione della richiesta&quot;*, controllare il sito Web per individuare eventuali errori.

## Lettura correlata

* [Pubblica e avvia](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/launch/overview) nella documentazione per gli sviluppatori.
* [Analisi protezione](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/security/security-scan) nella guida utente.
