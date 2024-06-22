<!-- Filename: Planning_for_Mini-Migration_-_Joomla_3.10.x_to_4.x / Display title: Planning voor mini-migratie - Joomla 3.10.x naar 4.x -->

Gaan van Joomla 3.10.x naar 4.x wordt beschouwd als mini-migratie ofwel
een kleine migratie. Dit betekent dat Joomla core extensies upgraden met
een “één-klik update” maar extensies van derden zijn discutabel en
moeten één voor één bekeken worden.

## Introductie

Migraties zijn een goed moment om doelen opnieuw te stellen, op te
schonen en andere gebieden/elementen van uw site te ontwikkelen. Hoe
meer georganiseerd u bent in uw ideeën/gedachten/plannen hoe beter.
Plan, plan, plan. Het plannen maakt de uitvoering makkelijker.

Begin met plannen door zich de volgende vragen te stellen of de taken
uit te voeren die hieronder staan. U kunt meer items hebben afhankelijk
van de complexiteit van uw site. Helaas kunnen we niet ieder mogelijk
scenario weergeven. Ga naar het
<a href="https://forum.joomla.org/viewforum.php?f=812"
class="external text" target="_blank" rel="noreferrer noopener">Migreren
en upgraden naar Joomla 4.x Forum</a> voor hulp.

## De 3.10.x brug

Joomla 3.10.x is bedoeld om als brug te fungeren tussen de Joomla 3
levenscyclus en de Joomla 4 levenscyclus. Joomla 3.10.x zal allereerst
een release zijn die achterdeuren bevat voor de API wijzigingen in de
Joomla 4.x ontwikkeltak om de overgang naar de volgende hoofdrelease
voor de community te vergemakkelijken. Nieuw in Joomla 3.10.x is een
geweldige functie in de Joomla! update-component om u te helpen met het
mini-migratie proces: de  voor-update
controle.
Zodra uw website geüpdatet is naar 3.10, zal de voor-update controle u
toestaan de compatibiliteit te controleren met Joomla 4.0 van uw PHP en
SQL opties, instellingen, en de extensies die u gebruikt zolang de
extensie-ontwikkelaars de doelplatform tag gebruiken. Zie dedocumentatie voor meer informatie.

## Plannen van acties

Het volgende veronderstelt dat u uw Joomla 3.x site al bijgewerkt heeft
naar versie 3.10.x. Dit stelt u in staat te profiteren van de
voor-update controle als onderdeel van uw planning.

1.  Zorg dat uw website draait op 3.10.x.
2.  Beoordeel uw originele site doelstellingen. Migratie is een
    gelegenheid om zich te richten op uw doelstellingen of van richting
    te veranderen.
3.  Voldoet uw server aan de minimum <a
    href="https://www.joomla.org/about-joomla/technical-requirements.html"
    class="external text" target="_blank"
    rel="noreferrer noopener">technische vereisten</a> voor Joomla 4? Zo
    niet, dan moet u van hosting veranderen. Geen beter moment om van
    hosting te veranderen als tijdens een migratie.
4.  Welk soort ontwikkelomgeving gebruikt u? Een ontwikkelomgeving op
    een lokaal apparaat? Een sub-domein of submap op de server? Een
    nieuw server/hosting account als gevolg van technische
    specificaties?
5.  Maak een lijst met alle extensies van derden die gebruikt worden.
    Dit omvat componenten, modules, plugins, talen, en templates. U kunt
    ze kopiëren/plakken in een document ter referentie als u dat wil.
    Een stuk papier en een pen zijn voldoende. Neem ook mee of de
    extensie zwaar, gemiddeld, nauwelijks of helemaal niet gebruikt
    wordt.
6.  Stel vast of de extensies van derden waarop u vertrouwd klaar zijn
    voor de versie van Joomla waarnaar u migreert door de 'Volgende
    Joomla' optie te kiezen (als u op Joomla 3.10.x zit) in de Joomla
    update component en te controleren of ze compatibel zijn met
    Joomla 4. Voer de update naar 4.x niet uit, selecteer alleen maar
    'Volgende Joomla' in de Joomla update opties zodat de voor-update
    controle wordt getoond. Dit helpt je om een opsomming te krijgen van
    extensies die gebruikt worden en hun compatibiliteit. Het is niet
    een vervanging van het gebruik van Extensies → Beheren. Meer
    hierover in de Stap-voor-Stap en de documentatie van de  Voor-update
    controle
    component. Dit is eenvoudig om voorbereid te zijn op wat extensies
    van derden blijven, verdwijnen of vervangen worden.
7.  Stel vast of u echt al de extensies die u gebruikt nodig heeft. Is
    het zo dat Joomla 4 ingebouwde functies heeft die het gebruik van
    extensies van derden niet nodig maken?
8.  Kijk eens door uw categorieën en artikelen. Is er een grote
    schoonmaak nodig zodat u geen onnodige inhoud hoeft te migreren?
9.  En uw template? Als u uw template heeft gekocht van een derde, is er
    dan een 4.x uitvoering van? Wilt u het blijven gebruiken? Is er een
    upgrade pad gepubliceerd door de ontwikkeleaar? Is de nieuwe versie
    responsive? Is uw template een aangepast template? Of is het
    behoorlijk aangepast vanuit een template van derden? Het Joomla core
    template voor Joomla 3.x, **Protostar is NIET compatibel met Joomla
    4**. Na migratie verdwijnt het. Het gebruik van het Joomla core
    template voor Joomla 4.x, Cassiopeia kan een optie zijn. Kijk, voor
    een uitgebreid overzicht met template gebaseerde overwegingen, bij
     Template overwegingen tijdens de
    migratie.
10. Als u uw template inwisselt voor een nieuwe, heeft het dan nieuwe
    afbeeldingen nodig? Bijvoorbeeld, als uw huidige site een witte
    achtergrond heeft en uw logo en andere afbeeldingen zijn .jpg
    afbeeldingen met een witte achtergrond ziet het er niet mooi uit in
    een nieuw template met een gebroken witte of gekleurde achtergrond.
11. Als u uw siteontwerp of navigatie herontwerpt of aanpassingen maakt,
    heeft u dan verouderde pagina's die een verwijzing nodig hebben?
    Indien dat zo is, documenteer ze dan. Een spreadsheet is behulpzaam
    bij het documenteren van links die zullen veranderen.

<a
href="https://docs.joomla.org/Joomla_3.x_to_4.x_Step_by_Step_Migration"
id="content-button" class="button expand">Stap-voor-stap migreren van
Joomla 3.10 naar 4.x</a>
