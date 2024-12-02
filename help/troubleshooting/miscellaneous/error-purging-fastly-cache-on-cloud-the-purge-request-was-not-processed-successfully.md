---
title: Errore durante l’eliminazione della cache Fastly nel cloud (richiesta di eliminazione non elaborata correttamente)
description: 'Questo articolo corregge l’errore che si verifica quando si utilizza l’opzione Fastly Purge: *La richiesta di eliminazione non è stata elaborata correttamente*. Fastly è un servizio CDN e di caching incluso con Adobe Commerce sui piani e le implementazioni dell’infrastruttura cloud. Se si tenta di utilizzare un’opzione di eliminazione Fastly e questa non viene elaborata, è possibile che nell’ambiente siano presenti credenziali Fastly errate o che si sia verificato un problema.'
exl-id: 568b1f4c-2ccb-4740-a6e4-d227a55fcfe6
feature: Cache, Cloud, Paas
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# Errore durante l’eliminazione della cache Fastly nel cloud (richiesta di eliminazione non elaborata correttamente)

In questo articolo viene fornita una correzione per quando si utilizza un&#39;opzione di eliminazione Fastly e viene visualizzato l&#39;errore: *La richiesta di eliminazione non è stata elaborata correttamente*. Fastly è un servizio CDN e di caching incluso con Adobe Commerce sui piani e le implementazioni dell’infrastruttura cloud. Se si tenta di utilizzare un’opzione di eliminazione Fastly e questa non viene elaborata, è possibile che nell’ambiente siano presenti credenziali Fastly errate o che si sia verificato un problema.

Queste informazioni sono utili per verificare e testare le intestazioni Fastly per il sito live e i server di origine.

## Versioni interessate

* Adobe Commerce su infrastruttura cloud 2.1.X e versioni successive
* 1.2.27 e versioni successive

## Problema

La memorizzazione in cache funziona, ma quando tenti di eliminarla ricevi un errore o non funziona. L’errore include: &quot;La richiesta di eliminazione non è stata elaborata correttamente&quot;.

## Causa

È possibile che nell&#39;ambiente siano impostate credenziali non corrette o che sia necessario caricare snippet VCL.

## Risolvi

### Controlla credenziali Fastly

Verifica di disporre dell’ID Fastly Service e del token API corretti nell’ambiente. Se si dispone di credenziali di staging in produzione, le eliminazioni potrebbero non essere elaborate o elaborate in modo errato.

1. Accedi al tuo amministratore Commerce locale come amministratore.
1. Fai clic su **Archivi** > Impostazioni > **Configurazione** > **Avanzate** > **Sistema** ed espandi **Cache a pagina intera**.    ![magento_full_page_cache_2.4.1.png](assets/magento_full_page_cache_2.4.1.png)
1. Espandi Fastly Configuration e verifica l’ID servizio Fastly e il token API per il tuo ambiente.
1. Se si modificano i valori, fare clic su Verifica credenziali.

### Controlla snippet VCL

Se le credenziali sono corrette, è possibile che si verifichino problemi con le VCL. Per elencare e rivedere i VCL per servizio, inserisci la seguente chiamata API in un terminale:

```
curl -X GET -s https://api.fastly.com/service/<Service ID>/version/<Editable Version #>/snippet -H "Fastly-Key:FASTLY_API_TOKEN"
```

Rivedi l’elenco delle VCL. In caso di problemi con le VCL predefinite da Fastly, puoi caricare nuovamente o verificare il contenuto in base alle [VCL predefinite](https://github.com/fastly/fastly-magento2/tree/master/etc/vcl_snippets). Per la modifica dei VCL personalizzati, vedere [Snippet VCL Fastly personalizzati](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html) nella Guida all&#39;infrastruttura cloud di Commerce.

## Ulteriori informazioni

Nella documentazione per gli sviluppatori:

* [Informazioni su Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html)
* [Configurazione rapida](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html)
* [Snippet VCL Fastly personalizzati](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/custom-vcl-snippets/fastly-vcl-custom-snippets.html)
