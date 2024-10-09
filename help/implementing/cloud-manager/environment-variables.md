---
title: Cloud Manager-omgevingsvariabelen
description: De standaardmilieuvariabelen kunnen via Cloud Manager worden gevormd en worden beheerd en aan het runtime milieu worden verstrekt, dat in configuratie OSGi moet worden gebruikt.
exl-id: 5cdd5532-11fe-47a3-beb2-21967b0e43c6
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 9cde6e63ec452161dbeb1e1bfb10c75f89e2692c
workflow-type: tm+mt
source-wordcount: '988'
ht-degree: 0%

---


# Cloud Manager-omgevingsvariabelen {#environment-variables}

Standaardomgevingsvariabelen kunnen worden geconfigureerd en beheerd via Cloud Manager. Zij worden verstrekt aan het runtime milieu en kunnen in configuraties worden gebruikt OSGi. Omgevingsvariabelen kunnen milieuspecifieke waarden of omgevingsgeheimen zijn, op basis van wat wordt gewijzigd.

## Overzicht {#overview}

Omgevingsvariabelen bieden een groot aantal voordelen voor gebruikers van AEM as a Cloud Service:

* Ze stellen het gedrag van uw code en toepassing in staat te variëren op basis van context en omgeving. Ze kunnen bijvoorbeeld worden gebruikt om verschillende configuraties in de ontwikkelomgeving mogelijk te maken in vergelijking met de productie- of werkgebiedomgevingen om kostbare fouten te voorkomen.
* Ze hoeven slechts eenmaal te worden geconfigureerd en ingesteld en kunnen indien nodig worden bijgewerkt en verwijderd.
* Hun waarden kunnen op om het even welk punt in tijd worden bijgewerkt en onmiddellijk zonder de behoefte aan om het even welke codeveranderingen of plaatsingen van kracht worden.
* Zij kunnen code van configuratie scheiden en de behoefte verwijderen om gevoelige informatie in versiecontrole te omvatten.
* Ze verbeteren de beveiliging van de AEM as a Cloud Service-toepassing omdat ze buiten de code leven.

De meest gangbare gebruiksgevallen voor het gebruik van omgevingsvariabelen zijn:

* De AEM-toepassing verbinden met verschillende externe eindpunten
* Een verwijzing gebruiken bij het opslaan van wachtwoorden in plaats van rechtstreeks in de codebasis
* Wanneer er meerdere ontwikkelomgevingen in een programma voorkomen en sommige configuraties van de ene omgeving tot de andere verschillen

## Omgevingsvariabelen toevoegen {#add-variables}

>[!NOTE]
>
>U moet een lid van de **rol ](/help/onboarding/cloud-manager-introduction.md#role-based-premissions) zijn van de Manager van de Plaatsing 0} om omgevingsvariabelen toe te voegen of te wijzigen.[**

1. Logboek in Adobe Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/).
1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer één u wilt leiden.
1. Van de zijnavigatiebar, selecteer het **venster van Milieu&#39;s** voor het gekozen programma dan het milieu waarvoor u een milieuvariabele wilt creëren.
1. Binnen het detail van het milieu, selecteer het **lusje van de Configuratie** dan **** toevoegen om de **dialoog van de Configuratie van het Milieu** te openen.
   * Als u een omgevingsvariabele voor het eerst toevoegt, kunt u **zien toevoegen Configuratie** knoop in het centrum van de pagina. U kunt deze knoop gebruiken of **** toevoegen om de **dialoog van de Configuratie van het Milieu** te openen.

   ![ het lusje van de Configuratie ](assets/configuration-tab.png)

1. Voer de details van de variabele in.
   * **Naam**
   * **Waarde**
   * **Toegepaste Dienst** - bepaalt waarvoor de dienst (Auteur/Publish/Voorproef) de variabele van toepassing is of als het op alle diensten van toepassing is
   * **Type** - bepaalt als de variabele normale variabele of een geheim is

   ![ Toevoegend een variabele ](assets/add-variable.png)

1. Nadat u uw nieuwe variabele ingaat, moet u **selecteren** in de laatste kolom van de rij toevoegt die de nieuwe variabele bevat.
   * U kunt veelvoudige variabelen meteen ingaan door een nieuwe lijn in te gaan en **te selecteren voeg** toe.

   ![ sparen variabelen ](assets/save-variables.png)

1. Selecteer **sparen** om uw variabelen voort te zetten.

Een indicator met de status **die** bijwerkt wordt getoond bij de bovenkant van de lijst en naast de onlangs toegevoegde variabele om erop te wijzen dat het milieu met de configuratie wordt bijgewerkt. Na voltooiing, is de nieuwe milieuvariabele zichtbaar in de lijst.

![ Bijwerkend variabelen ](assets/updating-variables.png)

>[!TIP]
>
>Als u veelvoudige variabelen wilt toevoegen, wordt het geadviseerd om de eerste variabele toe te voegen, dan gebruiken **** knoop in de **dialoog van de Configuratie van het Milieu** om de extra variabelen toe te voegen. Op deze manier kunt u ze met één update toevoegen aan de omgeving.

## Omgevingsvariabelen bijwerken {#update-variables}

Nadat u milieuvariabelen hebt gecreeerd, kunt u hen bijwerken gebruikend **toevoegen/bijwerken** knoop om de **dialoog van de Configuratie van het Milieu** te lanceren.

1. Logboek in Adobe Cloud Manager bij [ my.cloudmanager.adobe.com ](https://my.cloudmanager.adobe.com/).
1. Cloud Manager geeft een overzicht van de verschillende beschikbare programma&#39;s. Selecteer de map die u wilt beheren.
1. In het navigatievenster, selecteer het **venster van Milieu&#39;s** voor het gekozen programma dan het milieu waarvoor u een milieuvariabele wilt wijzigen.
1. Binnen het detail van het milieu, selecteer het **lusje van de Configuratie** dan uitgezocht **voeg/werk** in het hoogste recht toe om de **dialoog van de Configuratie van het Milieu** te openen.
1. Gebruikend de ellipsknoop in de laatste kolom van de rij van de variabele wilt u wijzigen, uitgezocht **uitgeven** of **Schrapping**.

   ![ geef of schrap veranderlijke ](assets/edit-delete-variable.png) uit

1. Bewerk indien nodig de omgevingsvariabele.
   * Tijdens het bewerken verandert de knop voor ovaal in opties om terug te keren naar de oorspronkelijke waarde of om uw wijziging te bevestigen.
   * Als u geheimen bewerkt, kunnen de waarden alleen worden bijgewerkt en niet worden weergegeven.

   ![ geef veranderlijke ](assets/edit-variable.png) uit

1. Nadat u de vereiste configuratieveranderingen hebt aangebracht, uitgezocht **sparen**.

[ zoals wanneer het toevoegen van variabelen ](#add-variables), wordt een indicator met de status **die** bijwerkt getoond bij de bovenkant van de lijst en naast de onlangs bijgewerkte variabele(s) om erop te wijzen dat het milieu met de configuratie wordt bijgewerkt. Na voltooiing, zijn de bijgewerkte milieuvariabelen zichtbaar in de lijst.

>[!TIP]
>
>Als u veelvoudige variabelen wilt bijwerken, wordt het geadviseerd om de **dialoog van de Configuratie van het 0} Milieu te gebruiken {om alle noodzakelijke variabelen onmiddellijk bij te werken alvorens** sparen **te tikken of te klikken.** Op deze manier kunt u ze met één update toevoegen aan de omgeving.

## Omgevingsvariabelen gebruiken {#using}

Omgevingsvariabelen kunnen uw `pom.xml` -configuraties veiliger en flexibeler maken. Bijvoorbeeld, moeten de wachtwoorden niet hard worden gecodeerd en uw configuratie kan aanpassen gebaseerd op de waarden in omgevingsvariabelen.

U hebt als volgt toegang tot omgevingsvariabelen en geheimen via XML.

* `${env.VARIABLE_NAME}`

Zie het document [ VestigingsProject ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repository-support-password-protected-maven-repositories) voor een voorbeeld van hoe te om beide soorten variabelen in a `pom.xml` dossier te gebruiken.

Zie de [ officiële Gemaakte documentatie ](https://maven.apache.org/settings.html#quick-overview) voor meer details.

## Beschikbaarheid van omgevingsvariabele {#availability}

Omgevingsvariabelen kunnen op verschillende plaatsen worden gebruikt.

### Auteur, Voorvertoning en Publish {#author-preview-publish}

Zowel normale omgevingsvariabelen als geheimen kunnen worden gebruikt in de ontwerpomgeving, voorvertoningsomgeving en in de publicatieomgeving.

### Dispatcher {#dispatcher}

Slechts kunnen de regelmatige milieuvariabelen met [ worden gebruikt de verzender ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html) geheimen niet worden gebruikt.

Omgevingsvariabelen kunnen echter niet worden gebruikt in `IfDefine` -instructies.

>[!TIP]
>
>U zou uw gebruik van milieuvariabelen met [ verzender plaatselijk ](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/dispatcher-tools.html) moeten bevestigen alvorens op te stellen.

### OSGi-configuraties {#osgi}

Zowel kunnen de regelmatige milieuvariabelen als de geheimen in [ configuraties OSGi ](/help/implementing/deploying/configuring-osgi.md) worden gebruikt.

### Pipetvariabelen {#pipeline}

Naast milieuvariabelen, zijn er ook pijpleidingsvariabelen, die tijdens de bouwstijlfase worden blootgesteld. Leer meer over pijpleidingsvariabelen onder [ Bouwstijl Milieu ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#pipeline-variables).
