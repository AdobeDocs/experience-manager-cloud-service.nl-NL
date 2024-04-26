---
title: Logbestanden openen en beheren
description: Leer hoe u logboeken kunt openen en beheren om uw ontwikkelingsproces in AEM as a Cloud Service te ondersteunen.
exl-id: f17274ce-acf5-4e7d-b875-75d4938806cd
source-git-commit: d1b2226a1deec2e71056c43c84672cb4a358bc8c
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---


# Logbestanden openen en beheren {#manage-logs}

Leer hoe u logboeken kunt openen en beheren om uw ontwikkelingsproces in AEM as a Cloud Service te ondersteunen.

U kunt een lijst met beschikbare logbestanden voor de geselecteerde omgeving openen met de opdracht **Omgevingen** kaart van **Overzicht** pagina of pagina Omgevingsdetails.

Logboeken worden zeven dagen bewaard.

## Logbestanden downloaden {#download-logs}

Ga als volgt te werk om logbestanden te downloaden:

1. Aanmelden bij Cloud Manager [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) en selecteert u de gewenste organisatie.

1. Op de **[Mijn programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)** -console, selecteert u het programma.

1. Ga naar de **Omgevingen** kaart van **Overzicht** pagina.

1. Selecteren **Logbestanden downloaden** in het ovaalmenu.

   ![Menu-item voor logbestanden downloaden](assets/download-logs1.png)

1. In de **Logbestanden downloaden** selecteert u de gewenste **Service** in het keuzemenu

   ![Het dialoogvenster Logbestanden downloaden](assets/download-preview.png)

   In geval van [Aanvullende publicatieregio&#39;s](/help/operations/additional-publish-regions.md) zijn ingeschakeld voor uw omgeving, kunt u elk gebied selecteren en de bijbehorende logbestanden afzonderlijk downloaden, zoals hieronder wordt weergegeven:

   ![Logbestanden downloaden voor extra publicatiegebieden](assets/download-publish-region-logs.png)

1. Nadat u de service hebt geselecteerd, klikt u op het downloadpictogram naast het logbestand dat u wilt ophalen.

U kunt uw logbestanden ook openen via het dialoogvenster **Omgevingen** pagina.

![Logbestanden van het scherm Environment](assets/download-logs.png)

## Logbestanden via API {#logs-through-api}

Naast het downloaden van logboeken door UI, zijn de logboeken beschikbaar door API en bevel-lijn interface.

Als u de logbestanden voor een specifieke omgeving wilt downloaden, lijkt de opdracht op het volgende.

```shell
$ aio cloudmanager:download-logs --programId 5 1884 author aemerror
```

Ook, kunt u logboeken als bevel-lijn interface staart.

```shell
$ aio cloudmanager:tail-log --programId 5 1884 author aemerror
```

U kunt de volgende opdrachten gebruiken om de milieu-id (1884 in dit voorbeeld) en de beschikbare service- of lognaamaopties te verkrijgen.

```shell
$ aio cloudmanager:list-environments
Environment Id Name                     Type  Description                          
1884           FoundationInternal_dev   dev   Foundation Internal Dev environment  
1884           FoundationInternal_stage stage Foundation Internal STAGE environment
1884           FoundationInternal_prod  prod  Foundation Internal Prod environment
 
 
$ aio cloudmanager:list-available-log-options 1884
Environment Id Service    Name         
1884           author     aemerror     
1884           author     aemrequest   
1884           author     aemaccess    
1884           publish    aemerror     
1884           publish    aemrequest   
1884           publish    aemaccess    
1884           dispatcher httpderror   
1884           dispatcher aemdispatcher
1884           dispatcher httpdaccess
```

### Aanvullende bronnen {#resources}

>[!TIP]
>
>Uitchecken [deze videobron](https://app.frame.io/reviews/28cdf463-b7fc-443b-a54a-93cb7da6567e/dbf158f1-568b-4efc-8fbc-3b241561cbab) voor meer informatie over foutopsporing AEM as a Cloud Service.

Zie de volgende aanvullende bronnen voor meer informatie over de API en Adobe I/O CLI van Cloud Manager:

* [Documentatie voor API voor cloud Manager](https://developer.adobe.com/experience-cloud/cloud-manager/)
* [ADOBE I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager)

Zie de volgende aanvullende bronnen voor meer informatie over logbestanden in AEM as a Cloud Service:

* [Cloud 5 AEM logbestanden](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/cloud-5/cloud5-aem-log-files.html)
* [Foutopsporing AEM as a Cloud Service met logbestanden](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs.html)
