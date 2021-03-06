---
title: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2020.6.0
description: Opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service versie 2020.6.0
feature: Release Information
exl-id: 879a5025-f94f-4549-bf6e-e1cc6b6a7b58
source-git-commit: 09d5d125840abb6d6cc5443816f3b2fe6602459f
workflow-type: tm+mt
source-wordcount: '604'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager as a Cloud Service 2020.6.0 {#release-notes}

Deze pagina bevat een overzicht van de opmerkingen bij de release voor Cloud Manager in AEM as a Cloud Service 2020.6.0.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM as a Cloud Service 2020.6.0 is 4 juni 2020.

## Wat is er nieuw? {#whats-new-cloud-manager}

* Een gebruiker in de *Zakelijke eigenaar* rol in Cloud Manager kan nu een Sandbox-programma verwijderen van de bestemmingspagina (via de knop voor snelle actie op de programmakaart) of van binnen het programma.

   Zie [Een Sandbox-programma verwijderen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) voor meer informatie .

* Een gebruiker van het Sandbox-programma in *Zakelijke eigenaar* of *Implementatiebeheer* rol in Cloud Manager kan nu hun productie- en werkgebiedomgeving verwijderen die is ingesteld via de interface van Cloud Manager. De verwijderoptie is nu beschikbaar via de milieucaart op de **Overzicht van programma&#39;s** en de **Omgevingen** pagina. Als u de verwijderoptie in Productie of Werkgebied selecteert, wordt ook de andere optie uit de set verwijderd.

   Zie [Een Sandbox-programma verwijderen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) voor meer informatie .

* Op de landingspagina worden de aanvoermarkeringen aangebracht om de gebruiker te informeren en te informeren over de basisnavigatie.

* De tekens van de coating op **Programmaoverzicht** pagina om de gebruiker te informeren en te instrueren over de standaardnavigatie in Cloud Manager om deze te starten.

* A **LEREN** Deze pagina is nu beschikbaar in Cloud Manager en is toegankelijk via de bovenste navigatie. Deze pagina bevat bronnen die gebruikers helpen bij het leren van de meestgebruikte workflows die relevant zijn voor hun rollen die zijn toegewezen in Cloud Manager.

* Sandbox-programma&#39;s worden nu ge??dentificeerd door middel van een **Sandbox** badge die wordt weergegeven op de programmakaart op de landingspagina en naast de naam van het programma in de **Programmaoverzicht** pagina.

* Een gebruiker in de rol SysAdmin heeft nu met ????n klik toegang tot de plaats in Admin Console van waar de gebruikersrollen of de toestemmingen aan de Manager van de Wolk kunnen worden beheerd. A **Toegang beheren** Deze knop is nu beschikbaar op de landingspagina naast de **Programma toevoegen** knop.

   Zie [SysAdmin-taken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html#sysadmin-tasks) voor meer informatie .

* Een gebruiker met de rol SysAdmin heeft nu met ????n klik rechtstreeks vanuit Cloud Manager toegang tot de instantie van de auteur.

   Zie [Toegang tot instantie Auteur beheren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html#manage-access-aem) voor meer informatie .

* Het logbestand Build bevat nu een lijst met ontdekte artefacten, waaronder overgeslagen inhoudspakketten.

* De stap Build controleert nu of alle gegenereerde inhoudspakketten alle verplichte eigenschappen (naam, groep en versie) bevatten.

* De stap Build controleert nu of de build ten minste ????n inhoudspakket heeft geproduceerd.

### Opgeloste problemen {#bug-fixes-cm}

* In bepaalde situaties worden de pictogrammen in de **Programma maken** is onjuist uitgelijnd.

* De AEM release-id wordt niet consistent weergegeven op het tabblad **Overzicht van programma&#39;s** pagina.

* Wanneer het vormen van de productiepijplijn, **Geplande implementatie** deze optie is voor sommige klanten niet zichtbaar.

### Bekende problemen {#known-issues-cm}

* De omgevingen in een Sandbox-programma worden gehiberd wanneer gedurende een bepaalde periode geen activiteit wordt gedetecteerd. Deze status wordt niet waargenomen in Cloud Manager. De status kan echter worden waargenomen via de Developer Console. Dit probleem wordt in een komende release opgelost.

* De koppeling naar de ontwikkelaarsconsole rechtstreeks vanuit Cloud Manager geeft de optie voor het dehiberneren/hberneren van de omgeving van een Sandbox-programma niet weer. Voeg het patroon toe om dit probleem te verhelpen, eenmaal in de Developer Console `#release-cm-p1234-e5678` aan het einde van de URL, waarbij *1234* is de programma-id en *5678* is de milieu-id. Dit probleem wordt in een komende release opgelost.
