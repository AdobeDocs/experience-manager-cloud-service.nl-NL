---
title: Inhoud uit bron extraheren
description: Inhoud uit bron extraheren
exl-id: c5c08c4e-d5c3-4a66-873e-96986e094fd3
source-git-commit: a2e14d73fd6b8138799799c6408a0846224cd8c9
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 19%

---

# Inhoud uit bron extraheren {#extracting-content}

## Extractieproces in gereedschap voor inhoudsoverdracht {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="Inhoud extraheren"
>abstract="Extractie heeft betrekking op het extraheren van inhoud van de bron AEM instantie naar een tijdelijk gebied dat migratieset wordt genoemd. Een migratieset is een opslaggebied op de cloud dat door Adobe wordt geleverd om overgedragen content tijdelijk op te slaan tussen de AEM-broninstantie en de AEM Cloud Service-instantie."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-extraction-process" text="Extractie naar boven"


Voer de onderstaande stappen uit om uw migratieset te extraheren uit de Content Transfer-tool:

>[!NOTE]
>Als Amazon S3, Azure Data Store of File Data Store wordt gebruikt als het type gegevensopslag, kunt u de optionele stap voor het kopiëren uitvoeren om de extractiefase aanzienlijk te versnellen. De pre-copy stap is het meest effectief voor de eerste volledige extractie en inname. Om dit te doen zult u moeten vormen en `azcopy.config` bestand voordat extractie wordt uitgevoerd. Zie [Afhandeling van grote opslagplaatsen voor inhoud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) voor meer informatie .

>[!IMPORTANT]
>Voer het gereedschap Toewijzing gebruiker uit voordat u inhoud uit de bron extraheert. Zie [Het gereedschap Toewijzing gebruiker gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html?lang=en) voor meer informatie .

1. Een migratieset selecteren vanuit **Inhoud overbrengen** wizard en klik op **Extraheren** om de extractie te starten.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam12.png)

   >[!IMPORTANT]
   >
   >Zorg ervoor dat de Extractiesleutel geldig is en niet dicht bij zijn vervaldatum is. Als deze bijna verlopen is, kunt u de Extractietoets vernieuwen door de migratieset te selecteren en op Eigenschappen te klikken. Klikken op **Vernieuwen**. Hiermee gaat u naar Cloud Acceleration Manager waar u kunt klikken op **Extractietoets kopiëren**. Telkens wanneer u klikt op **Extractietoets kopiëren**Er wordt een nieuwe extractiesleutel gegenereerd die 14 dagen geldig is vanaf het moment waarop deze is gemaakt.
   >[!afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam13.png)

1. Hiermee wordt het dialoogvenster Extractie weergegeven. Klikken op **Extraheren** om de extractiefase te starten.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam14.png)

   >[!NOTE]
   >U kunt de container tijdens de extractiefase overschrijven. Indien **Stapelcontainer overschrijven** is uitgeschakeld, kan het extracties versnellen voor volgende migraties waarbij de paden van de inhoud of de instellingen van versies niet zijn gewijzigd. Als de instellingen voor de inhoudspaden of de include-versies echter zijn gewijzigd, **Stapelcontainer overschrijven** moet zijn ingeschakeld.

   >[!IMPORTANT]
   >Als de gebruikerstoewijzing niet is uitgevoerd op deze migratieset voordat de inhoud uit de bron is geëxtraheerd, wordt een waarschuwing weergegeven met de melding dat de stap Gebruikerstoewijzing in behandeling is, zoals in de bovenstaande afbeelding wordt getoond. Klikken op **Kaartgebruikers** om het gereedschap Toewijzing gebruiker uit te voeren.

1. De **Extractie** wordt nu het veld weergegeven **UITVOEREN** status om aan te geven dat de extractie wordt uitgevoerd.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam15.png)

   U kunt op **Voortgang van weergave** voor een korrelig beeld van de lopende extractie.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam16.png)

   U kunt de voortgang van de extractiefase ook controleren vanuit Cloud Acceleration Manager door de pagina Content Transfer te bezoeken.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam17.png)

1. Als de extractie is voltooid, controleert u de overige kolommen zoals **Bron** en **Paden** voor details van de migratieset die u hebt gevuld door op te klikken **...** en vervolgens **Details weergeven**.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam18.png)


## Extractie aanvullen {#top-up-extraction-process}

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>Na de eerste overdracht van content wordt het aangeraden om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service. Als u de voorkopiestap hebt gebruikt voor de eerste volledige extractie, kunt u de voorkopie voor volgende aanvullende extracties overslaan (als de instelbare migratie kleiner is dan 200 GB) omdat dit tijd kan toevoegen aan het gehele proces.
>Bovendien is het van essentieel belang dat de inhoudstructuur van bestaande inhoud niet wordt gewijzigd vanaf het moment dat de eerste extractie wordt uitgevoerd tot het moment dat de aanvullende extractie wordt uitgevoerd. Top-ups kunnen niet worden uitgevoerd op inhoud waarvan de structuur is gewijzigd sinds de eerste extractie. Zorg ervoor dat u dit tijdens het migratieproces beperkt.

Als het extractieproces is voltooid, kunt u deltacontent overdragen via de extractiemethode voor aanvullen.

Voer de onderstaande stappen uit:

1. Ga naar de **Inhoud overbrengen** en selecteert u de migratieset waarvoor u de extractie bovenaan wilt uitvoeren. Klik op **Extract** om de extractie te starten.

   ![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam19.png)

1. De **Extractie van migratieset** wordt weergegeven. Klikken op **Extraheren**.

   >[!IMPORTANT]
   >Zorg dat de optie **Overwrite staging container during extraction** (voor het overschrijven van de stagingcontainer tijdens de extractie) is uitgeschakeld.
   >![afbeelding](/help/journey-migration/content-transfer-tool/assets-ctt/cttcam20.png)


## Volgende functies {#whats-next}

Nadat u de opdracht Inhoud uit bron extraheren hebt geleerd in het gereedschap Inhoud overbrengen, kunt u nu leren hoe u het opmaakproces in het gereedschap Inhoud overbrengen start. Zie [Inhoud in doel invoegen](/help/journey-migration/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) om te leren hoe u uw migratieset kunt opnemen via het gereedschap Inhoud overbrengen.
