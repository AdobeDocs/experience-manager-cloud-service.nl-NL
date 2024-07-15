---
title: Rapportering in Dynamic Media
description: Leer hoe u een foutrapport opvraagt voor Dynamic Media die URL's levert die mislukken.
contentOwner: Rick Brough
feature: Asset Management
role: User
hide: true
hidefromtoc: true
exl-id: 2488f813-df15-4dbb-8747-f827ee5925e1
source-git-commit: aa7429d9ca9f67979303c0b85c9dbd5b8c74c05c
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 0%

---

# Een foutrapport aanvragen voor URL&#39;s die niet zijn geleverd door Dynamic Media

U kunt om een foutenrapport verzoeken dat Dynamic Media URLs identificeert die op leveringstijd ontbrak. Het rapport is een aggregatie van gegevens tot vijf dagen en is beschikbaar in CSV-indeling. Het foutenrapport bevat de volgende informatie:

* Leverings-URL voor Dynamic Media is mislukt - Een mislukte URL is een door Dynamic Media gegenereerde URL die geen inhoud kan produceren op het moment van levering.
* Referrer-URL - De referentie-URL waarvan de mislukte leverings-URL wordt aangeroepen.
* Aantal mislukkingen - Het aantal keren dat de leverings-URL is geladen en dat tot een fout heeft geleid.

Wanneer u om het foutenrapport verzoekt, e-mailt het team van Adobe Dynamic Media het rapport aan u, in Csv formaat. Het heeft betrekking op een periode van vijf dagen vanaf de dag waarop uw verzoek is ingediend.

U kunt een foutenrapport eens per maand, voor een bepaald bedrijf aanvragen.

**om een foutenrapport voor levering URLs van Dynamic Media te verzoeken die ontbreken:**

1. [ verzend een e-mail naar reports-dynamic-media@adobe.com ](mailto:reports-dynamic-media@adobe.com) met de bedrijfsnaam die met uw rekening van Dynamic Media wordt geassocieerd.

   Als u niet de bedrijfsnaam kent, zie de ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/config-dm.html?lang=en#configuring-dynamic-media-cloud-services) pagina van de Configuratie 0} Dynamic Media {in **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Dynamic Media Configuation]**. [ Voor Browser van de Configuratie van Dynamic Media pagina, klik **[!UICONTROL global]**, selecteer *[Dynamic_Media_folder_icon]* checkbox, dan uitgezochte **[!UICONTROL Edit]**. U hebt beheerdersrechten nodig AEM u toegang wilt krijgen tot de Dynamic Media Configuration-pagina.

   ![ die tot de pagina van de Configuratie van Dynamic Media toegang hebben.](/help/assets/dynamic-media/assets/reporting-accessdmconfig.png)
