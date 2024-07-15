---
title: Trova tabelle MySQL di grandi dimensioni
description: '"Per identificare le tabelle di grandi dimensioni, connettiti al database come descritto nell’articolo [Connetti al database](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database) ed esegui il seguente comando, dove "project_id" è l’ID del progetto Cloud:"'
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '97'
ht-degree: 0%

---

# Trova tabelle MySQL di grandi dimensioni

Per identificare le tabelle di grandi dimensioni, connettiti al database come descritto nell&#39;articolo [Connetti al database](https://devdocs.magento.com/cloud/project/project-conf-files_services-mysql.html#connect-to-the-database) ed esegui il comando seguente, dove `project_id` è l&#39;ID del progetto cloud:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Verrebbe visualizzato l’elenco completo delle tabelle e le relative dimensioni. Puoi esaminare l’elenco e identificare le tabelle che richiedono attenzione a causa delle dimensioni elevate.
