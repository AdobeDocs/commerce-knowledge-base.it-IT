---
title: Impossibile clonare l’archivio GitHub del Magento
description: Questo articolo corregge alcuni casi in cui non è possibile clonare l’archivio GitHub di Magento.
exl-id: 65de77b5-496d-42a3-ab2e-1fff9df97160
feature: Data Import/Export
role: Developer
source-git-commit: 35d4f2130d0ec71f71f5f20aa8a7c76207e7a35a
workflow-type: tm+mt
source-wordcount: '62'
ht-degree: 0%

---

# Impossibile clonare l’archivio GitHub del Magento

Questo articolo corregge alcuni casi in cui non è possibile clonare l’archivio GitHub di Magento.

## Dettaglio {#detail}

L&#39;errore è simile al seguente:

```bash
Cloning into 'magento2'...
Permission denied (publickey).
fatal: The remote end hung up unexpectedly
```

## Soluzione {#solution}

Carica la chiave SSH in GitHub come descritto nella [pagina della guida GitHub](https://help.github.com/articles/generating-ssh-keys) .
