---
title: Inhoud uit bron extraheren
description: Inhoud uit bron extraheren
source-git-commit: 86df5e29567d9da8bc56c1c62b11ab1444586415
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 39%

---


# Inhoud uit bron extraheren {#extracting-content}

## Extractieproces in gereedschap voor inhoudsoverdracht {#extraction-process}

>[!CONTEXTUALHELP]
>id="aemcloud_ctt_extraction"
>title="Inhoud extraheren"
>abstract="Extractie heeft betrekking op het extraheren van inhoud van de bron AEM instantie naar een tijdelijk gebied dat migratieset wordt genoemd. Een migratieset is een opslaggebied op de cloud dat door Adobe wordt geleverd om overgedragen content tijdelijk op te slaan tussen de AEM-broninstantie en de AEM Cloud Service-instantie."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-content-transfer-tool.html?lang=en#top-up-extraction-process" text="Extractie naar boven"

>[!IMPORTANT]
>Voer het gereedschap Toewijzing gebruiker uit voordat u inhoud uit de bron extraheert. Zie [Het gereedschap Toewijzing gebruiker gebruiken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html?lang=en) voor meer informatie .

Voer de onderstaande stappen uit om uw migratieset te extraheren uit de Content Transfer-tool:
>[!NOTE]
>Als Amazon S3 of Azure Data Store wordt gebruikt als het type gegevensopslag, kunt u de optionele stap voor het kopiëren uitvoeren om de extractiefase aanzienlijk te versnellen. Om dit te doen zult u moeten vormen en `azcopy.config` bestand voordat extractie wordt uitgevoerd. Zie [Afhandeling van grote opslagplaatsen voor inhoud](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) voor meer informatie .

1. Een migratieset selecteren vanuit **Inhoud overbrengen** wizard en klik op **Extraheren** om de extractie te starten.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/extraction-01.png)

1. De **Extractie van migratieset** wordt weergegeven en klikt u op **Extraheren** om de extractiefase te starten.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/extraction-02.png)

   >[!NOTE]
   >U kunt de stagingcontainer tijdens de extractiefase overschrijven indien u dat wilt.

1. De **Extractie** wordt nu het veld weergegeven **UITVOEREN** status om aan te geven dat de extractie wordt uitgevoerd.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/extraction-03.png)

   Zodra de extractie is voltooid, wordt de status van de migratieset bijgewerkt naar **FINISHED** en wordt een *effen groen* wolkpictogram weergegeven onder het veld **INFO**.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/extraction-04.png)

   >[!IMPORTANT]
   >De interface heeft een functie voor automatisch opnieuw laden waarmee de **Inhoud overbrengen** elke 30 seconden.
   >Bij het starten van de extractiefase wordt een schrijfvergrendeling geactiveerd. Deze wordt na *60 seconden* weer vrijgegeven. Als u een extractie stopt, moet u dus eerst een minuut wachten tot de vergrendeling is gedeactiveerd voordat u opnieuw een extractie start.

## Extractie aanvullen {#top-up-extraction-process}

De Content Transfer-tool heeft een functie die ondersteuning biedt voor differentiële aanvulling van content. Hierbij worden alleen die wijzigingen overgedragen die zijn aangebracht sinds de vorige activiteit voor contentoverdracht.

>[!NOTE]
>Na de eerste overdracht van content wordt het aangeraden om regelmatig differentiële aanvullingen van content uit te voeren. Zo houdt u de periode waarin content wordt &#39;bevroren&#39; voor de uiteindelijke differentiële contentoverdracht zo kort mogelijk, voordat u live gaat op Cloud Service.
>Bovendien is het van essentieel belang dat de inhoudstructuur van bestaande inhoud niet wordt gewijzigd vanaf het moment dat de eerste extractie wordt uitgevoerd tot het moment dat de aanvullende extractie wordt uitgevoerd. Top-ups kunnen niet worden uitgevoerd op inhoud waarvan de structuur is gewijzigd sinds de eerste extractie. Zorg ervoor dat u dit tijdens het migratieproces beperkt.

Als het extractieproces is voltooid, kunt u deltacontent overdragen via de extractiemethode voor aanvullen.

Voer de onderstaande stappen uit:

1. Ga naar de **Inhoud overbrengen** en selecteert u de migratieset waarvoor u de extractie bovenaan wilt uitvoeren. Klik op **Extract** om de extractie te starten.

   ![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/extraction-05.png)

1. De **Extractie van migratieset** wordt weergegeven. Klikken op **Extraheren**.

   >[!IMPORTANT]
   >Zorg dat de optie **Overwrite staging container during extraction** (voor het overschrijven van de stagingcontainer tijdens de extractie) is uitgeschakeld.
   >![afbeelding](/help/move-to-cloud-service/content-transfer-tool/assets-ctt/extraction-06.png)


## Volgende functies {#whats-next}

Nadat u de opdracht Inhoud uit bron extraheren hebt geleerd in het gereedschap Inhoud overbrengen, kunt u nu leren hoe u het opmaakproces in het gereedschap Inhoud overbrengen start. Zie [Inhoud in doel invoegen](/help/move-to-cloud-service/content-transfer-tool/using-content-transfer-tool/ingesting-content.md) om te leren hoe u uw migratieset kunt opnemen via het gereedschap Inhoud overbrengen.
