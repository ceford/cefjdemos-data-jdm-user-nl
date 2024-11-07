<!-- Filename: Joomla_3.x_to_4.x_Step_by_Step_Migration / Display title: Joomla 3 naar 4 Stap voor Stap  -->

## Inleiding

**Waarschuwing:** Deze gids gaat ervan uit dat je begint met Joomla 3.10.x. Als je een eerdere versie gebruikt, zorg er dan voor dat je eerst upgrade naar Joomla 3.10 voordat je doorgaat naar Joomla 4. Er is geen haast. Zorg ervoor dat al je extensies klaar zijn voor Joomla 4.x. Joomla 3.10.x wordt ondersteund tot 16 augustus 2023.

De volgende instructies zijn stap voor stap handleidingen om een 3.10.x site te migreren naar Joomla! 4.x. Hoewel er honderden verschillende scenario's zijn, geeft dit je de basisprocedure om te volgen. Zeer complexe migraties zullen waarschijnlijk het gevolg zijn van geïnstalleerde externe extensies. Je wordt aangemoedigd om contact op te nemen met de ontwikkelaars van externe extensies die op je Joomla-site zijn geïnstalleerd voor hun voorgestelde pad om hun extensies te migreren.

## Stap voor Stap

### Een Ontwikkellocatie Opzetten

1.  Zorg ervoor dat je de nieuwste Joomla 3.10.x versie draait voordat 
    je verdergaat.
2.  Maak een back-up van je live 3.10.x site. Je kunt een aangeraden 
    tool gebruiken (zie de *Aangeraden Tools* onderaan de pagina) of je 
    kunt dit handmatig doen.
    -  [Back-up Basisprincipes voor een Joomla! Website](https://docs.joomla.org/Special:MyLanguage/Backup_Basics_for_a_Joomla!_Web_Site)
    -  [Wat zijn de beste praktijken voor site-back-ups?](https://docs.joomla.org/Special:MyLanguage/What_are_the_best_practices_for_site_backups%3F)
3.  Zorg ervoor dat je omgeving voldoet aan de 
    [technische vereisten voor Joomla 4](https://downloads.joomla.org/technical-requirements) voordat je verdergaat.
4.  Maak een nieuwe database en nieuwe gebruiker om je 3.10.x site naar 
    te herstellen.
5.  Maak een testsite of bouwplaats om in te werken en herstel de 
    back-up kopie van je 3.10.x site op een van de volgende plaatsen:
    - Een subdomein.
    - Een subdirectory.
    - Een lokaal apparaat. Joomla heeft een gedetailleerde tutorial over 
      het installeren van XAMPP. Echter, [WAMP](https://www.wampserver.com/en/),
      [MAMP](https://www.mamp.info/en/windows/) en
      [LAMP](https://sourceforge.net/projects/lampas/) zijn alle geschikte 
      alternatieven.
    - Een nieuw hostingaccount op een tijdelijk domein in de root. (Als je 
      de host wil veranderen tijdens het migreren.)
      - Een site herstellen op een lokaal apparaat.
        Zie [Joomla lokaal installeren](https://docs.joomla.org/Special:MyLanguage/Installing_Joomla_locally) 
        en [Je werkstation instellen voor Joomla-ontwikkeling](https://docs.joomla.org/Special:MyLanguage/Setting_up_your_workstation_for_Joomla_development).
      - Een site herstellen met een tool vermeld onderaan de pagina. 
        (Bekijk de ontwikkelaarsdocumentatie.)
6.  Update je Joomla! 3.10.x instance naar de nieuwste onderhoudsrelease 
    op je testlocatie.
7.  Zorg ervoor dat je het nieuwste database-schema hebt bijgewerkt naar 
    de nieuwste versie van 3.10.x door naar **Extensiebeheerder → Database** tab te gaan. Als je schema niet 
    up-to-date is zoals in de volgende afbeelding, klik dan op de **Herstellen** knop:<br> 
    ![joomla 3 extensies database](../../../en/images/migration/admin-extension-database-fix.png)
8.  Leeg de prullenbak: Heb je artikelen in de prullenbak? Zo ja, verwijder 
    ze (en alle toepasselijke media die mogelijk aan hen gekoppeld zijn als 
    ze elders op de site niet worden gebruikt). Artikelen (categorieën en 
    menu-items ook) die in de prullenbak zijn achtergelaten kunnen problemen 
    veroorzaken bij het migreren zonder fouten.
9.  Test.
10. Nogmaals een back-up maken.

### Beoordeel Elke Extensie

Tijdens je planning heb je bepaald welke third-party extensies blijven of 
weggaan en hoe ze migreren. Voor dit gedeelte van de Stap voor Stap, gebruik je 
twee verschillende gedeelten van de site intensief: de *Pre-Update Check* in 
**Componenten → Joomla! Update** en **Extensies → Beheer → Beheer**. Je gaat alle 
extensies bekijken die op je site zijn geïnstalleerd. Je bepaalt of ze 
moeten worden bijgewerkt naar de nieuwste versie of verwijderd. Meer details in 
[Pre-Update Check](https://docs.joomla.org/Special:MyLanguage/:Pre-Update_Check).

1.  Gebruikmakend van de **Pre-Update Check** om de Pre-Update Check te 
    gebruiken, moet je de Joomla! Update component instellen op Joomla 4. Volg hiervoor:
2.  Ga naar **Componenten → Joomla Update**. Het zou moeten zeggen dat er 
    geen updates zijn gevonden. Als dat niet het geval is, update Joomla 
    naar de laatste versie (moet 3.10.x zijn) en test. Maak dan nog een back-up. 
    Klik op de Opties knop in de rechterbovenhoek.
3.  Selecteer *Joomla Volgende* in de vervolgkeuzelijst voor Update Kanaal.<br> 
    ![update opties kanaal selectie](../../../en/images/migration/update-options-channel.png)
4.  Klik op **Opslaan & Sluiten**
5.  Je zult dan je Geïnstalleerde Joomla Versie zien, de laatste Joomla! 
     versie en de URL voor het updatepakket. Joomla laat je opnieuw 
     de vereisten zien voor Joomla 4. Als het aangeeft dat je een 
     incompatibel systeem of extensies hebt, zal het je hier vertellen. Neem 
     een moment om deze pagina te bekijken.<br> 
    ![update naar 4 pre update controle](../../../en/images/migration/update-to-4-pre-update-check.png)
    <div class="alert alert-warning"><strong>Let op:</strong> Update nu 
    NIET naar Joomla! 4. Dit is alleen om je third-party extensies 
    voor te bereiden en de site compatibel te maken met Joomla! 4.</div>
6.  Kijk naar de Pre-Update Check en de Pre-Update Check van de Extensie 
    in het Pre-Update Check tabblad van de Joomla Update component. Als 
    er ergens een extensie die niet in je planning staat, hier wordt vermeld, 
    voeg hem dan toe aan je lijst van extensies om te onderzoeken.
7.  Als je in het verleden van Joomla! 2.5 naar 3.x bent gemigreerd, zijn 
    er mogelijk enkele overgebleven extensies die moeten worden opgeruimd. 
    De volgende zijn oudere 2.5 of 3.x extensies die moeten worden verwijderd 
    voordat je naar Joomla 4 bijwerkt:
    - plg_content_geshi
    - Bluestork Beheerderssjabloon
    - Beez_20
    - Beez5
    - Atomic
    1.  Als het gaat om sjablonen, verwijder dan alle kern frontend- of 
        backend-sjablonen behalve Protostar en Beez3 (frontend sjablonen) 
        en Isis of Hathor (beheerderssjablonen). **OPMERKING: Protostar is 
        NIET compatibel met Joomla 4**. Bij migratie zal het verdwijnen. 
        Je moet één sjabloon als *standaard* hebben geselecteerd en je kunt 
        Protostar of Beez3 gebruiken. Protostar verdwijnt bij migratie naar 
        Joomla 4.x.
    2.  Als je andere bestanden tegenkomt die moeten worden verwijderd, 
        voeg ze dan toe aan deze pagina. Dit is een wiki, dus iedereen kan 
        bijdragen aan de pagina. Bij voorbaat dank voor je bijdrage.
8.  Je zult de labels opmerken voor of een extensie compatibel is of niet. 
    Deze labels vertellen over het algemeen een waar verhaal als ze zeggen Nee of Ja. 
    Als ze zeggen *Ontbreken Compatibiliteitslabel* betekent het dat de 
    extensieontwikkelaar geen label in hun extensie gebruikte, dus we weten niet 
    of het wel of niet compatibel is met Joomla 4. Praat met de ontwikkelaar om te 
    verifiëren.
9.  **Extensies bijwerken:** update alle extensies die je in je website 
    wilt behouden. In Joomla! 3.10.x kun je gaan naar **Extensiebeheerder → Tabblad Update** en 
    klik **Zoek Updates** wat een tooltip zal toevoegen in de Versie kolom, in de 
    Tabblad Beheren, die enkele compatibiliteitsinformatie van de back-end geeft. 
    Deze functionaliteit ondersteunt alleen extensies die bijwerken via het 
    Extensie Beheer Update tabblad. Als je extensies hebt geïnstalleerd die de 
    Joomla extensie-update niet gebruiken, moeten ze handmatig worden beoordeeld 
    zoals hieronder gedetailleerd staat. Hetzelfde geldt voor die extensies die 
    een tooltip hebben. Je moet nog steeds het type pakket en migratiepad met de 
    extensieontwikkelaar controleren om te verifiëren hoe te upgraden/migreren.
10. Onderzoek en Verwijder Extensies: ga naar **Extensiebeheerder → Beheer**.
11. Klik op de Knop *Zoek Hulpmiddelen* om de filteropties weer te geven.
12. Selecteer Pakket uit de vervolgkeuzelijst *Selecteer Type*.<br> 
    ![extensies beheerpagina](../../../en/images/migration/extensions-manage.png)
    <div class="alert alert-info">Het selecteren van Pakket 
    eerst wordt aanbevolen, omdat als er iets is dat je moet verwijderen 
    in een pakket, het automatisch de bijbehorende Modules, Plug-ins of 
    iets anders in het pakket in één keer zal verwijderen.</div>
13. Verwijder alle Pakketten die niet langer nodig zijn of niet 
    zullen migreren naar Joomla 4.
14. Herhaal dit proces door het Tabblad Beheren door te nemen voor 
    alle Typen in de vervolgkeuzelijst: Component, Bestand, Taal, Bibliotheek, 
    Module, Plug-in en Sjabloon. Als de Auteur zegt Joomla! Project, 
    laat die extensies dan met rust. Voor alle anderen, zorg ervoor dat 
    je degene die niet worden gebruikt of niet compatibel zijn met 
    Joomla!  4.x verwijdert. 
    <div class="alert alert-danger"><strong>OPMERKING!</strong> 
    Je zult geen sjabloon kunnen verwijderen die als standaard is ingesteld. 
    Je moet een Core ondersteund sjabloon selecteren zoals Beez3 of Protostar 
    en dan de sjabloon verwijderen als je dat moet doen.
    <em>Een andere herinnering:</em> <strong>Protostar is niet 
    compatibel met Joomla 4</strong>. Bij migratie zal het verdwijnen. 
    Het selecteren ervan als standaard brengt je simpelweg naar Joomla 4.x.</div>
15. Maak een notitie van de versies van Pakketten en Componenten die 
    je momenteel gebruikt en op je site wilt behouden. Je kunt ze kopiëren en 
    plakken in een document voor referentie.
16. Voor alle extensies die je behoudt maar niet de Extensiebeheerder gebruiken 
    om met één klik bij te werken (**Extensies → Beheer → Update**) update alle 
    extensies naar de nieuwste versies.
17. Voordat en terwijl je bijwerkt, noteer of de extensies zowel 3.10.x als 
    4.x versies in hetzelfde pakket hebben. Als dat zo is, zullen ze prima zijn 
    om met één klik te updaten. Zo niet, en 3.10 en 4.x hebben verschillende 
    pakketten, dan moet je ze geval per geval bekijken. Meestal vallen ze in een 
    van de volgende scenario's:
    - De extensie heeft aparte pakketten, maar bij het upgraden naar 4.x, 
      detecteren ze dit automatisch en werken ze nog steeds. Zorg ervoor 
      dat de ontwikkelaar dit bevestigt.
    - De extensie heeft aparte pakketten die moeten worden verwijderd in 3.10.x 
      en vervolgens geïnstalleerd met de Joomla 4.x versie zodra de site is 
      gemigreerd. Een voorbeeld hiervan kan een content plug-in zijn. Het is erg 
      eenvoudig om het in 3.10.x te verwijderen en vervolgens opnieuw te 
      installeren in 4.x.
    - Zie [Sjabloon Overwegingen](https://docs.joomla.org/Special:MyLanguage/Template_Considerations_During_Migration)
      voor meer specifieke informatie over sjablonen en 
      [Converting a Previous Joomla! Version Template](https://docs.joomla.org/J3.x:Converting_A_Previous_Joomla!_Version_Template)

#### Aantekeningen over Zoeken (com_search)

Zoeken (com_search) zal worden ontkoppeld in Joomla 4.x. Zoeken (com_search) 
zal migreren naar Joomla 4. Na migratie moet je het bijwerken naar de Joomla 
4.x versie via com_installer. Het zal worden onderhouden, maar meer op dezelfde 
manier als een third-party extensie door updates te ontvangen via 
com_installer. 
Het wordt aanbevolen om vanaf nu Slim Zoeken (com_finder) te gebruiken. Zoeken 
is nog steeds beschikbaar in de [Joomla Extensie Directory](https://extensions.joomla.org/category/official-extensions/).

#### Aantekeningen over Webkoppelingen

Webkoppelingen werden ontkoppeld in Joomla 3.4.als het in gebruik was op een 2.5 
site, zou het migratieproces dit noteren en de Webkoppelingen component en gegevens 
migreren. Voor de migratie van 3.10.x naar 4.x zal het hetzelfde zijn. Het is 
nog steeds beschikbaar en wordt onderhouden op de JED bij [Officiële Extensies](https://extensions.joomla.org/category/official-extensions).

#### Aantekeningen over Legacy-Routes

Legacy-routes zullen niet beschikbaar zijn in Joomla 4.x. Alleen Modern zal 
beschikbaar zijn. Wanneer je de migratie doet, als je Legacy-routes gebruikt, 
zal het systeem deze automatisch veranderen in Modern-routes. Je wilt je website 
controleren op verbroken links na de migratie naar Joomla 4.x en *voordat je 
live gaat*.

### Overstappen naar Joomla! 4.x

Zodra je je third-party extensies hebt bijgewerkt of verwijderd zodat alleen 
diegenen die compatibel zijn met Joomla! 4 in je installatie blijven, ga dan verder 
met de volgende stappen:

1.  Ga naar **Systeem → Algemene Configuratie → Server tab** en 
    verander Foutenrapportage van Systeem Default naar Maximum. Zorg ervoor 
    dat je Opslaan & Sluiten.<br> 
    ![systeem algemene configuratie server tabblad](../../../en/images/migration/system-global-configuration-server-tab.png)
2.  Maak nog een back-up.
3.  Ga naar **Componenten → Joomla Update**. (Het zou moeten zeggen dat er 
    geen updates zijn gevonden. Als dat niet zo is, update Joomla naar de 
    nieuwste versie en test. Maak dan nog een back-up.) Klik op de Opties knop 
    in de rechterbovenhoek.
4.  Selecteer *Joomla Volgende* uit de vervolgkeuzelijst voor Update Kanaal.<br> 
    ![component joomla werkbij selecteer update kanaal](../../../en/images/migration/update-select-channel.png)
5.  Klik op **Opslaan & Sluiten**.
6.  Je zult dan je Geïnstalleerde Joomla Versie zien, de Laatste Joomla! 
    versie en de URL voor het updatepakket. Joomla laat je nogmaals 
    de vereisten zien voor Joomla 4. Als het aangeeft dat je een 
    incompatibel systeem of extensies hebt, zal het je hier vertellen. 
    Neem een moment om deze pagina te bekijken.<br> 
    ![e update controle voor joomla 4](../../../en/images/migration/update-check.png)
7.  Als de update niet verschijnt, ga naar **Extensiebeheerder → Update** en 
    druk op Cache Wisselen uit de werkbalk. Nu zou de update naar Joomla! 4 
    moeten verschijnen.
8.  Steek je vingers over elkaar, en zorg ervoor dat je die back-up beschikbaar 
    hebt voor het geval dat.
9.  Klik op de Installeer de Update knop.
10. Maak thee terwijl de voortgangsbalk volledig groen laad. Hoe lang dit duurt, 
    is afhankelijk van je site, internetverbinding en server snelheid. Het proces 
    duurt ongeveer twee minuten. Wanneer de update klaar is, word je waarschijnlijk 
    uitgelogd van de Beheerder. Log opnieuw in. Twee keer.
11. Als alles goed gaat, krijg je een totaal nieuwe look van het back-end 
    beheerderspaneel.<br> 
    ![joomla 4 of 5 start dashboard](../../../en/images/migration/j4-home-dashboard.png)
12. Ga naar **Systeem → Onderhoud → Database** en klik op *Herstellen* als 
    er fouten verschijnen.
13. In **Systeem → Installeren → Ontdekken** kijk of er extensies te installeren 
     zijn. (Dit zou er niet moeten zijn!)
14. Ga naar de voorkant van je site en kijk of deze verschijnt, zelfs als het niet 
    de juiste sjabloon is. Als het doet, vervolg. Zo niet, zie veelvoorkomende 
    fouten tijdens migratie.
15. Maak een back-up.
16. Installeer je nieuwe sjabloon of andere extensies als je die te installeren 
    hebt. Vaak back-uppen.
17. Configureer ze. Vaak back-uppen.
18. Run een gebroken link checker en herstel verbroken links.
19. Test alles. Vaak back-uppen.
20. Als alles werkt zoals verwacht, zet je Foutenrapportage terug naar Systeem 
    Default (**Systeem → Algemene Configuratie → Server tabblad**). Zorg ervoor dat 
    je **Opslaan & Sluiten**.

### Live gaan met je Joomla! 4.x Site

1.  Wanneer je klaar bent om live te gaan, maak je een back-up van je 3.10 site 
    voor de laatste keer. Herstel het in een subdirectory of subdomein als je dat 
    wilt.
2.  Maak een back-up van je Joomla! 4.x site en verplaats of herstel je Joomla! 
    4.x site naar de root (of wijzig de naamservers als je aan het bouwen was op 
    een tijdelijk domein bij een nieuw hostingaccount root).
3.  Test nogmaals.
4.  ALS je beveiligingswijzigingen hebt aangebracht aan het .htaccess bestand 
    in het verleden, moet je mogelijk een regel (of regels) daarin veranderen 
    om naar de volgende versie van Joomla 4 te updaten. Ga naar 
    [Htaccess wijzigingen na Joomla 4](https://docs.joomla.org/Htaccess_changes_after_joomla4.0.4) 
    om te bepalen of je je bestand moet wijzigen of niet.
5.  Verwijder de Joomla! 3.10 site van de server binnen een paar dagen 
    tenzij je je *robots.txt* bestand hebt bewerkt om de zoekmachine 
    crawlers te blokkeren.
6.  Verwijder alle ontwikkelsites waarmee je hebt gewerkt of houd ze up-to-date 
    als ze een actuele versie draaien om hackpogingen op je server af te weren.

Als er gegevens zijn gewijzigd op de 3.10 site terwijl je migreerde naar 4.x, 
wil je die gegevens verplaatsen naar de 4.x site voordat je live gaat. Je kunt 
dit handmatig doen (zorg ervoor dat je dezelfde gebruikers-ID's behoudt - ga in 
volgorde) of door een [third-party extensie](https://extensions.joomla.org/category/migration-a-conversion/data-import-a-export%20transfer%20tool/third-party%20extension/) te 
gebruiken.

## Voorgestelde Hulpmiddelen

- [Akeeba Backup](http://extensions.joomla.org/extensions/access-a-security/site-security/backup/1606)
  is erg populair voor back-up en herstel.
- Meer [back-uptools](https://extensions.joomla.org/tags/backup/).

*Vertaald door openai.com*

