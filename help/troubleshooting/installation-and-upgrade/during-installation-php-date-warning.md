---
title: Durante l'installazione, avvertenza data PHP
description: Questo articolo fornisce una correzione per un avviso di data PHP durante l'installazione.
exl-id: f82c77a9-bbcd-4426-96a0-b3f4b704860b
feature: Install, Upgrade
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '71'
ht-degree: 1%
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
