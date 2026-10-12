---
title: Impossibile clonare l’archivio GitHub di Magento
description: Questo articolo fornisce una correzione per i casi in cui non è possibile clonare l’archivio GitHub di Magento.
exl-id: 65de77b5-496d-42a3-ab2e-1fff9df97160
feature: Data Import/Export
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '67'
ht-degree: 0%
---
# Impossibile clonare l’archivio GitHub di Magento

Questo articolo fornisce una correzione per i casi in cui non è possibile clonare l’archivio GitHub di Magento.

## Dettaglio {#detail}

L&#39;errore è simile al seguente:

```bash
Cloning into 'magento2'...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly
```

## Soluzione {#solution}

Carica la chiave SSH in GitHub come descritto nella [pagina della guida GitHub](https://help.github.com/articles/generating-ssh-keys) .
