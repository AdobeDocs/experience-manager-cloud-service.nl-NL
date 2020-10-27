---
title: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.6.0
description: Opmerkingen bij de release voor Cloud Manager in AEM als Cloud Service Release 2020.6.0
translation-type: tm+mt
source-git-commit: ca690144a8254d5ffba354f0f96d9ef1c5202533
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---


# Opmerkingen bij de release voor Cloud Manager in Adobe Experience Manager als Cloud Service 2020.6.0 {#release-notes}

Deze pagina bevat de releaseopmerkingen voor Cloud Manager in AEM als Cloud Service 2020.6.0.

## Releasedatum {#release-date}

De releasedatum voor Cloud Manager in AEM als Cloud Service 2020.6.0 is 4 juni 2020.

## Wat is er nieuw?{#whats-new-cloud-manager}

* Een gebruiker met de rol *Zakelijke eigenaar* in Cloud Manager kan nu een Sandbox-programma verwijderen van de bestemmingspagina (via de knop voor snelle actie op de programmakaart) of van binnen het programma.

   Raadpleeg [Sandbox-programma](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) verwijderen voor meer informatie.

* Een gebruiker van het Sandbox- programma in de rol van *bedrijfseigenaar* of *plaatsingsmanager* in de Manager van de Wolk kan nu hun Productie en milieu van het Stadium schrappen die via de UI van de Manager van de Wolk wordt geplaatst. De verwijderingsoptie is nu zowel beschikbaar op de kaart Milieu op de pagina Overzicht **van** Programma&#39;s als op de pagina **Milieu** . Als u de verwijderoptie in Productie of Werkgebied selecteert, wordt ook de andere optie uit de set verwijderd.

   Raadpleeg [Sandbox-programma](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/cloud-service-programs/creating-a-program.html) verwijderen voor meer informatie.

* Op de landingspagina worden de aanvoermarkeringen aangebracht om de gebruiker te informeren en te informeren over de basisnavigatie.

* Op de pagina **Programmaoverzicht** staan codetekens waarmee u de gebruiker informeert en informeert over de standaardnavigatie in Cloud Manager om deze te starten.

* Er is nu een pagina **LEREN** beschikbaar in Cloud Manager, die toegankelijk is via de bovenste navigatie. Deze pagina bevat bronnen die gebruikers helpen bij het leren van de meestgebruikte workflows die relevant zijn voor hun rollen die zijn toegewezen in Cloud Manager.

* Sandboxprogramma&#39;s worden nu geïdentificeerd door middel van een **Sandbox** -badge die wordt weergegeven op de programmacode op de landingspagina en naast de programmanaam op de pagina **Program Overview** .

* Een gebruiker in de rol SysAdmin heeft nu met één klik toegang tot de plaats in Admin Console van waar de gebruikersrollen of de toestemmingen aan de Manager van de Wolk kunnen worden beheerd. Een knop Toegang **** beheren is nu beschikbaar op de bestemmingspagina naast de knop Programma **** toevoegen.

   Raadpleeg [SysAdmin-taken](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/navigation.html#sysadmin-tasks) voor meer informatie.

* Een gebruiker met de rol SysAdmin heeft nu met één klik rechtstreeks vanuit Cloud Manager toegang tot de instantie van de auteur.

   Zie Toegang [beheren tot instantie](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/onboarding/getting-access/navigation.html#manage-access-aem) Auteur voor meer informatie.

* Het logbestand Build bevat nu een lijst met ontdekte artefacten, waaronder overgeslagen inhoudspakketten.

* De stap Build controleert nu of alle gegenereerde inhoudspakketten alle verplichte eigenschappen (naam, groep en versie) bevatten.

* De stap Build controleert nu of de build ten minste één inhoudspakket heeft geproduceerd.

### Bug Fixes {#bug-fixes-cm}

* In bepaalde situaties zijn de pictogrammen in het dialoogvenster **Programma** maken onjuist uitgelijnd.

* De AEM release-id wordt niet consistent weergegeven op de pagina Overzicht **van** programma&#39;s.

* Wanneer het vormen van de productiepijpleiding, was de **Geplande optie van de Plaatsing** niet zichtbaar voor sommige klanten.

### Bekende problemen {#known-issues-cm}

* De omgevingen in een Sandbox-programma worden gehiberd wanneer gedurende een bepaalde periode geen activiteit wordt gedetecteerd. Deze status wordt niet waargenomen in Cloud Manager. De status kan echter worden waargenomen via de Developer Console. Dit probleem wordt in een komende release opgelost.

* De koppeling naar de ontwikkelaarsconsole rechtstreeks vanuit Cloud Manager geeft de optie voor het dehiberneren/hberneren van de omgeving van een Sandbox-programma niet weer. Om dit aan te pakken, één keer in de Console van de Ontwikkelaar, voeg het patroon `#release-cm-p1234-e5678` aan het eind van url toe, waar *1234* identiteitskaart van het Programma en *5678* milieu identiteitskaart is Dit probleem wordt in een komende release opgelost.
