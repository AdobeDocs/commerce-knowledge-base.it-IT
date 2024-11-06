---
title: Spazio su disco insufficiente
description: Questo articolo suggerisce soluzioni per la situazione in cui si esaurisce lo spazio in un determinato ambiente di Adobe Commerce su infrastruttura cloud.
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Spazio su disco insufficiente

Questo articolo suggerisce soluzioni per la situazione in cui si esaurisce lo spazio in un determinato ambiente di Adobe Commerce su infrastruttura cloud.

## Prodotti e versioni interessati

* Adobe Commerce sull&#39;infrastruttura cloud, tutte le [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Spazio su disco insufficiente con directory scrivibili. Un sintomo può essere [distribuzione bloccata](/help/troubleshooting/deployment/deployment-stuck-with-unable-to-upload-the-application-to-the-remote-cluster-error.md).

Per verificare l&#39;utilizzo del disco, eseguire il comando seguente:

```bash
df -h var/
```

## Causa

La directory `var` è in genere quella che potrebbe occupare molto spazio e può essere pulita facilmente.

Adobe Commerce archivia tutti i file di registro nella directory `var`. Vengono creati nuovi file di registro e quelli vecchi vengono archiviati ogni giorno. Ma se il numero di errori generati continua a crescere, i file di registro occupano sempre più spazio.

I file di importazione/esportazione personalizzati vengono memorizzati anche nella directory `var` e occupano spazio se il loro numero aumenta.

## Soluzione

Opzioni soluzione:

* Verifica se disponi di file di registro di grandi dimensioni e indaga il motivo per cui sono grandi, correggi il problema che genera una grande quantità di output di registro.
* Pulire la directory `var`.
* Configurare un processo cron per tenere traccia delle dimensioni della directory `var` e pulirla.
* Allocare più spazio su disco, se ne sono presenti alcuni inutilizzati. (Consulta la sezione seguente per informazioni su come verificare qual è il limite di spazio).
   * Per la pianificazione Starter, tutti gli ambienti e gli ambienti Pro plan Integration, è possibile allocare spazio su disco se ne sono inutilizzati alcuni, come descritto in [Gestione spazio su disco: allocazione spazio su disco](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space#application-disk-space).
   * Per gli ambienti Pro plan di staging e produzione, contattare l&#39;assistenza per allocare più spazio su disco se sono presenti alcuni elementi inutilizzati.
* Se hai raggiunto il limite di spazio e riscontri ancora problemi di spazio insufficiente, puoi acquistare altro spazio su disco. Per ulteriori informazioni, contatta il team dell’account Adobe.

### Verifica limite di spazio su disco

Per verificare lo spazio disponibile per ogni ambiente Adobe Commerce sull’infrastruttura cloud:

1. Accedi alla [console cloud](https://console.adobecommerce.com).
1. Nel dashboard **[!UICONTROL All projects]**, seleziona il progetto pertinente. Nell&#39;angolo sinistro viene visualizzata la disponibilità di spazio su disco.

   ![spazio_progetto.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
