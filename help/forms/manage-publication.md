---
title: Hoe kan ik formulieren publiceren of verwijderen bij voorvertoningen of publicatie-exemplaren?
description: Leer het publiceren of het unpublishing van het AEM auteursmilieu aan voorproef of publiceer instanties. Of u uw formulieren nu test op een testomgeving of ze live implementeert voor eindgebruikers, AEM beschikt over gestroomlijnde tools om dit proces efficiënt te beheren.
Keywords: 6.5 forms to cloud service, 6.5 forms to cs, manage publication, , AEM Forms 6.5 to Cloud Service, AEM form migration to cloud service, Forms Manage publication, AF Manage publication, Adaptive Forms Manage publication, Cloud Manage publication
contentOwner: khsingh
feature: Adaptive Forms
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
role: User, Developer
level: Intermediate
source-git-commit: 242dcbc5bb541dfac601454fb75dec3bdff1ea64
workflow-type: tm+mt
source-wordcount: '834'
ht-degree: 0%

---


# &#x200B; Publicatie beheren in Experience Manager Forms

Als Adobe Experience Manager Forms-beheerder kunt u formulieren publiceren van uw auteur naar Experience Manager Forms. U kunt plannen om een formulier of map op een latere datum of tijd te publiceren. Na publicatie kunnen gebruikers de formulieren openen en invullen.

U kunt het formulier publiceren of de publicatie ervan ongedaan maken met behulp van de optie Publish of Publicatie beheren die beschikbaar is in de Experience Manager Forms-interface. Als u de oorspronkelijke formulieren of map in Experience Manager Forms daarna wijzigt, worden de wijzigingen pas in het publicatieexemplaar doorgevoerd als u het document opnieuw publiceert vanuit Experience Manager Forms. Hiermee zorgt u ervoor dat wijzigingen die in uitvoering zijn, niet beschikbaar zijn in het publicatieexemplaar. Alleen wijzigingen die door een beheerder zijn gepubliceerd, zijn beschikbaar in de publicatie-instantie.

## Publish-formulieren met Publish, optie

Met de optie Publiceren kunt u direct een formulier publiceren. Navigeer in de Experience Manager Forms-console naar de bovenliggende map en selecteer een formulier dat u wilt publiceren. Klik op de optie Publish op de werkbalk, bekijk alle referentie-elementen die met het formulier worden gepubliceerd en klik op Publish.

Een schermafbeelding van een computer

Beschrijving automatisch gegenereerd

## Publish of Publicatie van formulieren ongedaan maken met Publicatie beheren


Met Publicatie beheren kunt u inhoud publiceren of de publicatie van en naar het geselecteerde doel ongedaan maken, inhoud vanuit de map Formulieren en documenten aan de publicatielijst toevoegen, referenties selecteren om te publiceren en de publicatie naar een latere datum of tijd plannen.


Navigeer in de Experience Manager Forms-console naar de bovenliggende map en selecteer een formulier dat u wilt publiceren. Klik op Publicatie beheren op de werkbalk.


Een schermafbeelding van een computer

Beschrijving automatisch gegenereerd



De volgende opties zijn beschikbaar in de interface Publicatie beheren:

* Handelingen

   * Publish: Publish-formulieren naar de geselecteerde bestemming
   * Publiceren ongedaan maken: publiceren van formulieren vanaf doel

* Doel

   * Publish: Publish vormt een Experience Manager Forms (AEM) Publish-exemplaar.
   * Voorbeeld: Publish-formulieren naar voorbeeld van Experience Manager Forms (AEM).

* Planning

   * Nu: Publish-formulieren direct
   * Later: Publish-formulieren op basis van de activeringsdatum of -tijd



Om verder te gaan, klik **daarna**. Gebruik op het tabblad Bereik de opties voor Inhoud toevoegen om meer inhoud toe te voegen voor publicatie. U kunt bijvoorbeeld meer Forms- of Document met recordbestanden toevoegen.

### Inhoud toevoegen

Als u publiceert naar Experience Manager Forms, kunt u meer inhoud (formulieren, elementen en mappen) toevoegen aan de publicatielijst. U kunt meer formulieren, elementen of mappen aan de lijst toevoegen vanuit de map Formulisanddocuments. U kunt echter geen elementen uit meerdere mappen tegelijk toevoegen.

Een schermafbeelding van een computer

Beschrijving automatisch gegenereerd

Klik **toevoegen Inhoud** knoop om meer inhoud toe te voegen. U kunt meerdere elementen uit een map toevoegen of meerdere mappen tegelijk toevoegen. U kunt echter geen elementen uit meerdere mappen tegelijk toevoegen.

Als u de referenties wilt configureren die u wilt publiceren voor een formulier of andere middelen, selecteert u het formulier of het element en klikt u op Gepubliceerde verwijzingen.

Een schermafbeelding van een computer

Beschrijving automatisch gegenereerd

Schakel in het dialoogvenster Gepubliceerde verwijzingen de elementen uit die u niet wilt publiceren en klik op Gereed.


Een schermafbeelding van een computer

Beschrijving automatisch gegenereerd


## Publish of publiceer het formulier later


Met de optie Later publiceren of publiceren kunt u niet alleen formulieren op een latere datum en tijd publiceren, maar kunt u ook een workflow configureren. De formulieren worden gepubliceerd of niet gepubliceerd nadat de workflow is voltooid. Een formulier plannen voor publiceren of verwijderen:

1. Navigeer in de Experience Manager Forms-console naar de bovenliggende map en selecteer het formulier dat u wilt plannen voor publicatie.
1. Klik op Publicatie beheren op de werkbalk.
1. Klik op Publish of Unpublish from Action en selecteer vervolgens Doel waar u de inhoud wilt publiceren of de publicatie ervan ongedaan wilt maken.

   * Voorbeeld: gebruik de optie Voorvertoning om te publiceren of de publicatie naar een Experience Manager Forms-voorvertoningsomgeving ongedaan te maken. De Experience Manager Forms-voorbeeldomgevingen worden gebruikt om formulieren te testen onder ontwikkelaars.
   * Publish: gebruik de optie Experience Manager Forms Publish om het formulier naar de publicatieomgeving van Experience Manager Forms te verzenden nadat het formulier klaar is voor gebruik in een productieomgeving.


1. Selecteer Later in planning.

1. Selecteer een activeringsdatum en geef de datum en tijd op. Klik op Volgende.

   Een schermafbeelding van een computer

   Beschrijving automatisch gegenereerd

1. Voeg indien nodig inhoud toe op het tabblad Bereik. Klik op Volgende.

   Een schermafbeelding van een computer

   Beschrijving automatisch gegenereerd

1, (Optioneel) Geef op het tabblad Workflows een titel voor de workflow op. Klik later op Publish.

Een schermafbeelding van een computer

Beschrijving automatisch gegenereerd

## Publicatiestatus bepalen

Er zijn meerdere manieren om de publicatiestatus te bepalen:

* Meld u aan bij de doelinstantie om de gepubliceerde formulieren en andere elementen te controleren (afhankelijk van de geplande datum of tijd).

* Gebruik de tijdlijnweergave om de publicatiestatus te bepalen.

* Gebruik het menu met pagina-informatie in de Adaptieve Forms-editor.