---
title: Impossibile accedere all’interfaccia utente di Adobe Commerce sull’infrastruttura cloud
description: Questo articolo fornisce soluzioni per il problema che impedisce l’accesso all’interfaccia utente di Adobe Commerce on Cloud Infrastructure e causa il messaggio "Errore 403".
exl-id: 948e4acd-abd6-4562-b9c0-771a977188ba
feature: Cloud, Paas
role: Developer
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 5a951749-fac9-5bc7-9a98-ebe4ff066437
    internal-label: Cloud
  - id: 00451af3-7b97-5414-9992-3a6c269e413f
    internal-label: Paas
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
source-git-commit: 6c96745ec333f45361f77f8116cd9a5684da0aa0
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%
---
# Impossibile accedere all’interfaccia utente di Adobe Commerce sull’infrastruttura cloud

Questo articolo fornisce soluzioni per il problema per cui non è possibile accedere all&#39;interfaccia utente di Adobe Commerce on Cloud Infrastructure e ricevere l&#39;*errore 403*.

## Problema

Quando tenti di accedere all&#39;interfaccia utente di Adobe Commerce on Cloud Infrastructure per la prima volta, viene visualizzato l&#39;errore *403: Accesso all&#39;ambiente negato*. Questo errore potrebbe verificarsi perché andando all’URL cloud per la prima volta viene caricato il ramo principale e potresti non avere accesso a tale ramo.

## Soluzione

Se ricevi un errore 403 quando accedi all’URL per la prima volta, assicurati di avere un ruolo nel ramo principale.

1. СContatta il proprietario della licenza o un utente con privilegi avanzati sul progetto e assicurati che ti abbiano fornito l&#39;accesso come **utente a livello di ambiente**, descritto anche in [Progetti cloud > Gestisci utenti da Cloud Console](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=it#manage-users-from-the-cloud-console) nella nostra documentazione per sviluppatori.

   Se disponi solo di un ruolo applicabile in un ramo specifico, dovrai passare all’URL di quel ramo, ad esempio,
   `https://console.adobecommerce.com/<owner-name>/<project-id>/<branch-name>`

   La prossima volta che accedi all’URL principale, per impostazione predefinita verrà utilizzato l’ultimo ambiente visitato.

1. Se non riesci ancora ad accedere, сcontatta il proprietario della licenza o un utente con privilegi avanzati sul progetto e assicurati che ti abbiano fornito l&#39;accesso come **utente a livello di progetto**, come descritto in [Progetti cloud > Aggiungere un utente al progetto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/user-access.html?lang=it#add-a-user-to-the-project) nella documentazione per gli sviluppatori.
1. Se l&#39;errore persiste, [invia un ticket di supporto](https://experienceleague.adobe.com/it/docs/support-resources/adobe-support-tools-guide/adobe-commerce-support/adobe-commerce-help-center-user-guide#submit-ticket).
