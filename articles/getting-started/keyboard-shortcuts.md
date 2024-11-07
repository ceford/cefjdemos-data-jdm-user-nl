<!-- Filename: Keyboard_Shortcuts / Display title: Sneltoetsen  -->

## Inleiding

Het toetsenbord kan in de beheerdersinterface worden gebruikt om enkele acties uit te voeren die normaal met een muis of touchpad worden gedaan. Er zijn bijvoorbeeld sneltoetsen om de huidige pagina op te slaan, naar het *Startdashboard* te gaan of een *Opties*-formulier te openen.

Er is een overzicht van alle sneltoetsen, dat kan worden geopend door achtereenvolgens de toetsen **J** en **X** in te voeren (niet tegelijkertijd en gebruik niet de Shift-toets die normaal gebruikt wordt voor hoofdletters). Tenzij je de plugin-instellingen wijzigt, moet je de toetsen binnen 2 seconden indrukken.

De functie is standaard ingeschakeld. Het kan worden uitgeschakeld of geconfigureerd onder **Beheerder → Systeem → Plugins → Systeem - Toetsenbord Sneltoetsen**. Momenteel is de enige configuratie de time-out: hoe lang het systeem wacht op je volgende toetsinvoer. Standaard wacht het 2000 milliseconden (2 seconden). 

## Standaard Sneltoetsen in Joomla

- J + A - Slaat de huidige inhoud op
- J + S - Voor Opslaan & Sluiten
- J + Q - Annuleert de huidige pagina
- J + N - Drukt op de *Nieuw* knop
- J + F - Zet de focus op het Zoekveld
- J + O - Gaat naar Opties
- J + H - Hulpscherm opent (kan een browser pop-up waarschuwing activeren)
- J + M - Schakelt de menubalk in of uit
- J + X - Geeft een lijst van beschikbare sneltoetsen weer
- J + D - Gaat direct naar het Home Dashboard

## Derden Partij Sneltoetsen - Informatie voor Ontwikkelaars

Andere ontwikkelaars kunnen ook hun sneltoetsen toevoegen. De Joomla-plugin roept de *onLoadShortcuts* gebeurtenis aan, die ook door andere plugins kan worden gebruikt. De gebeurtenis moet worden toegevoegd aan de lijst van *getSubscribedEvents* binnen de plugin. De toegewezen functie zou er als volgt uit kunnen zien:

```php
    public function onLoadShortcuts(EventInterface $event): void {
       $shortcuts = $event->getArgument('shortcuts');
       $exampleShortcuts = array('example' => (object)['shortcut' => 'E', 'title' => 'Geweldig Voorbeeld', 'selector' => '#menu-collapse']);
       $event->setArgument('shortcuts',  array_merge($shortcuts, $exampleShortcuts));
    }
```
Besteed speciale aandacht aan het array_merge deel: Wanneer de al bestaande sneltoetsen niet worden samengevoegd met de nieuwe, worden de oude overschreven.

Ontwikkelaars kunnen een array aanleveren met sneltoetsobjecten:

    { shortcut: string, selector: string, title: string }

- De *Sneltoets* moet een toetsenbordinvoer zijn, gescheiden door een plus, bijv. `Y` of `ALT + Z + 7` (momenteel is er echt geen filtering). Houd er rekening mee dat elke sneltoetsenreeks zal beginnen met **J**.
- *Selectors* zijn CSS-selectors of URL's om het doel te specificeren. Wanneer het een invoerelement betreft, krijgt de sneltoets focus zoals het geval is bij het zoekveld. Anders wordt het element aangeklikt of de URL opgeroepen.
- De *Titel* zal worden getoond in het overzicht. Het zou bijvoorbeeld de naam van het doel kunnen zijn.

## Redenen voor het gebruik van J + X

Sommigen vragen zich misschien af waarom er gekozen is voor sequentiële sneltoetsen of de **J** als startpunt in plaats van Ctrl of iets anders. De belangrijkste redenen zijn toegankelijkheid en het vermijden van onderbrekingen door andere software. Bijvoorbeeld, *Ctrl + S* zou handig zijn voor het opslaan van een artikel, maar wordt al gebruikt door browsers. Hetzelfde kan gebeuren met schermlezers of wachtwoordmanagers. Dus de veiligere optie was om iets Joomla-specifieks te gebruiken, zoals de **J** aan het begin.

Het andere probleem is dat het niet altijd mogelijk is om meer dan één toets tegelijk in te drukken. Windows heeft hiervoor de Sticky Key-modus, maar die werkt alleen voor modifiertoetsen zoals Shift, Ctrl en Alt. Dus de plugin gebruikt vanaf het begin sequentiële invoer, waardoor het door meer mensen kan worden gebruikt, zelfs zonder de hulp van OS-modus.

*Vertaald door openai.com*

