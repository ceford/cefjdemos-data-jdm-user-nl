<!-- Filename: J4.x:Submenus / Display title: Submenu's  -->

## Menu Basis

In Joomla dragen drie elementen bij aan de weergave van een menu voor de gebruiker:

- Een Menu is een container voor menu-items.
- Een Menu-item is een link naar een sitepagina of externe pagina.
- Een Menumodule biedt een methode om het menu toe te wijzen aan een positie op de pagina en om aspecten van de weergave of het gedrag van het menu of de pagina te beheersen.

Eenvoudige menu's bestaan uit lijsten met links. Soms hebben leden van een lijst ouder-kindrelaties die worden weergegeven als ingesprongen kinderen of uitklaplijsten. Ouder-kindrelaties kunnen tot elk niveau worden genesteld. Echter, nestelen boven twee niveaus kan lijsten onaantrekkelijk en onhandig in gebruik maken.

Er zijn situaties waarin je de kinderen van een hoofdmenu als een apart submenu wilt weergeven. Een veelvoorkomend gebruiksvoorbeeld is om een submenu aan de linkerkant van een pagina te tonen, de pagina-inhoud in het midden en een inhoudsopgave van de pagina aan de rechterkant. Deze tutorial legt uit hoe je dit kunt doen.

### Voorbeeldgegevens

Stel dat je een reeks artikelen over dieren hebt. Het kan gaan over huisdieren, een dierenarts informatiesheet of een dierentuin. Het volgende is een korte voorbeeldstructuur voor demonstratiedoeleinden:

    Dieren
        Katten
            Burmees
            Russische Blauwe
        Honden
            Collies
            Pomeranians

De lijsten kunnen vrij lang zijn, dus je wilt misschien alleen een lijst van kattenrassen weergeven op pagina's over katten en alleen een lijst van hondenrassen op pagina's over honden. De volgende screenshot toont de gewenste lay-out die de gebruiker wil bereiken:

![submenu doelen dieren katten](../../../en/images/menus/submenus-objectives-animals-cats.png)

In dit voorbeeld, wanneer de gebruiker het menu-item Dieren selecteert, wordt de Dierenpagina geladen en verdwijnt de Kattenmenumodule (geen Hondemodule ook). Selecteer het menu-item Katten en de Kattenmenumodule verschijnt naast de Kattenpagina. Selecteer het menu-item Burmees en de Burmeespagina verschijnt. Selecteer het menu-item Honden en de Kattenmenumodule wordt vervangen door een Hondemodule naast de Hondenpagina.

Om deze tutorial zelf te proberen, moet je een aantal artikelen maken, een menu met menu-items en drie menumodules.

## Artikelen Maken

Als je erg efficiënt bent, kun je een artikel maken en vervolgens een menu-item vanuit het artikel creëren. Hiervoor moet je eerst een nieuw menu aanmaken en enkele extra stappen ondernemen tijdens het creëren van het artikel. Het is dus het beste om het in eerste instantie eenvoudig te houden en te beginnen met je nieuwe artikelen:

- Selecteer **Inhoud** → **Artikelen** → **+** in het menu van de beheerder.
  Of selecteer de knop `Nieuw` in de Artikellijst.
- Vul het formulier in zoals je voor elk artikel zou doen.
- Selecteer de knop `Opslaan & Nieuw` van `Opslaan & Sluiten` om verder te gaan met het volgende nieuwe artikel.

De voorbeeldgegevens hierboven vereisen zeven artikelen.  

## Een Nieuw Menu Maken

Vanuit het Administrator menu:

- Selecteer **Menu's** → **Beheren**.
- Klik op de Menulijst-pagina op de knop `Nieuw` om een nieuw menu te maken.
- Geef in het Menu’s: Toevoegen-formulier het menu een titel: Dieren en een unieke naam: dieren.
- In sommige gevallen moet u zichzelf herinneren waarvoor dit menu is. Vul daarom het beschrijvingsveld in.
- Opslaan of Opslaan & Sluiten.

![submenu’s nieuw menu](../../../en/images/menus/submenus-new-menu.png)

## Menu-items maken

Er zijn zeven menu-items te maken.

### Dieren Menu-item

De nieuwe menu-items worden geplaatst in het menu Dieren.

- Selecteer **Menu's**→**Dieren**→**+** vanuit het Administratormenu.
- Vul het formulier Menu: Item bewerken in.
  - Titel: Dieren
  - Menu-itemtype: Enkel artikel
  - Selecteer artikel: Dieren - dit is het hoofdartikel dat wordt gebruikt om de serie over Dieren in te leiden
  - Menu: Dieren
  - Ouder: - Geen ouder - dit is de menu-root
- Selecteer **Opslaan & Nieuw** in de `Opslaan & Sluiten` drop-down lijst.

### Katten Menu-item

Dit is grotendeels een herhaling van het Dieren menu-item. Behalve:

- Titel moet Katten zijn.
- Het artikel dat geselecteerd moet worden in het veld Selecteer artikel is `Katten`.
- Het ouder-item moet worden ingesteld op `Dieren`.

### Birmaans Menu-item

Herhaal opnieuw. Behalve:

- Titel moet Birmaans zijn.
- Het artikel dat geselecteerd moet worden in het veld Selecteer artikel is `Birmaans`.
- Het ouder-item moet worden ingesteld op `Katten`.

### Meer Menu-items

Ga door tot je zeven menu-items hebt, één voor elk artikel.

## Lijst van Menu Items

Wanneer je al je menu-items hebt aangemaakt, controleer dan of ze de juiste ouder-kind-relaties hebben en of ze in de juiste volgorde staan. Je kunt sorteren op de kolom 'Volgorde' (de tweede kolom) en de grijphandvatten (verticale ellipsis) gebruiken om items in de juiste volgorde te slepen. Als een item een verkeerde ouder heeft, selecteer dan gewoon de titel van het item en wijzig de ouder in het menu: bewerk item formulier.

![submenu's menu items lijst](../../../en/images/menus/submenus-menu-items-list.png)  

## Menu Modules

In deze fase heb je een menu, maar er is geen module toegewezen aan een positie op de pagina. Je zou het hele menu als standaardmenu of uitklapmenu kunnen gebruiken. Het doel van deze handleiding is echter om te laten zien hoe je submenu's kunt maken. Daarvoor heb je drie verschillende modules nodig:

- Een module Dieren voor een submenu met menu-items over Dieren, Katten en Honden.
- Een module Katten voor een submenu met menu-items over kattenrassen.
- Een module Honden voor een submenu met menu-items over hondenrassen.

## Module Submenu Dieren

Via het Beheerdersmenu:

- Selecteer **Inhoud** → **Site-modules** → **+** of selecteer `Nieuw` uit de
  Modulelijst (Site).
- Selecteer de **Menu** module.
- Voer in het bewerkingsformulier Modules: Menu de volgende gegevens in:
  - Titel: Dieren
  - Selecteer Menu: Dieren
  - Basisitem: Dieren (dit is het bovenliggende menu-item)
  - Startniveau: 1
  - Eindniveau: 2 (dit beperkt de items tot de menu-items van Katten en
    Honden)
  - Positie: zijbalk-links (of waar het je uitkomt)

![submenu's dieren module](../../../en/images/menus/submenus-animals-module.png)

### Toewijzing Dierenmenu

Submenu's worden normaal gesproken alleen weergegeven op pagina's waar ze relevant zijn, in
dit geval op slechts drie pagina's. Vanuit het Menu Toewijzing tabblad:

- Stel het veld Moduletoewijzing in op `Alleen op de geselecteerde pagina's`. Dat
  onthult een hiërarchische lijst van alle items in alle menu's.
- Vink de vakjes aan bij Dieren, Katten en Honden.
- Vink de vakjes aan bij de rassen van katten en honden. Anders verdwijnt het
  submenudieren op pagina's over rassen.
- Zorg ervoor dat geen andere vakjes zijn aangevinkt.
- Opslaan & Sluiten

![submenu's dieren module menu toewijzing](../../../en/images/menus/submenus-animals-module-menu-assignment.png)

## Module voor het Submenu van Katten

Dit lijkt erg op:

- Selecteer **Inhoud**→**Site Modules**→**+** of selecteer `Nieuw` uit de
  Modules (Site) lijst.
- Selecteer de **Menu** module.
- Voer in het Modules: Menu bewerkformulier de volgende gegevens in:
  - Titel: Katten
  - Selecteer Menu: Dieren
  - Basisitem: Katten (dit is het bovenliggende menu-item)
  - Startniveau: 3
  - Eindniveau: Alles
  - Positie: zijbalk-links (of waar dan ook passend)

### Toewijzing van Kattenmenu

Vanuit de Menu Toewijzing

- Stel het veld Module Toewijzing in op `Alleen op de geselecteerde pagina's`. Dat onthult een hiërarchische lijst van alle items in alle menu's.
- Vink de vakjes aan bij Katten, Burmees en Russische Blauwe. Zorg ervoor dat geen andere vakjes zijn aangevinkt.
- Opslaan & Sluiten

## Hondensubmenu-module

Meer van hetzelfde...

## Menu Item Alias

Tot nu toe gaat alles goed! Maar er is geen link naar de dierenpagina vanuit het hoofdmenu of een van de andere sitenavigaties. De gemakkelijke manier om dit te verhelpen is met een Menu Item Alias. Voor dit voorbeeld wordt een invoer gemaakt in het menu bovenaan de pagina, getiteld Hoofdmenu Blog. Vanuit het beheerdersmenu:

- Selecteer **Menu's** → **Hoofdmenu Blog** (of welk sitenavigatie jouw voorkeur heeft).
- Selecteer de `Nieuw`-knop in de werkbalk.
- Vul het formulier Menu's: Item Bewerken in
  - Titel: Dieren
  - Alias: wezens - er is al een menu-item genaamd Dieren, dus je moet een andere alias gebruiken.
  - Menu-item Type: Menu Item Alias
  - Menu-item: Dieren - geselecteerd uit de lijst met bestaande menu-items.

![submenu dieren alias](../../../en/images/menus/submenus-animals-alias.png)

- Opslaan
- Volgorde - na opslaan kan de volgorde worden gewijzigd. In dit voorbeeld wordt het als eerste geplaatst.

## Controleer het resultaat

Bekijk de pagina's op je site. In dit voorbeeld zullen de meeste pagina's de submenu's niet aan de linkerzijde tonen. De link 'Dieren' in het bovenste menu zal de dierenpagina openen, vanwaar het mogelijk is om naar de pagina's Katten of Honden te navigeren:

![submenu doelen dieren honden](../../../en/images/menus/submenus-objectives-animals-dogs.png)

*Vertaald door openai.com*

