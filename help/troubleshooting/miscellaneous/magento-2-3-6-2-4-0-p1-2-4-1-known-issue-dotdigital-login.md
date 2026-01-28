---
title: 'Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1 problema noto: accesso dotdigital'
description: Questo articolo descrive un problema noto di Adobe Commerce 2.3.6, 2.4.0-p1 e 2.4.1 per il quale è impossibile accedere a [dotdigital](https://dotdigital.com/) tramite il pannello di amministrazione quando l’account dotdigital è abilitato.
exl-id: 427d895c-8c03-4ced-813a-eeaa67f1d1f0
feature: Configuration
role: Developer
source-git-commit: 38b4d310cab9dccad142c244f6e07f8421a9894d
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 0%

---

# Adobe Commerce 2.3.6, 2.4.0-p1, 2.4.1 problema noto: accesso dotdigital

Questo articolo descrive un problema noto di Adobe Commerce 2.3.6, 2.4.0-p1 e 2.4.1 per cui è impossibile accedere a [dotdigital](https://dotdigital.com/) tramite il pannello di amministrazione quando l&#39;account dotdigital è abilitato.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.3.6 (solo browser Safari)
* Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.4.0-p1 (solo browser Safari)
* Adobe Commerce su infrastruttura cloud e Adobe Commerce on-premise 2.4.1 (solo browser Safari)

## Problema

<u>Prerequisiti</u>:

1. account dotdigital esistente.
1. In Adobe Commerce sono presenti credenziali API dotdigital valide.

<u>Passaggi da riprodurre</u>:

1. Vai a **Archivi** > **Configurazione** > **DOTDIGITAL** > **Impostazioni chat** > **Abilitato** è impostato su *Sì.*
1. Fai clic su **Configura** in **Configura widget chat** o **Configura team chat**.

<u>Risultati previsti</u>:

La pagina delle impostazioni della chat deve essere aperta correttamente tramite il pannello di amministrazione.

<u>Risultati effettivi</u>:

Impossibile accedere a dotdigital.

## Soluzione

Soluzione alternativa: utilizza un browser alternativo a Safari per questa particolare situazione.