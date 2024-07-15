---
title: Risolvere i problemi relativi agli errori dello strumento di compatibilità per l'aggiornamento
description: In questo articolo vengono illustrati gli errori che possono verificarsi durante l'utilizzo di Upgrade Compatibility Tool e vengono fornite soluzioni per correggerli in modo da poter eseguire correttamente lo strumento.
exl-id: 1cce1146-942e-46cb-a395-8da9e472cd39
feature: Customer Service, Install, Upgrade
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Risolvere i problemi relativi agli errori dello strumento di compatibilità per l&#39;aggiornamento

In questo articolo vengono illustrati gli errori che possono verificarsi durante l&#39;utilizzo di Upgrade Compatibility Tool e vengono fornite soluzioni per correggerli in modo da poter eseguire correttamente lo strumento.

## Prodotti e versioni interessati

* [Upgrade Compatibility Tool](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html) è compatibile con le versioni di Adobe Commerce a partire dalla versione 2.3.0.

## Errore di segmentazione

<u>Causa</u>:

Quando due moduli hanno lo stesso nome, lo strumento di compatibilità per l’aggiornamento mostra un errore di segmentazione.

<u>Soluzione</u>:

Per evitare questo errore, si consiglia di specificare il percorso del modulo come argomento:

```bash
bin/uct upgrade:check --current-version=2.4.4 path/to/the/module
```

>[!WARNING]
>
> Lo strumento di compatibilità per l’aggiornamento potrebbe non essere in grado di analizzare la base di codice se contiene una dipendenza circolare tra i metodi.

## Output vuoto

<u>Passaggi da riprodurre</u>:

1. Se dopo aver eseguito questo comando:

   ```bash
   bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
   ```

1. L&#39;unico output è `Upgrade compatibility tool`:

   ```terminal
   bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
   Upgrade compatibility tool
   ```

<u>Causa</u>:

La probabile causa è una limitazione della memoria PHP.

Esistono due possibili soluzioni per evitare questa limitazione della memoria PHP.

<u>Soluzione 1</u>:

Ignorare la limitazione di memoria impostando `memory_limit` su `-1`:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

>[!NOTE]
>
> `M2_VERSION` è la versione Adobe Commerce di destinazione che desideri confrontare con la tua istanza Adobe Commerce.

<u>Soluzione 2</u>:

L&#39;aggiunta dell&#39;opzione `-m` consente a Upgrade Compatibility Tool di analizzare ogni modulo specifico in modo indipendente per evitare di incontrare due moduli con lo stesso nome nell&#39;istanza Adobe Commerce.

Questa opzione di comando consente inoltre a Upgrade Compatibility Tool di analizzare una cartella contenente diversi moduli:

```bash
bin/uct upgrade:check /<dir>/<instance-name> -m /vendor/<vendor-name>/
```

Per ulteriori informazioni sulle opzioni dell&#39;interfaccia della riga di comando, vedere [Eseguire lo strumento in un&#39;interfaccia della riga di comando](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/run.html).
