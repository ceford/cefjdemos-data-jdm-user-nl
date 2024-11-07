<!-- Filename: jdocmanual?manual=user&heading=migration&filename=migration-basics.md / Display title: Basisprincipes van Migratie  -->

## Terminologie

Joomla! documenten gebruiken verschillende termen om de overgang van een oudere versie naar een nieuwere versie aan te duiden:

* **Migratie of mini-migratie** is een term die meestal wordt toegepast op de overgang van een oudere naar een nieuwere *Hoofd*versie, soms via verschillende tussenliggende *Hoofd*versies.
* **Upgrade** is een term die meestal wordt toegepast op de overgang van een recente versie naar de volgende versie in een reeks van *Kleine* versies.
* **Update** is een term die meestal wordt gebruikt voor het Upgrade-proces met behulp van de Joomla Update-component. Dit is het woord dat te zien is in de beheerdersinterface in Joomla! 3, 4 en 5. Voortaan zal de term *Update* in dit artikel worden gebruikt.

Het is ook nuttig om te weten dat Joomla de Semantic Versioning-standaard volgt. Kort gezegd, gegeven een versienummer MAJOR.MINOR.PATCH, zoals 5.1.0:

* De **MAJOR** versie staat breuken in achterwaartse compatibiliteit toe.
* De **MINOR** versie maakt extra functionaliteit mogelijk op een manier die achterwaarts compatibel is binnen de Hoofdversie.
* De **PATCH** versie staat achterwaarts compatibele bugfixes toe.

Er kunnen extra achtervoegsels zijn, zoals *alpha*, *beta* of *rc*, maar niet in stabiele releases die bedoeld zijn voor productiesites.

## Redenen om te Updaten

De redenen om te updaten zijn talrijk en gevarieerd:

* **Beveiliging** Hoewel Joomla! erkend wordt als een zeer veilig CMS, worden er
af en toe kwetsbaarheden ontdekt en opgelost in Minor of Patch releases.
* **Wijzigingen in hosting** Joomla maakt gebruik van de *PHP* programmeertaal
en een databaseserver zoals *MySQL*, *MariaDB* of *PostGres*. Deze ontwikkelen
zich verder en hostingdiensten moeten up-to-date blijven. Dus je zou kunnen
merken dat een oudere versie van Joomla niet langer werkt of niet goed functioneert
als je van hostingdienst verandert.
* **Ontwerpwijzigingen** Je wilt misschien dat je site er beter uitziet, beter
werkt met mobiele apparaten en beter scoort bij zoekmachines. Je moet mogelijk
voldoen aan wettelijke *Toegankelijkheid* vereisten.
* **Functionaliteit** Je wilt wellicht een Joomla-extensie gebruiken die een
functie biedt die niet beschikbaar is bij de kern Joomla-extensies. De keuzes
kunnen beperkt zijn door je huidige Major versie.

## Back-up maken voor update

**Dit is echt belangrijk!** Zelfs als je al meerdere tussentijdse updates hebt uitgevoerd, is het mogelijk dat er iets misgaat tijdens het updateproces. Dit kan je site onbruikbaar maken. Het standaardadvies dat op de forums wordt gegeven, is om terug te keren naar je laatste back-up, uit te zoeken waarom de back-up is mislukt, het te herstellen en het vervolgens opnieuw te proberen.

**Akeeba Backup** is een gratis tool die te verkrijgen is via de Joomla Extensies Directory (JED) en waartoe je directe toegang hebt via Systeem / Extensies installeren / Installeren vanuit het web. Het kost slechts een minuut of twee om te downloaden en te installeren. Het analyseert je systeem om een profiel in te stellen met behulp van een Configuratiewizard. Vervolgens maakt het een back-up die je kunt downloaden voor veilige bewaring.

## Zelfevaluatie

Voordat je een *Grote* of *Kleine* versie-update uitvoert, moet je je systeem en je bestaande externe extensies beoordelen op compatibiliteit met de doelversie van Joomla. Het is een goed idee om een lijst te maken van de derde partij extensies die je hebt geïnstalleerd. In Joomla 4 en 5 heeft de lijst *Systeem / Extensies / Beheren* een filter om **Niet-kernextensies** te selecteren. Dit is niet aanwezig in Joomla 3.

Je kunt ook de **Forum Post Assistant** gebruiken. Dit is een hulpmiddel bedoeld om een site te analyseren en een rapport te maken dat geschikt is om op de Joomla Fora te plaatsen, zodat de Forumexperts je kunnen helpen met het diagnosticeren van problemen op je site. Het heeft echter een privé-gebruikersinterface die je alles over je site vertelt. De extensielijsten (Componenten, enz.) geven aan welke *Derde Partij* zijn.

De problemen die zich voordoen tijdens updates worden meestal geassocieerd met externe extensies die niet codecompatibel zijn met je doelversie van Joomla. Je moet elke extensie controleren op compatibiliteit en **deïnstalleren** van extensies die bekend staan als incompatibel. Je kunt mogelijk later compatibele versies installeren.

Je zou een van de standaard Site templates als je **standaard template** moeten instellen:

* Joomla! 1.5 standaardtemplates zijn Rhuk_milkyway, JA Purity, Beez.
* Joomla! 2.5 standaardtemplates zijn Atomic, Beez3 en Beez25.
* Joomla! 3 standaardtemplates zijn Protostar en Beez3.
* Joomla! 4 standaardtemplate is alleen Cassiopeia.

## Lokale Test

Indien mogelijk, is het het beste om een lokale testomgeving in te stellen op je laptop of thuiswerkstation om je updateprocedure te testen. Je kunt de back-up van je online site gebruiken om je testsite te vullen. Je thuisomgeving moet in staat zijn om een kopie van je live site te draaien en moet over voldoende PHP- en database-specificaties beschikken om de bijgewerkte site te draaien. Er is een apart artikel dat beschrijft hoe je een thuis testomgeving in kunt stellen.

## Aanvullende Informatie

Er zijn een aantal artikelen die specifieke update-scenario's beschrijven die niet in deze handleiding zijn opgenomen omdat ze oud of repetitief zijn.

* https://docs.joomla.org/Why_Migrate
* https://docs.joomla.org/Migration_Step_by_Step_Self_Assessment
* https://docs.joomla.org/J3.x:Updating_Joomla_(Install_Method)
* https://docs.joomla.org/J3.x:Updating_Joomla_(Update_Method)
* https://docs.joomla.org/Planning_Migration_-_Joomla_1.5_to_4
* https://docs.joomla.org/Planning_for_Migration
* https://docs.joomla.org/Pre-Update_Check
* https://docs.joomla.org/Template_Considerations_During_Migration
* https://docs.joomla.org/J3.x:Update_fails_with_an_error_message
* https://docs.joomla.org/Converting_an_existing_website_to_a_Joomla!_website
* https://docs.joomla.org/Potential_backward_compatibility_issues_in_Joomla_4
->
*Vertaald door openai.com*

