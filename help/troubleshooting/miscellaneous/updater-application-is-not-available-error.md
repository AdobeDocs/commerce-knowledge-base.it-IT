---
title: Errore "Applicazione di aggiornamento non disponibile"
description: In questo articolo viene illustrata la soluzione per il problema "L'applicazione di aggiornamento non è disponibile" che potrebbe verificarsi quando si tenta di aggiornare/installare Adobe Commerce on-premise utilizzando l'Installazione guidata Web.
exl-id: 85e55ed8-0bc9-4378-b722-46be98ce2638
feature: Configuration
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Errore &quot;L’applicazione di aggiornamento non è disponibile&quot;

In questo articolo viene illustrata la soluzione per il problema &quot;L&#39;applicazione di aggiornamento non è disponibile&quot; che potrebbe verificarsi quando si tenta di aggiornare/installare Adobe Commerce on-premise utilizzando l&#39;Installazione guidata Web.

## Problema

Nel controllo di idoneità viene visualizzato il seguente messaggio:

![Screen_Shot_2019-08-29_at_1.39.12_PM.png](assets/Screen_Shot_2019-08-29_at_1.39.12_PM.png)

## Prodotti/versioni interessati

* Adobe Commerce on-premise 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x


## Soluzione

Per risolvere questo problema, verifica se è presente `<magento_root>/update` directory che contiene file e sottodirectory. In caso contrario, vedere [Configurare l’aggiornamento](https://devdocs.magento.com/guides/v2.3/comp-mgr/updater/update-updater.html) nella documentazione per gli sviluppatori.
