---
title: '[!DNL Live Search] visualizza i prodotti esauriti indipendentemente dalle impostazioni di stato scorte in admin'
description: Questo articolo fornisce informazioni sul problema noto in cui la pagina di elenco dei prodotti (PLP) mostra l’errore *Non è possibile trovare prodotti che corrispondono alla selezione* mentre il popover di ricerca restituisce alcuni elementi.
exl-id: 2a351b83-407c-444a-a761-4932b5b88843
feature: Admin Workspace, Categories, Orders, Products, Search
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# [!DNL Live Search] visualizza i prodotti esauriti indipendentemente dalle impostazioni di stato del magazzino in admin

>[!IMPORTANT]
>
>Questo problema è stato risolto in [[!DNL Live Search] [2.0.4]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/release-notes.html). Per installare la versione più recente, fare riferimento a [Aggiornamento [!DNL Live Search]](https://experienceleague.adobe.com/docs/commerce-merchant-services/live-search/onboard/install.html#update) nella guida utente.

Questo articolo fornisce informazioni sul problema noto in cui la pagina di elenco dei prodotti (PLP) mostra *Impossibile trovare prodotti corrispondenti alla selezione* errore durante la ricerca.

## Prodotti e versioni interessati

Adobe Commerce (tutti i metodi di distribuzione) 2.4.x

## Problema

[!DNL Live Search] visualizza i risultati della ricerca indipendentemente dalle impostazioni dello stato del titolo in Adobe Commerce Admin. Anche quando **[!UICONTROL Display Out-of-Stock Products]** è impostato su *No*, vengono visualizzati i prodotti. Genera l’errore PLP *Impossibile trovare prodotti corrispondenti alla selezione*.

<u>Passaggi da riprodurre</u>:

1. Crea una categoria, aggiungi i prodotti. (Esempio: Categoria = _Jeans_, Prodotto1 = _Jeans blu_, Prodotto2 = _Jeans neri_)
1. Prepara tutti i prodotti della categoria esauriti.
1. Imposta **[!UICONTROL Display Out-of-Stock Products]** a *No*.
1. Nella vetrina, immetti *Jeans* nel campo di ricerca.
1. Clic **[!UICONTROL View All]** nel pop-up.

<u>Risultato previsto</u>:

Vedete la *Impossibile trovare prodotti corrispondenti alla selezione* sul PLP e non viene visualizzato alcun prodotto nel pop-up di ricerca.

<u>Risultato effettivo</u>:

Vedete la *Impossibile trovare prodotti corrispondenti alla selezione* sul PLP, ed entrambi i prodotti sono visualizzati nel pop-up di ricerca.

## Soluzione

Al momento non esiste una soluzione per questo problema. Nostro [!DNL Live Search] il team fornirà a breve un’impostazione per configurare [!DNL Live Search] per visualizzare correttamente i prodotti.

## Lettura correlata

[Installa [!DNL Live Search]](https://docs.magento.com/user-guide/live-search/install.html) nella guida utente.
