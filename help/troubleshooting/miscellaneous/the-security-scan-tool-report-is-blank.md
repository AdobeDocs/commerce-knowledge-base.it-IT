---
title: Il report dello strumento Security Scan è vuoto
description: Questo articolo corregge il problema relativo alla visualizzazione di una pagina vuota al posto del rapporto effettivo da parte dello strumento Security Scan. Per risolvere il problema, potrebbe essere necessario aggiungere gli IP utilizzati dallo strumento al Inserisco nell'elenco Consentiti di del firewall.
exl-id: e5f7f8c6-2dd3-44e3-8d19-f1f38d06dd6c
feature: Compliance, Security
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Il report dello strumento Security Scan è vuoto

Questo articolo corregge il problema relativo alla visualizzazione di una pagina vuota al posto del rapporto effettivo da parte dello strumento Security Scan. Per risolvere il problema, potrebbe essere necessario aggiungere gli IP utilizzati dallo strumento al Inserisco nell&#39;elenco Consentiti di del firewall.

## Prodotti e versioni interessati:

* Adobe Commerce (tutti i metodi di distribuzione) e Magento Open Source, Tutte le versioni

## Problema

<u>Passaggi da riprodurre</u>:

1. Configurare lo strumento Security Scan per controllare il sito Web, come descritto in [Security Scan](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) nella guida utente.
1. Nella colonna Azioni selezionare **Esegui analisi**.

<u>Risultati previsti</u>:

Visualizza la notifica di completamento del rapporto e la possibilità di aprirlo.

<u>Risultati effettivi</u>:

Nessuna notifica e nessun rapporto disponibile.

## Causa

È possibile che il problema si verifichi perché lo strumento Security Scan non è riuscito a raggiungere il sito Web. Ciò significa che il sito Web non è accessibile o che lo strumento Security Scan è bloccato.

## Soluzione

Prova ad aprire il tuo sito web.

* Se la pagina viene caricata correttamente, potrebbe essere necessario aggiungere gli IP utilizzati dagli strumenti di analisi della sicurezza al Inserisco nell&#39;elenco Consentiti del firewall. Sono utilizzati i seguenti IP: 52.87.98.44, 34.196.167.176, 3.218.25.102 alle porte 80 e 443.
* Se il sito non viene caricato e restituisce il messaggio *&quot;Si è verificato un errore durante l&#39;elaborazione della richiesta&quot;*, controllare il sito Web per individuare eventuali errori.

## Lettura correlata

* [Pubblica e avvia](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/launch/overview) nella documentazione per gli sviluppatori.
* [Analisi protezione](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/security/security-scan) nella guida utente.
