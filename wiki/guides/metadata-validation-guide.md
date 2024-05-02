---
source-git-commit: 0cfb7dc0dce68bcb0933a5ae49b0cd5a8b5b5a39
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---
# Guida alla convalida dei metadati

Per garantire la corretta formattazione dei metadati nei file MD, è stato implementato un test di convalida dei metadati. Questo documento fornisce linee guida per aiutare i collaboratori a evitare alcuni degli errori di convalida dei metadati più comuni.

**Esempio di metadati:**

```markdown
---
title: This is a title
labels: article,labels,tags
---

Article content...
```

## Errori di convalida comuni e come evitarli/correggerli

Di seguito sono riportati alcuni degli scenari più comuni in cui si verificano errori di convalida dei metadati.

### Due punti nei metadati

Se il titolo o le etichette oppure entrambi contengono due punti, si verifica un errore di convalida.

**Esempio:**

```markdown
---
title: Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,article,labels,tags
---
```

Per evitare questo errore, racchiudi il titolo o le etichette (o entrambi, se entrambi hanno due punti) in **virgolette singole**.

**Esempio:**

```markdown
---
title: 'Patch: Unable to validate VAT number - Adobe Commerce on cloud infrastructure'
labels: 'patch: 2041.1,article,labels,tags'
---
```

### Due punti e virgolette singole o apostrofo nei metadati

La soluzione precedente non funziona se il titolo o le etichette contengono due punti, virgolette singole o apostrofi.

**Esempio:**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure
labels: patch: 2041.1,'article',labels,tags
---
```

Questo errore viene corretto racchiudendo il titolo o le etichette (o entrambi) in **virgolette doppie**.

**Esempio:**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe Commerce on cloud infrastructure"
labels: "patch: 2041.1,'article',labels,tags"
---
```

### Due punti, virgolette doppie e virgolette singole o apostrofo nei metadati

**Esempio:**

```markdown
---
title: Patch: Can't validate 'VAT' number - Adobe "Commerce" on cloud infrastructure
labels: patch: 2041.1,'article',"labels",can't,tags
---
```

In questo caso, racchiudi il titolo o le etichette (o entrambi) in **virgolette doppie** e utilizza un **barra rovesciata** per applicare l&#39;escape a tutte le virgolette doppie nel titolo e nelle etichette.

**Esempio:**

```markdown
---
title: "Patch: Can't validate 'VAT' number - Adobe \"Commerce\" on cloud infrastructure"
labels: "patch: 2041.1,'article',\"labels\",can't,tags"
---
```

### Campi mancanti nei metadati

Se nei metadati manca il campo titolo o il campo etichette, si verifica un errore di convalida.

**Esempio:**

```markdown
---
title: This is a title
---
```

OPPURE

```markdown
---
labels: article,labels,tags
---
```

Per evitare questo errore, includi entrambi i campi nei metadati.

Il campo delle etichette può essere lasciato vuoto e non darà luogo a un errore, ma il campo del titolo deve essere compilato.

**Esempio:**

```markdown
---
title: Unlike labels the title field must be filled
labels:
---
```
