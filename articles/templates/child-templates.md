<!-- Filename: J4.x:Child_Templates / Display title: Kindsjablonen -->

## Inleiding

Kindsjablonen gebruiken alle bestanden van hun ouder-sjablonen, behalve voor bestanden met dezelfde naam die je in het kindsjabloon plaatst. Kindsjabloonbestanden worden niet beïnvloed door Joomla-updates. Dus je zou je eigen index.php-bestand in een kindsjabloon kunnen plaatsen en dat iets heel anders laten leveren dan het standaard sjabloon, zoals extra moduleposities of alternatieve extensie-overschrijvingen.

Een voorbeeldscenario: stel dat je wilt dat sommige van je pagina's verschijnen met een blauw thema, de standaardkleuren van Cassiopeia, en andere pagina's met een groen thema. Een eenvoudige manier om dit te bereiken is met een kindsjabloon dat zijn eigen user.css-stijlblad gebruikt.

## Uitgewerkt voorbeeld

Start vanuit **Systeem → Sjablonen paneel → Sitesjablonen**

- Selecteer *Cassiopeia Details en Bestanden*.
- Selecteer de knop *Maak Kindersjabloon*.
- Vul het Kindersjabloon pop-updialoogvenster in en selecteer de knop
  Maak Kindersjabloon:

![kindersjabloon aanmaakmodaal](../../../en/images/templates/child-templates-create-green.png)

Selectie van Cassiopeia - Standaard in het veld Aanvullende Sjabloonstijlen lijkt onnodig (is dat een fout?).

- Selecteer *Sluiten* van de Toolbar om het oudersjabloonformulier te sluiten.
- Selecteer het nieuwe sjabloon, *Cassiopeia_green Details en Bestanden*, uit de lijst met Sjablonen.

Op dit moment is er een mapstructuur, maar slechts één bestand: templateDetails.xml. Dat bestand kan worden aangepast als je aspecten van de sjabloonconfiguratie wilt wijzigen, bijvoorbeeld sjabloonposities toevoegen of verwijderen.

### Creëer een user.css bestand

- Selecteer de knop *Nieuw Bestand* in de Toolbar.
- Zorg ervoor dat je in het formulier *Creëer of Upload een nieuw bestand* de map `css` selecteert.
- Vul de bestandsnaam in met `user`. Voeg GEEN achtervoegsel toe!
- Selecteer het Bestandstype `.css`.
- Selecteer de knop *Creëer*.

![kindersjabloon creëer user css formulier](../../../en/images/templates/child-templates-create-green-user-css.png)

Het user.css-bestand is leeg, klaar om aangepaste stijlen in te voeren. Voer het volgende in om het groene thema te starten:
```css
    .container-header {
      background-color: darkgreen;
      background-image: none;
    }
    h1, h2, h3, h4, h5, h6 {
      color: darkgreen;
    }
    .h1, .h2, .h3, .h4, .h5, .h6 {
      color: darkgreen;
    }
    a, a:hover, a:focus {
      color: darkgreen;
    }
    .btn-info {
        background-color: darkgreen;
        border-color: #30638d;
        color: #fff;
    }
    .btn-primary, .btn-primary:focus, .btn-primary:hover {
        background-color: darkgreen;
        border-color: var(--cassiopeia-color-hover);
    }

    .btn-check:focus + .btn-info, .btn-info:focus, .btn-info:hover {
        background-color: darkgreen;
        border-color: #264f71;
        color: #fff;
    }
```
Je moet mogelijk later terugkomen naar dit user.css-bestand om meer stijlen toe te voegen.

- Selecteer *Opslaan en Sluiten* of afzonderlijk *Opslaan* en vervolgens *Bestand Sluiten*.
- Selecteer *Sluiten* om het Aangepast formulier te sluiten.

### Menu-item

Op dit punt is er een menu-item nodig om gebruik te maken van het kindersjabloon. Een nieuwe Joomla 4-installatie heeft het Hoofdmenu in de rechterzijbalk met één item erin. Dat lijkt een goede plek voor een nieuw menu-item.

- Selecteer **Menu's → Hoofdmenu** vanuit het Beheerdersmenu.
- Selecteer de knop *Nieuw* in de Toolbar.
- Voer een geschikte titel in, *Groene Uitgelichte Artikelen* lijkt in dit geval passend.
- Selecteer de **Menutype → Selecteer** knop.
- Selecteer een menutype vanuit de Menutype pop-updialoog - Uitgelichte Artikelen in dit voorbeeld.
- Selecteer *cassiopeia_manual - Standaard* vanuit het *Sjabloon Stijl* veld.

![kindersjabloon menu-item bewerk formulier](../../../en/images/templates/child-templates-create-green-menu-item.png)

- Voor de doeleinden van de volgende schermafbeelding is het Blog Indeling ingesteld op Leading Artikelen: 0, Intro Artikelen: 3 en Multi Kolom Richting: Over.

### Siteweergave

- Op de startpagina van je site selecteer je het zojuist aangemaakte menu-item.

![site met aangepast groene thema sjabloon](../../../en/images/templates/child-templates-green-site-result.png)

### Bewerk de Stijl

- Selecteer **Systeem → Sjablonen paneel → Sitesjabloonstijlen** vanuit het Beheerdersmenu.
- Selecteer *Cassiopeia_green - Standaard* uit de Stijllijst.
- Verander de Stijlnaam naar *Cassiopeia Groen*. Dat maakt de naam in lijsten netter.
- Selecteer *Opslaan en Sluiten*.

*Vertaald door openai.com*

