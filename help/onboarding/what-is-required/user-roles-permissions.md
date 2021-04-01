---
title: Gebruikersrollen en -machtigingen
description: Deze pagina beschrijft gebruikersrollen en toestemmingen. Volg deze pagina om te leren hoe u gebruikers kunt toevoegen en toewijzen aan Cloud Manager Roles.
translation-type: tm+mt
source-git-commit: b48be794da0b91722fb45ccefbe83e2b0b22d2a9
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 6%

---


# Rollen van wolkenbeheer {#user-roles-permissions}

## Gebruikersrollen {#user-roles}

Veel functies in Cloud Manager vereisen specifieke machtigingen om te werken en beperken de handelingen die u uitvoert binnen de gebruikersinterface op basis van de toegewezen rollen en machtigingen. In sommige gevallen, als u niet de toestemming hebt om een actie te voeren, is de interfacecontrole aanwezig, maar gehandicapt.

Als er een actie is wilt u, maar niet, de sectie hieronder controleren, [Gebruikersrollen en Toestemmingen](#permissions). Afhankelijk van uw doel, kunt u de Beheerder van het Systeem contacteren en om de rol verzoeken u wenst.

Cloud Manager definieert momenteel vier rollen voor gebruikers die de beschikbaarheid van specifieke functies bepalen:

* Business Owner
* Deployment Manager
* Program Manager
* Developer

>[!NOTE]
>De ontwikkelaar persona in Admin Console is niet gerelateerd aan de rol van de Ontwikkelaar in [!UICONTROL Cloud Manager].

## Uw rollen bekijken {#view-roles}

Als u uw rol in Cloud Manager wilt weergeven, meldt u zich aan bij de interface van Cloud Manager, selecteert u het profielpictogram in de rechterbovenhoek en selecteert u **Gebruikersrollen**, zoals in de onderstaande afbeelding wordt getoond.

>[!NOTE]
>Zie [Navigeren naar Cloud Manager](/help/onboarding/what-is-required/navigate-to-cloud-manager.md) voor meer informatie over aanmelden naar Cloud Manager.

![](/help/onboarding/what-is-required/assets/admin-console-9.png)

### Het profiel van het integratieproduct {#integration-product-profile}

Naast het bovenstaande maakt Cloud Manager automatisch een productprofiel met de naam &quot;Integrations - Cloud Service&quot;. Dit productprofiel wordt gebruikt voor de integratie tussen Adobe Experience Manager en andere Adobe-producten. Dit productprofiel **moet** niet worden geschrapt. Als u dit profiel per ongeluk verwijdert, moet het handmatig opnieuw worden gemaakt. De weergavenaam voor dit profiel **must** is `CM_CS_DEFAULT`.


## Gebruikersrollen en -machtigingen {#permissions}

[!UICONTROL Cloud Manager] heeft pre-gevormde rollen met aangewezen toestemmingen. Een ontwikkelaar ontwikkelt bijvoorbeeld code en heeft de toestemming om de code door te sturen naar de Git-opslagplaats. Alternatief, heeft een bedrijfseigenaar verschillende toestemmingen die hen toestaan om programma&#39;s toe te voegen en uit te geven, milieu&#39;s toe te voegen, en plaatsingen goed te keuren.

Elk van de rollen heeft specifieke toestemmingen verbonden aan het. Bijvoorbeeld, als u in de rol van a bent:

* ***Bedrijfs Eigenaar***, hebt u de toestemming om een nieuw programma toe te voegen of een programma uit te geven, een milieu toe te voegen of bij te werken, de pijpleiding toe te voegen/uit te geven en om het even welke pijpleiding in werking te stellen, en code aan AEM milieu of codekwaliteit op te stellen.

* ***De Manager*** van de plaatsing, hebt u de toestemming om een milieu toe te voegen of bij te werken, om het even welke pijpleiding in werking te stellen, en code aan AEM milieu of code-kwaliteit op te stellen.

* ***De ontwikkelaar***, hebt u de toestemming om Persoonlijk Token van de Toegang te produceren om tot Git toegang te hebben.

   >[!NOTE]
   > Een gebruiker kan aan veelvoudige rollen worden toegewezen. Bijvoorbeeld het toewijzen van de rollen Bedrijfs van de Eigenaar en van de Manager van de Plaatsing aan een gebruiker geeft hen de combinatie of de som deze toestemmingen.


De volgende tabel geeft een overzicht van de rollen en de bijbehorende machtigingen in Cloud Manager.

| Machtiging | Beschrijving | Zakelijke eigenaar | Implementatiebeheer | Programmabeheerder | Ontwikkelaar |
|--- |--- |--- |--- |--- |--- |
| Programma toevoegen<br>Programma bewerken | Voeg een nieuw programma toe.<br>Een programma bewerken - Oplossingen of invoegtoepassingen toevoegen of verwijderen | x |  |  |  |
| Omgeving maken | Maak Prod+Stage, Dev, omgevingen. | x | x |  |  |
| Omgeving bijwerken | Prod+werkgebied, Dev, omgevingen bijwerken. | x | x |  |  |
| Omgeving verwijderen | Verwijder Niet-prod, Dev, omgevingen. | x | x |  |  |
| Instellingen pijpleiding | Setup of Edit Pipeline. |  | x |  |  |
| Uitvoering pijpleiding | Start de pijplijn. | x | x |  |  |
| Uitvoering pijpleiding | Belangrijke 3-Tier-fouten afwijzen/goedkeuren. | x | x | x |  |
| Uitvoering pijpleiding | Geef GoLive-goedkeuring op. | x | x | x |  |
| Uitvoering pijpleiding | Plan de Implementatie van de Productie. | x | x | x |  |
| Pipet verwijderen | Hiermee wordt het verwijderen van een pijpleiding toegestaan. |  | x |  |  |
| Uitvoering annuleren | Huidige uitvoering annuleren. |  | x |  |  |
| Token voor persoonlijke toegang genereren | Toegangspoort. |  | x |  | x |

