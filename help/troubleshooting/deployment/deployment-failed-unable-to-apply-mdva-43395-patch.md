---
title: "Distribuzione non riuscita: impossibile applicare la patch MDVA-43395"
description: Questo articolo fornisce una soluzione al problema, in cui il tentativo di applicare la patch MDVA-43395 genera una distribuzione non riuscita.
exl-id: 5341be3a-a9d7-4a4b-9755-8c585c6922a4
feature: Deploy
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Distribuzione non riuscita: impossibile applicare la patch MDVA-43395

Questo articolo fornisce una soluzione al problema, in cui il tentativo di applicare la patch MDVA-43395 genera una distribuzione non riuscita.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud (tutte le versioni)

## Problema

Impossibile applicare la patch MDVA-43395.

## Causa

I commercianti cloud non devono applicare la patch MDVA-43395 separatamente se hanno installato [magento/magento-cloud-patches 1.0.16](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html#v1016), che include già la patch.

## Soluzione

Per risolvere il problema, rimuovere le patch MDVA-43395 e MDVA-43443 dalla directory `m2-hotfixes` e ridistribuirle.

Se si fosse in grado di applicare la patch MDVA-43443 tramite la directory `m2-hotfixes`, sarà comunque necessario rimuoverla come indicato sopra. Le versioni future di Adobe Commerce conterranno già queste patch, pertanto l’aggiornamento potrebbe causare errori di distribuzione in un secondo momento.

Per verificare se la patch è stata applicata, eseguire il comando `vendor/bin/magento-patches -n status |grep 43443`.
Se vengono visualizzati più risultati come questo, rimuovere la patch MDVA-43443 dalla cartella `m2-hotfixes`:

```bash
$ vendor/bin/magento-patches -n status |grep 43443
║ MDVA-43443              │ Parser token new fix                                         │ Other           │ Adobe Commerce Support │ Applied     │ Patch type: Required                                     ║
║ N/A                     │ ../m2-hotfixes/MDVA-43443_EE_2.4.2-p2_COMPOSER_v1.patch      │ Other           │ Local                  │ Applied     │ Patch type: Custom                                       ║
```

## Lettura correlata

* [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.
* [Patch cloud per Commerce](https://devdocs.magento.com/cloud/release-notes/mcp-release-notes.html#v1016) nella documentazione per gli sviluppatori.
