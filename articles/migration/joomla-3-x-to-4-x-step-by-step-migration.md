<!-- Filename: Joomla_3.x_to_4.x_Step_by_Step_Migration / Display title: Stap-voor-stap migreren van Joomla 3.x naar 4.x -->

<img
src="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/25px-Stop_hand_nuvola.svg.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/4/41/Stop_hand_nuvola.svg.png/38px-Stop_hand_nuvola.svg.png 1.5x, https://docs.joomla.org/images/4/41/Stop_hand_nuvola.svg.png 2x"
data-file-width="40" data-file-height="40" width="25" height="25"
alt="Stop hand nuvola.svg.png" />Waarschuwing!

Deze handleiding gaat ervan uit dat u begint met Joomla 3.10.x. Als u op
een eerdere versie zit zorg er dan voor dat u eerst upgrade naar Joomla
3.10 voor naar Joomla 4 te gaan. Er is geen haast. Zorg dat al uw
extensies klaar zijn voor Joomla 4.x. Joomla 3.10.x wordt tot 16
augustus 2023 ondersteund.


Het volgende zijn stap-voor-stap instructies om uw 3.10.x website naar
Joomla! 4.x te migreren. Hoewel er honderden verschillende scenario's
zijn, geeft dit de te volgen basis-procedure. Zeer complexe migraties
zijn waarschijnlijk het gevolg van geïnstalleerde extensies van derden.
U wordt aangemoedigd contact te zoeken met de ontwikkelaars van
geïnstalleerde extensies van derden op uw Joomla website voor het door
hun voorgestelde pad voor het migreren van hun extensies.

## Introductie

De migratie van Joomla! 3.10.x naar 4.x wordt beschouwd als een
mini-migratie. Dit is zo omdat de Joomla core extensies zullen upgraden
met een “één-klik” upgrade via de Joomla! Update component in het
beheergedeelte van Joomla. Veel extensies van derden hebben ook een
één-klik upgrade. Sommigen niet. Bij iedere extensie moet gekeken worden
welk pad gevolgd moet worden om van 3.10 naar 4.x te gaan. Als dat nog
niet gedaan is, kan dit
Zelfonderzoek
en deze  Planning voor 3.10 naar 4.x
migratie
gelezen worden voor onderstaande stappen te volgen.
Joomla! core extensies zijn:

- Categorieën
- Artikelen
- Menu's
- Modules (core modules - niet van derden)
- Actielogs
- Advertenties
- Velden
- Inhoud historie
- Contactpersonen
- Berichten
- Nieuwsfeeds
- Verwijzingen
- Zoeken (ontkoppeld in 4.x. Bestaande 3.x sites migreren nog. We raden
  echter aan vanaf nu Slim zoeken te gebruiken. Zie de opmerkingen onder
  Beoordeel elke extensie)
- Slim zoeken
- Tags
- Weblinks (ontkoppeld maar uw site gebruikt het misschien nog en het
  migreert mee. Zie de opmerkingen onder Beoordeel elke extensie)

## Stap voor stap

### Zet een ontwikkellocatie op

1.  Zorg ervoor de nieuwste Joomla 3.10.x versie te gebruiken voor
    verder te gaan.
2.  Maak een backup van de live 3.10.x site. U kunt een aanbevolen
    hulpmiddel gebruiken (zie de *Aanbevolen hulpmiddelen* onderaan de
    pagina) of doe het handmatig.
    -  Backup basis voor een Joomla!
      website
    -  Wat zijn de best practices voor site
      backups?
3.  Zorg ervoor dat de omgeving voldoet aan de
    <a href="https://downloads.joomla.org/technical-requirements"
    class="external text" target="_blank"
    rel="noreferrer noopener">technische vereisten voor Joomla 4</a>
    voor verder te gaan.
4.  Maak een nieuwe database en gebruiker aan om de 3.10.x site naar te
    laden.
5.  Maak een testsite of werkomgeving aan om op te werken en restore de
    backup kopie van de 3.10.x site op een van de volgende plekken:
    - Een sub-domein.
    - Een sub-map.
    - Een lokaal device. Joomla heeft een gedetailleerde handleiding
      over het installeren van
      <a href="https://sourceforge.net/projects/xampp/" class="external text"
      target="_blank" rel="nofollow noreferrer noopener">XAMPP</a> op
      XAMPP. Echter
      <a href="https://www.wampserver.com/en/" class="external text"
      target="_blank" rel="nofollow noreferrer noopener">WAMP</a>,
      <a href="https://www.mamp.info/en/windows/" class="external text"
      target="_blank" rel="nofollow noreferrer noopener">MAMP</a>,
      <a href="https://sourceforge.net/projects/lampas/" class="external text"
      target="_blank" rel="nofollow noreferrer noopener">LAMP</a> zijn
      geschikte alternatieven.
    - Een nieuw hosting account op een tijdelijk domein in de root. (Als
      van host wordt gewijzigd tijdens het het migratieproces.)
      - Restoren van een site op een lokaal device. Zie  Joomla lokaal
        installeren
        en  Het instellen van het werkstation voor
        Joomla-ontwikkeling.
      - Restoren van een website met een hulpmiddel onderaan de pagina.
        (Lees de ontwikkelaars documentatie.)
6.  Op de test locatie, update de Joomla! 3.10.x versie naar de nieuwste
    release.
7.  Zorg ervoor dat bijgewerkt is naar de nieuwste database schema's
    voor de nieuwste 3.10.x versie door te gaan naar het
    **Extensies **→** Database** tabblad. Als het database schema niet
    bijgewerkt is zoals op de volgende afbeelding klik dan op de
    **Repareren** knop:<img
    src="https://docs.joomla.org/images/thumb/3/3c/J310-admin-extension-database-fix-nl.png/800px-J310-admin-extension-database-fix-nl.png"
    class="thumbborder" decoding="async"
    srcset="https://docs.joomla.org/images/thumb/3/3c/J310-admin-extension-database-fix-nl.png/1200px-J310-admin-extension-database-fix-nl.png 1.5x, https://docs.joomla.org/images/3/3c/J310-admin-extension-database-fix-nl.png 2x"
    data-file-width="1420" data-file-height="394" width="800" height="222"
    alt="J310-admin-extension-database-fix-nl.png" />
8.  Leeg prullenbak: Heeft u artikelen in de prullenbak? Indien dat zo
    is, verwijder ze dan (en eventuele media die eraan gekoppeld zijn en
    niet elders op de site gebruikt worden). Artikelen (categorieën en
    menu-items ook) die in de prullenbak achterblijven kunnen problemen
    veroorzaken bij het voltooien van een migratie zonder fouten.
9.  Test.
10. Maak opnieuw een back-up aan.

### Beoordeel elke extensie

In de
planning,
bepaalde u welke extensies van derden blijven of verdwijnen en hoe ze
migreren. Voor dit deel van de stap-voor-stap migratie gebruikt u twee
verschillende secties van de site uitgebreid; De pre-update-controle in

Componenten

 Voor-update controle.

1.  Gebruik de **Pre-update check**: om de Pre-update check te
    gebruiken, moet u de Joomla! Update component op Joomla 4 zetten.
    volg om dit te doen:
2.  Ga naar **Componenten **→** Joomla update**. (Het moet melden dat er
    geen updates beschikbaar zijn. Als dat niet zo is, update Joomla dan
    naar de nieuwste versie (moet 3.10.x zijn) en test. Maak dan nog een
    backup aan.) Klik op de Opties knop in de rechter bovenhoek.
3.  Selecteer *Volgende Joomla* uit de keuzelijst als Updatekanaal.<img
    src="https://docs.joomla.org/images/thumb/8/82/Migration_J3toJ4_update_channel-nl.png/800px-Migration_J3toJ4_update_channel-nl.png"
    class="thumbborder" decoding="async"
    srcset="https://docs.joomla.org/images/thumb/8/82/Migration_J3toJ4_update_channel-nl.png/1200px-Migration_J3toJ4_update_channel-nl.png 1.5x, https://docs.joomla.org/images/8/82/Migration_J3toJ4_update_channel-nl.png 2x"
    data-file-width="1261" data-file-height="646" width="800" height="410"
    alt="Migration J3toJ4 update channel-nl.png" />
4.  Klik op Opslaan & sluiten
5.  U ziet nu uw geïnstalleerde Joomla versie, de nieuwste Joomla!
    versie en de URL van het update pakket. Joomla toont opnieuw de
    vereisten voor Joomla 4. Als het aangeeft dat u een niet compatibel
    systeem of extensies heeft dan vermeld het dat hier. Neem een
    ogenblik de tijd deze pagina te bekijken.<img
    src="https://docs.joomla.org/images/thumb/b/b9/J310-admin-update_to_4-pre_update_check-nl.png/800px-J310-admin-update_to_4-pre_update_check-nl.png"
    class="thumbborder" decoding="async"
    srcset="https://docs.joomla.org/images/thumb/b/b9/J310-admin-update_to_4-pre_update_check-nl.png/1200px-J310-admin-update_to_4-pre_update_check-nl.png 1.5x, https://docs.joomla.org/images/b/b9/J310-admin-update_to_4-pre_update_check-nl.png 2x"
    data-file-width="1270" data-file-height="658" width="800" height="414"
    alt="J310-admin-update to 4-pre update check-nl.png" />
6.  Kijk bij de Voor-update controle en de Extensie Voor-update controle
    op het Voor-update controle tabblad van de Joomla update component.
    Als een extensie die niet in uw planning staat hier wordt opgenoemd
    , voeg hem dan toe aan uw lijst met extensies om te onderzoeken.
7.  Als u in het verleden gemigreerd bent van Joomla! 2.5 naar 3.x, dan
    kunnen er nog een aantal overgebleven extensies zijn die opgeschoond
    moeten worden. De volgenden zijn een aantal oudere 2.5 of 3.x
    extensies die gedeïnstalleerd moeten worden voor het updaten naar
    Joomla 4:
    - plg_content_geshi
    - Bluestork Administrator Template
    - Beez_20
    - Beez5
    - Atomic

    1.  Als het aankomt op templates, deïnstalleer dan alle core
        frontend en backend templates behalve Protostar en Beez3
        (frontend templates) en Isis of Hathor (administrator
        templates). **Let op: Protostar is NIET compatibel met Joomla
        4**. Na migratie verdwijnt het. U moet één template geselecteerd
        hebben als "standaard" en u kunt Protostar of Beez3 gebruiken.
        Protostar zal verdwijnen na migratie naar Joomla 4.x.
    2.  Als u andere bestanden tegenkomt die gedeïnstalleerd moeten
        worden, voeg ze dan toe aan deze pagina. Dit is een wiki,
        iedereen kan dus bijdragen aan de pagina. Alvast bij voorbaat
        bedankt voor je hulp.
8.  U zult de labels zien die aangeven of een extensies compatibel is of
    niet. Deze labels vertellen in principe het ware verhaal als ze NEE
    of JA aangeven. Als ze aangeven “Ontbrekende compatibiliteit tag”
    dan betekent het dat extensie ontwikkelaar geen tag hebben gebruikt
    in de extensie zodat we niet weten of het wel of niet compatibel is
    met Joomla 4. Neem contact op met de ontwikkelaar om het te
    controleren.
9.  **Update Extensies**: update iedere extensie die u op de website
    wilt behouden. In Joomla! 3.10.x kunt u gaan naar **Extensie
    Beheren **→** Updaten** en klik op **Vind updates** waarna een
    tooltip zichtbaar wordt in de Versie kolom, onder het Beheer
    tabblad, waar compatibiliteit informatie van het beheergedeelte
    verschijnt. Deze functionaliteit ondersteund alleen extensies die
    updaten via het Extensie beheer update tabblad. Als u extensies
    heeft geïnstalleerd die de Joomla extensie update niet gebruiken dan
    moeten ze handmatig beoordeeld worden zoals hieronder aangeven.
    Hetzelfde geld voor die extensies die een tooltip hebben. U moet nog
    steeds het type pakket en migratiepakket controleren bij de
    ontwikkelaar om te controleren hoe te upgraden/migreren.
10. Onderzoek en de installeer Extensies Extensies: ga naar **Extensies
    Beheren **→** Beheren**
11. Klik op de knop *Zoekmiddelen* om de filteropties te tonen
12. Selecteer pakket vanuit de *Selecteer type* uitklaplijst.<img
    src="https://docs.joomla.org/images/thumb/9/91/J310-admin-extension-manage-package-nl.png/800px-J310-admin-extension-manage-package-nl.png"
    decoding="async"
    srcset="https://docs.joomla.org/images/thumb/9/91/J310-admin-extension-manage-package-nl.png/1200px-J310-admin-extension-manage-package-nl.png 1.5x, https://docs.joomla.org/images/9/91/J310-admin-extension-manage-package-nl.png 2x"
    data-file-width="1405" data-file-height="684" width="800" height="389"
    alt="J310-admin-extension-manage-package-nl.png" />Er wordt
    aangeraden eerst Pakket te selecteren omdat als er iets in een
    pakket gedeïnstalleerd moet worden, modules, plugins of iets anders,
    dit in een pakket in één keer automatisch gebeurt.
13. Deïnstalleer elk pakket dat niet meer nodig is of niet naar Joomla 4
    migreert.
14. Herhaal dit proces door door het beheer-tabblad te gaan voor ieder
    type in de drop-down lijst: Component, Bestand, Taal, Bibliotheek,
    Module, Plugin en Template. Als de auteur Joomla! Project is, laat
    ze dan met rust. Slim zoeken is een Joomla core ondersteunde
    extensie hoewel het Auteur veld leeg kan zijn. Voor alle andere,
    zorg ervoor dat ze u ze deïnstalleert als ze niet gebruikt worden of
    niet compatiebel zijn met Joomla! 4.x. **NOTE!** U kunt een template
    dat Standaard is niet deïnstalleren . U moet een core ondersteund
    template selecteren zoals Beez3 of Protostar en dan het template
    deïnstalleren.
    *Denk hier ook aan:* **Protostar is niet compatibel met Joomla
    4.x**. Na migratie verdwijnt het. Het als standaard selecteren
    brengt u naar Joomla 4.x.
15. Noteer de versies van pakketten en componenten die momenteel
    aanwezig zijn en die je wilt behouden op je site. Je kunt ze
    kopiëren/plakken naar een document, als referentie.
16. Voor extensies die je wil houden, maar waar waarvoor je het
    Extensiebeheer niet gebruikt voor een update-via-een-klik,
    (**Extensies **→** Beheer **→** Update**) update alle extensies naar
    de nieuwste versie.
17. Let op, voor en tijdens het updaten, of extensies zowel een 3.10.x &
    4.x versie hebben in hetzelfde pakket. Als dat zo is, dan voldoen ze
    aan een "update-via-een-klik" Zo niet en 3.10 en 4.x verschillende
    pakketten hebben, moet het van geval tot geval bekeken worden. Ze
    behoren normaliter in een van de volgende scenario's:
    - De extensies hebben verschillende pakketten maar bij het upgraden
      naar 4.x detecteren dit ze automatisch en werken nog. Verzeker je
      ervan dat de ontwikkelaar dit bevestigd.
    - De extensie heeft verschillende pakketten die gedeïnstalleerd
      moeten worden in 3.10.x en dan geïnstalleerd worden in de Joomla
      4.x versie als de site gemigreerd is. Een voorbeeld hiervan kan
      een inhoud plugin zijn. Het is heel eenvoudig om hem in 3.10.x te
      de-installeren en opnieuw in 4.x te installeren.
    - Zie  Template
      overwegingen
      voor meer specifieke informatie over templates en [Converteren van
      een template uit een eerdere Joomla!
      versie](https://docs.joomla.org/J3.x:Converting_A_Previous_Joomla!_Version_Template "Special:MyLanguage/J3.x:Converting A Previous Joomla! Version Template")

#### Opmerkingen over Zoeken (com_search)

Zoeken (com_search) wordt ontkoppeld in Joomla 4.x. Zoeken (com_search)
migreert naar Joomla 4. Na migratie, moet hij geüpdatet worden naar de
Joomla 4.x versie via com_installer. Hij wordt nog steeds onderhouden,
maar meer zoals bij een extensie van derden door het ontvangen van
updates via com_installer. Aanbevolen wordt Slim zoeken in de toekomst
te gebruiken (com_finder). Zoeken blijft beschikbaar via
<a href="https://extensions.joomla.org/category/official-extensions/"
class="external free" target="_blank"
rel="noreferrer noopener">https://extensions.joomla.org/category/official-extensions/</a>.

#### Opmerkingen over Weblinks

Weblinks is ontkoppelt in Joomla 3.4. Als het gebruikt werd in een 2.5
site, dan zal het migratieproces dit herkennen en de Weblinks component
en gegevens migreren. Voor de migratie van 3.10.x naar 4.x geldt
hetzelfde. Het is beschibaar en wordt onderhouden in de JED via
<a href="https://extensions.joomla.org/category/official-extensions/"
class="external text" target="_blank"
rel="noreferrer noopener">Officiële extensies</a>.

#### Opmerkingen over verouderde Routering

Verouderde routering is niet beschikbaar in Joomla 4.x. Alleen Modern
zal beschikbaar zijn. Als de migratie wordt uitgevoerd, bij gebruik van
verouderde routering, dan zal het systeem het automatisch veranderen
naar Modern routeren. Er zal een verbroken link controle moeten worden
uitgevoerd op de site na het migreren naar Joomla 4.x en *voor live
wordt gegaan*.

### Naar Joomla! 4.x gaan

Ga, als de extensies van derden óf geüpdatet óf gedeïnstalleerd zijn
zodat alleen degene compatibel met Joomla! 4 over zijn in de
installatie, door met de volgende stappen:

1.  Ga naar het **Systeem **→** Algemene instellingen **→** Server
    tabblad** en zet Foutrapportage van Standaard van het systeem naar
    Maximum. Zorg er voor te drukken op Opslaan & sluiten. <img
    src="https://docs.joomla.org/images/thumb/6/6e/J310-system-global-config-server-tab-nl.png/500px-J310-system-global-config-server-tab-nl.png"
    class="thumbborder" decoding="async"
    srcset="https://docs.joomla.org/images/thumb/6/6e/J310-system-global-config-server-tab-nl.png/750px-J310-system-global-config-server-tab-nl.png 1.5x, https://docs.joomla.org/images/6/6e/J310-system-global-config-server-tab-nl.png 2x"
    data-file-width="764" data-file-height="466" width="500" height="305"
    alt="J310-system-global-config-server-tab-nl.png" />
2.  Maak nog een back-up aan.
3.  Ga naar **Components **→** Joomla Update**. (Het zou moeten zeggen
    dat er geen updates beschikbaar zijn. Als dat niet zo is, update
    Joomla naar de nieuwste versie en test. Maak dan weer een back-up
    aan.) Klik op de Opties knop rechts boven.
4.  Selecteer *Volgende Joomla* in de uitklaplijst van het
    Updatekanaal.<img
    src="https://docs.joomla.org/images/thumb/8/88/J310-component-joomla-update-select-support-nl.png/500px-J310-component-joomla-update-select-support-nl.png"
    class="thumbborder" decoding="async"
    srcset="https://docs.joomla.org/images/8/88/J310-component-joomla-update-select-support-nl.png 1.5x"
    data-file-width="697" data-file-height="429" width="500" height="308"
    alt="J310-component-joomla-update-select-support-nl.png" />
5.  Klik op Opslaan & sluiten
6.  U ziet nu uw geïnstalleerde Joomla versie, de nieuwste Joomla!
    versie en de URL van het update pakket. Joomla toont opnieuw de
    vereisten voor Joomla 4. Als het aangeeft dat u een niet compatibel
    systeem of extensies heeft dan vermeld het dat hier. Neem een
    ogenblik de tijd deze pagina te bekijken.<img
    src="https://docs.joomla.org/images/thumb/c/c0/J310-to-j4-dev-update-found-nl.png/800px-J310-to-j4-dev-update-found-nl.png"
    class="thumbborder" decoding="async"
    srcset="https://docs.joomla.org/images/thumb/c/c0/J310-to-j4-dev-update-found-nl.png/1200px-J310-to-j4-dev-update-found-nl.png 1.5x, https://docs.joomla.org/images/c/c0/J310-to-j4-dev-update-found-nl.png 2x"
    data-file-width="1384" data-file-height="882" width="800" height="510"
    alt="J310-to-j4-dev-update-found-nl.png" />
7.  Ga, als de update niet wordt getoond naar **Extensie **→** Updaten**
    en druk op Cache opschonen in de werkbalk. Nu zou de update naar
    Joomla! 4 zichtbaar moeten worden.
8.  Kruis je vingers en zorg dat de back-up beschikbaar is in het geval
    dat.......
9.  Klik op de 'Installeer de update' knop.
10. Zet thee terwijl de statusbalk volledig groen wordt. De tijd dat dit
    kost hangt af van de site, Internet verbinding en server snelheid.
    Het proces duurt ongeveer twee minuten. Als de update klaar is wordt
    je waarschijnlijk uitgelogd uit het beergedeelte. Log opnieuw in.
    Tweemaal.
11. Als alles goed gaat, heb je een volledig nieuwe weergave in het
    beheergedeelte.<img
    src="https://docs.joomla.org/images/thumb/8/8e/J4-administrator-overview-nl.png/800px-J4-administrator-overview-nl.png"
    class="thumbborder" decoding="async"
    srcset="https://docs.joomla.org/images/thumb/8/8e/J4-administrator-overview-nl.png/1200px-J4-administrator-overview-nl.png 1.5x, https://docs.joomla.org/images/8/8e/J4-administrator-overview-nl.png 2x"
    data-file-width="1386" data-file-height="643" width="800" height="371"
    alt="J4-administrator-overview-nl.png" />
12. Ga naar **Systeem **→** Onderhoud **→** Database** en klik op
    *Repareer* als er fouten zichtbaar worden.
13. Kijk bij **Systeem **→** Installeren **→** Ontdekken** of er
    extensies zijn om te installeren. (Er zouden er geen moeten zijn!)
14. Ga naar de website en kijk of hij zichtbaar wordt, zelfs als het
    niet het juiste template is. Ga verder als hij zichtbaar wordt. Zo
    niet, kijk bij  Veel voorkomende fouten tijdens
    migratie.
15. Maak een back-up.
16. Installeer het nieuwe template of andere extensies als die
    geïnstalleerd moeten worden. Maak vaak een back-up aan.
17. Stel ze in. Maak vaak een back-up aan.
18. Draai een controle op verbroken links en repareer ze.
19. Test alles. Maak vaak een back-up aan.
20. Zet, als alles naar verwachting werkt, de foutopsporing terug op
    Systeem standaard (**Systeem **→** Algemene
    instellingen **→** Server tabblad**). Druk op Opslaan & sluiten.

### Live gaan met je Joomla! 4.x site

1.  Als je klaar bent om live te gaan, back-up de 3.10 site voor de
    laatste keer. Restore hem in een sub-map of sub-domein indien
    gewenst.
2.  Back-up de Joomla! 4.x site en verplaats of restore de Joomla! 4.x
    site naar de root (of wijzig nameservers als op een tijdelijk domein
    bij een nieuwe hosting wordt ontwikkeld).
3.  Test opnieuw.
4.  ALS er in het verleden veiligheids wijzigingen aan zijn gebracht aan
    het .htaccess bestand, moeten er misschien regel(s) aangepast worden
    bij de update naar de volgende versie van Joomla 4. Ga naar
    <a href="https://docs.joomla.org/Htaccess_changes_after_joomla4.0.4"
    class="external text" target="_blank" rel="noreferrer noopener">Htaccess
    wijzigingen na joomla4.0.4</a> om te bepalen of het bestand al dan
    niet moet worden aangepast.
5.  Verwijder de Joomla! 3.10 site binnen een paar dagen van de server
    behalve als het *robots.txt* bestand is aangepast om zoekmachines te
    blokkeren.
6.  Verwijder alle ontwikkelsites waarmee gewerkt is of houdt ze
    up-to-date om hackpogingen op uw server af te weren.

Als u gegevens heeft gewijzigd op uw 3.10 site tijdens het migreren naar
4.x, dan wilt u die gegevens verplaatsen naar de 4.x site voor live te
gaan. U kunt dit handmatig doen (zorg er voor dezelfde gebruiker ID's te
houden - op volgorde) of door een <a
href="https://extensions.joomla.org/category/migration-a-conversion/data-import-a-export"
class="external text" target="_blank" rel="noreferrer noopener">transfer
hulpmiddel/extensie van derden</a> te gebruiken.

## Aanbevolen hulpmiddelen

- <a
  href="http://extensions.joomla.org/extensions/access-a-security/site-security/backup/1606"
  class="external text" target="_blank" rel="noreferrer noopener">Akeeba
  Backup</a> is erg populair voor back-up en restore. Voor meer
  <a href="https://extensions.joomla.org/tags/backup/"
  class="external text" target="_blank" rel="noreferrer noopener">back-up
  hulpmiddelen</a>.

## Verwante informatie
