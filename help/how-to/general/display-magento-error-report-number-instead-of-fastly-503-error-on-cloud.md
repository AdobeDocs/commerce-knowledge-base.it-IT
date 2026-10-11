---
title: Visualizza il numero della segnalazione errori di Adobe Commerce invece dell’errore Fastly 503
description: 'Per impostazione predefinita, Fastly nasconde tutti gli errori Adobe Commerce dietro l’errore **503 Service Unavailable**. Per visualizzare il numero del rapporto del registro errori di Adobe Commerce (per trovarlo nei registri e visualizzare i dettagli dell’errore), apri il sito web omettendo Fastly seguendo la procedura riportata di seguito:'
exl-id: c0a4a9f8-a674-4cef-8088-e844594e6076
feature: Cache, Cloud
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%
---
# Visualizza il numero della segnalazione errori di Adobe Commerce invece dell’errore Fastly 503

Per impostazione predefinita, Fastly nasconde tutti gli errori Adobe Commerce dietro l&#39;errore **503 Servizio non disponibile**. Per visualizzare il numero del rapporto del registro errori di Adobe Commerce (per trovarlo nei registri e visualizzare i dettagli dell’errore), apri il sito web omettendo Fastly seguendo la procedura riportata di seguito:

1. Aggiungi il dominio e l’indirizzo IP dell’applicazione al file hosts sul computer locale.
1. Cancella la cache del browser e i cookie (o passa alla modalità in incognito).
1. Apri nuovamente il sito web del tuo negozio per visualizzare l’errore Adobe Commerce.

Una volta visualizzato l’errore Adobe Commerce autentico e il numero della segnalazione di errore, puoi ottenere i dettagli nel file della segnalazione di errore seguendo questi passaggi:

1. SSH nell’ambiente interessato. Consulta [SSH in un ambiente](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/secure-connections) nella documentazione per gli sviluppatori.
1. Individuare il file `./var/report/{error_number}`.

## Aggiungi dominio applicazione e indirizzo IP al file host: passaggi dettagliati

1. Controllare l&#39;IP del server dell&#39;archivio eseguendo il comando `nslookup` nella riga di comando del computer locale:
   * Utenti dell’architettura Pro (ambienti di staging e produzione):

   ```
   nslookup {your_project_id}.ent.magento.cloud
   ```

   * Utenti dell’architettura di avvio (tutti gli ambienti); utenti dell’architettura di Pro (ambiente di integrazione):

   ```
   nslookup gw.{your_region}.magentosite.cloud
   ```

1. Aggiungere il dominio di archiviazione e l&#39;IP del server applicazioni al file hosts nel computer locale utilizzando il formato seguente:

```
{server_IP} {store_domain}
```
