<!-- Filename: J4.x:Cassiopeia_templateDetails.xml / Display title: Cassiopeia templateDetails.xml  -->

## Locatie en Doel

Je kunt een voorbeeld van een `templateDetails.xml`-bestand vinden onder **Systeem → Site Templates → Cassiopeia Details en Bestanden**. Je kunt het daar ook bewerken als je daar een goede reden voor hebt. Anders, laat het met rust! Elke template heeft zo'n bestand en een kindtemplate bestaat aanvankelijk uit een bestandsstructuur die alleen dit ene bestand bevat.

Het `templateDetails.xml`-bestand bevat de gegevens die Joomla! nodig heeft om de template te beheren en weer te geven. Dit omvat meta-data die gebruikt wordt om informatie over de template te geven, de locaties van mappen en bestanden, de template module posities en de door de gebruiker selecteerbare configuratie-opties. De inhoud van het templateDetails.xml-bestand zal verschillen per template.

## Cassiopeia templateDetails.xml

Bestanden in xml-formaat hebben een goed gedefinieerde structuur. Een xml-bestand moet de juiste syntax hebben, anders werkt het niet!

### XML-formaat

De eerste regel van elke `templateDetails.xml` moet beginnen met de XML doctype-definitie.

De volgende regel vertelt Joomla! dat de gegevens in dit bestand bedoeld zijn voor een site template-uitbreiding. Alle templategegevens zijn opgenomen binnen de openings- en sluitingstags.

```xml
<extension type="template" client="site">
...
</extension>
```

### Metadata

Het eerste deel van de templategegevens definieert meestal template-informatie, zoals: namen, data, contactgegevens, auteursrechten, versienummer en beschrijving.

```xml
<extension version="3.1" type="template" client="site">
	<name>cassiopeia</name>
	<version>1.0</version>
	<creationDate>2017-02</creationDate>
	<author>Joomla! Project</author>
	<authorEmail>admin@joomla.org</authorEmail>
	<copyright>(C) 2017 Open Source Matters, Inc.</copyright>
	<description>TPL_CASSIOPEIA_XML_DESCRIPTION</description>
	<inheritable>1</inheritable>
```

Merk op dat een template die kindertemplates kan hebben, de inheritable waarde op 1 heeft staan. Kindertemplates hebben deze waarde ingesteld op 0. Deze gegevens worden gebruikt in de Templates: Templates (Site) lijst zoals hieronder weergegeven.

![site templates lijst](../../../en/images/templates/templates-list.png)

De beschrijving bevat een taalcode en niet de daadwerkelijke beschrijvingstekststring. De sleutel wordt tijdens de uitvoeringstijd vervangen door de tekst verkregen uit een taalbestand. De taalbestanden worden gedefinieerd in de taal sectie van `templateDetails.xml`.

![templates bewerk stijl formulier](../../../en/images/templates/templates-edit-style.png)

### Mappen en Bestanden

Mappen en bestanden voor de Cassiopeia-template worden opgeslagen op twee afzonderlijke locaties. De php en gerelateerde bestanden worden opgeslagen in de site/templates map. De mediabestanden (css, afbeeldingen, js en scss) worden opgeslagen in de site/media map. Die locaties worden als volgt gedefinieerd in het xml-bestand:

```xml
	<files>
		<filename>component.php</filename>
		<filename>error.php</filename>
		<filename>index.php</filename>
		<filename>joomla.asset.json</filename>
		<filename>offline.php</filename>
		<filename>templateDetails.xml</filename>
		<folder>html</folder>
	</files>
	<media destination="templates/site/cassiopeia" folder="media">
		<folder>js</folder>
		<folder>css</folder>
		<folder>scss</folder>
		<folder>images</folder>
	</media>
```

Dit is het patroon dat te zien is in alle moderne Joomla 4 en 5 templates. De structuur kan worden gezien in de Templates: Aanpassen (Cassiopeia) formulier:

![templates aanpassen cassiopeia pagina](../../../en/images/templates/templates-customise-cassiopeia.png)

### Moduleposities

De beschikbare moduleposities worden als volgt gedefinieerd:

```xml
	<positions>
		<position>topbar</position>
		<position>below-top</position>
		<position>menu</position>
		<position>search</position>
		<position>banner</position>
		<position>top-a</position>
		<position>top-b</position>
		<position>main-top</position>
		<position>main-bottom</position>
		<position>breadcrumbs</position>
		<position>sidebar-left</position>
		<position>sidebar-right</position>
		<position>bottom-a</position>
		<position>bottom-b</position>
		<position>footer</position>
		<position>debug</position>
	</positions>
```

Elke tag creëert een modulepositie die beschikbaar is vanuit de positieslijst in een modulebewerkingsformulier. Het eenvoudige formaat van de positieslijst betekent dat deze eenvoudig kan worden aangepast. Bijvoorbeeld, om een nieuwe modulepositie toe te voegen aan de lijst **in een kindtemplate**, voeg je eenvoudig een nieuwe tag toe met een unieke naam, gebruikmakend van alleen kleine letters zonder spaties. Houd er rekening mee dat dit alleen de positie toevoegt aan modulebewerkingsformulieren en aanvullend ontwikkeling in andere templatebestanden vereist is om de nieuwe positie aan de voorkant weer te geven.

Cassiopeia heeft voldoende templateposities! Als je denkt dat je er een extra nodig hebt, heb je waarschijnlijk ongelijk. Vergeet niet dat elk aantal modules kan worden toegewezen aan een enkele positie en in volgorde kan worden gesorteerd op de Modulens lijstpagina. Beschikbare posities:

![Cassiopeia template posities diagram](../../../en/images/templates/cassiopeia-template-positions.png)

Je kunt de moduleposities in elk template ook zien: van **Systeem → Site Templates** selecteer de Opties knop in de Werkbalk. Stel in het Opties formulier het Voorvertonen van Moduleposities veld in op Ingeschakeld. Opslaan en Sluiten. Ga naar je site en voeg ?tp=1 aan het einde toe van elke URL (of &tp=1 als er al een ? in de URL staat). Joomla laat alle beschikbare templateposities zien, zelfs die nog niet zijn gebruikt:

![Cassiopeia template posities](../../../en/images/templates/templates-template-positions-by-tp.png)

### Talen

Taalbestanden maken vertaling van statische tekst in het template mogelijk. Het tpl_cassiopeia.ini bestand bevat sleutels naar tekstvertalingen voor tekst die door de Gebruiker wordt bekeken. Het tpl_cassiopeia.sys.ini bestand bevat sleutels naar tekstvertalingen voor tekst die door de Beheerder wordt gezien.

```xml
	<languages folder="language">
		<language tag="en-GB">en-GB/tpl_cassiopeia.ini</language>
		<language tag="en-GB">en-GB/tpl_cassiopeia.sys.ini</language>
	</languages>
```

De taalbestanden voor de standaard Engelse GB-taal zijn opgeslagen in site/language/en-GB/. Andere talen zouden op dezelfde wijze worden opgeslagen in bestanden met de juiste ISO-taalcode, bijvoorbeeld fr-FR voor Frans in Frankrijk of de-DE voor Duits in Duitsland (wat anders kan zijn dan Zwitsers Duits of Oostenrijks Duits).

### Opties

Een template kan weergave-opties aanbieden die door de Beheerder kunnen worden gekozen in het Template: Stijl bewerken formulier. Bijvoorbeeld, het Geavanceerd tabblad van de Cassiopeia-template stelt een Beheerder in staat om het Merkteken te wijzigen, een Logo toe te voegen, een Lettertype Schema te selecteren en meer.

![templates stijl bewerken formulier geavanceerd tabblad](../../../en/images/templates/templates-edit-style-advanced.png)

De template-opties worden gedefinieerd binnen een structuur die velden binnen fieldsets creëert. Elke fieldset verschijnt als een tabblad in het bewerkingsformulier. Dit is de structuur die het Geavanceerd tabblad hierboven weergegeven creëert.

```xml
	<config>
		<fields name="params">
			<fieldset name="advanced">
				<field
					name="brand"
					type="radio"
					label="TPL_CASSIOPEIA_BRAND_LABEL"
					default="1"
					layout="joomla.form.field.radio.switcher"
					filter="boolean"
					>
					<option value="0">JNO</option>
					<option value="1">JYES</option>
				</field>
				...
			</fieldset>
		</fields>
	</config>
```

Individuele opties worden gedefinieerd met de `<field>` tag. Elke `<fieldset>`, en elke `<field>` parameter binnen een `<fieldset>`, vereist een unieke naam die wordt gedefinieerd door een **name** attribuut. Deze naam definieert de parameter zelf en wordt gebruikt om instellingen door te geven aan de frontend-bestanden. Elke parameter bevat ook een **label** attribuut en een **description** attribuut. De labeltekst verschijnt met de parameter in het instellingsscherm om aan te geven waarvoor de instelling wordt gebruikt en meer gedetailleerde informatie kan worden opgenomen in de beschrijving.

Een parameter veld kan vrijwel elk type invoerveld met corresponderende opties zijn. Dit wordt geselecteerd door het **type** attribuut. Eventuele noodzakelijke opties, zoals radio-knop of selectiekeuzes, worden gedefinieerd in `<option>` tags. CSS-classnamen kunnen worden gedefinieerd met het **class** attribuut en een standaardwaarde kan worden gedefinieerd met behulp van het **default** attribuut.

Hieronder staan de optie definities in de standaard Cassiopeia-template. In dit voorbeeld gebruiken alle Labels, Beschrijvingen en Opties taalstrings definitie uit de Taalbestanden, zoals beschreven in de vorige sectie, evenals enkele uit de Joomla! core, zodat ze indien nodig in verschillende talen kunnen worden vertaald.

```xml
	<config>
		<fields name="params">
			<fieldset name="advanced">
				<field
					name="brand"
					type="radio"
					label="TPL_CASSIOPEIA_BRAND_LABEL"
					default="1"
					layout="joomla.form.field.radio.switcher"
					filter="boolean"
					>
					<option value="0">JNO</option>
					<option value="1">JYES</option>
				</field>

				<field
					name="logoFile"
					type="media"
					default=""
					label="TPL_CASSIOPEIA_LOGO_LABEL"
					showon="brand:1"
				/>

				<field
					name="siteTitle"
					type="text"
					default=""
					label="TPL_CASSIOPEIA_TITLE"
					filter="string"
					showon="brand:1"
				/>

				<field
					name="siteDescription"
					type="text"
					default=""
					label="TPL_CASSIOPEIA_TAGLINE_LABEL"
					description="TPL_CASSIOPEIA_TAGLINE_DESC"
					filter="string"
					showon="brand:1"
				/>

				<field
					name="useFontScheme"
					type="groupedlist"
					label="TPL_CASSIOPEIA_FONT_LABEL"
					default="0"
					>
					<option value="0">JNONE</option>
					<group label="TPL_CASSIOPEIA_FONT_GROUP_LOCAL">
						<option value="media/templates/site/cassiopeia/css/global/fonts-local_roboto.css">Roboto (local)</option>
					</group>
					<group label="TPL_CASSIOPEIA_FONT_GROUP_WEB">
						<option value="https://fonts.googleapis.com/css2?family=Fira+Sans:wght@100;300;400;700&amp;display=swap">Fira Sans (web)</option>
						<option value="https://fonts.googleapis.com/css2?family=Noto+Sans:wght@100;300;400;700&amp;family=Roboto:wght@100;300;400;700&amp;display=swap">Roboto + Noto Sans (web)</option>
					</group>
				</field>

				<field
					name="noteFontScheme"
					type="note"
					description="TPL_CASSIOPEIA_FONT_NOTE_TEXT"
					class="alert alert-warning"
				/>

				<field
					name="colorName"
					type="filelist"
					label="TPL_CASSIOPEIA_COLOR_NAME_LABEL"
					default="colors_standard"
					fileFilter="^custom.+[^min]\.css$"
					exclude="^colors.+"
					stripext="true"
					hide_none="true"
					hide_default="true"
					directory="media/templates/site/cassiopeia/css/global/"
					validate="options"
					>
					<option value="colors_standard">TPL_CASSIOPEIA_COLOR_NAME_STANDARD</option>
					<option value="colors_alternative">TPL_CASSIOPEIA_COLOR_NAME_ALTERNATIVE</option>
				</field>

				<field
					name="fluidContainer"
					type="radio"
					layout="joomla.form.field.radio.switcher"
					default="0"
					label="TPL_CASSIOPEIA_FLUID_LABEL"
					>
					<option value="0">TPL_CASSIOPEIA_STATIC</option>
					<option value="1">TPL_CASSIOPEIA_FLUID</option>
				</field>

				<field
					name="stickyHeader"
					type="radio"
					label="TPL_CASSIOPEIA_STICKY_LABEL"
					layout="joomla.form.field.radio.switcher"
					default="0"
					filter="integer"
					>
					<option value="0">JNO</option>
					<option value="1">JYES</option>
				</field>

				<field
					name="backTop"
					type="radio"
					label="TPL_CASSIOPEIA_BACKTOTOP_LABEL"
					layout="joomla.form.field.radio.switcher"
					default="0"
					filter="integer"
					>
					<option value="0">JNO</option>
					<option value="1">JYES</option>
				</field>
			</fieldset>
		</fields>
	</config>
```

In dit voorbeeld omvat de `<fieldset name="advanced">` tag alle parameters en het gebruikt het **name** attribuut om het *Geavanceerd* tabblad in de interface te creëren. Alles wat nodig is om een ander tabblad in de interface te maken is een andere `<fieldset>` tag met een ander **name** attribuut. Met dit in gedachten is het relatief eenvoudig om zoveel extra tabbladen en parameters te creëren als nodig in een template.

Een potentieel gebruik van extra parameters is in overrides of lay-outs voor zowel ouder- als kindertemplates.

## Samenvatting

Dit is het templateDetails.xml-bestand dat door Cassiopeia wordt gebruikt:

```xml
<?xml version="1.0" encoding="utf-8"?>
<extension type="template" client="site">
	<name>cassiopeia</name>
	<version>1.0</version>
	<creationDate>2017-02</creationDate>
	<author>Joomla! Project</author>
	<authorEmail>admin@joomla.org</authorEmail>
	<copyright>(C) 2017 Open Source Matters, Inc.</copyright>
	<description>TPL_CASSIOPEIA_XML_DESCRIPTION</description>
	<inheritable>1</inheritable>
	<files>
		<filename>component.php</filename>
		<filename>error.php</filename>
		<filename>index.php</filename>
		<filename>joomla.asset.json</filename>
		<filename>offline.php</filename>
		<filename>templateDetails.xml</filename>
		<folder>html</folder>
	</files>
	<media destination="templates/site/cassiopeia" folder="media">
		<folder>js</folder>
		<folder>css</folder>
		<folder>scss</folder>
		<folder>images</folder>
	</media>
	<positions>
		<position>topbar</position>
		<position>below-top</position>
		<position>menu</position>
		<position>search</position>
		<position>banner</position>
		<position>top-a</position>
		<position>top-b</position>
		<position>main-top</position>
		<position>main-bottom</position>
		<position>breadcrumbs</position>
		<position>sidebar-left</position>
		<position>sidebar-right</position>
		<position>bottom-a</position>
		<position>bottom-b</position>
		<position>footer</position>
		<position>debug</position>
	</positions>
	<languages folder="language">
		<language tag="en-GB">en-GB/tpl_cassiopeia.ini</language>
		<language tag="en-GB">en-GB/tpl_cassiopeia.sys.ini</language>
	</languages>
	<config>
		<fields name="params">
			<fieldset name="advanced">
				<field
					name="brand"
					type="radio"
					label="TPL_CASSIOPEIA_BRAND_LABEL"
					default="1"
					layout="joomla.form.field.radio.switcher"
					filter="boolean"
					>
					<option value="0">JNEE</option>
					<option value="1">JJAA</option>
				</field>

				<field
					name="logoFile"
					type="media"
					default=""
					label="TPL_CASSIOPEIA_LOGO_LABEL"
					showon="brand:1"
				/>

				<field
					name="siteTitle"
					type="text"
					default=""
					label="TPL_CASSIOPEIA_TITLE"
					filter="string"
					showon="brand:1"
				/>

				<field
					name="siteDescription"
					type="text"
					default=""
					label="TPL_CASSIOPEIA_TAGLINE_LABEL"
					description="TPL_CASSIOPEIA_TAGLINE_DESC"
					filter="string"
					showon="brand:1"
				/>

				<field
					name="useFontScheme"
					type="groupedlist"
					label="TPL_CASSIOPEIA_FONT_LABEL"
					default="0"
					>
					<option value="0">JNONE</option>
					<group label="TPL_CASSIOPEIA_FONT_GROUP_LOCAL">
						<option value="media/templates/site/cassiopeia/css/global/fonts-local_roboto.css">Roboto (lokaal)</option>
					</group>
					<group label="TPL_CASSIOPEIA_FONT_GROUP_WEB">
						<option value="https://fonts.googleapis.com/css2?family=Fira+Sans:wght@100;300;400;700&amp;display=swap">Fira Sans (web)</option>
						<option value="https://fonts.googleapis.com/css2?family=Noto+Sans:wght@100;300;400;700&amp;family=Roboto:wght@100;300;400;700&amp;display=swap">Roboto + Noto Sans (web)</option>
					</group>
				</field>

				<field
					name="noteFontScheme"
					type="note"
					description="TPL_CASSIOPEIA_FONT_NOTE_TEXT"
					class="alert alert-warning"
				/>

				<field
					name="colorName"
					type="filelist"
					label="TPL_CASSIOPEIA_COLOR_NAME_LABEL"
					default="colors_standard"
					fileFilter="^custom.+[^min]\.css$"
					exclude="^colors.+"
					stripext="true"
					hide_none="true"
					hide_default="true"
					directory="media/templates/site/cassiopeia/css/global/"
					validate="options"
					>
					<option value="colors_standard">TPL_CASSIOPEIA_COLOR_NAME_STANDARD</option>
					<option value="colors_alternative">TPL_CASSIOPEIA_COLOR_NAME_ALTERNATIVE</option>
				</field>

				<field
					name="fluidContainer"
					type="radio"
					layout="joomla.form.field.radio.switcher"
					default="0"
					label="TPL_CASSIOPEIA_FLUID_LABEL"
					>
					<option value="0">TPL_CASSIOPEIA_STATIC</option>
					<option value="1">TPL_CASSIOPEIA_FLUID</option>
				</field>

				<field
					name="stickyHeader"
					type="radio"
					label="TPL_CASSIOPEIA_STICKY_LABEL"
					layout="joomla.form.field.radio.switcher"
					default="0"
					filter="integer"
					>
					<option value="0">JNEE</option>
					<option value="1">JJAA</option>
				</field>

				<field
					name="backTop"
					type="radio"
					label="TPL_CASSIOPEIA_BACKTOTOP_LABEL"
					layout="joomla.form.field.radio.switcher"
					default="0"
					filter="integer"
					>
					<option value="0">JNEE</option>
					<option value="1">JJAA</option>
				</field>
			</fieldset>
		</fields>
	</config>
</extension>
```

*Vertaald door openai.com*

