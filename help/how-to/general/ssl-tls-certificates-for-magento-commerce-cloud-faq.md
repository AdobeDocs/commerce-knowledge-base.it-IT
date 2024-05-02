---
title: Certificati SSL (TLS) per Adobe Commerce sull’infrastruttura cloud
description: Questo articolo fornisce risposte rapide alle domande su come ottenere certificati SSL (TLS) per il tuo sito Adobe Commerce nell’infrastruttura cloud.
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: 43c3e5f95c4b54e235140cd5b3978d3887af5ee1
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# Certificati SSL (TLS) per Adobe Commerce sull’infrastruttura cloud

Questo articolo fornisce risposte rapide alle domande su come ottenere certificati SSL (TLS) per il tuo sito Adobe Commerce nell’infrastruttura cloud.

## Quale certificato SSL/TLS fornisce Adobe?

L&#39;Adobe fornisce un [Crittografiamo il certificato SSL/TLS](https://letsencrypt.org/) per distribuire traffico HTTPS protetto da [!DNL Fastly]. Adobe fornisce un certificato per ogni ambiente Adobe Commerce su infrastruttura cloud Architettura del piano Pro, Staging e Adobe Commerce su infrastruttura cloud Ambiente di pianificazione iniziale per proteggere tutti i domini in tale ambiente.

## Che cosa comprende un certificato?

Per l’architettura del piano Pro, sia gli ambienti dedicati alla gestione temporanea che quelli dedicati alla produzione avranno un certificato SSL creato. Ogni ambiente dedicato al di fuori degli ambienti di integrazione Platform-as-a-Service (PaaS) disporrà di questo certificato per gli URL assegnati a tale ambiente.

Per l’architettura del piano Starter e gli ambienti di integrazione PaaS, sarà presente un dominio tecnico predefinito fornito con l’ambiente e protetto da un certificato separato.

## Come aggiungere un nuovo dominio per il certificato esistente?

Per aggiungere il dominio al servizio in [!DNL Fastly]:

1. Puntare il dominio in DNS a prod.magentocloud.map.fastly.net e attendere fino a 6 ore.
1. [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) richiesta di aggiunta di questo dominio alla configurazione Nginx (se non l’hai già fatto in precedenza).

## Come si richiede un certificato?

Caso 1

Se non hai ancora avviato un sito Web, potresti aver ricevuto il CNAME per la richiesta di verifica ACME dal tuo consulente tecnico clienti (CTA). È necessaria una richiesta ACME solo se non è possibile indirizzare immediatamente il DNS all’URL di produzione e ottenere i certificati SSL creati in anticipo.

Caso 2

Se il sito è già attivo e/o puoi puntare immediatamente agli URL che verranno utilizzati per il sito live, non è necessario richiedere un CNAME ACME. Dopo aver aggiunto gli URL necessari al sito Adobe Commerce sull’infrastruttura cloud e aver indirizzato il DNS all’indirizzo [!DNL Fastly], la convalida HTTP funzionerà e creerà il certificato SSL per la prima volta oppure aggiornerà il certificato con URL aggiuntivi.

## Posso usare un mio certificato SSL/TLS?

Puoi fornire un certificato SSL/TLS personalizzato invece di utilizzare [Crittografiamo il certificato](https://letsencrypt.org/) fornite dall’Adobe.

Tuttavia, questo processo richiede un lavoro aggiuntivo per l&#39;impostazione e la manutenzione. Devi innanzitutto generare una richiesta di firma del certificato (CSR, Certificate Signing Request) per il nome di dominio (o nome comune) del sito web e fornirla al fornitore SSL per fornire un certificato SSL.

Una volta ottenuto il certificato SSL, invia una [Ticket di supporto Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) oppure utilizza il tuo CTA per aggiungere certificati con hosting personalizzato agli ambienti cloud.

* Se i domini non sono più in uso, verranno eliminati automaticamente dal nostro sistema e non sono necessarie ulteriori azioni.
* Se possiedi già un certificato, caricalo utilizzando un client SFTP (SSH File Transfer Protocol) in un percorso di file inaccessibile al web sul server e [invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket) per comunicare il percorso del file.

>[!WARNING]
>
>È importante che non carichi i file del certificato direttamente nel ticket. In caso contrario, i certificati verranno considerati compromessi e Adobe dovrà richiedere un nuovo certificato.
>I file devono essere caricati sul server tramite SFTP; non utilizzare altri metodi, come il commit dei file nell’archivio (operazione che deve essere eseguita solo per file immutabili che non contengono dati sensibili).

## Nome del certificato

Il nome del certificato SSL è rilevante solo per l’URL principale, è il nome host principale denominato dal primo URL e deve corrispondere per essere convalidato e creato. Se disponi di alcuni URL, questi verranno aggiunti al certificato come voci di nome alternativo soggette. Se disponi di più URL che puntano a un Adobe Commerce sul sito dell’infrastruttura cloud, avrai una sola certificazione URL con nome comune e aggiungerai nomi alternativi dei soggetti per proteggere il tuo sito con SSL.

## Quale dominio verrà visualizzato nel campo Nome comune del certificato?

Il dominio visualizzato sul certificato è solo il primo dominio aggiunto al certificato TLS, popola il **Nome comune** (**CN**) e i browser visualizzano prima questo nome. Il **Nome alternativo soggetto** (**SAN**) contiene tutti i nomi DNS per il certificato TLS. Non è possibile modificare o richiedere il Nome comune visualizzato.

## Posso utilizzare certificati TLS con caratteri jolly?

I certificati TLS con caratteri jolly possono essere utilizzati solo con il certificato personalizzato e non con i certificati Adobe Commerce Let&#39;s Encrypt. Come parte dell’ottimizzazione TLS, Adobe sta cessando il supporto dei certificati TLS con caratteri jolly. Stiamo identificando e contattando i commercianti che utilizzano un certificato con caratteri jolly con i certificati Let&#39;s Encrypt di Adobe e che sono configurati in [!DNL Fastly] per Adobe Commerce. Stiamo chiedendo che questi certificati con caratteri jolly vengano sostituiti con domini esatti per garantire la copertura TLS. Per sostituire un certificato TLS con caratteri jolly, visita la [sezione dominio](https://devdocs.magento.com/cloud/cdn/configure-fastly-customize-cache.html#manage-domains) del [!DNL Fastly] plugin. Da qui è possibile aggiungere domini esatti e rimuovere il carattere jolly. Si noti che il DNS dovrà puntare a [!DNL Fastly] per indirizzare questi nuovi domini attraverso la rete CDN. Dopo l’aggiunta dei domini e l’aggiornamento del DNS, viene creata una [Crittografiamo](https://letsencrypt.org/) verrà eseguito il provisioning del certificato. Se non rimuovi un dominio che punta a [!DNL Fastly] utilizzando un carattere jolly, Adobe eliminerà il certificato condiviso. Questo può causare un’interruzione del sito se non hai configurato l’FQDN dell’URL e lo stesso FQDN dell’URL nel DNS. Devi quindi confermare che anche gli URL configurati abbiano una corrispondenza uno-a-uno nel proprio DNS che punta a [!DNL Fastly].

## Cosa devo fare se il mio dominio non punta più ad Adobe Commerce?

Se il dominio non fa più riferimento a Adobe Commerce, rimuovilo da [!DNL Fastly]/Adobe Commerce. Consulta [!DNL Fastly] [Eliminazione di un dominio](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain) per ulteriori informazioni. Anche se non è necessario puntare il dominio ad Adobe Commerce, verifica se è necessario un certificato TLS di dominio di livello superiore. Se è necessario un dominio di primo livello, aggiorna il DNS in modo che punti ad Adobe Commerce. Se fa già riferimento ad Adobe Commerce, aggiorna il record CAA in modo da includere [let-encrypt](https://letsencrypt.org/). Se esegui questi passaggi, vedrai il certificato LE aggiornato con gli URL secondari necessari coperti dal certificato&#x200B;.

## Lettura correlata

[Provisioning dei certificati SSL/TLS](https://devdocs.magento.com/cloud/cdn/configure-fastly.html#provision-ssltls-certificates) nella documentazione per gli sviluppatori
