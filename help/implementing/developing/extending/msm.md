---
title: Het beheer van meerdere sites uitbreiden
description: Leer hoe u de functionaliteit van beheer voor meerdere sites uitbreidt.
exl-id: 4b7a23c3-65d1-4784-9dea-32fcceca37d1
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: tm+mt
source-wordcount: '2337'
ht-degree: 0%

---

# Het beheer van meerdere sites uitbreiden {#extending-the-multi-site-manager}

Dit document helpt u begrijpen hoe te om de functionaliteit van de Multisite Manager uit te breiden en behandelt de volgende onderwerpen.

* Meer informatie over de belangrijkste leden van de MSM Java API
* Creeer een nieuwe synchronisatieactie die in een rollout configuratie kan worden gebruikt
* De standaardtaal en -landcodes wijzigen

>[!TIP]
>
>Deze pagina is eenvoudiger te begrijpen in de context van het document [Inhoud opnieuw gebruiken: beheer voor meerdere sites.](/help/sites-cloud/administering/msm/overview.md)

>[!CAUTION]
>
>De beheer van meerdere sites en de bijbehorende API worden gebruikt bij het ontwerpen van een website en zijn daarom alleen bedoeld voor gebruik in een auteursomgeving.

## Overzicht van de Java API {#overview-of-the-java-api}

Beheer van meerdere sites bestaat uit de volgende pakketten:

* [com.day.cq.wcm.msm.api](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/package-frame.html)
* [com.day.cq.wcm.msm.commons](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/commons/package-frame.html)

De belangrijkste MSM API-objecten werken als volgt (zie ook de sectie [Gebruikte termen](/help/sites-cloud/administering/msm/overview.md#terms-used)):

![Belangrijkste MSM API-objecten](assets/msm-api-interaction.png)

* **`Blueprint`** - A `Blueprint` (zoals in [blauwdrukconfiguratie](/help/sites-cloud/administering/msm/overview.md#source-blueprints-and-blueprint-configurations)) geeft de pagina&#39;s aan waarvan een live kopie inhoud kan overnemen.

  ![Blauwdruk](assets/msm-blueprint-interaction.png)

   * Het gebruik van een blauwdrukconfiguratie ( `Blueprint`) is optioneel, maar:

      * Hiermee kan de auteur de opdracht **Uitrol** optie op de bron om uitdrukkelijk wijzigingen in levende exemplaren te duwen die van deze bron erven.
      * Hiermee kan de auteur **Site maken**, waarmee de gebruiker eenvoudig talen kan selecteren en de structuur van de live kopie kan configureren.
      * Het bepaalt de standaardrollout configuratie voor om het even welke resulterende levende exemplaren.

* **`LiveRelationship`** - de `LiveRelationship` Hiermee geeft u de verbinding (relatie) op tussen een bron in de actieve kopieervertakking en de equivalente bron/blauwdrukbron.

   * De relaties worden gebruikt bij het realiseren van overerving en rollout.
   * `LiveRelationship` objecten bieden toegang (verwijzingen) tot de rollout-configuraties ( `RolloutConfig`), `LiveCopy`, en `LiveStatus` objecten die verband houden met de relatie.

   * Er wordt bijvoorbeeld een live kopie gemaakt in `/content/copy/us` van de bron/blauwdruk op `/content/wknd/language-masters`. De middelen `/content/wknd/language-masters/en/jcr:content` en `/content/copy/us/en/jcr:content` vormen een relatie.

* **`LiveCopy`** - A `LiveCopy` bevat de configuratiedetails voor de relaties (`LiveRelationship`) tussen de bronnen van de live kopie en de bron-/blauwdrukbronnen ervan.

   * Gebruik de `LiveCopy` klasse voor toegang tot het pad van de pagina, het pad van de bron-/blauwdrukpagina, de rollout-configuraties en of onderliggende pagina&#39;s ook in de `LiveCopy`.

   * A `LiveCopy` knooppunt wordt elke keer gemaakt **Site maken** of **Live kopie maken** wordt gebruikt.

* **`LiveStatus`** - `LiveStatus` objecten bieden toegang tot de runtimestatus van een `LiveRelationship`. Wordt gebruikt om de synchronisatiestatus van een live kopie te controleren.

* **`LiveAction`** - A `LiveAction` is een actie die op elk middel wordt uitgevoerd dat bij de rollout betrokken is.

   * `LiveAction`s alleen gegenereerd door `RolloutConfig`s.

* **`LiveActionFactory`** - A `LiveActionFactory` create `LiveAction` objecten die `LiveAction` configuratie. Configuraties worden opgeslagen als bronnen in de opslagplaats.

* **`RolloutConfig`** - de `RolloutConfig` bevat een lijst met `LiveActions`te gebruiken wanneer deze wordt geactiveerd. De `LiveCopy` erft de `RolloutConfig` en het resultaat is aanwezig in de `LiveRelationship`.

   * Als u voor het eerst een live kopie maakt, wordt ook een `RolloutConfig` (waardoor de `LiveAction`s).

## Nieuwe synchronisatiehandeling maken {#creating-a-new-synchronization-action}

U kunt aangepaste synchronisatiehandelingen maken voor gebruik met uw rollout-configuraties. Dit kan handig zijn als de [geïnstalleerde handelingen](/help/sites-cloud/administering/msm/live-copy-sync-config.md#installed-synchronization-actions) voldoet niet aan uw specifieke toepassingsvereisten.

Hiertoe maakt u twee klassen:

* De uitvoering van de [`com.day.cq.wcm.msm.api.LiveAction`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveAction.html) interface die de handeling uitvoert.
* Een component OSGi die uitvoert [`com.day.cq.wcm.msm.api.LiveActionFactory`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveActionFactory.html) en maakt instanties van uw `LiveAction` class

De `LiveActionFactory` maakt instanties van de `LiveAction` klasse voor een bepaalde configuratie:

* `LiveAction` klassen omvatten de volgende methoden:

   * `getName` - Retourneert de naam van de handeling

      * De naam wordt gebruikt om naar de actie, bijvoorbeeld, in rollout configuraties te verwijzen.

   * `execute` - Voert de taken van de actie uit

* `LiveActionFactory` de klassen omvatten de volgende leden:

   * `LIVE_ACTION_NAME` - Een veld dat de naam bevat van de bijbehorende `LiveAction`

      * Deze naam moet overeenkomen met de waarde die wordt geretourneerd door de `getName` van de `LiveAction` klasse.

   * `createAction` - Maakt een instantie van de `LiveAction`

      * De optionele `Resource` parameter kan worden gebruikt om configuratieinformatie te verstrekken.

   * `createsAction` - Retourneert de naam van de gekoppelde `LiveAction`

### De LiveAction Configuration-node openen {#accessing-the-liveaction-configuration-node}

Gebruik de `LiveAction` configuratieknooppunt in de opslagplaats om informatie op te slaan die het runtimegedrag van de `LiveAction` -instantie. Het knooppunt in de opslagplaats dat het `LiveAction` de configuratie is beschikbaar voor de `LiveActionFactory` object bij uitvoering. Daarom kunt u eigenschappen aan de configuratieknoop toevoegen en hen in uw gebruiken `LiveActionFactory` de uitvoering, indien nodig.

Bijvoorbeeld een `LiveAction` moet de naam van de auteur van de blauwdruk opslaan. Een bezit van de configuratieknoop omvat de bezitsnaam van de blauwdruk pagina die de informatie opslaat. Tijdens runtime wordt de `LiveAction` wint de bezitsnaam van de configuratie terug, dan verkrijgt de bezitswaarde.

De parameter van [`LiveActionFactory.createAction`](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/day/cq/wcm/msm/api/LiveActionFactory.html) methode is een `Resource` object. Dit `Resource` object staat voor `cq:LiveSyncAction` knoop voor deze levende actie in de rollout configuratie.

Zie [Een rollout-configuratie maken](/help/sites-cloud/administering/msm/live-copy-sync-config.md#creating-a-rollout-configuration) voor meer informatie .

Zoals gebruikelijk wanneer het gebruiken van een configuratieknoop, zou u het aan een moeten aanpassen `ValueMap` object:

```java
public LiveAction createAction(Resource resource) throws WCMException {
        ValueMap config;
        if (resource == null || resource.adaptTo(ValueMap.class) == null) {
            config = new ValueMapDecorator(Collections.<String, Object>emptyMap());
        } else {
            config = resource.adaptTo(ValueMap.class);
        }
        return new MyLiveAction(config, this);
}
```

### Toegang tot doelknooppunten, bronknooppunten en de LiveRelationship {#accessing-target-nodes-source-nodes-and-the-liverelationship}

De volgende objecten worden opgegeven als parameters van de `execute` van de `LiveAction` object:

* A [`Resource`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/Resource.html) object dat de bron van de actieve kopie vertegenwoordigt
* A `Resource` object dat het doel van de live kopie vertegenwoordigt.
* De [`LiveRelationship`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/wcm/msm/api/LiveRelationship.html) object voor de live kopie
   * De `autoSave` waarde geeft aan of uw `LiveAction` moeten wijzigingen opslaan die in de repository zijn aangebracht
   * De `reset` waarde geeft de terugzetmodus aan.

Via deze objecten kunt u informatie opvragen over de `LiveCopy`. U kunt ook de opdracht `Resource` te verkrijgen objecten `ResourceResolver`, `Session`, en `Node` objecten. Deze objecten zijn handig voor het bewerken van inhoud in opslagruimten:

In de eerste regel van de volgende code is de bron de `Resource` object van de bronpagina:

```java
ResourceResolver resolver = source.getResourceResolver();
Session session = resolver.adaptTo(javax.jcr.Session.class);
Node sourcenode = source.adaptTo(javax.jcr.Node.class);
```

>[!NOTE]
>
>De `Resource` argumenten kunnen `null` of `Resources` objecten die niet worden aangepast aan `Node` objecten, zoals [`NonExistingResource`](https://developer.adobe.com/experience-manager/reference-materials/cloud-service/javadoc/org/apache/sling/api/resource/NonExistingResource.html) objecten.

## Een nieuwe rollout-configuratie maken {#creating-a-new-rollout-configuration}

U kunt een rollout configuratie tot stand brengen wanneer de geïnstalleerde rollout configuraties niet aan uw toepassingsvereisten voldoen twee stappen volgen:

* [De rollout-configuratie maken](#create-the-rollout-configuration)
* [Synchronisatiehandelingen toevoegen aan de rollout-configuratie](#add-synchronization-actions-to-the-rollout-configuration)

De nieuwe rollout configuratie is dan beschikbaar aan u wanneer het plaatsen van rollout configuraties op een blauwdruk of een levende exemplaarpagina.

>[!TIP]
>
>Zie ook de [aanbevolen procedures voor het aanpassen van rollouts](/help/sites-cloud/administering/msm/best-practices.md#customizing-rollouts).

### De configuratie van de rollout maken {#create-the-rollout-configuration}

Een rollout-configuratie maken:

1. CRXDE Lite openen bij `https://<host>:<port>/crx/de`.

1. Navigeren naar `/apps/msm/<your-project>/rolloutconfigs`, de aangepaste versie van uw project van `/libs/msm/wcm/rolloutconfigs`.

   * Als dit uw eerste configuratie is, dit `/libs` vertakking moet worden gebruikt als een sjabloon om de nieuwe vertakking onder `/apps`.

1. Maak onder deze locatie een knooppunt met de volgende eigenschappen:

   * **Naam**: De knooppuntnaam van de rollout-configuratie, bijvoorbeeld `contentCopy` of `workflow`
   * **Type**: `cq:RolloutConfig`

1. Voeg de volgende eigenschappen toe aan dit knooppunt:

   * **Naam**: `jcr:title`
     **Type**: `String`
     **Waarde**: Een identificerende titel die in UI zal verschijnen

   * **Naam**: `jcr:description`
     **Type**: `String`
     **Waarde**: Een optionele beschrijving.

   * **Naam**: `cq:trigger`
     **Type**: `String`
     **Waarde**: De [Rollouttrigger](/help/sites-cloud/administering/msm/live-copy-sync-config.md#rollout-triggers) te gebruiken
      * `rollout`
      * `modification`
      * `publish`
      * `deactivate`

1. Klikken **Alles opslaan**.

### Synchronisatiehandelingen toevoegen aan de configuratie van de rollout {#add-synchronization-actions-to-the-rollout-configuration}

Rolloutconfiguraties worden opgeslagen onder de [rollout configuration node](#create-the-rollout-configuration) die u in het kader van de `/apps/msm/<your-project>/rolloutconfigs` knooppunt.

Onderliggende knooppunten van het type toevoegen `cq:LiveSyncAction` synchronisatiehandelingen toevoegen aan de rollout-configuratie. De volgorde van de actieknooppunten voor synchronisatie bepaalt de volgorde waarin de acties plaatsvinden.

1. Selecteer in CRXDE Lite de optie [Rolloutconfiguratie](#create-the-rollout-configuration) knooppunt, bijvoorbeeld `/apps/msm/myproject/rolloutconfigs/myrolloutconfig`.

1. Maak een knooppunt met de volgende knoopeigenschappen:

   * **Naam**: De knooppuntnaam van de synchronisatiehandeling
      * De naam moet gelijk zijn aan **Naam van handeling** in de onderstaande tabel [Synchronisatiehandelingen](/help/sites-cloud/administering/msm/live-copy-sync-config.md#installed-synchronization-actions) zoals `contentCopy` of `workflow`.
   * **Type**: `cq:LiveSyncAction`

1. Voeg en vorm zo vele knopen van de synchronisatieactie toe aangezien u vereist.

1. Wijzig de rangschikking van de actieknoppen zodat de volgorde overeenkomt met de volgorde waarin u deze wilt uitvoeren.
   * Het bovenste actieknooppunt komt eerst voor.

## Een eenvoudige LiveActionFactory-klasse maken en gebruiken {#creating-and-using-a-simple-liveactionfactory-class}

Volg de procedures in deze paragraaf om een `LiveActionFactory` en gebruik het in een rollout configuratie. De procedures gebruiken Maven en Eclipse om het `LiveActionFactory`:

1. [Maak het gemaakte project](#create-the-maven-project) en importeert u deze in Eclipse.
1. [Afhankelijkheden toevoegen](#add-dependencies-to-the-pom-file) naar het POM-bestand.
1. [Implementeer de `LiveActionFactory` interface](#implement-liveactionfactory) en zet de bundel OSGi op.
1. [De rollout-configuratie maken](#create-the-example-rollout-configuration).
1. [Live kopie maken](#create-the-live-copy).

[Het Maven-project en de broncode van de Java-klasse](https://github.com/Adobe-Marketing-Cloud/experiencemanager-java-msmrollout) is beschikbaar in de openbare Git-opslagplaats.

### Maven {#create-the-maven-project}

Voor de volgende procedure moet u de volgende `adobe-public` naar het bestand met Maven-instellingen.

* Voor informatie over het adobe-public profiel raadpleegt u [De insteekmodule voor het inhoudspakket verkrijgen](/help/implementing/developing/tools/maven-plugin.md#obtaining-the-content-package-maven-plugin)
* Zie Maven voor meer informatie over het instellingenbestand Maven [Instellingenverwijzing](https://maven.apache.org/settings.html).

1. Open een terminal- of opdrachtregelsessie en wijzig de directory om te wijzen naar de locatie waar u het project wilt maken.
1. Voer de volgende opdracht in:

   ```text
   mvn archetype:generate -DarchetypeGroupId=com.day.jcr.vault -DarchetypeArtifactId=multimodule-content-package-archetype -DarchetypeVersion=1.0.0 -DarchetypeRepository=adobe-public-releases
   ```

1. Geef de volgende waarden op bij interactieve prompt:

   * **`groupId`**: `com.adobe.example.msm`
   * **`artifactId`**: `MyLiveActionFactory`
   * **`version`**: `1.0-SNAPSHOT`
   * **`package`**: `MyPackage`
   * **`appsFolderName`**: `myapp`
   * **`artifactName`**: `MyLiveActionFactory package`
   * **`packageGroup`**: `myPackages`

1. Eclipse starten en [het Maven-project importeren.](/help/implementing/developing/tools/eclipse.md#import-the-maven-project-into-eclipse)

### Afhankelijkheden toevoegen aan het POM-bestand {#add-dependencies-to-the-pom-file}

Afhankelijkheden toevoegen zodat de compiler Eclipse naar de klassen kan verwijzen die in het dialoogvenster `LiveActionFactory` code.

1. Open het bestand vanuit de Eclipse Project Explorer `MyLiveActionFactory/pom.xml`.

1. Klik in de editor op de knop `pom.xml` en zoek de `project/dependencyManagement/dependencies` sectie.

1. Voeg de volgende XML toe binnen de `dependencyManagement` en sla het bestand op.

   ```xml
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-msm-api</artifactId>
     <version>5.6.2</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.api</artifactId>
     <version>2.4.3-R1488084</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-wcm-api</artifactId>
     <version>5.6.6</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.commons.json</artifactId>
     <version>2.0.6</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
     <version>5.6.4</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.jcr.jcr-wrapper</artifactId>
     <version>2.0.0</version>
     <scope>provided</scope>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
     <version>5.6.4</version>
     <scope>provided</scope>
    </dependency>
   ```

1. Open het POM-bestand voor de bundel vanuit **Project Explorer** om `MyLiveActionFactory-bundle/pom.xml`.

1. Klik in de editor op de knop `pom.xml` en zoek de sectie project/afhankelijkheden. Voeg de volgende XML binnen het gebiedsdeelelement toe en bewaar dan het dossier:

   ```xml
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-msm-api</artifactId>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.api</artifactId>
    </dependency>
    <dependency>
     <groupId>com.day.cq.wcm</groupId>
     <artifactId>cq-wcm-api</artifactId>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.commons.json</artifactId>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
    </dependency>
    <dependency>
     <groupId>org.apache.sling</groupId>
     <artifactId>org.apache.sling.jcr.jcr-wrapper</artifactId>
    </dependency>
    <dependency>
     <groupId>com.day.cq</groupId>
     <artifactId>cq-commons</artifactId>
    </dependency>
   ```

### LiveActionFactory implementeren {#implement-liveactionfactory}

Het volgende `LiveActionFactory` klasse implementeert een klasse `LiveAction` die berichten over de bron en doelpagina&#39;s registreert, en kopieert `cq:lastModifiedBy` eigenschap van het bronknooppunt naar het doelknooppunt. De naam van de live actie is `exampleLiveAction`.

1. In de Ontdekkingsreiziger van het Project van de Verduistering, klik met de rechtermuisknop aan `MyLiveActionFactory-bundle/src/main/java/com.adobe.example.msm` verpakken en klikken **Nieuw** > **Klasse**.

1. Voor de **Naam**, enter `ExampleLiveActionFactory` en klik vervolgens op **Voltooien**.

1. Open de `ExampleLiveActionFactory.java` , vervangt u de inhoud door de volgende code en slaat u het bestand op.

   ```java
   package com.adobe.example.msm;
   
   import java.util.Collections;
   
   import org.apache.felix.scr.annotations.Component;
   import org.apache.felix.scr.annotations.Property;
   import org.apache.felix.scr.annotations.Service;
   import org.apache.sling.api.resource.Resource;
   import org.apache.sling.api.resource.ResourceResolver;
   import org.apache.sling.api.resource.ValueMap;
   import org.apache.sling.api.wrappers.ValueMapDecorator;
   import org.apache.sling.commons.json.io.JSONWriter;
   import org.apache.sling.commons.json.JSONException;
   
   import org.slf4j.Logger;
   import org.slf4j.LoggerFactory;
   
   import javax.jcr.Node;
   import javax.jcr.RepositoryException;
   import javax.jcr.Session;
   
   import com.day.cq.wcm.msm.api.ActionConfig;
   import com.day.cq.wcm.msm.api.LiveAction;
   import com.day.cq.wcm.msm.api.LiveActionFactory;
   import com.day.cq.wcm.msm.api.LiveRelationship;
   import com.day.cq.wcm.api.WCMException;
   
   @Component(metatype = false)
   @Service
   public class ExampleLiveActionFactory implements LiveActionFactory<LiveAction> {
    @Property(value="exampleLiveAction")
    static final String actionname = LiveActionFactory.LIVE_ACTION_NAME;
   
    public LiveAction createAction(Resource config) {
     ValueMap configs;
     /* Adapt the config resource to a ValueMap */
           if (config == null || config.adaptTo(ValueMap.class) == null) {
               configs = new ValueMapDecorator(Collections.<String, Object>emptyMap());
           } else {
               configs = config.adaptTo(ValueMap.class);
           }
   
     return new ExampleLiveAction(actionname, configs);
    }
    public String createsAction() {
     return actionname;
    }
    /************* LiveAction ****************/
    private static class ExampleLiveAction implements LiveAction {
     private String name;
     private ValueMap configs;
     private static final Logger log = LoggerFactory.getLogger(ExampleLiveAction.class);
   
     public ExampleLiveAction(String nm, ValueMap config){
      name = nm;
      configs = config;
     }
   
     public void execute(Resource source, Resource target,
       LiveRelationship liverel, boolean autoSave, boolean isResetRollout)
         throws WCMException {
   
      String lastMod = null;
   
      log.info(" *** Executing ExampleLiveAction *** ");
   
      /* Determine if the LiveAction is configured to copy the cq:lastModifiedBy property */
      if ((Boolean) configs.get("repLastModBy")){
   
       /* get the source's cq:lastModifiedBy property */
       if (source != null && source.adaptTo(Node.class) !=  null){
        ValueMap sourcevm = source.adaptTo(ValueMap.class);
        lastMod = sourcevm.get(com.day.cq.wcm.msm.api.MSMNameConstants.PN_PAGE_LAST_MOD_BY, String.class);
       }
   
       /* set the target node's la-lastModifiedBy property */
       Session session = null;
       if (target != null && target.adaptTo(Node.class) !=  null){
        ResourceResolver resolver = target.getResourceResolver();
        session = resolver.adaptTo(javax.jcr.Session.class);
        Node targetNode;
        try{
         targetNode=target.adaptTo(javax.jcr.Node.class);
         targetNode.setProperty("la-lastModifiedBy", lastMod);
         log.info(" *** Target node lastModifiedBy property updated: {} ***",lastMod);
        }catch(Exception e){
         log.error(e.getMessage());
        }
       }
       if(autoSave){
        try {
         session.save();
        } catch (Exception e) {
         try {
          session.refresh(true);
         } catch (RepositoryException e1) {
          e1.printStackTrace();
         }
         e.printStackTrace();
        }
       }
      }
     }
     public String getName() {
      return name;
     }
   
     /************* Deprecated *************/
     @Deprecated
     public void execute(ResourceResolver arg0, LiveRelationship arg1,
       ActionConfig arg2, boolean arg3) throws WCMException {
     }
     @Deprecated
     public void execute(ResourceResolver arg0, LiveRelationship arg1,
       ActionConfig arg2, boolean arg3, boolean arg4)
         throws WCMException {
     }
     @Deprecated
     public String getParameterName() {
      return null;
     }
     @Deprecated
     public String[] getPropertiesNames() {
      return null;
     }
     @Deprecated
     public int getRank() {
      return 0;
     }
     @Deprecated
     public String getTitle() {
      return null;
     }
     @Deprecated
     public void write(JSONWriter arg0) throws JSONException {
     }
    }
   }
   ```

1. Wijzig met de terminal- of opdrachtsessie de directory in de `MyLiveActionFactory` directory (de Maven projectdirectory). Voer vervolgens de volgende opdracht in:

   ```shell
   mvn -PautoInstallPackage clean install
   ```

1. De AEM `error.log` bestand moet aangeven dat de bundel is gestart, zichtbaar in de logboeken op `https://<host>:<port>/system/console/status-slinglogs`.

   ```text
   13.08.2013 14:34:55.450 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent RESOLVED
   13.08.2013 14:34:55.451 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent STARTING
   13.08.2013 14:34:55.451 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle BundleEvent STARTED
   13.08.2013 14:34:55.453 *INFO* [OsgiInstallerImpl] com.adobe.example.msm.MyLiveActionFactory-bundle Service [com.adobe.example.msm.ExampleLiveActionFactory,2188] ServiceEvent REGISTERED
   13.08.2013 14:34:55.454 *INFO* [OsgiInstallerImpl] org.apache.sling.audit.osgi.installer Started bundle com.adobe.example.msm.MyLiveActionFactory-bundle [316]
   ```

### De voorbeeldconfiguratie voor rollout maken {#create-the-example-rollout-configuration}

Creeer de MSM rollout configuratie die gebruikt `LiveActionFactory` die u hebt gemaakt:

1. Een [De Configuratie van de uitrol met de standaardprocedure](/help/sites-cloud/administering/msm/live-copy-sync-config.md#creating-a-rollout-configuration) met de eigenschappen:

   * **Titel**: Voorbeeld van rollout Configuration
   * **Naam**: examplerolloutconfig
   * **cq:trigger**: `publish`

### Voeg de Actieve Actie aan de Configuratie van de Uitvoer van het Voorbeeld toe {#add-the-live-action-to-the-example-rollout-configuration}

Vorm de rollout configuratie die u in de vorige procedure creeerde zodat het gebruikt `ExampleLiveActionFactory` klasse.

1. Open CRXDE Lite.

1. De volgende node maken onder `/apps/msm/rolloutconfigs/examplerolloutconfig/jcr:content`:

   * **Naam**: `exampleLiveAction`
   * **Type**: `cq:LiveSyncAction`

1. Klikken **Alles opslaan**.

1. Selecteer de `exampleLiveAction` knooppunt en een eigenschap toevoegen die aan de `ExampleLiveAction` de klasse `cq:LastModifiedBy` eigenschap moet worden gerepliceerd van de bron naar het doelknooppunt.

   * **Naam**: `repLastModBy`
   * **Type**: `Boolean`
   * **Waarde**: `true`

1. Klikken **Alles opslaan**.

### Live kopie maken {#create-the-live-copy}

[Een live kopie maken](/help/sites-cloud/administering/msm/creating-live-copies.md#creating-a-live-copy-of-a-page) van de Engels/tak van Producten van de WKND verwijzingsplaats gebruikend uw rollout configuratie:

* **Bron**: `/content/wknd/language-masters/en/products`

* **Rolloutconfiguratie**: Voorbeeld van rollout Configuration

Activeer **Producten** (engels) pagina van de brontak en bekijk de logboekberichten die `LiveAction` klasse genereert:

```xml
16.08.2013 10:53:33.055 *INFO* [Thread-444535] com.adobe.example.msm.ExampleLiveActionFactory$ExampleLiveAction  ***ExampleLiveAction has been executed.***
16.08.2013 10:53:33.055 *INFO* [Thread-444535] com.adobe.example.msm.ExampleLiveActionFactory$ExampleLiveAction  ***Target node lastModifiedBy property updated: admin ***
```

## Taalnamen en standaardlanden wijzigen {#changing-language-names-and-default-countries}

AEM gebruikt een standaardset taal- en landcodes.

* De standaardtaalcode is de tweeletterige code in kleine letters, zoals gedefinieerd door ISO-639-1.
* De standaardlandcode is de tweelettercode in kleine letters of hoofdletters, zoals gedefinieerd in ISO 3166.

MSM gebruikt een opgeslagen lijst van taal en landcodes om de naam van het land te bepalen dat met de naam van de taalversie van uw pagina wordt geassocieerd. U kunt de volgende aspecten van de lijst indien nodig wijzigen:

* Taaltitels
* Landnamen
* Standaardlanden voor talen (voor codes zoals `en`, `de`, onder andere)

De taallijst wordt opgeslagen onder de `/libs/wcm/core/resources/languages` knooppunt. Elk onderliggend knooppunt vertegenwoordigt een taal of een taal-land:

* De naam van het knooppunt is de taalcode (zoals `en` of `de`), of de taal_landcode (zoals `en_us` of `de_ch`).

* De `language` bezit van de knoop slaat de volledige naam van de taal voor de code op.
* De `country` eigenschap of the node slaat de volledige naam van het land voor de code op.
* Wanneer de knooppuntnaam slechts uit een taalcode (zoals `en`), de landgoederen `*`en een aanvullende `defaultCountry` in de eigenschap wordt de code van het taalland opgeslagen om aan te geven welk land moet worden gebruikt.

![Taaldefinitie](assets/msm-language-manager.png)

De talen wijzigen:

1. Open CRXDE Lite.
1. Selecteer de `/apps` map en klik op **Maken** vervolgens **Map maken.**

1. Geef de nieuwe map een naam `wcm`.

1. Herhaal de vorige stap om de `/apps/wcm/core` mapstructuur. Een knooppunt van het type maken `sling:Folder` in `core` gebeld `resources`.

1. Klik met de rechtermuisknop op de knop `/libs/wcm/core/resources/languages` knoop en klik **Kopiëren**.
1. Klik met de rechtermuisknop op de knop `/apps/wcm/core/resources` map en klik op **Plakken**. Wijzig de onderliggende knooppunten naar wens.
1. Klikken **Alles opslaan**.
1. Klikken **Gereedschappen**, **Bewerkingen** dan **Webconsole**. Van deze console klik **OSGi** vervolgens **Configuratie**.
1. Zoeken en klikken **Day CQ WCM Language Manager** en wijzigt u de waarde van **Taallijst** tot `/apps/wcm/core/resources/languages`en klik vervolgens op **Opslaan**.

   ![Day CQ WCM Language Manager](assets/msm-language-manager.png)

## MSM-vergrendelingen configureren in pagina-eigenschappen {#configuring-msm-locks-on-page-properties}

Wanneer u een aangepaste pagina-eigenschap maakt, moet u mogelijk overwegen of de nieuwe eigenschap kan worden geïmplementeerd voor live kopieën.

Als bijvoorbeeld twee nieuwe pagina-eigenschappen worden toegevoegd:

* E-mailadres contactpersoon:

   * Deze eigenschap hoeft niet te worden uitgevoerd, omdat deze in elk land (of merk, enzovoort) anders zal zijn.

* Belangrijke visuele stijl:

   * Het projectvereiste is dat dit eigendom wordt uitgevoerd zoals het (gewoonlijk) voor alle landen (of merken, enzovoort) gemeenschappelijk is.

Daarna moet u ervoor zorgen dat:

* E-mailadres contactpersoon:

   * Is uitgesloten van de opgerolde eigenschappen.
   * Zie [Synchronisatie van actieve kopie configureren](/help/sites-cloud/administering/msm/live-copy-sync-config.md#excluding-properties-and-node-types-from-synchronization) voor meer informatie .

* Belangrijke visuele stijl:

   * Zorg ervoor dat u deze eigenschap alleen mag bewerken als overerving is geannuleerd.
   * Zorg er ook voor dat u de overerving opnieuw kunt instellen. Dit wordt gecontroleerd door de ketting/gebroken-ketting verbindingen te klikken die om op de status van de verbinding aan te geven knevels.

Of een pagina-eigenschap moet worden geïmplementeerd en, afhankelijk van het annuleren/opnieuw installeren van overerving tijdens het bewerken, wordt dan gecontroleerd door de dialoogvenster-eigenschap:

* `cq-msm-lockable`

   * Hiermee wordt het kettingkoppelingssymbool in het dialoogvenster gemaakt.
   * Dit staat slechts het uitgeven toe als de overerving wordt geannuleerd (ketting-verbinding wordt gebroken).
   * Dit geldt alleen voor het eerste onderliggende niveau van de bron
      * **Type**: `String`
      * **Waarde**: Houdt de naam van het betrokken goed vast en is vergelijkbaar met de waarde van het goed `name`
         * Zie bijvoorbeeld
           `/libs/foundation/components/page/cq:dialog/content/items/tabs/items/basic/items/column/items/title/items/title`

Wanneer `cq-msm-lockable` is gedefinieerd, heeft het breken/sluiten van de keten op de volgende manier interactie met MSM tot gevolg:

* Als de waarde van `cq-msm-lockable` is:

   * **Relatief** (bijvoorbeeld `myProperty` of `./myProperty`)

      * Als u de keten breekt, wordt de eigenschap toegevoegd en verwijderd uit `cq:propertyInheritanceCancelled`.

   * **Absoluut** (bijvoorbeeld `/image`)

      * Als u de keten breekt, wordt de overerving geannuleerd door de `cq:LiveSyncCancelled` mixen naar `./image` en instellen `cq:isCancelledForChildren` tot `true`.

      * Als u de keten sluit, wordt de overerving hersteld.

>[!NOTE]
>
>`cq-msm-lockable` is van toepassing op het eerste onderliggende niveau van de bron die moet worden bewerkt en is niet functioneel op een voorouder van een dieper niveau, ongeacht of de waarde als absoluut of relatief is gedefinieerd.

>[!NOTE]
>
>Wanneer u overerving opnieuw inschakelt, wordt de pagina-eigenschap voor live kopiëren niet automatisch gesynchroniseerd met de eigenschap source. U kunt handmatig een synchronisatie aanvragen als dit vereist is.
