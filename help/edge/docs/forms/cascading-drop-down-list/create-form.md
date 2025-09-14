---
title: Formulier maken met de universele editor
description: Aangepast formulier maken om de vervolgkeuzelijst met trapsgewijze gegevens te testen met de API-integratie
feature: Edge Delivery Services
role: User
source-git-commit: 53e476981874597bfb7f9293e67b2d135c72b318
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Formulier maken met de universele editor

Maak het volgende formulier met de universele editor. Het formulier heeft 3 vervolgkeuzelijsten waarvan de waarden worden ingevuld met de API-integratie
![ adaptive-form ](assets/address-form.png)

## Land van verblijf

Bij initialisatie wordt het land van de woonplaats ingevuld met de resultaten van de API-oproep.
![ initialize-event ](assets/initialize-event.png)

## Succes-handler

De succeshandler is gedefinieerd om de opsomming en enumNames van de vervolgkeuzelijst met landen in te stellen met de juiste waarden uit de array geonames. De geonames-array is beschikbaar onder de optie Payload van de gebeurtenis
![ gebeurtenis-lading ](assets/event-payload.png)
![ succes-manager ](assets/success-handler.png)

## Onderliggende waarden ophalen

De vervolgkeuzelijst Staat of provincie wordt gevuld wanneer de gebruiker een selectie maakt in de vervolgkeuzelijst Land van verblijf. De geonameId verbonden aan het geselecteerde land wordt overgegaan als inputparameter aan de integratie GetChildren API

![ get-children ](assets/invoke-service-get-children.png)

De sucmanager werd bepaald om enum/enumNames van de StateOrProvince drop-down gebied te plaatsen
![ get-children-success-handler ](assets/child-success-handler.png)

Als de provincie is geselecteerd, kunt u de vervolgkeuzelijst met steden vullen met het bovenstaande patroon waarmee de vervolgkeuzelijst met staten of provincies wordt gevuld.