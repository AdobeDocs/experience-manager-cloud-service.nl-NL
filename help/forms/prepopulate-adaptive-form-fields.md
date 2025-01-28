---
title: Procedure voor het vooraf invullen van adaptieve formuliervelden
description: Bestaande gegevens gebruiken om velden van een adaptief formulier vooraf in te vullen. Gebruikers kunnen basisgegevens vooraf invullen in een formulier door zich aan te melden met hun sociale profielen.
topic-tags: develop
feature: Adaptive Forms, Foundation Components
exl-id: e2a87233-a0d5-48f0-b883-915fe56f105f
role: User, Developer
source-git-commit: b5340c23f0a2496f0528530bdd072871f0d70d62
workflow-type: tm+mt
source-wordcount: '2006'
ht-degree: 0%

---

# Aangepaste formuliervelden vooraf invullen{#prefill-adaptive-form-fields}

>[!NOTE]
>
> De Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/creating-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten.

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6,5 | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/prepopulate-adaptive-form-fields.html) |
| AEM as a Cloud Service | Dit artikel |

## Inleiding {#introduction}

U kunt de velden van een adaptief formulier vooraf invullen met bestaande gegevens. Wanneer een gebruiker een formulier opent, worden de waarden voor die velden vooraf ingevuld. Als u gegevens vooraf wilt invullen in een adaptief formulier, maakt u de gebruikersgegevens beschikbaar als een vooraf ingevulde XML/JSON in de indeling die voldoet aan de vooraf ingevulde gegevensstructuur van Adaptive Forms.

## Structuur van vooraf ingevulde gegevens {#the-prefill-structure}

Een adaptief formulier kan bestaan uit gebonden en niet-gebonden velden. Gebonden velden zijn velden die worden gesleept vanaf het tabblad Inhoudszoeker en die een niet-lege waarde voor de eigenschap `bindRef` bevatten in het dialoogvenster voor het bewerken van velden. Niet-gebonden velden worden rechtstreeks vanuit de deelbrowser van Sidekick gesleept en hebben een lege `bindRef` -waarde.

U kunt zowel gebonden als niet-gebonden velden van een adaptief formulier vooraf invullen. De vooraf ingevulde gegevens bevatten de secties afBoundData en afUnBoundData om zowel gebonden als niet-gebonden gebieden van een Adaptief Vorm vooraf in te vullen. De sectie `afBoundData` bevat de vooraf ingevulde gegevens voor gebonden velden en deelvensters. Deze gegevens moeten voldoen aan het bijbehorende formuliermodelschema:

- Voor Aanpassings Forms die het [ XFA vormmalplaatje ](#xfa-based-af) gebruiken, gebruik Prefill XML volgzaam met het gegevensschema van het malplaatje XFA.
- Voor Aanpassings Forms die [ schema van XML gebruiken ](#xml-schema-af), gebruik vooraf ingevulde XML volgzaam met de het schemastructuur van XML.
- Voor Adaptieve Forms die [ JSON schema ](#json-schema-based-adaptive-forms) gebruikt, gebruik Prefill JSON volgzaam met het schema JSON.
- Gebruik voor Adaptive Forms met FDM-schema de Prefill JSON die compatibel is met het FDM-schema.
- Voor Aanpassings Forms met [ geen vormmodel ](#adaptive-form-with-no-form-model), is er geen gebonden gegevens. Elk veld is een niet-gebonden veld en wordt voorgevuld met de niet-gebonden XML.

### Voorbeeld van vooraf ingevulde XML-structuur {#sample-prefill-xml-structure}

```xml
<?xml version="1.0" encoding="UTF-8"?>
<afData>
  <afBoundData>
     <employeeData>
        .
     </employeeData>
  </afBoundData>

  <afUnboundData>
    <data>
      <textbox>Hello World</textbox>
         .
         .
      <numericbox>12</numericbox>
         .
         .
    </data>
  </afUnboundData>
</afData>
```

### Voorbeeld van JSON-structuur vooraf invullen {#sample-prefill-json-structure}

```javascript
{
   "afBoundData": {
      "employeeData": { }
   },
   "afUnboundData": {
      "data": {
         "textbox": "Hello World",
         "numericbox": "12"
      }
   }
}
```

Voor gebonden velden met dezelfde bindref- of niet-gebonden velden met dezelfde naam worden de gegevens die zijn opgegeven in de XML-tag of het JSON-object, in alle velden ingevuld. Twee velden in een formulier worden bijvoorbeeld toegewezen aan de naam `textbox` in de vooraf ingevulde gegevens. Als tijdens runtime het eerste tekstvak A bevat, wordt A automatisch ingevuld in het tweede tekstvak. Deze koppeling wordt actieve koppeling van adaptieve formuliervelden genoemd.

### Adaptief formulier met XFA-formuliersjabloon {#xfa-based-af}

De structuur van vooraf ingevulde XML en de voorgelegde XML voor op XFA-Gebaseerde Adaptieve Forms is als volgt:

- **vooraf ingevulde de Structuur van XML**: Prefill XML voor op XFA-Gebaseerde Aangepaste Vorm moet met het gegevensschema van het XFA vormmalplaatje volgzaam zijn. Als u niet-gebonden velden vooraf wilt invullen, plaatst u de vooraf ingevulde XML-structuur in de tag `/afData/afBoundData` .

- **Voorgelegde Structuur van XML**: Wanneer geen vooraf ingevulde XML wordt gebruikt, bevat voorgelegde XML gegevens voor zowel verbindende als ongebonden gebieden in `afData` omslag markering. Als een vooraf ingevulde XML wordt gebruikt, heeft het voorgelegde XML-bestand dezelfde structuur als de vooraf ingevulde XML. Als de vooraf ingevulde XML begint met de hoofdtag `afData` , heeft de uitvoer-XML ook dezelfde indeling. Als vooraf ingevulde XML niet `afData/afBoundData` omslag heeft en in plaats daarvan direct van de markering van de schemawortel zoals `employeeData` begint, begint voorgelegde XML ook met de `employeeData` markering.

Prefill-Submit-Data-ContentPackage.zip

[ krijgt Dossier ](assets/prefill-submit-data-contentpackage.zip)
Voorbeeld met vooraf ingevulde gegevens en verzonden gegevens

### Adaptieve Forms op basis van XML-schema&#39;s  {#xml-schema-af}

De structuur van vooraf ingevulde XML en verzonden XML voor Adaptive Forms op basis van het XML-schema is als volgt:

- **vooraf ingevulde structuur van XML**: Prefill XML moet volgzaam aan het bijbehorende Schema van XML zijn. Als u niet-gebonden velden vooraf wilt invullen, plaatst u de vooraf ingevulde XML-structuur in de tag /afData/afBoundData.
- **Voorgelegde structuur van XML**: als geen vooraf ingevulde XML wordt gebruikt, bevat voorgelegde XML gegevens voor zowel verbindende als ongebonden gebieden in `afData` omslag markering. Als de vooraf ingevulde XML wordt gebruikt, heeft het voorgelegde XML-bestand dezelfde structuur als de vooraf ingevulde XML. Als de vooraf ingevulde XML begint met de hoofdtag `afData` , heeft de uitvoer-XML dezelfde indeling. Als de vooraf ingevulde XML niet `afData/afBoundData` wrapper heeft en in plaats daarvan direct begint vanaf de hoofdtag van het schema, zoals `employeeData` , begint de verzonden XML ook met de tag `employeeData` .

```xml
<?xml version="1.0" encoding="utf-8" ?>
<xs:schema targetNamespace="https://adobe.com/sample.xsd"
            xmlns="https://adobe.com/sample.xsd"
            xmlns:xs="https://www.w3.org/2001/XMLSchema">

    <xs:element name="sample" type="SampleType"/>

    <xs:complexType name="SampleType">
        <xs:sequence>
            <xs:element name="noOfProjectsAssigned" type="xs:string"/>
        </xs:sequence>
    </xs:complexType>
</xs:schema>
```

Voor velden waarvan het model het XML-schema is, worden de gegevens vooraf ingevuld in de tag `afBoundData` , zoals in het voorbeeld-XML hieronder wordt getoond. Deze kan worden gebruikt voor het vooraf invullen van een adaptief formulier met een of meer niet-gebonden tekstvelden.

```xml
<?xml version="1.0" encoding="UTF-8"?><afData>
  <afUnboundData>
    <data>
      <textbox>Ignorance is bliss :) </textbox>
    </data>
  </afUnboundData>
  <afBoundData>
    <data>
      <noOfProjectsAssigned>twelve</noOfProjectsAssigned>
    </data>
  </afBoundData>
</afData>
```

>[!NOTE]
>
>Het wordt aanbevolen geen niet-gebonden velden te gebruiken in gebonden deelvensters (deelvensters met niet-lege `bindRef` die zijn gemaakt door componenten te slepen van het tabblad Sidekick of Gegevensbronnen). Hierdoor kunnen gegevens van deze niet-gebonden velden verloren gaan. Daarnaast wordt aanbevolen dat de namen van de velden uniek zijn in het formulier, met name voor niet-gebonden velden.

#### Een voorbeeld zonder de omslag afData en afBoundData {#an-example-without-afdata-and-afbounddata-wrapper}

```xml
<?xml version="1.0" encoding="UTF-8"?><config>
 <assignmentDetails descriptionOfAssignment="Some Science Project" durationOfAssignment="34" financeRelatedProject="1" name="Lisa" numberOfMentees="1"/>
 <assignmentDetails descriptionOfAssignment="Kidding, right?" durationOfAssignment="4" financeRelatedProject="1" name="House" numberOfMentees="3"/>
</config>
```

### Adaptieve Forms op basis van JSON-schema {#json-schema-based-adaptive-forms}

Voor Adaptive Forms op basis van JSON-schema wordt de structuur van de prefill JSON en de ingediende JSON hieronder beschreven. Voor meer informatie, zie [ Creërend Adaptieve Forms gebruikend schema JSON ](adaptive-form-json-schema-form-model.md).

- **vooraf ingevulde JSON structuur**: Prefill JSON moet met het bijbehorende Schema JSON volgzaam zijn. Naar keuze, kan het in het /afData/afBoundData Voorwerp worden verpakt als u niet verbindende gebieden eveneens wilt vooraf invullen.
- **voorgelegde JSON structuur**: als geen prefill JSON wordt gebruikt, bevat voorgelegde JSON gegevens voor zowel gebonden als niet gebonden gebieden in afData omslagmarkering. Als de Prefill JSON wordt gebruikt, heeft de verzonden JSON dezelfde structuur als de Prefill JSON. Als de Prefill JSON begint met het afData-hoofdobject, heeft de uitvoer-JSON dezelfde indeling. Als de prefill JSON geen afData/afBoundData omslag heeft en in plaats daarvan direct van het schemawortelvoorwerp zoals gebruiker begint, begint voorgelegde JSON ook met het gebruikersvoorwerp.

```json
{
  "id": "https://some.site.somewhere/entry-schema#",
  "$schema": "https://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "address": {
      "type": "object",
      "properties": {
        "name": {
          "type": "string"
        },
        "age": {
          "type": "integer"
        }
      }
    }
  }
}
```

Voor velden die het JSON-schemamodel gebruiken, worden de gegevens voorgevuld in het afBoundData-object, zoals in het voorbeeld JSON hieronder wordt getoond. Deze kan worden gebruikt voor het vooraf invullen van een adaptief formulier met een of meer niet-gebonden tekstvelden. Hieronder ziet u een voorbeeld van gegevens met `afData/afBoundData` wrapper:

```json
{
  "afData": {
    "afUnboundData": {
      "data": { "textbox": "Ignorance is bliss :) " }
    },
    "afBoundData": {
      "data": { {
   "user": {
    "address": {
     "city": "Noida",
     "country": "India"
}}}}}}}
```

Hieronder ziet u een voorbeeld zonder `afData/afBoundData` wrapper:

```json
{
  "user": {
    "address": {
      "city": "Noida",
      "country": "India"
    }
  }
}
```

>[!NOTE]
>
> Het gebruiken van ongebonden gebieden in verbindende panelen (panelen met niet-lege bindRef die door componenten van de Sidekick of het lusje van Gegevensbronnen te slepen zijn gecreeerd) wordt **niet** geadviseerd aangezien het verlies van gegevens van de ongebonden gebieden zou kunnen veroorzaken. Het wordt aanbevolen unieke veldnamen te hebben in het formulier, vooral voor niet-gebonden velden.
>

### Adaptief formulier zonder formuliermodel {#adaptive-form-with-no-form-model}

Voor Adaptive Forms zonder formuliermodel staan de gegevens voor alle velden onder de `<data>` -tag van `<afUnboundData> tag` .

Let ook op het volgende:

De XML-labels voor de gebruikersgegevens die voor verschillende velden worden verzonden, worden gegenereerd met de naam van de velden. De veldnamen moeten daarom uniek zijn.

```xml
<?xml version="1.0" encoding="UTF-8"?><afData>
  <afUnboundData>
    <data>
      <radiobutton>2</radiobutton>
      <repeatable_panel_no_form_model>
        <numericbox>12</numericbox>
      </repeatable_panel_no_form_model>
      <repeatable_panel_no_form_model>
        <numericbox>21</numericbox>
      </repeatable_panel_no_form_model>
      <checkbox>2</checkbox>
      <textbox>Nopes</textbox>
    </data>
  </afUnboundData>
  <afBoundData/>
</afData>
```

## Prefill-service configureren {#configuring-prefill-service-using-configuration-manager}

Gebruik het `alloweddataFileLocations` bezit van de **Standaard vooraf ingevulde configuratie van de Dienst** om de plaats van de gegevensdossiers of een regex (regelmatige uitdrukking) voor de de dossierplaatsen van Gegevens te plaatsen.

In het volgende JSON-bestand wordt een voorbeeld weergegeven:

```JSON
  {
  "alloweddataFileLocations": "`file:///C:/Users/public/Document/Prefill/.*`"
  }
```

Om waarden van een configuratie te plaatsen, [ produceer OSGi Configuraties gebruikend de AEM SDK ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart) en [ stel de configuratie ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) aan uw instantie van de Cloud Service op.

>[!NOTE]
>
> - Prefill wordt standaard toegestaan via crx-bestanden voor alle typen adaptieve Forms (XSD, XDP, JSON, FDM en geen gebaseerd formuliermodel). Vooraf invullen is alleen toegestaan met JSON- en XML-bestanden.
> - Het crx-protocol zorgt voor de beveiliging van vooraf ingevulde gegevens en is daarom standaard toegestaan. Prefilling via andere protocollen met behulp van generieke regex kan kwetsbaarheid veroorzaken. Geef in de configuratie een veilige URL-configuratie op om uw gegevens te beveiligen.

## Het merkwaardige geval van herhaalbare deelvensters {#the-curious-case-of-repeatable-panels}

Over het algemeen worden gebonden (formulierschema) en niet-gebonden velden geschreven in dezelfde adaptieve vorm, maar het volgende is een paar uitzonderingen voor het geval de gebonden velden herhaalbaar zijn:

- Niet-gebonden herhaalbare deelvensters worden niet ondersteund voor Adaptieve Forms met de XFA-formuliersjabloon, XSD, JSON-schema of FDM-schema.
- Gebruik geen niet-gebonden velden in gebonden herhaalbare deelvensters.

>[!NOTE]
>
> Als vuistregel geldt dat gebonden en niet-gebonden velden niet door elkaar mogen worden gebruikt als ze doorsnede hebben in gegevens die door de gebruiker in niet-gebonden velden worden ingevuld. Indien mogelijk, zou u het schema of het XFA vormmalplaatje moeten wijzigen en een ingang voor niet verbindende gebieden toevoegen, zodat het ook verbindend wordt en zijn gegevens zoals andere gebieden in voorgelegde gegevens beschikbaar zijn.

## Ondersteunde protocollen voor het vooraf invullen van gebruikersgegevens {#supported-protocols-for-prefilling-user-data}

Adaptive Forms kan worden voorgevuld met gebruikersgegevens in de Prefill-gegevensindeling via de volgende protocollen wanneer deze worden geconfigureerd met geldige regex:

### Het protocol crx:// {#the-crx-protocol}

```javascript
http
https://`servername`/content/forms/af/xml.html?wcmmode=disabled&dataRef=crx:///tmp/fd/af/myassets/sample.xml
```

Het opgegeven knooppunt moet een eigenschap met de naam `jcr:data` hebben en de gegevens bevatten.

### Het protocol file://  {#the-file-protocol-nbsp}

```javascript
https://`servername`/content/forms/af/someAF.html?wcmmode=disabled&dataRef=file:///C:/Users/form-user/Downloads/somesamplexml.xml
```

Het betreffende bestand moet zich op dezelfde server bevinden.

### Het protocol https:// {#the-http-protocol}

```javascript
https://`servername`/content/forms/af/xml.html?wcmmode=disabled&dataRef=https://servername/somesamplexmlfile.xml
```

### Het protocol service:// {#the-service-protocol}

```javascript
https://`servername`/content/forms/af/abc.html?wcmmode=disabled&dataRef=service://[SERVICE_NAME]/[IDENTIFIER]
```

- SERVICE_NAME verwijst naar de naam van de prefill dienst OSGI. Zie [ creeer en stel een prefill dienst ](prepopulate-adaptive-form-fields.md#create-and-run-a-prefill-service) in werking.
- IDENTIFIER verwijst naar om het even welke meta-gegevens die door de Prefill dienst worden vereist OSGI om de Prefill gegevens te halen. Een id voor de aangemelde gebruiker is een voorbeeld van metagegevens die kunnen worden gebruikt.

>[!NOTE]
>
> Het doorgeven van verificatieparameters wordt niet ondersteund.

### Gegevenskenmerk instellen in slingRequest {#setting-data-attribute-in-slingrequest}

U kunt het kenmerk `data` ook instellen in `slingRequest` , waarbij het kenmerk `data` een tekenreeks is die XML of JSON bevat, zoals in de voorbeeldcode hieronder wordt getoond (Voorbeeld is voor XML):

```javascript
<%
           String dataXML="<afData>" +
                            "<afUnboundData>" +
                                "<data>" +
                                    "<first_name>"+ "Tyler" + "</first_name>" +
                                    "<last_name>"+ "Durden " + "</last_name>" +
                                    "<gender>"+ "Male" + "</gender>" +
                                    "<location>"+ "Texas" + "</location>" +
                                    "</data>" +
                            "</afUnboundData>" +
                        "</afData>";
        slingRequest.setAttribute("data", dataXML);
%>
```

U kunt een eenvoudige XML- of JSON-tekenreeks met al uw gegevens schrijven en deze in slingRequest instellen. Dit kan gemakkelijk in uw renderer JSP voor om het even welke component worden gedaan, die u in de pagina wilt omvatten waar u het slingRequest gegevensattribuut kunt plaatsen.

Bijvoorbeeld, waar u een specifiek ontwerp voor uw pagina met een specifiek type van kopbal wilt. Hiervoor kunt u uw eigen `header.jsp` schrijven, dat u kunt opnemen in uw paginacomponent en het kenmerk `data` instellen.

Een ander goed voorbeeld is een gebruiksgeval waarin u gegevens over aanmelding via sociale accounts, zoals Facebook, Twitter of LinkedIn, vooraf wilt invullen. In dit geval kunt u een eenvoudige JSP in `header.jsp` opnemen, die gegevens van de gebruikersrekening haalt en de gegevensparameter plaatst.

prefill-page component.zip

[ krijgt Dossier ](assets/prefill-page-component.zip)
Voorbeeld prefill.jsp in paginacomponent

## [!DNL AEM Forms] aangepaste Prefill-service {#aem-forms-custom-prefill-service}

U kunt de douane vooraf ingevulde dienst voor de scenario&#39;s gebruiken, waar u constant gegevens van een vooraf bepaalde bron leest. De Prefill-service leest gegevens uit gedefinieerde gegevensbronnen en vult de velden van het Adaptief formulier vooraf in met de inhoud van het Prefill-gegevensbestand. Hiermee kunt u ook vooraf ingevulde gegevens permanent koppelen aan een adaptief formulier.

### Een vooraf ingevulde service maken en uitvoeren {#create-and-run-a-prefill-service}

De prefill dienst is de dienst OSGi en door bundel OSGi verpakt. U maakt de OSGi-bundel, uploadt deze en installeert deze naar [!DNL AEM Forms] -bundels. Voordat u begint met het maken van de bundel:

- [ Download de  [!DNL AEM Forms]  Cliënt SDK ](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html)
- Het tekstbouwsteenpakket downloaden

- Plaats het gegevensbestand (vooraf ingevulde gegevens) in crx-bewaarplaats. U kunt het bestand op elke locatie in de map \contents van de crx-opslagplaats plaatsen.

[Bestand ophalen](assets/prefill-sumbit-xmlsandcontentpackage.zip)

#### Een vooraf ingevulde service maken {#create-a-prefill-service}

Het pakket boilerplate (voorbeeldservicepakket voor vooraf ingevulde bestanden) bevat een voorbeeldimplementatie van de [!DNL AEM Forms] Prefill-service. Open het tekstbouwsteenpakket in een code-editor. Open bijvoorbeeld het bouwsteenproject in Eclipse en bewerk het. Nadat u het bouwsteenpakket in een coderedacteur opent, voer de volgende stappen uit om de dienst tot stand te brengen.

1. Open het bestand src\main\java\com\adobe\test\Prefill.java voor bewerking.
1. Stel in de code de waarde in van:

   - `nodePath:` De knooppuntvariabele die naar de crx-gegevensopslaglocatie wijst, bevat een pad van het gegevensbestand (prefill). Bijvoorbeeld /content/prefilldata.xml
   - `label:` Met de parameter label wordt de weergavenaam van de service opgegeven. Bijvoorbeeld, de StandaardVooraf ingevulde Dienst

1. Sla het `Prefill.java` -bestand op en sluit het.
1. Voeg het pakket `AEM Forms Client SDK` toe aan de bouwstijlweg van het bouwsteenproject.
1. Compileer het project en creeer .jar voor de bundel.

#### De Prefill-service starten en gebruiken {#start-and-use-the-prefill-service}

Als u de Prefill-service wilt starten, uploadt u het JAR-bestand naar de [!DNL AEM Forms] webconsole en activeert u de service. De service verschijnt nu in de Adaptive Forms Editor. Een vooraf ingevulde service koppelen aan een adaptief formulier:

1. Open het Adaptief formulier in de Forms Editor en open het deelvenster Eigenschappen voor de Formuliercontainer.
1. Navigeer in de eigenschappenconsole naar [!DNL AEM Forms] container > Basic > Prefill Service.
1. Selecteer de standaardvoorgevulde service en klik op **[!UICONTROL Save]** . De service is gekoppeld aan het formulier.

<!-- ## Prepopulate data at client {#prefill-at-client}

When you prefill an Adaptive Form, the [!DNL AEM Forms] server merges data with an Adaptive Form and delivers the filled form to you. By default, the data merge action takes place at the server.

You can configure the [!DNL AEM Forms] server to perform the data merge action at the client instead of the server. It significantly reduces the time required to prefill and render Adaptive Forms. By default, the feature is disabled. You can enable it from the Configuration Manager or command line.

* To enable or disable from configuration manager:
  1. Open AEM Configuration Manager.
  1. Locate and open the Adaptive Form and Interactive Communication Web Channel Configuration
  1. Enable the Configuration.af.clientside.datamerge.enabled.name option
* To enable or disable from the command line:
  * To enable, run the following cURL command:
    `curl -u admin:admin -X POST -d apply=true \ -d propertylist=af.clientside.datamerge.enabled \ -d af.clientside.datamerge.enabled=true \ http://${crx.host}:${crx.port}/system/console/configMgr/Adaptive%20Form%20and%20Interactive%20Communication%20Web%20Channel%20Configuration`

  * To disable, run the following cURL command:
    `curl -u admin:admin -X POST -d apply=true \ -d propertylist=af.clientside.datamerge.enabled \ -d af.clientside.datamerge.enabled=false \ http://${crx.host}:${crx.port}/system/console/configMgr/Adaptive%20Form%20and%20Interactive%20Communication%20Web%20Channel%20Configuration`

   To take full advantage of the prepopulate data at client option, update your prefill service to return [FileAttachmentMap](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/forms/common/service/PrefillData.html) and [CustomContext](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/forms/common/service/PrefillData.html) -->