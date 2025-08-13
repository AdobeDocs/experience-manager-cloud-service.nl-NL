---
title: Opmerkingen bij de release voor Cloud Manager 2025.8.0
description: Meer informatie over de release van Cloud Manager 2025.8.0 in Adobe Experience Manager as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 24d9fc6f-462d-417b-a728-c18157b23bbe
source-git-commit: c93716b1a2453c26169020b32e66eb4207f13002
workflow-type: tm+mt
source-wordcount: '1377'
ht-degree: 0%

---

# Opmerkingen bij de release voor Cloud Manager 2025.8.0 in Adobe Experience Manager as a Cloud Service {#release-notes}

<!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2025.08.0+Release -->

Meer informatie over de release van Cloud Manager 2025.8.0 in AEM (Adobe Experience Manager) as a Cloud Service.

Zie ook de [ huidige versienota&#39;s voor Adobe Experience Manager as a Cloud Service ](/help/release-notes/release-notes-cloud/release-notes-current.md).

## Releasedatums {#release-date}

De releasedatum voor Cloud Manager 2025.8.0 in AEM as a Cloud Service is donderdag 7 augustus 2025.

De volgende geplande release is donderdag 4 september 2025.

## Nieuwe functies {#what-is-new}

* **Experience Hub van Adobe die spoedig komt**

  Vanaf 19 augustus 2025 start Adobe een gefaseerde uitrol van de nieuwe Experience Hub voor alle Adobe Experience Manager-gebruikers.

  Experience Hub is een eenduidig beginpunt dat gepersonaliseerde contextafhankelijke ervaringen biedt om gebruikers te helpen sneller doelstellingen te bereiken. De uitrol wordt uiterlijk op 26 augustus 2025 voltooid en beschikbaar gesteld aan alle gebruikers. De nieuwe Experience Hub is toegankelijk direct bij [ experience.adobe.com ](https://experience.adobe.com/). Meer leren, zie [ Adobe Experience Hub ](/help/implementing/cloud-manager/aem-home.md).

* **de vergunning van Edge Delivery Services kan in een programma van HIPAA op een zelfbediening manier worden omvat**

  Organisaties met vereisten op het gebied van gezondheidszorg of gevoelige gegevens kunnen nu Edge Delivery Services op een zelfbedieningsmanier gebruiken, waardoor HIPAA-naleving kan voldoen aan strenge regelgevingsnormen. <!-- CMGR-70016 -->

* **BYOG is nu beschikbaar voor Edge Delivery Services**

  Met Cloud Manager kunt u nu externe Git-opslagruimten configureren, waardoor flexibele workflows voor codebeheer mogelijk zijn. <!--(CMGR‑69010, CMGR‑70988) --> Hiermee kunt u ook code uit een gekozen vertakking rechtstreeks in de gebruikersinterface van Cloud Manager ophalen, waardoor taken in de handmatige opslagplaats worden beperkt. Zie [ de plaats van Edge Delivery vormen om een externe bewaarplaats van het Git te gebruiken ](/help/implementing/cloud-manager/edge-delivery/config-edge-delivery-site-with-byog.md) <!-- (CMGR‑68085)(CMGR-69015) --> <!-- KT: https://wiki.corp.adobe.com/display/DMSArchitecture/%5B2025%5D+Cloud+Manager+-+Bring+Your+Own+Git+with+EDS -->

* **Geautomatiseerde levering voor nieuwe toe:voegen-op Forms**

  Klanten met alleen sites hebben vaak een lichte, voordelige manier nodig om marketingformulieren te maken. De nieuwe invoegtoepassing AEM Forms Sites voldoet aan die vereisten door beperkte Forms-functies toe te voegen aan een Sites-programma. Het leidt ook tot een duidelijke verbeteringsweg aan het volledige aanbod van AEM Forms. <!-- (CMGR-64301) --> <!-- KT: CMGR Provisioning Support for AEM Forms Sites Add-On SKU https://wiki.corp.adobe.com/pages/viewpage.action?pageId=3578379797 -->

  De invoegtoepassing:
   * Koppelt aan een Sites-programma en implementeert deze naast het programma, geen apart Forms-programma of machtiging.
   * Hiermee worden eenvoudige praktijkvoorbeelden voor marketingformulieren bedoeld.
   * Verschijnt in de **Oplossingen &amp; toe:voegen-ons** lijst tijdens de verwezenlijking van het Programma van de Productie of het Programma van de Productie uitgeven, slechts wanneer IMS org beschikbare toe:voegen-op vergunningen van Forms houdt.

     ![ toe:voegen-ons van Forms ](/help/implementing/cloud-manager/release-notes/assets/forms-add-on.png) *toe:voegen-on van Forms kan in het Programma worden toegevoegd slechts als de toe:voegen-op vergunningen van Forms in uw IMS org beschikbaar zijn.*

     ![ Forms toe:voegen-op in Oplossingen &amp; toe:voegen-ONS wanneer het creëren van een productieprogramma ](/help/implementing/cloud-manager/release-notes/assets/forms-add-on-creating-production-program.png) *tijdens de Aanmaak van het Programma, kunt u toe:voegen-op Forms binnen de oplossing van Plaatsen selecteren.*

     ![ Forms toe:voegen-op wanneer het uitgeven van een productieprogramma ](/help/implementing/cloud-manager/release-notes/assets/forms-add-on-editing-production-program.png) *in **geeft Programma**&#x200B;uit, selecteer Forms toe:voegen-op voor het programma van Plaatsen, dan stel de pijpleiding in werking om het in de milieu&#39;s te activeren.*

     Voor meer informatie, zie [ een productieprogramma ](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) creëren.

## Beta-programma&#39;s {#private-beta-program}

Neem deel aan bètaprogramma&#39;s van Cloud Manager om exclusieve toegang te krijgen tot de volgende functies voordat ze in het algemeen worden uitgebracht.

De volgende mogelijkheden zijn momenteel beschikbaar:

### Één-klik terugschroeven van prijzen voor pijpleidingsplaatsingen {#one-click-rollback}

Snel aan een vorige plaatsing terugkeren als de recentste klantenbroncode niet zoals verwacht-geen behoefte werkt om de volledige pijpleiding opnieuw te voeren of begaat manueel terug.<!--https://jira.corp.adobe.com/browse/CMGR-69556 -->

![ herstel klantenbroncode van de kaart van Milieu ](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed.png) *van Milieu&#39;s hierboven die **tonen herstelt**>**Vorige code stelde**&#x200B;optie voor een geselecteerd milieu.*

![ herstel vorige code opgesteld dialoogdoos ](/help/implementing/cloud-manager/release-notes/assets/restore-previous-code-deployed-dialogbox.png)
*in **herstel vorige code opgesteld**&#x200B;dialoogdoos, herzie de momenteel opgestelde versie en de versie u wilt herstellen, dan klikken bevestigt **&#x200B;***.

![ Herstellend activering ](/help/implementing/cloud-manager/release-notes/assets/restoring-previous-code-deployed-restoring.png)
*Cloud Manager rolt het milieu terug naar de vroegere bouwstijl, houdt inhoud en configuratie intact, en merkt het milieu **Herstellend**&#x200B;tot de plaatsing voltooit.*

![ de codeversie van Source in gebruik ](/help/implementing/cloud-manager/release-notes/assets/environments-view-details-sourcecodeversion.png) *de mening van de Details van het Milieu, zoals hierboven gezien, toont nu ook de actieve bron-code versie in gebruik.*

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ restorecode@adobe.com ](mailto:restorecode@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID.

Zie [ de Vorige Code herstellen die in AEM as a Cloud Service ](/help/operations/restore-previous-code-deployed.md) wordt opgesteld.

Zie ook [ Inhoud terugzetten in AEM as a Cloud Service ](/help/operations/restore.md).

### Speciale testomgeving {#specialized-test-environment}

Cloud Manager steunt nu de toevoeging van een nieuw milieutype genoemd **Gespecialiseerde het Testen Milieu**. De omgeving is ontworpen om teams te helpen functies onder bijna-productieomstandigheden te valideren voordat ze live gaan. Dit omgevingstype is verschillend van *Productie + Stadium*, *Ontwikkeling*, of *Snelle Ontwikkeling* milieu&#39;s en biedt een geconcentreerde ruimte voor het runnen van geavanceerde bevestigingsscenario&#39;s aan.

**Recente verhogingen**

* U kunt een Specialized het Testen Milieu op een niet productiepijplijn door een eenvoudigere, meer intuïtieve werkschema nu vormen. De gestroomlijnde installatie versnelt voltooiing en vermindert configuratiefouten.
* **Inhoud van het Exemplaar** wordt nu gesteund in Gespecialiseerde het Testen milieu&#39;s. U kunt **Inhoud van het Exemplaar** veilig in geïsoleerde testende milieu&#39;s in werking stellen die Productie weerspiegelen. <!-- (CMGR‑68900) -->

Zie [ een Gespecialiseerde het Testen Milieu ](/help/implementing/cloud-manager/specialized-test-environment.md) toevoegen.

![ voeg milieu dialoogdoos met Gespecialiseerde het Testen van Milieu geselecteerde radioknoop ](/help/implementing/cloud-manager/release-notes/assets/specialized-test-environment.png) toe

Als u in het testen van deze nieuwe eigenschap en het delen van uw terugkoppelt geinteresseerd bent, verzend een e-mail naar [ grp-earlyadopter_cs_advtestenvironment@adobe.com ](mailto:grp-earlyadopter_cs_advtestenvironment@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID.


### Je eigen gang (BYOG) {#gitlab-bitbucket-azure-vsts}

<!-- BOTH CS & AMS -->

Klanten kunnen nu hun Azure DevOps Git-opslagruimten in Cloud Manager aan boord nemen, met ondersteuning voor zowel moderne Azure DevOps- als oudere VSTS-opslagruimten (Visual Studio Team Services).

* Voor Edge Delivery Services-gebruikers kan de ingebouwde opslagplaats worden gebruikt voor het synchroniseren en implementeren van sitecode.
* Voor AEM as a Cloud Service- en Adobe Managed Services-gebruikers (AMS) kan de opslagplaats worden gekoppeld aan zowel full-stack als frontend pijpleidingen.

De steun voor extra pijpleidingstypes en trekverzoekbevestiging door pijpleidingen van de codekwaliteit komt binnenkort.

Zie [ externe bewaarplaatsen in Cloud Manager ](/help/implementing/cloud-manager/managing-code/external-repositories.md) toevoegen.

![ voeg de dialoogdoos van de Bewaarplaats ](/help/implementing/cloud-manager/release-notes/assets/azure-repo.png) toe

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. Be sure to include which Git platform you want to use and whether you are on a private/public or enterprise repository structure. -->

**vaak gestelde vragen over BYOG**

| Vraag | Antwoord |
|---|---|
| *hoe kan een projectschakelaar terug naar de Adobe-Beheerde bewaarplaats van het Git indien nodig?* | Het is eenvoudig om terug te schakelen. [ werk de pijpleidingen ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) bij om aan de bewaarplaats van Adobe te richten en de externe bewaarplaats te verwijderen als het niet meer vereist is. |
| *is het mogelijk om verschillende bewaarplaatsen voor verschillende milieu&#39;s (bijvoorbeeld, niet-productie tegenover productie) te vormen om het testen in niet productie eerst toe te staan?* | Ja, verschillende opslagruimten kunnen worden geconfigureerd voor afzonderlijke omgevingen. De ontwikkelings- of codekwaliteitspijplijn kan bijvoorbeeld naar een externe opslagplaats verwijzen terwijl de productiepijplijn verbonden blijft met de Adobe-opslagplaats. Zorg ervoor dat de synchronisatietaak tussen de twee opslagruimten actief blijft tijdens deze configuratie. |
| *blijven de bestaande montages zoals `IP Allow` lijsten werken?* | Ja, bestaande `IP Allow` lijsten werken nog steeds zoals gewoonlijk. Nochtans, als de externe bewaarplaats van het Git door een firewall wordt beschermd, moeten de noodzakelijke [ adressen van Adobe IP aan de lijst van gewenste personen ](/help/implementing/cloud-manager/ip-allow-lists/introduction.md) worden toegevoegd. |
| *Werken al bewaarplaats GitLab URLs? De repository URL in gebruik volgt de notatie `https://gitlab_dedicated_url.com/path/repo-name.git` , die afwijkt van het voorbeeld in de documentatie.* | Ja, om het even welke bewaarplaats GitLab die API V3 of V4 steunt wordt gesteund, met inbegrip van zelf-ontvangen GitLab URLs als die in [ wordt beschreven voeg externe bewaarplaatsen in Cloud Manager ](/help/implementing/cloud-manager/managing-code/external-repositories.md) toe (`https://git-vendor-name.com/org-name/repo-name.git`). |


#### Toegangstokens beheren{#manage-access-tokens}

Het gebruik **beheert de Tokens van de Toegang** in Cloud Manager aan mening, hernoemt, en schrapt toegangstokens verbonden aan externe bewaarplaatsen BYOG, zoals Onderneming GitHub, GitLab, Bitbucket, en Azure DevOps.

Zie [ de Tokens van de Toegang beheren ](/help/implementing/cloud-manager/managing-code/manage-access-tokens.md).

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [Grp-CloudManager_BYOG@adobe.com](mailto:grp-cloudmanager_byog@adobe.com) from your email address associated with your Adobe ID. -->


### Edge Delivery Config Pipet toevoegen {#add-eds-pipeline}

Config Pipelines worden nu ondersteund voor sites die met Edge Delivery Services zijn gebouwd en deze mogelijkheid uitbreiden tot buiten de Cloud Service-omgevingen. U kunt **Pijpleidingen Config** gebruiken om montages zoals verkeer het filtreren regels en configuraties van de Firewall van de Toepassing van het Web (WAF) te beheren, waar toepasselijk. Zie [ Ondersteunde Configuraties ](/help/operations/config-pipeline.md#configurations).

**Recente verhoging**

* De pijpleidingen van Edge Delivery Services tonen nu **Configuratie** in de **Gestelde kolom van de Code**, toelatend onmiddellijke identificatie van configuratie-slechts plaatsingen. <!-- CMGR‑69681 -->
* Cloud Manager toont **Edge Delivery Pijpleiding** zodra een programma minstens één plaats van Edge Delivery Services en één in kaart gebracht domein bevat. Anders wordt de optie uitgeschakeld en bevat knopinfo waarin de ontbrekende vereisten worden uitgelegd. <!-- CMGR‑69680 -->
* Het **Edge Delivery** lusje toont een nieuwe **pijpleidingen van Edge Delivery** widget die van de naam, de Status, de Bewaarplaats, en Tak van elke pijpleiding een lijst maakt. <!-- (CMGR-69052) -->

  ![ Edge Delivery pijpleiding widget die pijpleidingsnaam, status, bewaarplaats, en tak tonen ](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-widget.png)

* Het **paneel van Filters** voegt de sectie van het Type van a **Levering** toe; omvat **levering van Edge** en **publiceren levering** checkboxes. <!-- (CMGR-69682) -->

  ![ paneel die van de Filter het nieuwe type van Levering van Edge toont levering en publiceert levering ](/help/implementing/cloud-manager/release-notes/assets/filter-delivery-type.png)

![ voeg de pijpleiding van Edge Delivery in Add drop-down lijst van de Pijpleiding ](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add.png) toe *toevoegend een pijpleiding van Edge Delivery van de **pagina van het Overzicht van het Programma**,**Pipelines**&#x200B;kaart.*

![ voeg de pijpleidingsdialoogdoos van Edge Delivery toe ](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-add-dialogbox.png) *voeg de pijpleidingsdialoogdoos van Edge Delivery toe.*

Zie [ toevoegen de Pijpleiding van Edge Delivery ](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md)

<!-- If you are interested in testing this new feature and sharing your feedback, send an email to [grp-aemeds-config-pipeline-adopter@adobe.com](mailto:grp-aemeds-config-pipeline-adopter@adobe.com) from your email address associated with your Adobe ID. -->


## Bugfixes

* De pijpleidingen leveren nu variabelen slechts aan de actieve het domeinconfiguratie van Edge Delivery Services, die om het even welke configuratie overslaat die tijdens pijpleidingsrecreatie wordt verwijderd. <!-- (CMGR‑70039) -->
* De uitvoering van de pijpleiding begint nu betrouwbaar; verholpen een kwestie waar sommige pijpleidingen er niet in slaagden te beginnen wegens interne fouten van de middelbehandeling. <!-- (CMGR‑58167) -->
* Met Content Copy worden Cloud Manager-machtigingen en -blokkeringen gevalideerd bij gebruikers die geen implementatiebeheer of beheerdersrechten hebben. <!-- (CMGR‑62097) -->


<!-- ## Known issues {#known-issues} -->

