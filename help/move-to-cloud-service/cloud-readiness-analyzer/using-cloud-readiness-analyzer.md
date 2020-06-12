---
title: Cloud Readiness Analyzer gebruiken
description: Cloud Readiness Analyzer gebruiken
translation-type: tm+mt
source-git-commit: 1739f81d4894f3e04cc4119f344a3bea5bd042d8
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 3%

---


# Cloud Readiness Analyzer gebruiken {#using-cloud-readiness-analyzer}

## Belangrijke overwegingen voor het gebruik van Cloud Readiness Analyzer {#imp-considerations}

Volg de onderstaande sectie om inzicht te krijgen in de belangrijke overwegingen bij het uitvoeren van de Cloud Readiness Analyzer (CRA):

* CRA wordt ondersteund op AEM-broninstanties met versie 6.1 en hoger
* CRA kan in elke omgeving worden uitgevoerd (bij voorkeur in *een werkgebiedomgeving* )

   >[!NOTE]
   >Om het ontdekkingstarief te verhogen en om het even welke vertragingen op bedrijfskritieke instanties te vermijden, wordt het geadviseerd om CRA op de bronauteur het opvoeren milieu&#39;s in werking te stellen die zo dicht mogelijk aan productiegroepen op de gebieden van aanpassingen, configuraties, inhoud en gebruikerstoepassingen zijn. Het kan ook worden uitgevoerd op een kloon van de *publicatieomgeving* .

## Beschikbaarheid {#availability}

De Cloud Readiness Analyzer kan als zip- dossier van het portaal van de Distributie van de Software worden gedownload. U kunt het pakket via Package Manager installeren op uw AEM-broninstantie (Adobe Experience Manager).

>[!NOTE]
>Download de Cloud Readiness Analyzer van het Portaal van de Distributie van de Software *hangend*.

## De Cloud Readiness Analyzer uitvoeren {#running-tool}

Ga als volgt te werk om Cloud Readiness Analyzer uit te voeren:

1. Select the Adobe Experience Manager and navigate to tools -> **Operations** -> **Cloud Readiness Analyzer**.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-1.png)

1. Nadat u op **Cloud Readiness Analyzer** hebt geklikt, wordt het rapport gegenereerd en na enkele minuten is het samenvattingsrapport beschikbaar voor uw AEM-instantie.

   >[!NOTE]
   >U moet naar beneden schuiven om het volledige rapport te kunnen bekijken.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-2.png)

### De resultaten bekijken in het overzichtsrapport {#viewing-the-results}

>[!IMPORTANT]
>De rapporten die zijn gegenereerd op basis van Cloud Readiness Analyzer zijn gebaseerd op patroondetectoren. Raadpleeg [Patroondetectoren](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/upgrading/pattern-detector.html) voor meer informatie.

Wanneer u de pagina omlaag hebt geschoven om het volledige samenvattingsrapport weer te geven, ziet u de volgende informatie voor elke categorie die in het rapport wordt gemarkeerd:

1. **Importniveau**

   In de volgende tabel wordt de betekenis van de verschillende belangrijke niveaus voor de analyse van patroondetectoren en gereedheid voor cloud beschreven.

   | Importniveau | Beschrijving |
   |--- |--- |
   | INFO/0 | Deze bevinding wordt ter informatie verstrekt. |
   | ADVISORY/1 | Deze bevinding is mogelijk een upgradeprobleem. Verdere onderzoeken worden aanbevolen. |
   | MAJOR/2 | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt. |
   | KRITIEK/3 | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt om functieverlies of prestatieverlies te voorkomen. |

1. **Beschrijving** De beschrijving bevat informatie over de gerapporteerde categorie.

1. **Documentatie URL** De documentatie URL staat u toe om de technische documentatie voor het bijbehorende type te bekijken.

1. **Bericht** Een beschrijving van het vinden in één enkel bericht.

### De resultaten weergeven in een CSV-indeling {#viewing-the-results-csv}

Het samenvattingsrapport is beschikbaar in de AEM-gebruikersinterface. U kunt het volledige rapport in een komma-gescheiden formaat (CSV) downloaden dat tijdens het refactoring proces nuttig is.

Voer de onderstaande stappen uit om een CSV-indeling van uw samenvattingsrapport te genereren:

1. 
   1. Select the Adobe Experience Manager and navigate to tools -> **Operations** -> **Cloud Readiness Analyzer**.

1. Zodra het rapport beschikbaar is, klik op **CSV** om het volledige samenvattingsrapport in komma-gescheiden waarden (CSV) formaat, zoals aangetoond in hieronder figuur te downloaden.

![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-3.png)


#### Het rapport bekijken in AEM 6.1 Instanties {#aem-instances-report}

Voer de onderstaande stappen uit om het CSV-rapport voor Adobe Experience Manager (AEM) 6.1 te downloaden:

1.Navigeer aan **Adobe Experience Manager Web ConsoleConfiguration** gebruikend `https://serveraddress:serverport/system/console/configMgr`.

1. Selecteer het tabblad **Status** en zoek in de vervolgkeuzelijst naar **Patroondetector** , zoals in de onderstaande afbeelding wordt getoond.

   ![afbeelding](/help/move-to-cloud-service/cloud-readiness-analyzer/assets/cra-4.png)

1. U kunt het samenvattingsrapport downloaden in een ZIP-map of in JSON-indeling.


