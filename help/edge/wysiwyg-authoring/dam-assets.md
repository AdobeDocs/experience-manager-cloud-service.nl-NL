---
title: Pagina's met DAM Assets publiceren met behulp van Edge Delivery Services
description: Leer welke instellingen nodig zijn om ervoor te zorgen dat uw DAM-middelen voor uw pagina's naadloos worden gepubliceerd naar Edge Delivery Services.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 160f0474-a72d-4183-a2b2-2f8ba177605d
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# Pagina&#39;s met DAM Assets publiceren met behulp van Edge Delivery Services {#dam-assets}

Leer welke instellingen nodig zijn om ervoor te zorgen dat uw DAM-middelen voor uw pagina&#39;s naadloos worden gepubliceerd naar Edge Delivery Services.

## Universal Editor, DAM Assets en Edge Delivery {#overview}

Wanneer u inhoud bewerkt voor de Universal Editor, kunt u natuurlijk elementen selecteren in de DAM. Wanneer u uw inhoud naar Edge Delivery Services publiceert, wordt de gerelateerde DAM-inhoud ook gepubliceerd.

Om dit naadloze gedrag te garanderen, moeten AEM en Edge Delivery Services juiste toegang hebben tot het DAM om te kunnen publiceren. Dit omvat:

* [ Zorgen dat de activa omslagen toegankelijk ](#accessible) zijn.
* [ Zorgen dat de activa omslag de juiste configuratie (zoals vereist) ](#configuration) wordt toegewezen.

## Assets-mappen toegankelijk maken {#accessible}

Wanneer het publiceren van pagina&#39;s van AEM aan Edge Delivery Services, [ wordt een technische rekening ](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) gebruikt. Dit account, met een naam in de notatie `<hash>@techacct.adobe.com` , wordt automatisch als een gebruiker gemaakt in AEM door Cloud Manager wanneer u een pagina publiceert die is gemaakt met de Universal Editor.

![ Technische rekening ](/help/edge/wysiwyg-authoring/assets/dam-assets/technical-account.png)

Deze technische account moet toegangsrechten hebben tot alle DAM-mappen om de inhoud ervan te kunnen publiceren. U kunt:

* Gebruik geen DAM-privémappen.
* Bied gebruikers van technische accounts toegang tot de DAM-mappen.

## Ervoor zorgen dat aan de Assets-map de juiste configuratie is toegewezen {#configuration}

In het algemeen is het voldoende dat uw technische account toegang heeft tot uw middelen in DAM om uw middelen samen met uw pagina&#39;s naar Edge Delivery Services te publiceren.

In twee extra gevallen is echter aanvullende configuratie nodig:

* Als u pagina&#39;s met andere elementen dan afbeeldingen, zoals PDF of video&#39;s, naar Edge Delivery Services wilt publiceren.
* Als u afbeeldingselementen onafhankelijk van de pagina&#39;s naar Edge Delivery Services wilt publiceren.

Om beide gebruiksgevallen te steunen, moet de a [ configuratie ](/help/implementing/developing/introduction/configurations.md) aan de omslag worden toegewezen DAM.

1. Meld u aan bij uw AEM ontwerpomgeving.
1. Onder **Plaatsen** selecteer de plaats waar u uw activa of de plaats publiceert waarmee de activa zullen worden geassocieerd.
1. Tik of klik **Eigenschappen** in de hulpmiddelbar.
1. Op het **Geavanceerde** lusje in het eigenschappenvenster, neem nota van de configuratie op de gebied **Configuratie van de Wolk**.
   * Dit wordt automatisch gemaakt wanneer u uw site maakt in de indeling `/conf/<site-name>` .
1. Tik of klik **annuleer** in het eigenschappenvenster en navigeer aan **Assets** -> **Dossiers** en selecteer uw omslag DAM.
1. Tik of klik **Eigenschappen** in de hulpmiddelbar.
1. Op het **Cloud Servicen** lusje van het eigenschappenvenster, op het **gebied van de Configuratie van de Wolk**, selecteer de zelfde configuratie zoals u eerder noteerde.
1. Tik of klik **sparen &amp; sluit**.
