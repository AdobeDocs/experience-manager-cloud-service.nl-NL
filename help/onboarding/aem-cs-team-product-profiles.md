---
title: AEM as a Cloud Service-team en productprofielen
description: Leer hoe AEM as a Cloud Service-teams en productprofielen toegang tot uw bekabelde Adobe-oplossingen kunnen verlenen en beperken.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 0ff50aa77711d70d372a1f43ad7336c39ab1167c
workflow-type: tm+mt
source-wordcount: '1821'
ht-degree: 0%

---


# AEM as a Cloud Service-team en productprofielen {#product-profiles}

Leer hoe AEM as a Cloud Service-teams en productprofielen toegang tot uw bekabelde Adobe-oplossingen kunnen verlenen en beperken.

## Productprofielen {#profiles}

Wanneer het verlenen van een gebruikerstoegang tot een specifieke oplossing van de Adobe, wilt u hen niet noodzakelijk volledige toegang verlenen. Met productprofielen kan elke oplossing beschikken over een eigen set gebruikersrechten. Deze zijn beschikbaar en toegankelijk via de [ Admin Console ](/help/journey-onboarding/admin-console.md).

De Adobe Admin Console heeft een gestructureerde hiërarchie van product, productinstanties, en productprofielen waar de interne gebruikers van een organisatie kunnen worden toegewezen lidmaatschap, die hen toegang tot de oplossingen en de eigenschappen geven die zijn vergunning gegeven.

<!-- Alexandru: Drafting for now 

Your AEM as a Cloud Service team members are added and assigned to one or more of the following product profiles via the Admin Console during onboarding.

* **AEM Administrators**: An AEM administrator is typically assigned to developers, in particular developers who need access to, for example, the development environments. The AEM administrator's product profile is used to grant administrator privileges in the associated AEM instance.

* **AEM Users**: AEM users are the users in your organization who use AEM as a Cloud Service generally to create content. These users need to access AEM to do their tasks. The AEM users product profile is typically assigned to an AEM content author who creates and reviews the content. This content can be of many types such as pages, assets, publications, and so on. The AEM users product profile shown below is assigned to these members.

![Product profiles](/help/onboarding/assets/admin-console-profiles.png) -->

## AEM as a Cloud Service-productprofielen {#aem-product-profiles}

AEM as a Cloud Service is een volledig eigen cloudaanbod dat AEM als service biedt. Het levert AEM op een wolkeninheemse manier, met nieuwe attributen zoals altijd, altijd huidig, altijd veilig, en altijd op schaal. Tezelfdertijd behoudt het het belangrijkste waardevoorstel dat AEM als klantgericht platform aan klanten verstrekt en ondernemingscoreteams toestaat om in hun ontwikkeling en leveringsprocedure te integreren. Zie [ Inleiding aan Adobe Experience Manager as a Cloud Service ](/help/overview/introduction.md) om meer over AEM as a Cloud Service te leren.

### Productinstanties op organisatieniveau {#org-level-product-instances}

>[!NOTE]
>
> Sommige productinstanties en productprofielen die in dit artikel worden beschreven, worden mogelijk alleen weergegeven voor nieuwe omgevingen. Met een toekomstig mechanisme kunnen bestaande omgevingen ook worden bijgewerkt.

Wanneer de Adobe het verlenen van vergunningen van een AEM oplossing voor het eerst verwerkt, zullen twee Instanties van het Product in Adobe Admin Console, onder het Product van Adobe Experience Manager as a Cloud Service verschijnen:

* **AEM op één niveau** - bevat één of meerdere Profiel van het Product dat toegang tot eigenschappen vertegenwoordigt die aan alle AEM milieu&#39;s, eerder dan enkel aan één enkel zijn
* **Cloud Manager** - bevat de Profielen van het Product die aan verschillende niveaus van toegang tot de eigenschappen van Cloud Manager beantwoorden.

<!--
>[!NOTE]
>
>For existing programs, the AEM Org-Level Product Instance is created upon selecting the **Update product** profiles action for a given environment.
-->

![ of de Instanties van het Product van het Niveau ](/help/onboarding/assets/orglevel.png)

Binnen de AEM Org-Vlakke Instantie van het Product is een Profiel genoemd AEM Org-Vlakke Verslaggevers, die op dit ogenblik niet wordt gebruikt, maar in de toekomst kan zijn om toegang tot het terugwinnen van informatie over AEM productvergunningen te vertegenwoordigen.

Wanneer een Forms Communication Solution een licentie heeft, wordt een overeenkomstig productprofiel ook weergegeven onder de AEM Org-Level Product Instance.

![ Profiel van het Product van Reporters ](/help/onboarding/assets/org-level-reporters.png)

### Product-instanties op milieuniveau en op niveau van niveaus {#environment-and-tier-level-product-instances}

Nadat u nieuwe programma&#39;s hebt voorzien in een of meer AEM omgevingen, worden per omgeving twee productexemplaren weergegeven die productprofielen bevatten voor auteur en publiceren.

![ Instanties van het Product van het Milieu ](/help/onboarding/assets/env-productinstances.png)

Hieronder vindt u de productprofielen in een productinstantie van de auteur voor een organisatie die een omgeving heeft ingericht in een programma met AEM Sites:

![ Instanties van het Product van Plaatsen ](/help/onboarding/assets/sites-product-instances.png)

In de volgende tabel vindt u een lijst met mogelijke productprofielen onder een specifieke instantie van het product die specifiek is voor de omgeving.

<table style="table-layout:auto">
    <tr>
        <th>Productinstantie</th>
        <th>Naamgevingsconventie</th>
        <th>Standaardservice</th>
        <th>Beschrijving</th>
    </tr>
    <tr>
        <td>AEM auteur</td>
        <td>AEM Sites Content Managers - auteur - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM Sites Content Managers</td>
        <td>
            <ul>
                <li>Bedoeld voor gecontroleerde toegang tot AEM Sites-ontwerpfuncties in deze omgeving. Gebruikers in dit productprofiel zijn lid van de groep AEM AEM Sites-inhoud die automatisch in AEM wordt gemaakt. De AEM groepstoestemmingen zouden in AEM met het gewenste toegangsniveau moeten worden gevormd.</li><br>
                <li>Als de standaardservice geselecteerd blijft
                    <ul>
                        <li>gebruikers in dit productprofiel zijn ook lid van de AEM "AEM Sites Content Managers - Service".</li>
                      <!--  <li>users in this product profile will have access to AEM Sites Content Management API.</li>
                        <li>an Adobe Developer Console API OAuth S2S project containing AEM Sites Content Management API can optionally be scoped to this environment.</li>-->
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Beheerders - auteur - Programma <code>id</code> - Omgeving <code>id</code></td>
        <td>AEM</td>
        <td>
            <ul>
                <li>Bedoeld voor onbeperkte toegang tot functies van AEM auteur- en publicatieomgeving. De gebruikers in dit productprofiel zullen lid van de AEM van de auteur AEM groep van Beheerders zijn automatisch gecreeerd in AEM.</li><br>
                <li>Als de standaardservice geselecteerd blijft
                    <ul>
                        <li>gebruikers in dit productprofiel zijn ook lid van de AEM "AEM Beheerders - Service"</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Gebruikers - auteur - Programma <code>id</code> - Omgeving <code>id</code></td>
        <td>AEM</td>
        <td>
            <ul>
                <li>Bedoeld voor zeer beperkte toegang tot AEM functies voor de auteursomgeving. Gebruikers in dit productprofiel zijn lid van de AEM "Medewerkers" die automatisch in AEM worden gemaakt</li><br>
                <li>Als de standaardservice geselecteerd blijft
                    <ul>
                        <li>gebruikers in dit productprofiel zijn ook lid van de AEM "AEM Users - Service"</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Verslaggevers - auteur - Program <code>id</code> - Omgeving <code>id</code></td>
        <td>AEM Verslaggevers</td>
        <td>
            <ul>
                <li>Momenteel niet gebruikt, maar in de toekomst kan toegang tot rapporteringsinformatie over de auteursrij voor dit milieu verlenen.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Assets Collaborator - auteur - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM Assets Collaborator-gebruikers</td>
        <td>
        <ul>
                <li>Bedoeld voor alleen-lezen toegang tot de DAM. Gebruikers in dit productprofiel zijn lid van de AEM "Medewerkers" die automatisch in AEM worden gemaakt.
                </li>
                <li>
                Bovendien worden hiermee de rechten van de Adobe Express op het creëren van variaties in activa vastgelegd.
                </li>
          <ul>
    </tr>
    <tr>
        <td></td>
        <td>AEM Assets Power User - auteur - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM Assets Power Users</td>
<td>
        <ul>
                <li>Bedoeld voor alleen-lezen toegang tot de DAM. Gebruikers in dit productprofiel zijn lid van de AEM "Medewerkers" die automatisch in AEM worden gemaakt.
                </li>
                <li>
                Bovendien worden hiermee de rechten van de Adobe Express op het creëren van variaties in activa vastgelegd.
                </li>
          <ul>
</td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Forms Content Managers - auteur - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM Forms Content Managers</td>
        <td>
            <ul>
                <li>Bedoeld voor gecontroleerde toegang tot AEM Forms-ontwerpfuncties in deze omgeving. Gebruikers in dit productprofiel zijn lid van de AEM AEM Forms-gebruikers, die automatisch in AEM wordt gemaakt.</li><br>
                <li>Als de standaardservice geselecteerd blijft
                    <ul>
                        <li>gebruikers in dit productprofiel zijn ook lid van de AEM "AEM Forms Content Managers - Service".</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Forms Developers - auteur - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM Forms Developers</td>
        <td>
            <ul>
                <li>Bedoeld voor gecontroleerde toegang tot AEM Forms-ontwerpfuncties in deze omgeving. Gebruikers in dit productprofiel zijn lid van de AEM AEM Forms-groep voor gebruikers in de formuliervoeding, die automatisch wordt gemaakt in AEM. Deze gebruikers hebben het recht om XDP's en de auteur Modellen van de Gegevens van de Vorm ook naast normale vormauteurstaken te uploaden.</li><br>
                <li>Als de standaardservice geselecteerd blijft
                    <ul>
                        <li>gebruikers in dit productprofiel zijn ook lid van de AEM "AEM Forms Developers - Service".</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Forms Communications Service Users - auteur - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM Forms Communications Service-gebruikers</td>
        <td>
            <ul>
                <li>Bedoeld voor gecontroleerde toegang tot AEM Forms Communications Services-functies in deze omgeving. Gebruikers in dit productprofiel zijn lid van de AEM AEM Forms-gebruikers, die automatisch in AEM wordt gemaakt.</li><br>
                <li>Als de standaardservice geselecteerd blijft
                    <ul>
                        <li>gebruikers in dit productprofiel zijn ook lid van de AEM "AEM Forms Communications Service Users - Service".</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td>AEM Publish</td>
        <td>AEM - Publiceren - Programma <code>id</code> - Omgeving <code>id</code></td>
        <td>AEM</td>
        <td>
            <ul>
                <li>Bedoeld voor zeer beperkte toegang tot AEM functies voor de auteursomgeving. Gebruikers in dit productprofiel zijn lid van de AEM "contrib" die automatisch worden gemaakt in AEM</li><br>
                <li>Als de standaardservice geselecteerd blijft
                    <ul>
                        <li>gebruikers in dit productprofiel zijn ook lid van de AEM "AEM Users - Service".</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Verslaggevers - Publiceren - Programma <code>id</code> - Milieu <code>id</code></td>
        <td>AEM Verslaggevers</td>
        <td>
            <ul>
                <li>Momenteel niet gebruikt, maar in de toekomst kan dit voor deze omgeving toegang bieden tot rapportage-informatie over de publicatielaag.</li>
            </ul>
        </td>
    </tr>
   <tr>
        <td></td>
        <td>AEM Forms Communications Service Users - publish - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM Forms Communications Service-gebruikers</td>
        <td>
            <ul>
                <li>Bedoeld voor gecontroleerde toegang tot AEM Forms Communications Services-functies in deze omgeving. Gebruikers in dit productprofiel zijn lid van de AEM AEM Forms-gebruikers, die automatisch in AEM wordt gemaakt.</li><br>
                <li>Als de standaardservice geselecteerd blijft
                    <ul>
                        <li>gebruikers in dit productprofiel zijn ook lid van de AEM "AEM Forms Communications Service Users - Service".</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
</table>

Merk op dat elk Profiel van het Product een bijbehorende Dienst van het Profiel van het Product heeft die door gebrek wordt toegelaten. Tenzij u complexe toegangsvereisten hebt, wordt het geadviseerd om enkel de StandaardDienst geselecteerd te houden. Een overeenkomstige AEM groep zal in AEM met de noemende overeenkomst `<Product Profile Prefix> - Service` worden gecreeerd (bijvoorbeeld, **de Inhoud van AEM Sites Managers - Dienst**), en de gebruikers in de profielen van het ouderproduct zullen automatisch leden van die overeenkomstige AEM groep worden.

De AEM groep in AEM verbonden aan de dienst zal de samengevoegde reeks gebruikers hebben die in alle bijbehorende Profielen van het Product van die dienst voor die milieu-rij combinatie bestaan.

![ de Diensten ](/help/onboarding/assets/services.png)

De volgende afbeelding vertegenwoordigt de AEM groepen die overeenkomen met het productprofiel en de service van de auteur van AEM Sites Content Managers.

![ AEM Groep aan de afbeelding van de Dienst ](/help/onboarding/assets/profile-to-service-mapping.png)

>[!NOTE]
>
>Elke gebruiker die aan een het productprofiel van AEM as a Cloud Service wordt toegewezen heeft read-only toegang tot Cloud Manager via de **** rol van de Gebruiker van Cloud Manager.
>
>De gebruikers met slechts de **rol van de Gebruiker 0} Cloud Manager kunnen in Cloud Manager registreren en aan de AEM auteursmilieu&#39;s (als zij bestaan) navigeren door de** Programma&#39;s **menuopties te gebruiken.** De **rol van de Gebruiker van 0} Cloud Manager {is niet voldoende om tot programmadetails toegang te hebben.** Als dergelijke toegang nodig is, moeten de gebruikers extra rollen door hun systeembeheerder worden verleend.

>[!WARNING]
>
>De **AEM Beheerders** naam van het productprofiel moet niet worden veranderd. Het veranderen van de naam van het **AEM Beheerders** productprofiel zal beheerderrechten uit alle gebruikers verwijderen die aan dat profiel worden toegewezen.

>[!TIP]
>
>* Meer over AEM productprofielen leren, zie [ Toewijzend AEM Profielen van het Product ](/help/journey-onboarding/assign-profiles-aem.md).
>* Voor meer informatie over het onboarding proces, zie [ onboarding reis ](/help/journey-onboarding/overview.md).

## Cloud Manager-productprofielen {#cloud-manager-product-profiles}

Cloud Manager beschikt over vooraf geconfigureerde productprofielen die kunnen worden beschouwd als op rollen gebaseerde machtigingen. Uw systeembeheerder is verantwoordelijk voor het instellen van uw Cloud Manager-team door deze toe te wijzen aan deze productprofielen.

>[!TIP]
>
>Zie [ Rol Gebaseerde Toestemmingen in Cloud Manager ](/help/onboarding/cloud-manager-introduction.md#role-based-permissions) voor meer details.

Aan elk van de productprofielen zijn specifieke machtigingen gekoppeld.

* **BedrijfsEigenaar**
   * In deze rol hebt u de toestemming om een nieuw programma toe te voegen of een programma uit te geven, een milieu toe te voegen of bij te werken, code in AEM milieu op te stellen, of de controles van de codekwaliteit uit te voeren.
   * Deze gebruiker is verantwoordelijk voor het definiëren van KPI&#39;s, het goedkeuren van productieimplementaties en het overschrijven van belangrijke 3-tivelige fouten indien nodig.
* **Manager van de Plaatsing**
   * In deze rol, hebt u de toestemming om een milieu toe te voegen of bij te werken, om het even welke pijpleiding in werking te stellen, en code op te stellen aan AEM milieu, of de controles van de codekwaliteit uit te voeren.
   * Deze gebruiker beheert implementatiebewerkingen en gebruikt Cloud Manager om staging-/productieimplementaties uit te voeren, CI-/CD-pijpleidingen te bewerken, belangrijke 3-tielfouten indien nodig goed te keuren en toegang te krijgen tot de git-opslagruimte.
* **Ontwikkelaar**
   * In deze rol, hebt u de toestemming om persoonlijke toegangstokens te produceren om tot git toegang te hebben.
   * Deze gebruiker ontwikkelt en test de code van de douanetoepassing en gebruikt hoofdzakelijk Cloud Manager om plaatsingsstatus te bekijken en kan tot de git bewaarplaats voor codeverplichtingen toegang hebben.
* **Manager van het Programma**
   * In deze rol, hebt u de toestemming om pijpleidingen te plannen, de de kwaliteitsspoorten van drie lagen met voeten te treden, en productiegoedkeuring te verstrekken.
   * Deze gebruiker gebruikt Cloud Manager om teamopstelling uit te voeren, status te herzien, KPIs te bekijken, en kan belangrijke 3-rij mislukkingen goedkeuren wanneer noodzakelijk.

Een gebruiker kan aan veelvoudige productprofielen worden toegewezen. Bijvoorbeeld, die zowel **BedrijfsEigenaar** toewijst en **Plaatsing leidt** r rollen aan een gebruiker hen de som deze toestemmingen.

Uw Cloud Manager-team omvat ten minste:

* Één **BedrijfsEigenaar**, die typisch ook de systeembeheerder is, en moet de eerste persoon aan login en toegang Cloud Manager zijn
* Één **Manager van de Plaatsing**
* Één **Ontwikkelaar**

>[!NOTE]
>
>Gebruikers die toegang tot AEM as a Cloud Service willen krijgen, moeten behoren tot een van de volgende twee productprofielen: `AEM Users` of `AEM Administrators` . Machtigingen om Cloud Manager te beheren volstaan niet.

>[!TIP]
>
>* Meer over het productprofielen van Cloud Manager leren, zie [ Toewijzend de Leden van het Team aan de Profielen van het Product van Cloud Manager ](/help/journey-onboarding/assign-profiles-cloud-manager.md).
>* Voor meer informatie over het onboarding proces, zie [ onboarding reis ](/help/journey-onboarding/overview.md).
