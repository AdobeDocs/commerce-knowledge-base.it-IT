---
title: lo sviluppo dell’origine git pull ha esito negativo durante l’aggiornamento del software Adobe Commerce
description: Questo articolo fornisce una correzione per i casi in cui non è possibile aggiornare il software Adobe Commerce durante l’esecuzione di "git pull origin development".
exl-id: b133253e-c160-4f15-a9b0-8591e93a1e9b
feature: Upgrade
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# lo sviluppo dell’origine git pull ha esito negativo durante l’aggiornamento del software Adobe Commerce

Questo articolo fornisce una correzione per i casi in cui non è possibile aggiornare il software Adobe Commerce durante l’esecuzione `git pull origin develop`.

## Dettagli

Uno dei passaggi per aggiornare il software Adobe Commerce consiste nell’aggiornare l’archivio locale eseguendo:

```bash
$ git pull origin develop
```

È possibile che venga visualizzato il seguente errore:

```terminal
error: Your local changes to the following files would be overwritten by merge:
<list of files>
```

Per individuare i file soggetti a sovrascrittura, leggere il messaggio o immettere:

```bash
git status
```

La sezione successiva illustra le soluzioni suggerite.

### Soluzioni consigliate

La soluzione dipende dal fatto che i file siano stati modificati intenzionalmente o meno nel file system di Adobe Commerce. Per ulteriori informazioni, consulta una delle sezioni seguenti.

#### File modificati intenzionalmente

Risolvere manualmente i conflitti nel modo consueto. Se non sai cosa fare, consulta [Guida GitHub](https://help.github.com/).

#### Non hai modificato intenzionalmente alcun file

Effettuare una delle seguenti operazioni:

* Se si è certi di non aver modificato alcun file e non si desidera rimuovere o sovrascrivere le modifiche nel file system di Adobe Commerce, immettere:

  </p>
    <pre><code class="language-bash">$ git reset --hard HEAD && git pull origin develop</code></pre>

  Dopodiché, continua da dove hai interrotto con l’aggiornamento Adobe Commerce.

* È possibile che un’impostazione di configurazione GitHub possa evitare questi errori in futuro. Per impostazione predefinita, GitHub memorizza il contenuto utilizzando i caratteri di fine riga predefiniti del sistema operativo. Se utilizzi Linux, ma un altro collaboratore ha eseguito il commit di una modifica utilizzando Windows, GitHub converte le terminazioni di riga di Windows in Linux quando cloni o richiami. Ciò dà l&#39;aspetto di una modifica ai file quando in realtà non è stata apportata alcuna modifica.

  Per configurare GitHub in modo da ignorare le terminazioni di riga, immetti il seguente comando nel client Git:

  </p>
    <pre><code class="language-bash">$ git config --system core.autocrlf false</code></pre>

  Se si utilizza Windows, immettere:

  </p>
    <pre><code class="language-bash">$ git config --system core.eol LF</code></pre>

  >[!NOTE]
  >
  >L’Adobe non consiglia o approva alcuna impostazione di configurazione GitHub particolare. I precedenti sono solo suggerimenti. Per ulteriori informazioni, consulta [Guida GitHub](https://help.github.com/).

  Continua da dove hai interrotto con il tuo aggiornamento Adobe Commerce.
