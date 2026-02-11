---
title: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: De huidige Nota's van de Versie van het Onderhoud van  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: e58e1355b923e1da447e3dbcfd0a81086aee3e66
workflow-type: tm+mt
source-wordcount: '1018'
ht-degree: 0%

---


# Opmerkingen bij de onderhoudsrelease {#maintenance-release-notes}

In het volgende gedeelte worden de opmerkingen bij de technische release voor de huidige onderhoudrelease van Experience Manager as a Cloud Service beschreven.

## Release 24288 {#24288}

Hieronder worden de voortdurende verbeteringen voor onderhoudsrelease 24288 samengevat, die op 4 februari 2026 openbaar werd gemaakt. De vorige onderhoudsrelease was release 23963.

De activering van de 2026.2.0-functie biedt de volledige functie die is ingesteld voor deze onderhoudrelease. Zie [&#x200B; Experience Manager geeft Roadmap &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) voor meer informatie vrij.

>[!NOTE]
>
>Release 2422 is privé gemaakt.

### Verbeteringen {#enhancements-24288}

* CNTBF-604: Maak een nieuwe versie van de contentbackflow-bundel.
* CQ-4361592: Voeg ondersteuning voor TypeHint toe voor het maken en bijwerken van projecten.
* CQ-4362198: Nieuwste vertalingen van AEM- en Granite-pakketten.
* GRANITE-36205: interne Oak-releaseversie bijwerken naar de nieuwste versie.
* GRANITE-59211: OPTEL: Toegevoegde nonce steun en zelfbediening configuratie.
* GRANITE-62166: Werk de migratiebundel bij om migratiestaten van migratiehulpmiddel opnieuw te gebruiken.
* GRANITE-62598: Verwijder overtollige bezit sluit van de filter van het inhoudspakket uit.
* GRANITE-62684: Maak de onderbreking van de cliëntcontactdoos configureerbaar door skyline-ops.
* GRANITE-62702: Vervang &#39;sling discovery&#39; door standalone implementatie voor online migratie.
* GRANITE-62763: Update Guava-afbrekingslijst op basis van ASSETS-rotatie.
* GRANITE-62771: De mislukte bouw van QuickStart wanneer de nieuwe verouderde gebiedsdelen Commons-Lang worden geïntroduceerd.
* GRANITE-62987: Werk de Felix-webconsole bij naar versie 5.0.18.
* GRANITE-6339: Verbetering van het leasemechanisme voor Azure migration-state blob.
* GRANITE-63343: voeg steun voor de recentste versie van de Sling API bundel in workflow.core toe.
* GRANITE-63799: Bump OIDC Authentication Bundle version.
* GRANITE-63821: Update QuickStart aan filevault versie fixend JCRVLT-831/JCRVLT-839.
* GRANITE-63827: Update QuickStart aan de recentste openbare versie van Oak (1.90.0).
* GRANITE-63888: Update QuickStart aan Jackrabbit 2.22.3.
* GRANITE-64030: Voeg sleutelwoorden en patronen aan de lijst van gewenste personen voor Validator van de Taal van de Uitdrukking toe.
* GRANITE-64050: Sta voor verborgen conf omslagen toe om externe productfunctionaliteit te verbergen.
* SITES-30452: Content API met ASO - Title and Description Suggestions.
* SITES-38099: Update `testing-model.txt` als u een hogere versie van de controles op de hygiëne wilt gebruiken.
* SKYOPS-43616: Migreer Jenkins-gegevens naar Vault in verzendopslagplaatsen.
* SKYOPS-108584: FABRIKANT van 0.6.0 tot 0.6.10.
* SKYOPS-115691: Upgrade de filterbundel CORS om de kopbal van de Oorsprong van de Varkenshaar op Preflight verzoeken toe te voegen.
* SKYOPS-123094: Werk Apache HTTP-componenten bij in Quickstart.
* SKYOPS-123236: Neem `rep:cugPolicy` op in het replicatiepakket.
* SKYOPS-123240: Werk CRXDE gebiedsdelen in QuickStart bij.
* SKYOPS-123247: Update Sling XSS bundle in QuickStart.
* SKYOPS-123250: Update Sling security bundle in Quickstart.
* SKYOPS-123327: Java 21 vereist voor AEM-CS SDK.
* SKYOPS-125574: Werk netcentric AC Tool bundles bij in QuickStart.
* SKYOPS-126150: Verbeter hoogste bevel voor de generatormanuscript van de draaddumps.

### Opgeloste problemen {#fixed-issues-24288}

* FORMS-23687: Los de mislukking van de bevestiging SSV wanneer bevat regel zonder standaardwaarde wordt gebruikt.
* GRANITE-48472: Fout bij het wijzigen van het wachtwoord op het tabblad Gebruikersinstellingen bewerken.
* GRANITE-50286: Los het lay-outprobleem in de statuskolom van Gebruikersbeheer modaal op.
* GRANITE-52301: Lokaliseren Kan wijzigingen in sessietekenreeks niet vastleggen in beveiligingsgroepen.
* GRANITE-52920: lokaliseer fout wanneer het creëren van gebruiker in Veiligheid leidt tot Nieuwe Gebruiker.
* GRANITE-54654: tekenreeks lokaliseren in het dialoogvenster Adobe IMS Configurations Check van Security.
* GRANITE-56371: Corrigeer onjuiste gegevensindeling in Security Trust Store.
* GRANITE-62717: Upgrade crypto keystore for JSafe password handling with non-ASCII characters.
* GRANITE-62789: Update overseinen-cliënt om geen herpogingswijze op inhoudsdistributie te steunen.
* GRANITE-62824: Repareren `NullPointerException` wanneer het toegang tot van het lusje van Groepen in de Redacteur van de Gebruiker.
* GRANITE-63080: maak het importeren van `org.slf4j.spi` compatibel met `slf4j 2.x` .
* GRANITE-63210: Werk de distributiekernis bij om de validatie van de verzender bij het publiceren op te lossen.
* GRANITE-63293: Corrigeer het verplichte pathfield waarbij de vereiste asterisk na de eerste ontwerpfase verloren gaat.
* GRANITE-63360: Corrigeer onjuiste informatie die wordt weergegeven wanneer meerdere paden zijn geselecteerd.
* SITES-36242: Npijl-omlaag GraphQL voert regex uit om de bypass van het verzendingsfilter te corrigeren.
* SITES-40122: Oplossing voor Edge Delivery-integratie met ImsService voor distributie van inhoud.
* SKYOPS-84379: Gebruik het recentste hulpmiddel van de FEITEN voor juiste eigenschapknevel opname door RDEs.
* SKYOPS-121216: herstel update naar Jackson 2.20.0-bibliotheken.

#### AEM Guides {#guides-24288}

* GUIDEN-38198: Wanneer het bijwerken van een gealigneerde vergelijking van MathML gebruikend de Edit optie van MathML van het contextmenu, wordt de bijgewerkte waarde niet weerspiegeld tot de pagina wordt verfrist.
* GUIDEN-38276: Kan versielabels niet verwijderen uit het deelvenster Versiegeschiedenis in de gebruikersinterface van Assets.
* GUIDEN-36641: Wanneer het produceren van de output van AEM Sites, de kaarttitels die sleutelwoorden en onderwerptitels met `<ph>` element bevatten worden niet inbegrepen in de gepubliceerde output.
* GUIDEN-37837: Wanneer het proberen om een onderwerp of een kaart te bewaren, kan de verrichting met een Mislukt om dossierfout, vooral tijdens intensieve taken van de activaverwerking of vertaalwerkschema&#39;s die op de achtergrond lopen periodiek ontbreken op te slaan.
* GUIDEN-2774: Het verbroken lijstrapport bevat onjuist externe koppelingen, geldig `keyrefs` en trefwoorden die correct zijn opgelost binnen het bereik van de huidige kaart.

>[!NOTE]
>
> Er is een het breken verandering in AEM Guides om zich van bewust te zijn: [&#x200B; Verbeterde behandeling voor Gelezen slechts dossiers &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2026-releases/2601-release/whats-new-2026-01-0#improved-handling-for-read-only-files).

Voor meer informatie over de nieuwe en verbeterde eigenschappen en kwesties die in de versie worden bevestigd, bekijk de [&#x200B; versie van Experience Manager Guides roadmap &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

### Bekende problemen {#known-issues-24288}

* SITES-40408: Het eindpunt van GraphQL keert 404 toe wegens de herschrijfregels van de douaneverzender.

### Verouderde functies en API&#39;s {#deprecated-24288}

* AEMSRE-2896: verbeter aangepaste logmanager configuratie behandeling.
* GRANITE-62802: verwijderde `commons-lang` afhankelijkheid verwijderen uit `granite.auth.saml` .
* GRANITE-62805: verwijderde `commons-lang` afhankelijkheid verwijderen uit `granite.httpcache.core` .
* GRANITE-62864: verwijderde `commons-lang` afhankelijkheid verwijderen uit `granite.jobs.async` .
* GRANITE-62865: verwijderde `commons-lang` afhankelijkheid verwijderen uit `granite.replication.core` .
* GRANITE-62868: verwijderde `commons-lang` afhankelijkheid verwijderen uit `granite.rest.api` .
* GRANITE-62895: verwijderde `commons-lang` afhankelijkheid verwijderen uit `translation.connector.msft.core` .
* GRANITE-63069: Afgekeurd `com.adobe.granite.httpcache.core` .
* GRANITE-63179: verwijderde `commons-lang` afhankelijkheid verwijderen uit `cq-workflow-impl` .
* GRANITE-63180: verwijderde `commons.lang` export uit `cq-mailer` bundle verwijderen.
* SKYOPS-123329: Drop Java 11-ondersteuning voor AEM Ethos-implementaties en -updates `commons-lang3` .
* SKYOPS-124983: Vervangen `nashorn.args` verwijderen uit opstartscripts van AEM.

Vervangen en verwijderde eigenschappen en APIs in AEM as a Cloud Service zijn gedetailleerd in [&#x200B; Vervangen en Verwijderde Eigenschappen en APIs &#x200B;](/help/release-notes/deprecated-removed-features.md) document.

### Beveiligingsproblemen {#security-24288}

AEM as a Cloud Service is gewijd aan het optimaliseren van de beveiliging en prestaties van uw platform. Deze onderhoudrelease verhelpt 10 geïdentificeerde kwetsbaarheden en versterkt onze inzet voor robuuste systeembescherming.

### Ingesloten technologieën {#embedded-tech-24288}

| Technologie | Versie | Koppeling |
|---|---|---|
| AEM Oak | 1 90,0 | [&#x200B; Oak 1.90.0 API &#x200B;](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.90.0/index.html) |
| AEM SLING-API | 2,27,6 | [&#x200B; Apache Sling API 2.27.6 API &#x200B;](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTML | 1.4.28-1.4.0 | [&#x200B; Specificatie van de Taal van het Malplaatje van HTML &#x200B;](https://github.com/adobe/htl-spec) |
| Apache HTTP Server | 2,4,65 | [&#x200B; Apache Httpd 2.4.65 &#x200B;](https://apache.googlesource.com/httpd/+/refs/tags/2.4.65/CHANGES) |
| AEM-kerncomponenten | 2.30.2. | [&#x200B; AEM WCM de Componenten van de Kern &#x200B;](https://github.com/adobe/aem-core-wcm-components) |
| Node.js | 14 (standaard) | [&#x200B; Ondersteunde versies Node.js &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-cloud-service/content/implementing/developing/developing-with-front-end-pipelines#node-versions) |
