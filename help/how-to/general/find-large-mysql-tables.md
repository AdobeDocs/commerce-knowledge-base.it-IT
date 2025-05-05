---
title: Trova tabelle MySQL di grandi dimensioni
description: '"Per identificare le tabelle di grandi dimensioni, connettiti al database come descritto nell’articolo [Connetti al database](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database) ed esegui il seguente comando, dove "project_id" è l’ID del progetto Cloud:"'
exl-id: dc5019bc-ab6c-4568-986f-0a294a0f3ac3
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Trova tabelle MySQL di grandi dimensioni

Per identificare le tabelle di grandi dimensioni, connettiti al database come descritto nell&#39;articolo [Connetti al database](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/configure/service/mysql#connect-to-the-database) ed esegui il comando seguente, dove `project_id` è l&#39;ID del progetto cloud:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "<project_id>"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

Verrebbe visualizzato l’elenco completo delle tabelle e le relative dimensioni. Puoi esaminare l’elenco e identificare le tabelle che richiedono attenzione a causa delle dimensioni elevate.

## Lettura correlata

[Best practice per la modifica delle tabelle del database](https://experienceleague.adobe.com/it/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) nel playbook di implementazione di Commerce
