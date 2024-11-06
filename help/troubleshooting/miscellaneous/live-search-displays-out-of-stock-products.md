---
title: '[!DNL Live Search] visualizza i prodotti esauriti indipendentemente dalle impostazioni dello stato delle scorte in admin'
description: Questo articolo fornisce informazioni sul problema noto in cui la pagina di elenco dei prodotti (PLP) mostra l’errore *Non è possibile trovare prodotti che corrispondono alla selezione* mentre il popover di ricerca restituisce alcuni elementi.
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search] mostra i prodotti esauriti indipendentemente dalle impostazioni dello stato delle scorte in admin

>[!IMPORTANT]
>
>Questo problema è stato risolto in [[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html). Per installare la versione più recente, consulta [Aggiornamento [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#update) nella guida utente.

Questo articolo fornisce informazioni sul problema noto in cui la pagina dell&#39;elenco dei prodotti (PLP) mostra l&#39;errore *Impossibile trovare prodotti corrispondenti alla selezione* mentre il popover di ricerca restituisce alcuni elementi.

## Prodotti e versioni interessati

Adobe Commerce (tutti i metodi di distribuzione) 2.4.x

## Problema

[!DNL Live Search] visualizza i risultati della ricerca indipendentemente dalle impostazioni dello stato del titolo nell&#39;amministratore di Adobe Commerce. Anche quando **[!UICONTROL Display Out-of-Stock Products]** è impostato su *No*, i prodotti vengono visualizzati. Si è verificato l&#39;errore PLP *Impossibile trovare prodotti corrispondenti alla selezione*.

<u>Passaggi da riprodurre</u>:

1. Crea una categoria, aggiungi i prodotti. (Esempio: Categoria = _Jeans_, Prodotto1 = _Blue Jeans_, Prodotto2 = _Black Jeans_)
1. Prepara tutti i prodotti della categoria esauriti.
1. Imposta **[!UICONTROL Display Out-of-Stock Products]** su *No*.
1. Nella vetrina, immetti *Jeans* nel campo di ricerca.
1. Fare clic su **[!UICONTROL View All]** nel popup.

<u>Risultato previsto</u>:

*Impossibile trovare prodotti corrispondenti al messaggio di selezione* in PLP e nessun prodotto visualizzato nel popup di ricerca.

<u>Risultato effettivo</u>:

*Impossibile trovare i prodotti corrispondenti al messaggio di selezione* in PLP ed entrambi i prodotti sono visualizzati nel popup di ricerca.

## Soluzione

Al momento non esiste una soluzione per questo problema. Il nostro team [!DNL Live Search] fornirà presto un&#39;impostazione per configurare [!DNL Live Search] per visualizzare correttamente i prodotti.

## Lettura correlata

[Installa [!DNL Live Search]](https://experienceleague.adobe.com/en/docs/commerce-merchant-services/live-search/install) nella guida utente.
