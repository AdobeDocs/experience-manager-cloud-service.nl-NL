---
title: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.6.0
description: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.6.0
feature: Geen informatie
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---


# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager als Cloud Service 2020.6.0 {#release-notes}

Deze pagina bevat de releaseopmerkingen voor Cloud Manager in AEM als Cloud Service 2020.6.0.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2020.6.0 is 4 juni 2020.

## Wat is er nieuw?{#whats-new-cloud-manager}

* Een gebruiker met de rol *Zakelijke eigenaar* in Cloud Manager kan nu een Sandbox-programma verwijderen van de bestemmingspagina (via de knop voor snelle actie op de Programmakaart) of van binnen het programma.

   Raadpleeg [Een Sandbox-programma verwijderen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) voor meer informatie.

* Een gebruiker van het Sandbox- Programma in *Bedrijfseigenaar* of *De rol van Manager van de Plaatsing* in de Manager van de Wolk kan nu hun Productie en milieu van het Stadium schrappen die via de UI van de Manager van de Wolk wordt geplaatst. De schrappingsoptie is nu beschikbaar bij zowel de kaart van het Milieu op **het Overzicht van Programma&#39;s** pagina als **Milieu** pagina. Als u de verwijderoptie in Productie of Werkgebied selecteert, wordt ook de andere optie uit de set verwijderd.

   Raadpleeg [Een Sandbox-programma verwijderen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) voor meer informatie.

* Op de landingspagina worden de aanvoermarkeringen aangebracht om de gebruiker te informeren en te informeren over de basisnavigatie.

* De markeringen van de coach op **Programma Overzicht** pagina om de gebruiker over basisnavigatie binnen de Manager van de Wolk te informeren en te instrueren om hen te krijgen begonnen.

* De pagina **LEARN** is nu beschikbaar in Cloud Manager, toegankelijk via de bovenste navigatie. Deze pagina bevat bronnen die gebruikers helpen bij het leren van de meestgebruikte workflows die relevant zijn voor hun rollen die zijn toegewezen in Cloud Manager.

* Sandboxprogramma&#39;s worden nu geïdentificeerd door middel van een **Sandbox**-badge die wordt weergegeven op de programmakaart op de landingspagina en naast de programmanaam op de pagina **Program Overview**.

* Een gebruiker in de rol SysAdmin heeft nu met één klik toegang tot de plaats in Admin Console van waar de gebruikersrollen of de toestemmingen aan de Manager van de Wolk kunnen worden beheerd. De knop **Toegang beheren** is nu beschikbaar op de bestemmingspagina naast de knop **Programma toevoegen**.

   Verwijs naar [Taken SysAdmin](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/navigation.html#sysadmin-tasks) voor meer details.

* Een gebruiker met de rol SysAdmin heeft nu met één klik rechtstreeks vanuit Cloud Manager toegang tot de instantie van de auteur.

   Raadpleeg [Toegang tot instantie Auteur beheren](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/navigation.html#manage-access-aem) voor meer informatie.

* Het logbestand Build bevat nu een lijst met ontdekte artefacten, waaronder overgeslagen inhoudspakketten.

* De stap Build controleert nu of alle gegenereerde inhoudspakketten alle verplichte eigenschappen (naam, groep en versie) bevatten.

* De stap Build controleert nu of de build ten minste één inhoudspakket heeft geproduceerd.

### Opgeloste problemen {#bug-fixes-cm}

* In bepaalde situaties zijn de pictogrammen in het dialoogvenster **Programma maken** onjuist uitgelijnd.

* De AEM release-id is niet consistent weergegeven op de pagina **Programs Overview**.

* Bij het configureren van de productiepijplijn was de optie **Geplande implementatie** niet zichtbaar voor sommige klanten.

### Bekende problemen {#known-issues-cm}

* De omgevingen in een Sandbox-programma worden gehiberd wanneer gedurende een bepaalde periode geen activiteit wordt gedetecteerd. Deze status wordt niet waargenomen in Cloud Manager. De status kan echter worden waargenomen via de Developer Console. Dit probleem wordt in een komende release opgelost.

* De koppeling naar de ontwikkelaarsconsole rechtstreeks vanuit Cloud Manager geeft de optie voor het dehiberneren/hberneren van de omgeving van een Sandbox-programma niet weer. Om dit aan te pakken, eens bij de Console van de Ontwikkelaar, voeg het patroon `#release-cm-p1234-e5678` aan het eind van url toe, waar *1234* de identiteitskaart van het Programma en *5678* milieu identiteitskaart is Dit probleem wordt in een komende release opgelost.
