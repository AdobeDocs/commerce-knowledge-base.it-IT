---
title: '"Errore "Indicativo di località non impostato" durante l''esecuzione di setup:upgrade"'
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce on cloud infrastructure 2.2.3 relativo all’errore *Area code is not set* (Il codice di area non è impostato) durante l’esecuzione del comando setup:upgrade.
exl-id: ace92331-6022-49fa-a776-d06d841b3b32
feature: Install, Upgrade
role: Developer
source-git-commit: 4617b915a62093e00da428a753d913a39d30f3a0
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# Errore &#39;Codice località non impostato&#39; durante l&#39;esecuzione di `setup:upgrade`

Questo articolo fornisce una patch per il problema noto di Adobe Commerce on Cloud Infrastructure 2.2.3 relativo all&#39;ottenimento dell&#39;errore *&quot;Area code is not set&quot;* durante l&#39;esecuzione del comando seguente:

```bash
setup:upgrade
```

>[!NOTE]
>
>Il problema è stato risolto in Adobe Commerce 2.2.4.

## Problema

Quando si esegue

```bash
bin/magento setup:upgrade
```

comando, viene visualizzato il seguente messaggio di errore: *&quot;Modulo &#39;Magento\_AdvancedSalesRule&#39;: Installazione dei dati...Codice area non impostato: è necessario impostare il codice area prima di avviare una sessione&quot;* e l&#39;esecuzione del comando viene interrotta. Il problema viene visualizzato perché la configurazione dell’area è richiesta prima dell’effettiva impostazione. La patch consente di rilevare l’errore e non di interrompere il processo di aggiornamento.

## Patch

La patch è allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[Scarica MDVA-10439\_EE\_2.2.3\_COMPOSER\_v1.patch](assets/MDVA-10439_EE_2.2.3_COMPOSER_v1.patch.zip)

## Versioni compatibili di Adobe Commerce:

La patch è stata creata per:

* Adobe Commerce sull’infrastruttura cloud 2.2.3

La patch è compatibile (ma potrebbe non risolvere il problema) anche con le seguenti versioni ed edizioni di Adobe Commerce:

* Adobe Commerce sull’infrastruttura cloud e Adobe Commerce on-premise 2.2.0 - 2.2.3

## Come applicare il cerotto

Per istruzioni, vedere [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella Knowledge Base di supporto.

## File allegati
