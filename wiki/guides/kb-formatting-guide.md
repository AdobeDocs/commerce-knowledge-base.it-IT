---
source-git-commit: c587986edc925c49bf95ab935888b59f265371af
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---
# Guida alla formattazione di KB

## Autore in Markdown

In generale, utilizziamo [Guida allo stile della sintassi Markdown di Adobe Experience League](https://experienceleague.adobe.com/docs/authoring-guide-exl/using/markdown/syntax-style-guide.html?lang=en), ma ci sono alcune differenze ed eccezioni. Inoltre, in alcuni casi sono necessari determinati tag HTML.

Di seguito sono riportati alcuni esempi della formattazione Markdown più comunemente utilizzata nel nostro archivio.

## Formattazione di base

Per formattare il testo in grassetto, racchiuderlo in due asterischi:

`This will be **bold** text`

Per formattare il testo in corsivo, utilizzare un singolo asterisco:

`This text will be *italics*`

Per formattare il testo come sottolineato, utilizzare `<ins>` tag:

`<ins>This text will be underlined</ins>`

Per aggiungere un&#39;interruzione di riga, utilizzare `<br>` HTML.


## Intestazioni

Utilizza la seguente formattazione per le intestazioni da H2 a H5. H1 non viene mai utilizzato poiché il titolo dell’articolo è considerato H1.

`## Header 2 `

`### Header 3 `

`#### Header 4`

`##### Header 5`

## Codice in linea e blocchi

Utilizza i singoli apici retroversi per racchiudere l’elemento di codice che desideri evidenziare:

Questo è \`codice in linea\` all&#39;interno di un paragrafo di testo.

### Blocchi di codice

Per inserire un blocco di codice, racchiudi il blocco di codice in tre apici retroversi e specifica la lingua dopo l’apertura dei tre apici retroversi:

sql \`\`\`

SELEZIONA NOME_TABELLA COME `Table`, ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES WHERE TABELLA_SCHEMA = &quot;%project_id%&quot; ORDINA PER (DATA_LENGTH + INDEX_LENGTH) DESC;

\`\`\`

Verrà eseguito il rendering come:

```sql
SELECT TABLE_NAME AS `Table`,
  ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024) AS `Size (MB)`
FROM information_schema.TABLES
WHERE TABLE_SCHEMA = "%project_id%"
ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
```

In base alle nostre regole di evidenziazione, devi sempre specificare una lingua per il blocco di codice.

Per l’elenco delle lingue supportate, consulta https://github.com/github/linguist/blob/master/lib/linguist/languages.yml.

Se l’evidenziazione non funziona per una determinata lingua in markdown (ovvero, la lingua non è supportata), per renderla almeno evidenziata quando viene pubblicata su https://support.magento.com/hc/en-us/, utilizza il seguente HTML:

```html
<pre><code class="language-%language-code%"
your code here
</pre></code>
```

Dove ``%language-code%`` sono i codici definiti da [Lingue supportate da Prism.js](https://prismjs.com/#supported-languages).

## Elenchi

Separa sempre gli elenchi dal resto del contenuto tramite righe vuote. Gli elenchi devono essere preceduti e seguiti da una riga vuota.

Utilizza la seguente formattazione per gli elenchi ordinati:

```markdown
1. First numbered list item.
1. Second numbered list item.
...
1. Last numbered list item.
```

Per creare un elenco puntato non ordinato, inizia una riga con *, + o -. Ma seleziona un metodo e utilizzalo in modo coerente in tutto l’articolo.

Esempio:

```markdown
* Unordered list item.
* Unordered list item.
---
* Last unordered list item.
```

Per aggiungere contenuto tra le voci di elenco, aggiungi 4 spazi all’inizio della riga:

```markdown
* List item.
* List item.
    Here's some content between list items.
* Here we continue the list
```

Puoi incorporare gli elenchi anche in questo modo.

## Collegamenti

I collegamenti esterni sono semplici:

```markdown
[Adobe](https://www.adobe.com)
```

### Collegamenti ad allegati

Qualsiasi tipo di allegato deve essere nei formati .png, .jpg e .jpeg. Per motivi di sicurezza, accettiamo solo gli allegati in uno dei tre formati.

Per inserire un&#39;immagine, posizionarla in *risorse* sottocartella nella stessa cartella di sezione dell’articolo e utilizza la sintassi seguente per inserire l’immagine nell’articolo:

```markdown
![alt text](assets/image.png)
```

Se desideri personalizzare le dimensioni dell’immagine, utilizza il seguente tag HTML:

```html
<img src = "assets/image.png" alt = "your alt text" width="custom width, ex: 250px">
```

```markdown
[asset_title](assets/%file_name%).
```

### Collegamenti a sezioni specifiche nell’articolo

Se devi fare riferimento a una sezione all’interno dell’articolo, non devi creare un ancoraggio separato. Vengono generati automaticamente in fase di pubblicazione per tutte le intestazioni H2-H6. Gli ancoraggi vengono generati dall’intestazione rendendo tutte le parole in minuscolo e utilizzando &quot;-&quot; per separare le parole.

Esempio:

```markdown
## This is header
```

Questo è un collegamento a questa intestazione:

```markdown
[this is link to the anchor in the same article](#this-is-header)
```

Se devi fare riferimento a un elemento diverso da header, utilizza HTML per definire l’elemento da aggiungere. [attributo id](https://www.w3schools.com/html/html_id.asp). Puoi quindi utilizzare Markdown o HTML per fare riferimento a questo ID.

### Collegamenti relativi e collegamenti ad altri articoli

Non utilizzare collegamenti relativi per fare riferimento agli articoli della Knowledge Base di supporto. Questi collegamenti non funzioneranno quando l&#39;articolo verrà pubblicato in [Centro assistenza Adobe Commerce](https://support.magento.com/hc/en-us).
Utilizza i collegamenti ipertestuali completi dalla sezione [Centro assistenza Adobe Commerce](https://support.magento.com/hc/en-us).


## Tabelle

Utilizzare [Formattazione HTML per le tabelle](https://www.w3schools.com/html/html_tables.asp).


## Avvisi e blocchi di informazioni

Blocco nota di successo:

```
>![success]
>
>This is a success note
```

Blocco di avvertenza:

```
>![warning]
>
>This is a warning
```

Blocco nota informazioni:

```
>![info]
>
>This is a block with additional info
```
