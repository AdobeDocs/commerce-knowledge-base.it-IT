---
title: Spazio su disco insufficiente
description: Questo articolo suggerisce soluzioni per la situazione in cui si esaurisce lo spazio in un determinato ambiente di Adobe Commerce su infrastruttura cloud.
exl-id: 1b2c25d3-ca1b-4409-8d6b-378aa0952f94
feature: Storage, Observability
role: Developer
source-git-commit: 9ee4145d5516a37fab1c092d539000627f242a93
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# Spazio su disco insufficiente

Questo articolo suggerisce soluzioni per la situazione in cui si esaurisce lo spazio in un determinato ambiente di Adobe Commerce su infrastruttura cloud.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutto [versioni supportate](https://magento.com/sites/default/files/magento-software-lifecycle-policy.pdf)

## Problema

Spazio su disco insufficiente con directory scrivibili. Un sintomo può essere [distribuzione bloccata](/help/troubleshooting/deployment/deployment-stuck-with-unable-to-upload-the-application-to-the-remote-cluster-error.md).

Per verificare l&#39;utilizzo del disco, eseguire il comando seguente:

```bash
df -h var/
```

## Causa

Il `var` La directory di solito è quella che potrebbe prendere molto spazio e può essere pulita facilmente.

Adobe Commerce archivia tutti i file di registro in `var` directory. Vengono creati nuovi file di registro e quelli vecchi vengono archiviati ogni giorno. Ma se il numero di errori generati continua a crescere, i file di registro occupano sempre più spazio.

I file di importazione/esportazione personalizzati vengono memorizzati anche nel `var` e occupare spazio se il loro numero aumenta.

## Soluzione

Opzioni soluzione:

* Verifica se disponi di file di registro di grandi dimensioni e indaga il motivo per cui sono grandi, correggi il problema che genera una grande quantità di output di registro.
* Pulisci `var` directory.
* Imposta un processo cron per tenere traccia delle dimensioni del `var` e pulirla.
* Allocare più spazio su disco, se ne sono presenti alcuni inutilizzati. (Consulta la sezione seguente per informazioni su come verificare qual è il limite di spazio).
   * Per la pianificazione iniziale, per tutti gli ambienti e per gli ambienti Pro plan Integration, è possibile allocare lo spazio su disco se sono presenti alcuni ambienti inutilizzati, come descritto in [Gestione dello spazio su disco: allocazione dello spazio su disco](https://devdocs.magento.com/guides/v2.3/cloud/project/manage-disk-space.html#application-disk-space).
   * Per gli ambienti Pro plan di staging e produzione, contattare l&#39;assistenza per allocare più spazio su disco se sono presenti alcuni elementi inutilizzati.
* Se hai raggiunto il limite di spazio e riscontri ancora problemi di spazio insufficiente, puoi acquistare altro spazio su disco. Per ulteriori informazioni, contatta il team dell’account di Adobe.

### Verifica limite di spazio su disco

Per verificare lo spazio disponibile per ogni ambiente Adobe Commerce sull’infrastruttura cloud:

1. Accedi a [Console cloud](https://console.adobecommerce.com).
1. Il giorno **[!UICONTROL All projects]** sulla dashboard, seleziona il progetto pertinente. Nell&#39;angolo sinistro viene visualizzata la disponibilità di spazio su disco.

   ![project_space.png](/help/troubleshooting/miscellaneous/assets/project_space.png)
