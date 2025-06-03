---
title: Aan de slag met Refactoring Tools
description: Leer hoe u aan de slag kunt met Refactoring Tools in AEM as a Cloud Service
source-git-commit: 20bb756c4a2eb37341da4582f19cf41e4d60304a
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 1%

---

# Aan de slag met Refactoring Tools {#getting-started-refactoring-tools}

## Beschikbaarheid {#availability}

<!-- Alexandru: duplicate contextualhelp id, drafting this for now

>[!CONTEXTUALHELP]
>id="aemcloud_rs_upload"
>title="Download"
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/release-notes/release-notes-current.html" text="Release Notes"
>additional-url="https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html" text="Software Distribution Portal"

-->

## De Refactoring-gereedschappen uitvoeren {#running-refactoring-tools}

Gebruik het gereedschap Refactoring om uw code te migreren voor compatibiliteit met AEM as a Cloud Service.

1. Als u nog geen CAM project hebt gecreeerd, verwijs naar [ Creërend en Lerend een Project in CAM ](/help/journey-migration/cloud-acceleration-manager/using-cam/getting-started-cam.md#create-project).
1. Klik de **Refactoring van de Code** kaart om de broncode te uploaden.

   ![afbeelding](/help/journey-migration/refactoring-tools/assets/rscam1.png)

1. Wanneer u eerst tot de **Mening van de Code van Source** toegang hebt, zult u een lege staat zien die u ertoe aanzet om uw broncode te uploaden.

   ![afbeelding](/help/journey-migration/refactoring-tools/assets/rscam2.png)

&#x200B;---

## Source-code uploaden {#uploading}

Wanneer de klanten eerst tot **Refactoring Hulpmiddelen** toegang hebben, worden zij voorgesteld met een lege staat in de **Mening van de Code van Source**. Voer de onderstaande stappen uit om uw project te uploaden en het inspectieproces te starten:

1. **toegang tot het Project uploadt Pagina**\
   Klik op het **Project uploadt** knoop in de lege staat om het uploadproces te beginnen.

   ![afbeelding](/help/journey-migration/refactoring-tools/assets/rscam3.png)

1. **upload Uw Code van Source**
   - Selecteer het ZIP-bestand voor de broncode in het dialoogvenster Uploaden.
   - Klik **uploaden** om te beginnen.
   - De voortgang van het uploaden wordt weergegeven in het dialoogvenster. De duur is afhankelijk van de grootte van uw project.

   ![afbeelding](/help/journey-migration/refactoring-tools/assets/rscam4.png)

1. **Proces van de Inspectie**
   - Na het uploaden, begint het **Proces van de Inspectie** automatisch op de achtergrond.
   - De **Mening van de Code van Source** zal nu uw geupload project en zijn inspectiestatus tonen.

1. **Status van de Inspectie** Het inspectieproces wordt ontworpen om de uitvoering van refactoring hulpmiddelen te vereenvoudigen door overheadkosten van handconfiguraties te verminderen.

   De inspectie zal een van de volgende statussen tonen:
   - **Lopend** - de inspectie is lopend.
   - **Klaar** - de inspectie is volledig; u kunt refactoring hulpmiddelen nu in werking stellen.
   - **Ontbroken** - een fout kwam voor. Klik op het project om het inspectieverslag te bekijken en eventuele problemen op te lossen.

   ![afbeelding](/help/journey-migration/refactoring-tools/assets/rscam5.png)

>[!NOTE]
>Als u een nieuw project uploadt, wordt het bestaande project verwijderd. Zorg ervoor dat de benodigde gegevens zijn opgeslagen voordat u verdergaat.

>[!NOTE]
>Refactoring-taken kunnen alleen worden uitgevoerd als het uploaden van de broncode is gelukt.

&#x200B;---

## Refactoring {#refactoring-jobs}

Wanneer u het **RefactoringBaan** lusje klikt, zult u een lijst van bestaande banen zien. Als er nog geen taken zijn gemaakt, wordt er een lege status weergegeven met de vraag of er nieuwe taken zijn gemaakt.

![afbeelding](/help/journey-migration/refactoring-tools/assets/rscam6.png)

### &#x200B;1. Maak een nieuwe Refactoring-taak

- Klik **creëren Nieuwe knoop van de Baan**.
- Selecteer het gewenste gereedschap of de gereedschappen voor het refactoring.
- Klik **Begin** om het refactoring proces in werking te stellen.

![afbeelding](/help/journey-migration/refactoring-tools/assets/rscam7.png)

>[!NOTE]
>U kunt individuele refactoring banen teweegbrengen of alle beschikbare hulpmiddelen in één gaan gebruiken **Alle Hulpmiddelen samen** optie.

&#x200B;---

### &#x200B;2. Taakstatus

- **Lopend** - de baan is momenteel lopend. De status wordt automatisch bijgewerkt na voltooiing of mislukking.
- **Voltooid** - de baan met succes gebeëindigd. U kunt nu de resultaten controleren of de vernieuwde code downloaden.
- **Ontbroken** - de baan ontmoette een fout. Klik op de taak om gedetailleerde logbestanden weer te geven en het probleem op te lossen.

![afbeelding](/help/journey-migration/refactoring-tools/assets/rscam8.png)

Wanneer de baan met succes wordt voltooid, wordt de **Download** knoop beschikbaar, toestaand u om terug te winnen:

- **het Refactored Project**: Dit is de bijgewerkte code nadat de transformatie wordt toegepast. Klanten kunnen de nieuwste code voor hun project downloaden.
- **Logboeken van de Activiteit**: Tijdens de baanuitvoering, worden alle stappen die door het hulpmiddel worden uitgevoerd en de aangebrachte veranderingen geregistreerd als deel van dit.
- **het Rapport van Bevindingen**: Dit rapport bevat punten die niet volledig door het hulpmiddel werden uitgevoerd maar nog moeten worden gericht. Al dergelijke veranderingen worden hier geregistreerd.

![afbeelding](/help/journey-migration/refactoring-tools/assets/rscam9.png)

>[!NOTE]
>Elke taak kan tot 1 uur duren. Neem contact op met Adobe Support als de status niet is bijgewerkt.

