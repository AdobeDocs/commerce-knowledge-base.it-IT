---
title: Certificati SSL (TLS) per Adobe Commerce sull’infrastruttura cloud
description: Questo articolo fornisce risposte rapide alle domande su come ottenere certificati SSL (TLS) per il tuo sito Adobe Commerce nell’infrastruttura cloud.
exl-id: 5a682d07-e4d7-4e81-a2ad-3232f2d8d9c1
feature: Cloud, Console
source-git-commit: da2df5fc4ab6cc10d86af806045ee884b01f291d
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 0%

---

# Certificati SSL (TLS) per Adobe Commerce sull’infrastruttura cloud

Questo articolo fornisce risposte rapide alle domande su come ottenere certificati SSL (TLS) per il tuo sito Adobe Commerce nell’infrastruttura cloud.

## Quale certificato SSL/TLS fornisce Adobe?

Adobe fornisce un [Crittografiamo il certificato SSL/TLS](https://letsencrypt.org/) convalidato dal dominio per gestire il traffico HTTPS protetto da [!DNL Fastly]. Adobe fornisce un certificato per ogni ambiente Adobe Commerce su infrastruttura cloud Architettura del piano Pro, Staging e Adobe Commerce su infrastruttura cloud Ambiente di pianificazione iniziale per proteggere tutti i domini in tale ambiente.

## Che cosa comprende un certificato?

Per l’architettura del piano Pro, sia gli ambienti dedicati alla gestione temporanea che quelli dedicati alla produzione avranno un certificato SSL creato. Ogni ambiente dedicato al di fuori degli ambienti di integrazione Platform-as-a-Service (PaaS) disporrà di questo certificato per gli URL assegnati a tale ambiente.

Per l’architettura del piano Starter e gli ambienti di integrazione PaaS, sarà presente un dominio tecnico predefinito fornito con l’ambiente e protetto da un certificato separato.

## Come aggiungere un nuovo dominio per il certificato esistente?

Per aggiungere il dominio al servizio in [!DNL Fastly]:

1. Puntare il dominio in DNS a prod.magentocloud.map.fastly.net e attendere fino a 6 ore.
1. [Invia un ticket di supporto](https://experienceleague.adobe.com/it/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) richiedendo di aggiungere questo dominio nella configurazione Nginx (se non l&#39;hai già fatto in precedenza).

## Come si richiede un certificato?

Caso 1

Se non hai ancora avviato un sito Web, potresti aver ricevuto il CNAME per la richiesta di verifica ACME dal tuo consulente tecnico clienti (CTA). È necessaria una richiesta ACME solo se non è possibile indirizzare immediatamente il DNS all’URL di produzione e ottenere i certificati SSL creati in anticipo.

Caso 2

Se il sito è già attivo e/o puoi puntare immediatamente agli URL che verranno utilizzati per il sito live, non è necessario richiedere un CNAME ACME. Dopo aver aggiunto gli URL necessari al sito Adobe Commerce sull&#39;infrastruttura cloud e aver puntato il DNS su [!DNL Fastly], la convalida HTTP funzionerà e creerà il certificato SSL per la prima volta oppure aggiornerà il certificato con URL aggiuntivi.

## Posso usare un mio certificato SSL/TLS?

È possibile fornire un proprio certificato SSL/TLS invece di utilizzare il [Crittografiamo il certificato](https://letsencrypt.org/) fornito da Adobe.

Tuttavia, questo processo richiede un lavoro aggiuntivo per l&#39;impostazione e la manutenzione. Devi innanzitutto generare una richiesta di firma del certificato (CSR, Certificate Signing Request) per il nome di dominio (o nome comune) del sito web e fornirla al fornitore SSL per fornire un certificato SSL.

Una volta ottenuto il certificato SSL, invia un [ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/it/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) o collabora con il tuo CTA per aggiungere certificati con hosting personalizzato agli ambienti cloud.

* Se i domini non sono più in uso, verranno eliminati automaticamente dal nostro sistema e non sono necessarie ulteriori azioni.
* Se possiedi già un certificato, caricalo utilizzando un client SFTP (SSH File Transfer Protocol) in un percorso di file inaccessibile al Web sul tuo server e [invia un ticket di supporto](https://experienceleague.adobe.com/it/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket) per comunicare al cliente il percorso del file.

>[!WARNING]
>
>È importante che non carichi i file del certificato direttamente nel ticket. In caso contrario, i certificati verranno considerati compromessi e Adobe dovrà richiedere un nuovo certificato.
>I file devono essere caricati tramite SFTP sul server in una cartella di tua scelta, ad esempio `var/ssl`, `/tmp/ssl`, ecc. : non utilizzare altri metodi, come il commit dei file nell’archivio (operazione da eseguire solo per file immutabili che non contengono dati sensibili).

## Nome del certificato

Il nome del certificato SSL è rilevante solo per l’URL principale, è il nome host principale denominato dal primo URL e deve corrispondere per essere convalidato e creato. Se disponi di alcuni URL, questi verranno aggiunti al certificato come voci di nome alternativo soggette. Se disponi di più URL che puntano a un Adobe Commerce sul sito dell’infrastruttura cloud, avrai una sola certificazione URL con nome comune e aggiungerai nomi alternativi dei soggetti per proteggere il tuo sito con SSL.

## Quale dominio verrà visualizzato nel campo Nome comune del certificato?

Il dominio visualizzato nel certificato è solo il primo dominio aggiunto al certificato TLS, popola il campo **Nome comune** (**CN**) e i browser visualizzano prima questo nome. Il campo **Nome alternativo soggetto** (**SAN**) contiene tutti i nomi DNS per il certificato TLS. Non è possibile modificare o richiedere il Nome comune visualizzato.

## Posso utilizzare certificati TLS con caratteri jolly?

I certificati TLS con caratteri jolly possono essere utilizzati solo con il certificato personalizzato e non con i certificati Adobe Commerce Let&#39;s Encrypt. Come parte dell’ottimizzazione di TLS, Adobe cesserà il supporto per i certificati TLS con caratteri jolly. Stiamo identificando e contattando i commercianti che utilizzano un certificato con caratteri jolly con i certificati Let&#39;s Encrypt di Adobe e che sono configurati nella console [!DNL Fastly] per Adobe Commerce. Stiamo chiedendo che questi certificati con caratteri jolly vengano sostituiti con domini esatti per garantire la copertura TLS. Per sostituire un certificato TLS con caratteri jolly, visita la [sezione dominio](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-custom-cache-configuration#manage-domains) del plug-in [!DNL Fastly]. Da qui è possibile aggiungere domini esatti e rimuovere il carattere jolly. Nota che il DNS dovrà puntare a [!DNL Fastly] affinché questi nuovi domini vengano instradati attraverso la rete CDN. Una volta aggiunti i domini e aggiornato il DNS, verrà eseguito il provisioning di un certificato [Crittografiamo](https://letsencrypt.org/) corrispondente. Se non rimuovi un dominio che punta a [!DNL Fastly] utilizzando un carattere jolly, Adobe eliminerà il certificato condiviso. Questo può causare un’interruzione del sito se non hai configurato l’FQDN dell’URL e lo stesso FQDN dell’URL nel DNS. È quindi necessario confermare che anche gli URL configurati hanno una corrispondenza uno-a-uno nel DNS che punta a [!DNL Fastly].

## Cosa devo fare se il mio dominio non punta più ad Adobe Commerce?

Se il dominio non fa più riferimento a Adobe Commerce, rimuoverlo dal sistema di [!DNL Fastly]/Adobe Commerce. Per ulteriori informazioni, vedere [!DNL Fastly] [Eliminazione di un dominio](https://docs.fastly.com/en/guides/working-with-domains#deleting-a-domain). Anche se non è necessario puntare il dominio ad Adobe Commerce, verifica se è necessario un certificato TLS di dominio di livello superiore. Se è necessario un dominio di primo livello, aggiorna il DNS in modo che punti ad Adobe Commerce. Se fa già riferimento ad Adobe Commerce, aggiorna il record CAA per includere [lets-encrypt](https://letsencrypt.org/). Se esegui questi passaggi, vedrai il certificato LE aggiornato con gli URL secondari necessari coperti dal certificato&#x200B;.

## Lettura correlata

[Fornire certificati SSL/TLS](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration#provision-ssltls-certificates) nella documentazione per gli sviluppatori
