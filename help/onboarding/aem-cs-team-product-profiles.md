---
title: AEM as a Cloud Service-team en productprofielen
description: Leer hoe AEM as a Cloud Service-team en productprofielen toegang tot uw Adobe-oplossingen met licentie kunnen verlenen en beperken.
exl-id: 7b1474c9-aca0-4354-8798-1abdcda2f6dd
feature: Onboarding
role: Admin, User, Developer
source-git-commit: b9cc5450effb70afcb67725fe38826646d947da9
workflow-type: tm+mt
source-wordcount: '2124'
ht-degree: 0%

---


# AEM as a Cloud Service-team en productprofielen {#product-profiles}

Leer hoe AEM as a Cloud Service-team en productprofielen toegang tot uw Adobe-oplossingen met licentie kunnen verlenen en beperken.

## Productprofielen {#profiles}

Wanneer u een gebruiker toegang geeft tot een specifieke Adobe-oplossing, wilt u deze niet altijd volledige toegang geven. Met productprofielen kan elke oplossing beschikken over een eigen set gebruikersrechten. Deze zijn beschikbaar en toegankelijk via [&#x200B; Admin Console &#x200B;](/help/journey-onboarding/admin-console.md).

De Adobe Admin Console heeft een gestructureerde hiërarchie van product, productinstanties, en productprofielen waar de interne gebruikers van een organisatie kunnen worden toegewezen lidmaatschap, die hen toegang tot de oplossingen en de eigenschappen geven die zijn vergunning gegeven.

<!-- Alexandru: Drafting for now 

Your AEM as a Cloud Service team members are added and assigned to one or more of the following product profiles via the Admin Console during onboarding.

* **AEM Administrators**: An AEM administrator is typically assigned to developers, in particular developers who need access to, for example, the development environments. The AEM administrator's product profile is used to grant administrator privileges in the associated AEM instance.

* **AEM Users**: AEM users are the users in your organization who use AEM as a Cloud Service generally to create content. These users need to access AEM to do their tasks. The AEM users product profile is typically assigned to an AEM content author who creates and reviews the content. This content can be of many types such as pages, assets, publications, and so on. The AEM users product profile shown below is assigned to these members.

![Product profiles](/help/onboarding/assets/admin-console-profiles.png) -->

## AEM as a Cloud Service-productprofielen {#aem-product-profiles}

AEM as a Cloud Service is een volledig &#39;cloud-native&#39; aanbod dat AEM als service biedt. Het biedt AEM op een native manier in de cloud, met nieuwe kenmerken zoals altijd ingeschakeld, altijd actueel, altijd veilig en altijd op schaal. Tegelijkertijd behoudt het de belangrijkste waardestelling die AEM biedt als aanpasbaar platform voor klanten en stelt het teams op bedrijfsniveau in staat in hun ontwikkelings- en leveringsprocedure te integreren. Zie [&#x200B; Inleiding aan Adobe Experience Manager as a Cloud Service &#x200B;](/help/overview/introduction.md) om meer over AEM as a Cloud Service te leren.

### Productinstanties op organisatieniveau {#org-level-product-instances}

>[!NOTE]
>
> Sommige productinstanties en productprofielen die in dit artikel worden beschreven, worden mogelijk alleen weergegeven voor nieuwe omgevingen. Zie [&#x200B; Toevoegend de Profielen van het Product voor Bestaande sectie van Milieu &#x200B;](#adding-product-profiles-for-existing-environments) voor hoe te om uw milieu&#39;s te moderniseren.

Als Adobe voor het eerst licenties voor een AEM-oplossing verwerkt, verschijnen er twee Product Instances in Adobe Admin Console, onder het Adobe Experience Manager as a Cloud Service-product:

* **AEM op één of ander niveau** - bevat één of meerdere Profiel van het Product dat toegang tot eigenschappen vertegenwoordigt die aan alle milieu&#39;s van AEM, eerder dan enkel aan één enkel zijn
* **Cloud Manager** - bevat de Profielen van het Product die aan verschillende niveaus van toegang tot de eigenschappen van Cloud Manager beantwoorden.

<!--
>[!NOTE]
>
>For existing programs, the AEM Org-Level Product Instance is created upon selecting the **Update product** profiles action for a given environment.
-->

![&#x200B; of de Instanties van het Product van het Niveau &#x200B;](/help/onboarding/assets/orglevel.png)

In de AEM Org-Level Product Instance bevindt zich een productprofiel met de naam AEM Org-Level Reporters, dat momenteel niet wordt gebruikt, maar in de toekomst wel toegang kan vertegenwoordigen tot het ophalen van informatie over AEM-productlicenties.

Wanneer een Forms Communication Solution een licentie heeft, wordt een overeenkomstig productprofiel ook weergegeven onder de AEM Org-Level Product Instance.

![&#x200B; Profiel van het Product van Reporters &#x200B;](/help/onboarding/assets/org-level-reporters.png)

### Product-instanties op milieuniveau en op niveau van niveaus {#environment-and-tier-level-product-instances}

Nadat u nieuwe programma&#39;s hebt voorzien in een of meer AEM-omgevingen, worden per omgeving twee Product-instanties weergegeven die productprofielen bevatten voor auteur en publiceren.

![&#x200B; Instanties van het Product van het Milieu &#x200B;](/help/onboarding/assets/env-productinstances.png)

Hieronder vindt u de productprofielen in een productinstantie van de auteur voor een organisatie die een omgeving heeft ingericht in een programma met AEM Sites:

![&#x200B; Instanties van het Product van Plaatsen &#x200B;](/help/onboarding/assets/sites-product-instances.png)

In de volgende tabel vindt u een lijst met mogelijke productprofielen onder een specifieke instantie van het product die specifiek is voor de omgeving.

<table style="table-layout:auto">
    <tr>
        <th>Productinstantie</th>
        <th>Naamgevingsconventie</th>
        <th>Standaardservice</th>
        <th>Beschrijving</th>
    </tr>
    <tr>
        <td>AEM-auteur</td>
        <td>AEM Sites Content Managers - auteur - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM Sites Content Managers</td>
        <td>
            <ul>
                <li>Bedoeld voor gecontroleerde toegang tot AEM Sites-ontwerpfuncties in deze omgeving. Gebruikers in dit productprofiel zijn lid van de AEM Sites-groep die de inhoud heeft gemaakt en die automatisch in AEM wordt gemaakt. De AEM-groepsmachtigingen moeten in AEM worden geconfigureerd met het gewenste toegangsniveau.</li><br>
                <li>Als de standaardservice geselecteerd blijft
                    <ul>
                        <li>gebruikers in dit productprofiel zijn ook lid van de AEM-groep "AEM Sites Content Managers - Service".</li>
                      <!--  <li>users in this product profile will have access to AEM Sites Content Management API.</li>
                        <li>an Adobe Developer Console API OAuth S2S project containing AEM Sites Content Management API can optionally be scoped to this environment.</li>-->
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM-beheerders - auteur - Programma <code>id</code> - Omgeving <code>id</code></td>
        <td>AEM-beheerders</td>
        <td>
            <ul>
                <li>Bedoeld voor onbeperkte toegang tot AEM-functies voor auteur en publicatie van omgeving. Gebruikers in dit productprofiel zijn lid van de AEM Administrator's auteurgroep van AEM die automatisch in AEM wordt gemaakt.</li><br>
                <li>Als de standaardservice geselecteerd blijft
                    <ul>
                        <li>gebruikers in dit productprofiel zullen ook lid zijn van de AEM-groep "AEM Administrators - Service"</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Users - auteur - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM-gebruikers</td>
        <td>
            <ul>
                <li>Bedoeld voor zeer beperkte toegang tot de milieueigenschappen van de AEM-auteur. Gebruikers in dit productprofiel zijn lid van de AEM-groep "Medewerkers" die automatisch in AEM wordt gemaakt</li><br>
                <li>Als de standaardservice geselecteerd blijft
                    <ul>
                        <li>gebruikers in dit productprofiel zijn ook lid van de AEM-groep "AEM Users - Service"</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Reporters - auteur - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM Reporters</td>
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
                <li>Werken met middelen van Experience Manager via integratie van Assets die beschikbaar is voor uw organisatie in andere Adobe-producten en niet-Adobe-toepassingen.
                </li>
                <li>Elementen maken en bewerken met behulp van ingebouwde Adobe Express en Firefly, waarbij gebruik wordt gemaakt van professioneel ontworpen sjablonen, merkpakketten, Adobe Stock-middelen enzovoort.</li>
                <li>Gebruik AEM Assets Content Hub Portal voor toegang tot en gebruik goedgekeurde middelen van uw organisatie.</li>
          <ul>
    </tr>
    <tr>
        <td></td>
        <td>AEM Assets Power User - auteur - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM Assets Power Users</td>
<td>
        <ul>
                <li>Open alle AEM Assets-mogelijkheden, inclusief het beheer van middelen, metagegevens en het algemene beheer en de automatisering van digitale middelen.</li>
                <li>Werken met middelen van Experience Manager via integratie van Assets die beschikbaar is voor uw organisatie in andere Adobe-producten en niet-Adobe-toepassingen.
                </li>
                <li>Elementen maken en bewerken met behulp van ingebouwde Adobe Express en Firefly, waarbij gebruik wordt gemaakt van professioneel ontworpen sjablonen, merkpakketten, Adobe Stock-middelen enzovoort.</li>
                <li>Gebruik AEM Assets Content Hub Portal voor toegang tot en gebruik goedgekeurde middelen van uw organisatie.</li>
          <ul>
</td>
    </tr>
    <tr>
        <td></td>
        <td>AEM Forms Content Managers - auteur - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM Forms Content Managers</td>
        <td>
            <ul>
                <li>Bedoeld voor gecontroleerde toegang tot AEM Forms-ontwerpfuncties in deze omgeving. Gebruikers in dit productprofiel zijn lid van de AEM-groep voor AEM Forms-formulieren en gebruikers, die automatisch in AEM wordt gemaakt.</li><br>
                <li>Als de standaardservice geselecteerd blijft
                    <ul>
                        <li>gebruikers in dit productprofiel zijn ook lid van de AEM-groep "AEM Forms Content Managers - Service".</li>
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
                <li>Bedoeld voor gecontroleerde toegang tot AEM Forms-ontwerpfuncties in deze omgeving. Gebruikers in dit productprofiel zijn lid van de AEM-groep voor gebruikers die gebruikmaken van AEM Forms-formulieren, die automatisch wordt gemaakt in AEM. Deze gebruikers hebben het recht om XDP's en de auteur Modellen van de Gegevens van de Vorm ook naast normale vormauteurstaken te uploaden.</li><br>
                <li>Als de standaardservice geselecteerd blijft
                    <ul>
                        <li>gebruikers in dit productprofiel zijn ook lid van de AEM-groep "AEM Forms Developers - Service".</li>
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
                <li>Bedoeld voor gecontroleerde toegang tot AEM Forms Communications Services-functies in deze omgeving. Gebruikers in dit productprofiel zijn lid van de AEM-groep voor AEM Forms-formulieren en gebruikers, die automatisch in AEM wordt gemaakt.</li><br>
                <li>Als de standaardservice geselecteerd blijft
                    <ul>
                        <li>gebruikers in dit productprofiel zijn ook lid van de AEM-groep "AEM Forms Communications Service Users - Service".</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td>AEM Publiceren</td>
        <td>AEM Users - publish - Program <code>id</code> - Environment <code>id</code></td>
        <td>AEM-gebruikers</td>
        <td>
            <ul>
                <li>Bedoeld voor zeer beperkte toegang tot de milieueigenschappen van de AEM-auteur. Gebruikers in dit productprofiel zijn lid van de AEM-groep "Contribute" die automatisch in AEM wordt gemaakt</li><br>
                <li>Als de standaardservice geselecteerd blijft
                    <ul>
                        <li>gebruikers in dit productprofiel zijn ook lid van de AEM-groep "AEM Users - Service".</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
    <tr>
        <td></td>
        <td>AEM-verslaggevers - publiceren - Programma <code>id</code> - Omgeving <code>id</code></td>
        <td>AEM Reporters</td>
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
                <li>Bedoeld voor gecontroleerde toegang tot AEM Forms Communications Services-functies in deze omgeving. Gebruikers in dit productprofiel zijn lid van de AEM-groep voor AEM Forms-formulieren en gebruikers, die automatisch in AEM wordt gemaakt.</li><br>
                <li>Als de standaardservice geselecteerd blijft
                    <ul>
                        <li>gebruikers in dit productprofiel zijn ook lid van de AEM-groep "AEM Forms Communications Service Users - Service".</li>
                    </ul>
                </li>
            </ul>
        </td>
    </tr>
</table>

Merk op dat elk Profiel van het Product een bijbehorende Dienst van het Profiel van het Product heeft die door gebrek wordt toegelaten. Tenzij u complexe toegangsvereisten hebt, wordt het geadviseerd om enkel de StandaardDienst geselecteerd te houden. Een overeenkomstige groep van AEM zal in AEM met de noemende overeenkomst `<Product Profile Prefix> - Service` (bijvoorbeeld, **de Inhoud van AEM Sites Managers - de Dienst**) worden gecreeerd, en de gebruikers in de profielen van het ouderproduct zullen automatisch lid van die overeenkomstige groep van AEM worden.

De AEM-groep in AEM die aan de service is gekoppeld, heeft de geaggregeerde set gebruikers die in alle bijbehorende productprofielen van die service voor die combinatie op milieuniveau bestaan.

![&#x200B; de Diensten &#x200B;](/help/onboarding/assets/services.png)

In de volgende afbeelding ziet u de AEM-groepen die overeenkomen met de productprofiel en service van de auteur van AEM Sites Content Managers.

![&#x200B; Groep van AEM aan de afbeelding van de Dienst &#x200B;](/help/onboarding/assets/profile-to-service-mapping.png)

>[!NOTE]
>
>Elke gebruiker die aan een het productprofiel van AEM as a Cloud Service wordt toegewezen heeft read-only toegang tot Cloud Manager via de **&#x200B;**&#x200B;rol van de Gebruiker van Cloud Manager.
>
>De gebruikers met slechts de **rol van de Gebruiker 0&rbrace; Cloud Manager kunnen in Cloud Manager registreren en aan de de auteursmilieu&#39;s van AEM navigeren (als zij) bestaan door de** Programma&#39;s **menuopties te gebruiken.** De **rol van de Gebruiker van 0&rbrace; Cloud Manager &lbrace;is niet voldoende om tot programmadetails toegang te hebben.** Als dergelijke toegang nodig is, moeten de gebruikers extra rollen door hun systeembeheerder worden verleend.

>[!WARNING]
>
>De **Beheerders van AEM** productprofielnaam moet niet worden veranderd. Het veranderen van de naam van het **productprofiel van de Beheerders van AEM** &lbrace;zal beheerderrechten uit alle gebruikers verwijderen die aan dat profiel worden toegewezen.

>[!TIP]
>
>* Meer over het productprofielen van AEM leren, zie [&#x200B; Toewijzend de Profielen van het Product van AEM &#x200B;](/help/journey-onboarding/assign-profiles-aem.md).
>* Voor meer informatie over het onboarding proces, zie [&#x200B; onboarding reis &#x200B;](/help/journey-onboarding/overview.md).

### Productprofielen toevoegen voor bestaande omgevingen {#adding-product-profiles-for-existing-environments}

In omgevingen die vóór begin april 2024 zijn gemaakt, ontbreken mogelijk de in bovenstaande secties beschreven productinstantie op Org-niveau en bepaalde productprofielen. Bestaande productprofielen zullen ook de de dienstknevels missen. U wordt aangeraden deze productprofielen bij te werken. Dit is een eerste vereiste voor toegang tot bepaalde toekomstige API&#39;s.

Als voor een of meer omgevingen in een programma de productprofielen moeten worden bijgewerkt, geeft Cloud Manager de onderstaande kennisgeving weer. Merk op dat een milieu op de recentste versie van AEM moet zijn alvorens zijn productprofielen kunnen worden bijgewerkt.

![&#x200B; Moderniseer de Profielen van het Product &#x200B;](/help/onboarding/assets/modernize-product-profiles.png)

Het klikken **voegt de knoop van Profielen van het Product** toe zal een menu openen dat opties toont om nieuwe productprofielen aan alle milieu&#39;s toe te voegen beschikbaar in het programma of de individuele milieu&#39;s.

![&#x200B; vervang Milieu&#39;s &#x200B;](/help/onboarding/assets/choose-env-r.png)

Klik **Alle Milieu&#39;s** om de nieuwe productprofielen aan alle milieu&#39;s in het programma toe te voegen. Alternatief, klik **Individuele Milieu&#39;s** om de nieuwe productprofielen aan geselecteerde milieu&#39;s toe te voegen; dit navigeert de gebruiker aan een milieu&#39;s die pagina van een lijst maken, waar **toevoegen de actie van de Profielen van het Product** van het **Meer pictogram van Opties** kan worden geselecteerd.

![&#x200B; Individuele Milieu&#39;s &#x200B;](/help/onboarding/assets/individual-environments.png)

U kunt productprofielen ook toevoegen aan geselecteerde omgevingen door naar de sectie Omgeving van de pagina Programmaoverzicht te navigeren, op het pictogram Meer opties voor een omgeving te klikken en Productprofielen toevoegen te selecteren.

In de status van de omgeving wordt het toevoegen van productprofielen weergegeven terwijl de nieuwe productprofielen worden toegevoegd en vervolgens wordt Running weergegeven wanneer het proces is voltooid.


## Cloud Manager-productprofielen {#cloud-manager-product-profiles}

Cloud Manager beschikt over vooraf geconfigureerde productprofielen die kunnen worden beschouwd als op rollen gebaseerde machtigingen. Uw systeembeheerder is verantwoordelijk voor het instellen van uw Cloud Manager-team door deze toe te wijzen aan deze productprofielen.

>[!TIP]
>
>Zie [&#x200B; Rol Gebaseerde Toestemmingen in Cloud Manager &#x200B;](/help/onboarding/cloud-manager-introduction.md#role-based-permissions) voor meer details.

Aan elk van de productprofielen zijn specifieke machtigingen gekoppeld.

* **BedrijfsEigenaar**
   * In deze rol hebt u de toestemming om een nieuw programma toe te voegen of een programma uit te geven, een milieu toe te voegen of bij te werken, code in het milieu van AEM op te stellen, of de controles van de codekwaliteit uit te voeren.
   * Deze gebruiker is verantwoordelijk voor het definiëren van KPI&#39;s, het goedkeuren van productieimplementaties en het overschrijven van belangrijke 3-tivelige fouten indien nodig.
* **Manager van de Plaatsing**
   * In deze rol, hebt u de toestemming om een milieu toe te voegen of bij te werken, om het even welke pijpleiding in werking te stellen, en code in het milieu van AEM op te stellen, of de controles van de codekwaliteit uit te voeren.
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
>* Meer over het productprofielen van Cloud Manager leren, zie [&#x200B; Toewijzend de Leden van het Team aan de Profielen van het Product van Cloud Manager &#x200B;](/help/journey-onboarding/assign-profiles-cloud-manager.md).
>* Voor meer informatie over het onboarding proces, zie [&#x200B; onboarding reis &#x200B;](/help/journey-onboarding/overview.md).
