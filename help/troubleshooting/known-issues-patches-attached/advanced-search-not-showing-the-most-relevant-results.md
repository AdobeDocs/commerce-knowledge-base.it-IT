---
title: La ricerca avanzata non mostra i risultati più rilevanti
description: Questo articolo fornisce una patch per il problema noto di Adobe Commerce, in cui la ricerca avanzata non mostra prima i risultati più rilevanti.
exl-id: 88f0782d-ba7d-4f19-9761-7894d978d334
feature: Search
role: Developer
source-git-commit: 1d2e0c1b4a8e3d79a362500ee3ec7bde84a6ce0d
workflow-type: tm+mt
source-wordcount: '269'
ht-degree: 0%

---

# La ricerca avanzata non mostra i risultati più rilevanti

Questo articolo fornisce una patch per il problema noto di Adobe Commerce, in cui la ricerca avanzata non mostra prima i risultati più rilevanti.

## Versioni interessate {#Advancedsearchnotshowingmostrelevantresults-Affectedversions}

* Adobe Commerce (tutte le opzioni di implementazione) 2.x.x
* Magento Open Source 2.x.x

## Problema {#Advancedsearchnotshowingmostrelevantresults-Description}

La funzione di ricerca avanzata non restituisce prima i risultati più rilevanti, come sta facendo la ricerca rapida. Il problema non dipende dal tipo di motore di ricerca selezionato.

<u>Passaggi da riprodurre:</u>

1. Sulla vetrina, vai alla ricerca rapida e cerca &quot;Giacca adatta&quot;.
1. Nota &quot;Giacca orione a due toni&quot; è il primo risultato.
1. Andare alla ricerca avanzata e cercare &quot;Giacca adatta&quot; nel campo del nome.

<u>Risultato previsto:</u>

Il &quot;Orion Two-Tone Fitting Jacket&quot; è il primo risultato quando si utilizza la ricerca avanzata, come risultato più rilevante.

<u>Risultato effettivo:</u>

La &quot;Orion Two-Tone Fitting Jacket&quot; non è il primo risultato, anche se è il più rilevante.

## Soluzione {#Advancedsearchnotshowingmostrelevantresults-Solution}

Per risolvere il problema, applica la patch allegata a questo articolo. Per scaricarlo, scorri verso il basso fino alla fine dell’articolo e fai clic sul nome del file, oppure fai clic sul seguente collegamento:

[Scarica MDVA-7256\_EE\_2.1.7\_v1.compositore.patch](assets/MDVA-7256_EE_2.1.7_v1.composer.patch.zip)

La patch aggiunge l’implementazione per l’ordinamento in base alla rilevanza per i risultati di ricerca avanzata come campo di ordinamento predefinito.

La patch è compatibile con tutte le versioni e le edizioni interessate.

## Come applicare il cerotto

Per istruzioni, consulta [Come applicare una patch del compositore fornita dall&#39;Adobe](/help/how-to/general/how-to-apply-a-composer-patch-provided-by-magento.md) nella nostra knowledge base di supporto.

## File allegati
