<!-- Filename: J4.x:Language_Overrides / Display title: Taaloverrides  -->

## Locaties van Taalbestanden

De meeste Joomla!-taalbestanden bevinden zich in taalmapjes, één in de site-root en een andere in de beheerdermap. Elke taal heeft zijn eigen submap gebaseerd op de RFC3066-standaard taalcodes. Elke extensie slaat zijn vertalingen op met een naam afgeleid van de extensienaam. Enkele voorbeelden:

    siteroot/language/en-GB/com_content.ini
    siteroot/administrator/language/en-GB/com_content.ini
    siteroot/administrator/language/en-GB/com_content.sys.ini

De bestanden bevatten regels die bestaan uit een sleutel en de bijbehorende vertaling:

    COM_CONTENT="Artikelen"
    COM_CONTENT_ADD_NEW_MENU_ITEM="Nieuw Menu-item"
    COM_CONTENT_ARTICLE_CONTENT="Inhoud"
    COM_CONTENT_ARTICLES_TABLE_CAPTION="Tabel van Artikelen"
    COM_CONTENT_ARTICLES_TITLE="Artikelen"

De Joomla PHP code gebruikt de sleutel. Deze wordt tijdens runtime vervangen door de tekstvertaling. Het .ini-bestand bevat vertalingen die door de extensie worden gebruikt. De sys.ini-bestanden bevatten vertalingen die door Joomla worden gebruikt om de extensie te beheren. Er kunnen honderden regels in een taalbestand staan.

Derde-partij extensies worden geadviseerd hun taalbestanden op te slaan in taalmapjes binnen de extensie. Daar zijn ze veilig tegen verwijdering mocht een beheerder besluiten een taal te deïnstellen. Voorbeeld:

    siteroot/components/com_countrybase/language/en-GB/com_countrybase.ini
    siteroot/administrator/components/com_countrybase/language/en-GB/com_countrybase.ini
    siteroot/administrator/components/com_countrybase/language/en-GB/com_countrybase.sys.ini

**Bewerk nooit een Joomla!-kern of derde partij taalbestand! Eventuele wijzigingen die u aanbrengt gaan verloren bij de volgende update. Als u de formulering van een taalitem wilt wijzigen, gebruik dan de formele Taaloverschrijving-component.**

Taaloverschrijvingen zijn jouw vervangingen voor kern of extensie taal-keyvertalingen. Dit zijn individuele vertalingen, één of twee, geen heel bestand! De taaloverschrijvingen voor een gegeven taal worden allemaal opgeslagen in één bestand:

    siteroot/language/overrides/en-GB.override.ini
    siteroot/language/overrides/fr-FR.override.ini
    siteroot/language/overrides/de-DE.override.ini

    siteroot/administrator/language/overrides/en-GB.override.ini
    siteroot/administrator/language/overrides/fr-FR.override.ini
    siteroot/administrator/language/overrides/de-DE.override.ini

### Laadvolgorde van Talen

Bij elke paginalading worden eerst de en-GB-taalvertalingen geladen. Dit zorgt ervoor dat er geen sleutels door sitegebruikers worden gezien. Als een andere taal in gebruik is, worden de vertalingen voor die taal vervolgens geladen, waarbij de en-GB-vertalingen worden vervangen. Andere talen lopen vaak achter op en-GB in het maken van vertalingen, dus gebruikers kunnen af en toe woorden of zinnen in het Engels zien tussen die van hun eigen taal.

Ten slotte worden de vertalingen geladen vanuit het taaloverschrijvingsbestand. Dit stelt de site in staat om alternatieve woorden of zinnen te gebruiken die passen bij lokale omstandigheden.

## Taaloverschrijvingen

Soms wil je een enkele vertaald taalitem vervangen door iets dat beter past bij lokale omstandigheden. Een veelvoorkomend geval is wanneer je een sjabloonoverschrijving of -indeling maakt en wat inhoud wilt toevoegen die gebruik maakt van een nieuwe taalsleutel. Het volgende voorbeeld illustreert een situatie waarin wat tekst is toegevoegd aan de uitlogindeling van de loginmodule, zoals beschreven in het artikel over Sjabloonindelingen. De alternatieve indeling heeft deze code:

```html
<p class="text-center">
Uw sessie verloopt om <br><?php echo $endTime; ?>
</p>
```

Voor een meertalige site met Engels, Frans en Duits moet de code worden aangepast:

```html
<p class="text-center">
<?php echo Text::_('TPL_CASSIOPEIA_MOD_LOGIN_SESSION_EXPIRES_AT')?><br><?php echo $endTime; ?>
</p>
```

Let op: als je de Sjabloonindeling tutorial hebt gevolgd, heb je mogelijk al een sleutel TPL_CASSIOPEIA_MOD_LOGIN_LAYOUT_EXPIRES die vertaald wordt als Verloopt. Maar die wordt gebruikt in siteroot/administrator/language/overrides.

De nieuwe sleutel kan nu in elke taal worden vertaald. De vertalingen worden opgeslagen in siteroot/language/overrides.

- Selecteer **Systeem **→** Beheer paneel **→** Taaloverschrijvingen**
- Selecteer je taal en de sitelocatie.
- Klik op de **Nieuw** knop en vul het formulier in. In dit voorbeeld is de taalsleutel **TPL_CASSIOPEIA_MOD_LOGIN_SESSION_EXPIRES_AT** en de tekst kan zijn **Uw sessie verloopt om**
- Sla het formulier op en sluit.
- Herhaal het vertaalproces voor elke taal.

![talen bewerk overschrijvingsformulier](../../../en/images/languages/language-overrides-edit.png)

Controleer ten slotte of de vertaling is geïmplementeerd.

![Resultaat van overschrijving in inlogformulier van site](../../../en/images/languages/language-overrides-custom-logout.png)

*Vertaald door openai.com*

