---
title: Risoluzione degli errori UTF-8 per il caricamento di file CSV
description: Questo articolo corregge il messaggio di errore "I file CSV devono utilizzare la codifica UTF-8". Questo messaggio di errore indica che il file che stai tentando di caricare contiene caratteri non validi o non consentiti. Mentre la codifica UTF-8 consente [la maggior parte dei caratteri](https://www.fileformat.info/info/charset/UTF-8/list.htm), alcuni non sono compatibili con Magento BI.
exl-id: 88d8e0b8-152e-4a6d-bc44-3b285e0eb0c3
feature: Data Import/Export
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '263'
ht-degree: 0%

---

# Risoluzione degli errori UTF-8 per il caricamento di file CSV

Questo articolo corregge il messaggio di errore &quot;I file CSV devono utilizzare la codifica UTF-8&quot;. Questo messaggio di errore indica che il file che stai tentando di caricare contiene caratteri non validi o non consentiti. Mentre la codifica UTF-8 consente [la maggior parte dei caratteri](https://www.fileformat.info/info/charset/UTF-8/list.htm), alcuni non sono compatibili con Magento BI.

Per risolvere il problema, è necessario modificare la codifica del file. Il salvataggio del file con la codifica corretta in genere risolve il problema, ma tieni presente che questa operazione potrebbe causare la perdita di alcune informazioni (ad esempio, i caratteri non validi potrebbero venire eliminati).

È consigliabile utilizzare [Testo sublime](https://www.sublimetext.com/2) per salvare e codificare il file.

1. Apri il file in Microsoft Excel, Google Docs, Apple Numbers o nel programma desiderato.
1. Fai clic su &#x200B;&#x200B; **File** > **Salva con nome** &#x200B;&#x200B; e scegli il formato &#x200B;&#x200B; **Valori separati da virgole (.csv)** per salvare il file.
1. Apri il file CSV in Testo sublime.
1. In Testo sublime passare a &#x200B;&#x200B; **File** > **Salva con codifica** > **UTF-8\*&#x200B;**. Il file CSV verrà salvato con codifica UTF-8.    ![csv_file_UTF-8_sublime_3.2.2_magento_BI.png](assets/csv_file_UTF-8_sublime_3.2.2_magento_BI.png)
1. [Carica i dati](https://experienceleague.adobe.com/it/docs/commerce-business-intelligence/mbi/analyze/connecting/using-file-uploader) (nella guida utente) in una nuova tabella in Magento BI.
