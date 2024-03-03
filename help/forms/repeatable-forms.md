---
description: Deze zelfstudie bevat instructies om een sectie van een formulier herhaalbaar te maken
title: Herhaalbare secties in Edge Delivery Services
feature: Edge Delivery Services
source-git-commit: fd2e5df72e965ea6f9ad09b37983f815954f915c
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---


# Herhaalbare secties in Edge Delivery

Een herhaalbare sectie is een component van een formulier dat meerdere malen wordt gedupliceerd of herhaald om informatie te verzamelen voor meerdere exemplaren van dezelfde gegevens.

Neem bijvoorbeeld een formulier dat wordt gebruikt om informatie te verzamelen van gebruikers die een lening aanvragen. Met het formulier kunnen gebruikers persoonlijke informatie verstrekken, waaronder gegevens over de coleners. De gebruikers kunnen details voor medeaanvragers ingaan, met deze sectie die herhaalbaar is.

![Herhaalbare secties in formulieren](/help/forms/assets/eds-repeatable.png)

## Vereisten

De Dienst van de Levering van de Rand van de opstelling (EDS) GitHub project gebruikend AEM boilerplate en kloon de overeenkomstige bewaarplaats GitHub op uw lokale machine. Zie [zelfstudie ontwikkelaar](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/edge-delivery/build/tutorial.html) voor meer informatie.

## Herhaalbare secties in Edge Delivery

Neem een voorbeeld van een aanvraagformulier voor een lening. Met dit formulier kunnen gebruikers persoonlijke gegevens verzenden. U kunt de details van de co-aanvrager omvatten gebruikend herhaalbare secties, met de optie om een minimum en maximum van drie co-aanvrager secties toe te voegen.

>[!NOTE]
>
> * U kunt een Microsoft Excel-bestand op uw SharePoint-site of Google Drive maken om de veldsets in een formulier herhaalbaar te maken.
> * In dit geval nemen we het voorbeeld van een Microsoft SharePoint. Voer de stappen uit zoals beschreven in [Hoe te om SharePoint te gebruiken](https://www.aem.live/docs/setup-customer-sharepoint).


Om herhaalbare secties in de Levering van de Rand toe te voegen:

1. [Een formulier ontwerpen met Microsoft Excel](#author-form)
2. [Het formulier voorvertonen en publiceren](#preview-form)

### Een formulier ontwerpen met Microsoft Excel {#author-form}

1. Ga naar uw Microsoft SharePoint-account en open of maak AEM Edge Delivery-projectdirectory.
2. Open een bestaand Microsoft Excel-bestand of maak een nieuw bestand.
In dit voorbeeld gebruiken we een Excel-werkblad genaamd `loan-application.xlsx` gemaakt op Microsoft SharePoint Site.
3. Nieuwe kolommen toevoegen met het label `Repeatable`, `Min`, en `Max` in uw Microsoft Excel-bestand.
4. Geef de waarde op voor de `Repeatable` kolom als `True` voor de veldset die u wilt herhalen.
5. Geef de waarden op voor de `Min` en `Max` kolommen. De `Min` waarde staat voor het minimale aantal exemplaren waarvoor het deelvenster wordt herhaald, terwijl de waarde `Max` Deze waarde vertegenwoordigt het maximale aantal exemplaren waarvoor het deelvenster wordt herhaald.
6. Sla uw Microsoft Excel-bestand op.

>[!NOTE]
>
> Hier is het [Lijntoepassing](/help/forms/assets/loan-application.xlsx) Excel-blad ter referentie.

### Het formulier voorvertonen/publiceren met uw Edge Delivery-service

1. Open of maak een nieuw documentbestand in een Microsoft SharePoint-site om het Excel-bestand erin in te sluiten met behulp van een `Form Block`. Open bijvoorbeeld de `index` en voeg een `Form Block`.
2. Open de bevelherinnering, navigeer aan uw AEM het projectfolder van de Levering van de Rand op uw lokale machine, en voer het bevel als uit `aem up`.

Het formulier is toegankelijk via `https://localhost:3000`, waar u op de knop `Add` voegt een nieuwe herhaalbare sectie toe voor het invoeren van de details van de medeaanvrager. U kunt de herhaalbare sectie ook verwijderen door op de knop `Delete` knop.

>[!NOTE]
>
> Als er een fout optreedt bij &quot;Pagina niet gevonden&quot; terwijl u uw formulier opent op de localhost, voegt u de mapnaam van de Microsoft SharePoint-site toe vóór de URL waar het formulier zich bevindt. Bijvoorbeeld: `http://localhost:3000/<dir-name>/`




