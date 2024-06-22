<!-- Filename: J3.x:Updating_Joomla_(Update_Method) / Display title: Het updaten van Joomla (update methode) -->

Dit is de aanbevolen methode om een Joomla CMS website bij te werken.

Dit is niet alleen de aanbevolen methode, het is de makkelijkste methode
om het Joomla CMS te updaten. Soms wordt deze methode aangeduid met
***Eén-klik-update***. Als u voor specifieke gevallen hier geen gebruik
van kunt maken (distributies, talen, host snelheid), dan kunt u het
Joomla CMS updaten met behulp van de
**installatiemethode**.

Deze methode is geschikt voor

- Alle Joomla CMS **3.x.x** to **3.x.x** - updates (onderhouds-update)

Deze methode is niet geschikt voor

- Joomla CMS **3.1.2** tot **≥ 3.1.3** - zie [Speciale instructies voor
  versie 3.1.2
  upgrades](https://docs.joomla.org/J3.x:Detailed_instructions_for_updating_from_3.1.2_to_3.1.4 "Special:MyLanguage/J3.x:Detailed instructions for updating from 3.1.2 to 3.1.4")

## Hoe updaten

Moet u uw Joomla installatie updaten? Als er een update beschikbaar is
staat er een boodschap die aangeeft dat er een update is, met een knop
om op te drukken.

<img
src="https://docs.joomla.org/images/c/c5/J3-update-control-panel-notify-nl.PNG"
class="thumbborder" decoding="async" data-file-width="450"
data-file-height="366" width="450" height="366"
alt="J3-update-control-panel-notify-nl.PNG" />

U vind ook een bericht onderaan de 'linker sidebar'.

<img
src="https://docs.joomla.org/images/1/13/J3-update-control-panel-notify-alternative-nl.PNG"
class="thumbborder" decoding="async" data-file-width="283"
data-file-height="242" width="283" height="242"
alt="J3-update-control-panel-notify-alternative-nl.PNG" />

Joomla zal u melden op de beheer-startpagina (controle paneel) als er
een update beschikbaar is. Het zal de update niet automatisch voor u
uitvoeren. Het is de verantwoording van de beheerder om het op te
starten en te controleren of het goed gegaan is.

Het volgende zijn de aanbevolen stappen om de update van uw Joomla CMS
installatie te voltooien.

### Stap 1: Backup

Zorg ervoor dat u een **HUIDIGE BACKUP** van uw site heeft! In veel
gevallen maakt uw host regelmatig site backup's. Vertrouw **NIET** op
deze backup's! Het wordt **ZEER AANBEVOLEN** zelf een backup aan te
maken.

### Stap 2: De update-component

U moet naar de update-component navigeren. Klik op de update 'knop' of
de 'sidebar link' die eerder bovenaan werd getoond of gebruik het
hoofdmenu, slecteer en klik op **Componenten **→** Joomla! Update**. U
ziet nu onderstaande afbeelding.

<img
src="https://docs.joomla.org/images/1/18/J3-joomla-update-component-nl.PNG"
class="thumbborder" decoding="async" data-file-width="800"
data-file-height="359" width="800" height="359"
alt="J3-joomla-update-component-nl.PNG" />

Selecteer, 'Schrijf bestanden direct' (standaard) of 'Schrijf bestanden
via FTP' als installatiemethode voor het uploaden van de nieuwe core
bestanden naar uw installatie. Heeft u een backup? Zie stap 1 hierboven.

### Stap 3: Start de update

Klik op de "Installeer de update" knop en de update zal beginnen.

<img
src="https://docs.joomla.org/images/f/fc/J3-updating-your-joomla-files-nl.PNG"
class="thumbborder" decoding="async" data-file-width="620"
data-file-height="359" width="620" height="359"
alt="J3-updating-your-joomla-files-nl.PNG" />

Als de update voltooid is ziet u een 'bijwerken geslaagd' bericht met de
nieuwe versie.

<img
src="https://docs.joomla.org/images/3/3d/J3-jooml-update-successful-nl.PNG"
class="thumbborder" decoding="async" data-file-width="646"
data-file-height="378" width="646" height="378"
alt="J3-jooml-update-successful-nl.PNG" />

Als de update voltooid is moet u uw browsercache legen om template CSS
wijzigingen door te voeren.

## Joomla update instellingen

In de meeste gevallen hoeft u deze instellingen niet te veranderen. De
standaard keuzes zorgen ervoor dat uw Joomla CMS installatie altijd
gecontroleerd is op de juiste update server en de juiste persoon met
beheerder rechten kan de installatie updaten.

Het instellingen scherm wordt bereikt door op de 'opties' knop te
drukken in het Joomla! update scherm. Als u op de 'opties' knop drukt
ziet u de volgende scherm.

<img
src="https://docs.joomla.org/images/1/14/J3-update-component-configure-server-nl.PNG"
class="thumbborder" decoding="async" data-file-width="748"
data-file-height="506" width="748" height="506"
alt="J3-update-component-configure-server-nl.PNG" />

### Instellingen updatekanaal

Het update bericht dat u ziet op de startpagina hangt af van de
instellingen van de updatekanaal en caching.

<img
src="https://docs.joomla.org/images/3/3a/J3-update-component-configure-server-options-nl.PNG"
class="thumbborder" decoding="async" data-file-width="487"
data-file-height="282" width="487" height="282"
alt="J3-update-component-configure-server-options-nl.PNG" />

De eerste optie toont de nieuwste update van de hoofdrelease die
gebruikt wordt (standaard). De tweede optie toont de nieuwste update van
de nieuwste hoofdrelease. Caching kan zorgen dat een beschikbare update
niet ontdekt wordt en u moet de cache legen.

### Rechten

<img
src="https://docs.joomla.org/images/6/69/J3-update-component-configure-server-permissions-nl.PNG"
class="thumbborder" decoding="async" data-file-width="979"
data-file-height="486" width="979" height="486"
alt="J3-update-component-configure-server-permissions-nl.PNG" />
