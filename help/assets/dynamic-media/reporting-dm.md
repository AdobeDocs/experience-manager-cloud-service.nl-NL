---
title: Rapportering in Dynamic Media
description: Leer hoe u een foutrapport opvraagt voor Dynamic Media die URL's levert die mislukken.
contentOwner: Rick Brough
feature: Asset Management
role: User
source-git-commit: 7ce15cc755c9db589001d543c16312096d88bcf0
workflow-type: tm+mt
source-wordcount: '262'
ht-degree: 0%

---


# Een foutrapport aanvragen voor URL&#39;s die niet zijn geleverd door Dynamic Media

U kunt om een foutenrapport verzoeken dat Dynamic Media URLs identificeert die op leveringstijd ontbrak. Het rapport is een aggregatie van gegevens tot vijf dagen en is beschikbaar in CSV-indeling. Het foutenrapport bevat de volgende informatie:

* Leverings-URL voor Dynamic Media is mislukt - Een mislukte URL is een door Dynamic Media gegenereerde URL die geen inhoud kan produceren op het moment van levering.
* Referrer-URL - De referentie-URL waarvan de mislukte leverings-URL wordt aangeroepen.
* Aantal mislukkingen - Het aantal keren dat de leverings-URL is geladen en dat tot een fout heeft geleid.

Wanneer u om het foutenrapport verzoekt, e-mailt het team van Adobe Dynamic Media het rapport aan u, in Csv formaat. Het heeft betrekking op een periode van vijf dagen vanaf de dag waarop uw verzoek is ingediend.

U kunt een foutenrapport eens per maand, voor een bepaald bedrijf aanvragen.

**Om een foutenrapport voor levering URLs van Dynamic Media aan te vragen die ontbreken:**

1. [Een e-mail verzenden naar reports-dynamic-media@adobe.com](mailto:reports-dynamic-media@adobe.com) met de bedrijfsnaam die aan uw Dynamic Media-account is gekoppeld.

   Als u de bedrijfsnaam niet weet, raadpleegt u de [Dynamic Media-configuratie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/config-dm.html?lang=en#configuring-dynamic-media-cloud-services) pagina in **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Dynamic Media Configuation]**. Klik op de pagina Dynamic Media Configuration Browser (-configuratiebrowser) op **[!UICONTROL global]**, selecteert u de *[Dynamic_Media_folder_icon]* selectievakje en selecteer vervolgens **[!UICONTROL Edit]**. U hebt beheerdersrechten nodig AEM u toegang wilt krijgen tot de Dynamic Media Configuration-pagina.

   ![Toegang tot de Dynamic Media Configuration-pagina.](/help/assets/dynamic-media/assets/reporting-accessdmconfig.png)




