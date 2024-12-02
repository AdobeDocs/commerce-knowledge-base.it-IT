---
title: Errore "L’applicazione di aggiornamento non è disponibile"
description: In questo articolo viene illustrata la soluzione per il problema "L'applicazione di aggiornamento non è disponibile" che potrebbe verificarsi quando si tenta di aggiornare/installare Adobe Commerce on-premise utilizzando l'Installazione guidata Web.
exl-id: 85e55ed8-0bc9-4378-b722-46be98ce2638
feature: Configuration
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
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

Per risolvere il problema, verificare se è presente una directory `<magento_root>/update` contenente file e sottodirectory. In caso contrario, consulta [Configurare l&#39;aggiornamento](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/updater-application-is-not-available-error) nella documentazione per gli sviluppatori.
