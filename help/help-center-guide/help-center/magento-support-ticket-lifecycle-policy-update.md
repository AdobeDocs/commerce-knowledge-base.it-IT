---
title: Aggiornamento dei criteri del ciclo di vita dei ticket di supporto Adobe Commerce
description: Questo articolo fornisce informazioni sull’aggiornamento dei criteri per il ciclo di vita dei ticket di supporto Adobe Commerce.
exl-id: c3fbcb4a-107f-48b3-afed-b9a0c5d0425c
source-git-commit: c1c2bd29e14f4cbfffb235801e95ec7cbb7c7a55
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 1%

---

# Aggiornamento dei criteri del ciclo di vita dei ticket di supporto Adobe Commerce

Questo articolo fornisce informazioni sull’aggiornamento dei criteri per il ciclo di vita dei ticket di supporto Adobe Commerce.

Nella tabella seguente sono illustrati gli scenari aggiornati. Puoi trovare i dettagli di ogni scenario nella sezione seguente.

<table>
 <tbody>
 <tr>
 <td class="wysiwyg-text-align-center"> </td>
 <td class="wysiwyg-text-align-center"><strong>Stato ticket</strong></td>
 <td class="wysiwyg-text-align-center"><strong>Giorni per "risolti"</strong></td>
 <td class="wysiwyg-text-align-center"><strong>Giorni a "Chiuso"</strong></td>
 <td class="wysiwyg-text-align-center"><strong>Tempistica delle notifiche</strong></td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>Il tecnico fornisce una soluzione</strong></td>
 <td class="wysiwyg-text-align-center">"In attesa della tua risposta"</td>
 <td class="wysiwyg-text-align-center">3</td>
 <td class="wysiwyg-text-align-center">6</td>
 <td class="wysiwyg-text-align-center">Giorni 3 e 6</td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>In attesa di informazioni dal cliente</strong></td>
 <td class="wysiwyg-text-align-center">"In attesa della tua risposta"</td>
 <td class="wysiwyg-text-align-center">N/D</td>
 <td class="wysiwyg-text-align-center">6</td>
 <td class="wysiwyg-text-align-center">Giorni 1, 3 e 6</td>
 </tr>
 <tr>
 <td class="wysiwyg-text-align-left"><strong>Il cliente imposta su "Risolto" o l’ingegnere della richiesta su "Risolto"</strong></td>
 <td class="wysiwyg-text-align-center">"Risolto"</td>
 <td class="wysiwyg-text-align-center">Immediato</td>
 <td class="wysiwyg-text-align-center">1</td>
 <td class="wysiwyg-text-align-center">Giorno 1</td>
 </tr>
 </tbody>
 </table>

## Scenari in dettaglio

### Quando un tecnico fornisce una soluzione

1. Una volta fornita una soluzione al cliente, il tecnico imposta lo stato del ticket su &quot;In attesa di risposta&quot;.
1. Se il cliente non risponde per 3 giorni dopo che lo stato è cambiato in &quot;In attesa di risposta&quot;, il ticket viene spostato in &quot;Risolto&quot; e il cliente riceve una notifica.
1. Se non viene ricevuta alcuna risposta dal cliente per 6 giorni dopo che lo stato è cambiato in &quot;In attesa della risposta&quot; - il ticket viene chiuso e il cliente viene informato.

### Quando un cliente richiede informazioni aggiuntive

1. Se è necessario un aggiornamento da parte del cliente, il tecnico imposta il ticket su &quot;In attesa della risposta&quot;.
1. Le notifiche vengono inviate al cliente il giorno 1 e il giorno 3 per richiedere il follow-up del cliente.
1. Se non viene ricevuta alcuna risposta dal cliente per 6 giorni dopo che lo stato è cambiato in &quot;In attesa della risposta&quot; - il ticket viene chiuso e il cliente viene informato.

### Ticket impostato su &quot;Risolto&quot; da un cliente

Quando un ticket è impostato su &quot;Risolto&quot; da un cliente, viene chiuso in un giorno e il cliente riceve una notifica.

### Il cliente indirizza il supporto per chiudere il ticket

Quando un cliente ordina al supporto Adobe Commerce di chiudere il ticket, questo viene chiuso in una giornata e il cliente ne viene informato.

## Lettura correlata

* [Invia un ticket di supporto](/help/help-center-guide/help-center/magento-help-center-user-guide.md#submit-ticket)
* [Il collegamento &quot;Invia un ticket&quot; non viene visualizzato nella pagina iniziale del Centro assistenza Adobe Commerce](/help/help-center-guide/help-center/magento-help-center-user-guide.md#no-submit-link)
* [Modulo di invio biglietto: il commerciante non viene visualizzato nel menu a discesa Organizzazione](/help/help-center-guide/help-center/magento-help-center-user-guide.md#merchant-not-displayed)
