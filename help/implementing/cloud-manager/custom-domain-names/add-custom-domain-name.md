---
title: Een aangepaste domeinnaam toevoegen
description: Leer hoe u een aangepaste domeinnaam kunt toevoegen met behulp van Domeininstellingen in Cloud Manager.
exl-id: 0fc427b9-560f-4f6e-ac57-32cdf09ec623
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 215f4630acb3eca4be501c7c5f5de7c60b550bf8
workflow-type: tm+mt
source-wordcount: '1089'
ht-degree: 0%

---


# Een aangepaste domeinnaam toevoegen {#adding-custom-domain-name}

Leer hoe te om een naam van het douanedomein toe te voegen gebruikend **Montages van het Domein** in Cloud Manager.

## Vereisten {#requirements}

Voldoe aan deze vereisten voordat u een aangepaste domeinnaam in Cloud Manager toevoegt.

* U moet een domeinSSL certificaat voor het domein hebben toegevoegd u *wilt toevoegen alvorens* een naam van het douanedomein zoals die in het document [&#x200B; wordt beschreven een SSL certificaat &#x200B;](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md) toevoegt.
* U moet de **BedrijfsEigenaar** of **rol van de Manager van de Plaatsing** hebben om een naam van het douanedomein in Cloud Manager toe te voegen.
* Gebruik de sneltoets of een andere CDN (Content Delivery Network).

>[!IMPORTANT]
>
>Als u een door Adobe beheerde CDN gebruikt, moet u nog steeds uw domein aan Cloud Manager toevoegen.

## Waar kunt u aangepaste domeinnamen toevoegen {#where-to-add-custom-domain-name}

U kunt een naam van het douanedomein van de [&#x200B; pagina van de Montages van het Domein &#x200B;](#adding-cdn-settings) in Cloud Manager toevoegen.

Wanneer u een aangepaste domeinnaam toevoegt, wordt het domein gediend met het meest specifieke, geldige certificaat. Als meerdere certificaten hetzelfde domein hebben, wordt de meest recente bijgewerkte versie gekozen. Adobe raadt u aan certificaten zodanig te beheren dat er geen overlappende domeinen zijn.

De stappen voor beide methoden die in dit document worden beschreven, zijn gebaseerd op Snelheid. Als u een verschillende CDN (het Netwerk van de Levering van de Inhoud) gebruikte, vorm uw domein met CDN u om hebt gekozen te gebruiken.

## Een aangepaste domeinnaam toevoegen {#adding-custom-domain-name-settings}

1. Logboek in Cloud Manager bij [&#x200B; my.cloudmanager.adobe.com &#x200B;](https://my.cloudmanager.adobe.com/) en selecteer de aangewezen organisatie.

1. Op de **[Mijn console van Programma&#39;s](/help/implementing/cloud-manager/navigation.md#my-programs)**, selecteer het programma.

1. In het zijmenu, onder **Diensten**, klik ![&#x200B; het pictogram van Montages &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Settings_18_N.svg) **Montages van het Domein**.

   ![&#x200B; het venster van de Montages van het Domein &#x200B;](/help/implementing/cloud-manager/assets/cdn/cdn-create.png)

1. Vlak de hoger-juiste hoek van de **pagina van de Montages van het Domein**, klik **voegt Domein** toe.

1. In **voeg domein** dialoogdoos toe, op het **gebied van de Naam van het Domein**, ga de naam van het douanedomein in u gebruikt.
Neem bij het invoeren van de domeinnaam geen `http://` , `https://` of spaties op.

   >[!NOTE]
   >
   >Als u zowel `www` als `non-www` versies van een domein nodig hebt, moet u ze afzonderlijk toevoegen. Bijvoorbeeld `example.com` en `www.example.com` .
   <!-- Marius Petria on SLACK tmp-skyline-cdn-certificates - Actually  my opinion is that this option should be explicit in UI (that was present in the initial mocks of the design but for some reason it was dropped). I think when adding a domain there should be a check mark to also add www.domain. When adding example.com Customer should be prompted with the following options: Do you also want to add www.example.com and have a redirect example.com -> www.example.com?Do you also want to add www.example.com and have a redirect www.example.com -> example.com? -->

1. Klik **creëren**.

1. In **verifieer domein** dialoogdoos, in **welk certificaattype u op het gebruiken van dit domein van plan bent?** selecteert u een van de volgende opties in de vervolgkeuzelijst:

   | Certificaattype, optie | Beschrijving |
   | --- | --- |
   | Adobe managed (DV) SSL-certificaat | Selecteer dit certificaattype als u een DV-certificaat (Domain Validation) wilt gebruiken. Deze optie is ideaal voor de meeste gevallen, die basisdomeinbevestiging verstrekken. Adobe beheert en vernieuwt het certificaat automatisch. |
   | Door de klant beheerd SSL-certificaat (OV/EV) | Selecteer dit certificaattype als u een EV/OV SSL-certificaat wilt gebruiken om het domein te beveiligen. Deze optie biedt uitgebreide beveiliging met OV (Organisation Validation) of EV (Extended Validation). Gebruik deze optie als u strengere controles, hogere vertrouwensniveaus of aangepaste controle over de certificaten nodig hebt. |

1. In **verifieer domein** dialoogdoos, die op het certificaattype wordt gebaseerd u selecteerde, doe één van het volgende:

   | Als u het certificaattype hebt geselecteerd | Beschrijving |
   | --- | ---  |
   | Door Adobe beheerd certificaat | a. Voltooi de [&#x200B; Adobe beheerde certificaatstappen &#x200B;](#adobe-managed-cert-steps) hieronder. Wanneer u de stappen voltooit, in **verifieer domein** dialoogdoos, **verifieert**.<ul><li>DNS de controle kan een paar uren aan proces wegens DNS propagatievertragingen vergen.</li><li>Cloud Manager verifieert uiteindelijk het bezit van de domeinnaam en werkt de status in de **lijst van de Montages van het Domein** bij. Zie [&#x200B; de status van de naam van het douanedomein van de Controle &#x200B;](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer details.</li>![&#x200B; verifieer domeinstatus &#x200B;](/help/implementing/cloud-manager/assets/domain-settings-verified.png)</li></ul>b. U bent nu klaar om [&#x200B; een Adobe geleid (DV) SSL certificaat &#x200B;](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#add-adobe-managed-ssl-cert) toe te voegen.</li></ul> |
   | Door de klant beheerd certificaat | a. Klik **OK**.<br> b. U bent nu klaar om [&#x200B; een klant beheerde (OV/EV) SSL certificaat &#x200B;](/help/implementing/cloud-manager/managing-ssl-certifications/add-ssl-certificate.md#add-customer-managed-ssl-cert) toe te voegen.<br> nadat u het certificaat toevoegt, wordt uw domeinnaam duidelijk zoals geverifieerd in de **2&rbrace; lijst van de Montages van het Domein &lbrace;.** Zie [&#x200B; de status van de naam van het douanedomein van de Controle &#x200B;](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) voor meer details.</li></ul><br>![&#x200B; verifieer domein voor een klant beheerd EV/OV- certificaat &#x200B;](/help/implementing/cloud-manager/assets/verify-domain-customer-managed-step.png) |

   >[!NOTE]
   >
   >Als u uw eigen door de klant beheerde SSL-certificaat (OV/EV of DV) gebruikt, hoeft u geen SSL-certificaat toe te voegen. Deze regel is ook van toepassing als u van plan bent om een klant-geleide CDN (het Netwerk van de Levering van de Inhoud) ***leverancier*** te gebruiken. In plaats daarvan, ga direct naar [&#x200B; een Afbeelding van het Domein &#x200B;](/help/implementing/cloud-manager/domain-mappings/add-domain-mapping.md) wanneer klaar toevoegen.


### Door Adobe beheerde certificaatstappen {#adobe-managed-cert-steps}

Als u het certificaattype *Adobe beheerde certificaat* selecteerde, voltooi de volgende stap in **verifieer domein** dialoogdoos.

![&#x200B; Adobe beheerde certificaatstappen &#x200B;](/help/implementing/cloud-manager/assets/cdn/cdn-create-adobe-dv-cert.png)

Om het domein in gebruik te verifiëren, moet u een NAAM toevoegen en verifiëren.

Een `CNAME` recordtype of een `A` recordtype leidt, zodra provisioned, al verkeer van Internet voor het domein aan waar het richt. Als die plaats niet provisioned is om het verkeer te dienen, is er een stroomonderbreking. Als het niet is getest, kunnen er fouten in de inhoud optreden. Daarom wordt deze stap altijd uitgevoerd nadat het testen is voltooid en u klaar bent om live te gaan.

Als u deze instellingen wilt configureren, moet u bepalen of een `CNAME` - of apex-record moet zijn geconfigureerd om uw aangepaste domeinnaam te laten verwijzen naar de Cloud Manager-domeinnaam. De volgende secties van dit document kunnen u helpen bepalen welk type van verslag voor uw DNS configuratie aangewezen is.

>[!NOTE]
>
>Voor door Adobe beheerde CDN&#39;s zijn bij het gebruik van DV-certificaten (Domain Validation) alleen sites met ACME-validatie toegestaan.


## DNS configureren{#config-dns}

>[!WARNING]
>
>Het principe &quot;register voor advertenties&quot; is hier van toepassing. Namelijk vorm DNS slechts *zou moeten worden uitgevoerd nadat* u de domeinafbeelding met succes hebt toegevoegd. Dit zorgt ervoor dat Cloud Manager herkent en valideert dat het domein in zijn eigen configuratie bestaat alvorens het op verzoeken om het kan antwoorden. Ook worden pogingen tot het overnemen van domeinen voorkomen.

Ben zeker u aan de volgende vereisten *voldoet alvorens* u uw DNS verslagen vormt:

* Identificeer uw domeingastheer of registrar als u het nog niet kent.
* U kunt de DNS-records voor het domein van uw organisatie bewerken of contact opnemen met de juiste persoon die dat kan.
* U hebt reeds uw gevormde naam van het douanedomein zoals die in het document [&#x200B; wordt beschreven Controlerend de Status van de Naam van het Domein &#x200B;](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) geverifieerd.

### CNAME-record {#adobe-managed-cert-cname-record}

Een canonieke naam of CNAME-record is een type DNS-record dat een aliasnaam toewijst aan een echte of canonieke domeinnaam. CNAME-records worden doorgaans gebruikt om een subdomein, zoals `www.example.com` , toe te wijzen aan het domein dat de inhoud van dat subdomein host.

Meld u aan bij het DNS-servicebureau en maak een `CNAME` -record om de aangepaste domeinnaam naar het doel te verwijzen, bijvoorbeeld in de volgende tabel.

| CNAME | Aangepast hoofdmappunt voor doel |
| --- | --- |
| `www.customdomain.com` | `cdn.adobeaemcloud.com` |

### APEX-record {#adobe-managed-cert-apex-record}

Een apex-domein is een aangepast domein dat geen subdomein bevat, zoals `example.com` . Een ex-domein wordt geconfigureerd met een `A` -, `ALIAS` - of `ANAME` -record via uw DNS-provider. Apex-domeinen moeten verwijzen naar specifieke IP-adressen.

Voeg de volgende `A` verslagen aan DNS montages van uw domein als uw domeinleverancier toe.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`

>[!TIP]
>
>Het *verslag van de NAAM* of *het verslag van A* kan op de regerende DNS server worden geplaatst om u tijd te bewaren.

<!--
![Customer managed certificate steps](/help/implementing/cloud-manager/assets/cdn/cdn-create-customer-cert.png)

To verify the domain in use, you are required to add and verify a TXT record.

A text record (also known as a TXT record) is a type of resource record in the Domain Name System (DNS). It lets you associate arbitrary text with a hostname. This text could include human-readable details like server or network information.

Cloud Manager uses a specific TXT record to authorize a domain to be hosted in a CDN service. Create a DNS TXT record in the zone that authorizes Cloud Manager to deploy the CDN service with the custom domain and associate it with the backend service. This association is entirely under your control and authorizes Cloud Manager to serve content from the service to a domain. This authorization may be granted and withdrawn. The TXT record is specific to the domain and the Cloud Manager environment.

#### Requirements {#customer-managed-cert-requirements}

Fulfill these requirements before adding a TXT record.

* Identify your domain host or registrar if you do not know it already.
* Be able to edit the DNS records for your organization's domain, or contact the appropriate person who can.
* First, add a custom domain name as described earlier in this article.

#### Add a TXT record for verification {#customer-managed-cert-verification}

1. In the **Verify domain** dialog box, Cloud Manager displays the name and TXT value to use for verification. Copy this value.

1. Log in to your DNS service provider and find the DNS records section. 

1. Add `aemverification.[yourdomainname]` as the **Name** of the value and add the TXT value exactly as it appears in the **Domain Name** field.

   **TXT record examples**

   | Domain | Name | TXT Value |
   | --- | --- | --- |
   | `example.com` | `_aemverification.example.com` | Copy the entire value displayed in the Cloud Manager UI. This value is specific to the domain and the environment. For example:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
   | `www.example.com` | `_aemverification.www.example.com` | Copy the entire value displayed in the Cloud Manager UI. This value is specific to the domain and the environment. For example:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

1. Save the TXT record to your domain host.

#### Verify TXT record {#customer-managed-cert-verify}

When you are done, you can verify the result by running the following command.

```shell
dig _aemverification.[yourdomainname] -t txt
```

The expected result should display the TXT value provided on the **Verification** tab of the **Add Domain Name** dialog of the Cloud Manager UI.

For example, if your domain is `example.com`, then run:

```shell
dig TXT _aemverification.example.com -t txt
```


>[!TIP]
>
>There are several [DNS lookup tools](https://www.ultratools.com/tools/dnsLookup) available. Google DoH can be used to look up TXT record entries and identify if the TXT record is missing or erroneous.

-->



<!--
## Next Steps {#next-steps}

Now that you created your TXT entry, you can verify your domain name status. Proceed to the document [Checking Domain Name Status](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) to continue setting up your custom domain name. -->


><!-- The TXT entry and the CNAME or A Record can be set simultaneously on the governing DNS server, thus saving time. -->
>
><!-- To do this, review the entire process of setting up a custom domain name as detailed in the document [Introduction to custom domain names](/help/implementing/cloud-manager/custom-domain-names/introduction.md) taking special note of the document [help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) and update your DNS settings appropriately. -->


