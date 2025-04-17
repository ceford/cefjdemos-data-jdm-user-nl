<!-- Filename: jdocmanual?manual=user&heading=performance&filename=accessibility-checker.md / Display title: Controle van de Toegankelijkheid   -->

## Systeem - Joomla Toegankelijkheidscontrole

Dit is een kernplugin die kan worden gebruikt om toegankelijkheid te controleren tijdens het maken van artikelinhoud. De volgende screenshot toont enkele plugin-instellingen:

![Pluginformulier instellingen](../../../en/images/performance/performance-jooa11y-plugin-form.png)

Met de optie **Altijd Tonen** ingesteld op *Aan* verschijnt het rapporticoon op elke pagina van de site. Dat is nuttig voor ontwikkeling maar moet nooit aan blijven voor een live site. Zet het op **Uit**!

Als de optie *Altijd Tonen* op *Aan* staat, heeft elke sitepagina een icoon rechtsonder met een telling van het aantal problemen. De volgende screenshot toont het icoon dat is geselecteerd om een informatief paneel te tonen. Het bevat een Pagina-overzicht, Leesbaarheidsopmerkingen en Waarschuwingen, die een voor een kunnen worden geselecteerd. Het eerste probleem is geselecteerd.

![Toegankelijkheid controle van de site](../../../en/images/performance/performance-jooa11y-site-display.png)

Het *Artikelen: Bewerken* formulier heeft een **Toegankelijkheidscontrole** knop in de werkbalk. Het toont de controle voor een individueel artikel in een pop-upvenster:

![Editor toegankelijkheidscontrole](../../../en/images/performance/performance-jooa11y-admin-display.png)

## Problemen Oplossen

De Accessibility Checker is een tool om problemen te identificeren. Het lost problemen niet op. Dat is aan jou. De checker heeft enkele instellingen die je naar behoefte aan of uit kunt zetten. Deze omvatten Contrast, Formulierlabels, Links (Geavanceerd) AAA, Leesbaarheid AAA, Donkere modus en Kleurfilter met simulatie van vier soorten gebrekkig kleurenzicht.

Voor meer informatie, zie het Sa11y Overzicht

Bijvoorbeeld, over Leesbaarheid, zegt het:

>Sa11y kan de leesbaarscore schatten van alle alinea’s en lijstinhoud. Een goede leesbaarscore is een indicatie dat je tekst begrijpelijk en gemakkelijk te verwerken is. Het is gebaseerd op de gemiddelde lengte van zinnen en woorden op je pagina, met behulp van een formule die bekend staat als de Flesch leestgemakstest (Wikipedia). Een "goede" leesbaarscore ligt tussen de 60 en 100. Soms kan het moeilijk zijn om een goede leesbaarscore te bereiken. De meeste van je pagina’s kunnen "moeilijk" aangeven. Onthoud dat deze functie alleen wordt gebruikt om de leesbaarheid van je inhoud te schatten. Het moet alleen als een referentie worden gebruikt, en niet als een indicatie van conformiteit. Sa11y berekent de leesbaarscore op basis van alle alinea (`<p>` tags) en lijstinhoud (`<li>` tags). Een lage score heeft geen invloed op de slaag- of faalstatus van Sa11y.

*Vertaald door openai.com*

