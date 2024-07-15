---
title: Errore "Area già impostata" durante il salvataggio della configurazione del tema in Admin
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce on Cloud Infrastructure 2.2.4 relativo al recupero del messaggio di errore *"Area già impostata"* quando si tenta di impostare un tema per la visualizzazione predefinita dello store in Commerce Admin.
exl-id: c4e34a73-b774-4447-ba8e-aaf208ad54c5
feature: Admin Workspace, Configuration, Themes
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# Errore &quot;Area già impostata&quot; durante il salvataggio della configurazione del tema in Admin

Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.2.4 relativo al recupero del messaggio di errore *&quot;Area già impostata&quot;* quando si tenta di impostare un tema per la visualizzazione predefinita dell&#39;archivio nell&#39;amministratore di Commerce.

## Problema

Si riceve il messaggio di errore &quot; *Si è verificato un errore durante il salvataggio della configurazione: area già impostata*&quot; quando si tenta di impostare un tema per la visualizzazione predefinita dell&#39;archivio.

<u>Passaggi da riprodurre</u>:

1. Accedi all’amministratore di Commerce.
1. Passa a **Contenuto** > **Struttura** > **Configurazione**.
1. Imposta l&#39;ambito di configurazione su *Visualizzazione archivio predefinita*.
1. Modifica il tema nel menu a discesa **Tema applicato**. Ad esempio, da *Luma* a *Vuoto.*
1. Fare clic su **Salva configurazione**.

<u>Risultato previsto</u>: il tema selezionato viene applicato alla visualizzazione predefinita dell&#39;archivio.

<u>Risultato effettivo</u>: tema non applicato, *&quot;Si è verificato un errore durante il salvataggio della configurazione: area già impostata&quot;* viene visualizzato il messaggio di errore.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, fai clic sul seguente collegamento o scorri verso il basso fino alla fine dell’articolo e fai clic sul file allegato:

[Scarica MDVA-11106\_EE\_2.2.4\_v1.compositore.patch](assets/MDVA-11106_EE_2.2.4_v1.composer.patch.zip)

## Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce sull’infrastruttura cloud 2.2.4

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce sull’infrastruttura cloud 2.0.X
* Adobe Commerce sull’infrastruttura cloud 2.1.X
* Adobe Commerce sull’infrastruttura cloud 2.2.0 - 2.2.5
* Adobe Commerce on-premise 2.0.X
* Adobe Commerce on-premise 2.1.X
* Adobe Commerce on-premise 2.2.0 - 2.2.5

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.

## File allegati
