---
title: I clienti UE non possono completare i pagamenti
description: Questo articolo fissa il problema relativo ai clienti dell'Unione europea che non sono in grado di completare i pagamenti.
exl-id: 8309d96b-47a3-4d27-b538-e6e3bcdfb7d4
feature: Orders, Payments
role: Developer
source-git-commit: 958179e0f3efe08e65ea8b0c4c4e1015e3c5bb76
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# I clienti UE non possono completare i pagamenti

Questo articolo fissa il problema relativo ai clienti dell&#39;Unione europea che non sono in grado di completare i pagamenti.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud, tutte le versioni
* Adobe Commerce on-premise 2.2.x, 2.3.x
* Magento Open Source 2.2.x, 2.3.x

## Problema

I clienti dell&#39;UE lamentano che le loro operazioni con carta di credito sono state rifiutate.

## Causa

L&#39;Unione europea ha rivisto il regolamento denominato Payment Services Directive (PSD) con una versione aggiornata di [PSD2](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32015L2366&amp;from=EN). Si tratta di una direttiva dell&#39;Unione europea (UE) che disciplina i servizi di pagamento e i prestatori di servizi di pagamento in tutta l&#39;UE e nello Spazio economico europeo (SEE). Il requisito di PSD2 è un&#39;autenticazione avanzata dei clienti per aumentare la sicurezza e l&#39;autenticazione dei dati di pagamento. Se le soluzioni di pagamento non sono conformi ai requisiti della direttiva, i clienti potrebbero non essere in grado di completare i pagamenti. Per ulteriori informazioni, consulta il [post correlato su Adobe Commerce DevBlog](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460).

## Soluzione

Segui i consigli della sezione [Recommendations provider di pagamenti Adobe Commerce di DevBlog](https://community.magento.com/t5/Magento-DevBlog/3D-Secure-2-0-changes/ba-p/136460#recommendations).
