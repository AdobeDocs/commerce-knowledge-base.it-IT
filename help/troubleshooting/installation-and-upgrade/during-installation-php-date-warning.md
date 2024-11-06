---
title: Durante l'installazione, avvertenza data PHP
description: Questo articolo fornisce una correzione per un avviso di data PHP durante l'installazione.
exl-id: f82c77a9-bbcd-4426-96a0-b3f4b704860b
feature: Install, Upgrade
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '61'
ht-degree: 0%

---

# Durante l&#39;installazione, avvertenza data PHP

Questo articolo fornisce una correzione per un avviso di data PHP durante l&#39;installazione.

## Dettagli {#details}

Durante l’installazione viene visualizzato il seguente messaggio:

```text
PHP Warning:  date(): It is not safe to rely on the system's timezone settings. [more]
```

### Soluzione {#solution}

Controllare attentamente l&#39;impostazione del fuso orario PHP. Consulta [Guida all&#39;installazione > Impostazioni PHP](https://experienceleague.adobe.com/en/docs/commerce-operations/installation-guide/prerequisites/php-settings) nella documentazione per gli sviluppatori.
