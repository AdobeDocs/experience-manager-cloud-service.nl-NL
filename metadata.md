---
product: adobe experience manager
description: Adobe Experience Manager als Cloud Service documentatie.
git-repo: https://git.corp.adobe.com/AdobeDocs/experience-manager-cloud-service.nl-NL
index: y
type: Documentatie
solution: Experience Manager
version: Cloud Service
cloud: Experience Cloud
translation-type: tm+mt
source-git-commit: 6908b5215dcbff0692d4e03dd1588ca5d34aeffe
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 1%

---


# Metagegevens voor intern gebruik

De meta-gegevens in het GitHub auteurssysteem zijn hiërarchisch en worden bepaald de volgende stijgende niveaus van precedent.

1. metadata.md
1. ToC
1. Artikel

De metagegevens die zijn gedefinieerd in het bestand metadata.md, worden toegepast op de volledige repo, maar kunnen worden overschreven op de ToC- en artikelniveaus. Als de metagegevens worden genegeerd, moet dat op het laagst mogelijke niveau gebeuren.

De metagegevens in het bestand Experience-manager-cloud-service.en repo zijn minimaal vereist.

metadata.md

* `product`
* `git-repo`
* `index`
* `solution-title`
* `solution-hub-url`
* `getting-started-title`
* `getting-started-url`
* `tutorials-title`
* `tutorials-url`

ToCs

* `sub-product`
* `user-guide-title`

Artikel

* `title`
* `description`
* `contentOwner` (alleen voor kernactiva onder  `/help/assets`)
