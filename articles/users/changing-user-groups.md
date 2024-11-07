<!-- Filename: Changing_user_groups / Display title: Gebruikersgroepen Wijzigen  -->

## Groepsovererving

Groepslijsten gebruiken een overervingspatroon. Bijvoorbeeld, een gebruiker in de Auteur-groep erft alle privileges van de Geregistreerd-groep en krijgt bovendien extra privileges. Evenzo erft een gebruiker in de Redacteur-groep alle privileges van de Auteur-groep en krijgt nog meer extra privileges. De back-endgroepen erven het hoogste priviligensniveau van de front-end.

Om deze reden hoef je slechts één groep voor een individuele gebruiker te selecteren - de groep met de meeste privileges.

## Stappen

Je kunt de groep van een gebruiker wijzigen door de volgende stappen te volgen. Je moet inloggen als een Beheerder of een Supergebruiker om de groepen van een gebruiker te kunnen wijzigen. Ook kan een Beheerder zichzelf of anderen geen Supergebruiker maken.

1.  Selecteer het **Gebruikers** item vanaf het *Home Dashboard*. Of...
2.  Selecteer **Gebruikers** en vervolgens **Beheren** vanuit het *Gebruikers*-menu.
3.  Zoek de gewenste gebruiker in de lijst van gebruikers. Je kunt zoeken op naam, gebruikersnaam, e-mail of id: prefix.
4.  Selecteer de naam van de gebruiker om te bewerken.
5.  Selecteer het tabblad *Toegewezen Gebruikersgroepen*.
6.  Selecteer de groep waar de gebruiker tot moet behoren.
7.  Selecteer *Opslaan*.

## Toegangscontrolelijst (ACL) voor Joomla

Het volgende is de toegangscontrolelijst
(ACL) voor Joomla. De gebruikersgroep wordt opgesomd en de opsommingstekens hieronder
beschrijven de rechten die bij die groep horen.

### Frontend Groepen

#### Gast

- Bekijk de openbare site en openbare artikelen

#### Geregistreerd

- Gastgroepprivileges
- Bekijk geregistreerde artikelen
- Geen toegang tot items die beperkt zijn tot de Gastgroep

#### Auteur

- Geregistreerde groep privileges
- Nieuwe artikelen aanmaken
- Bewerk artikelen die ze bezitten
- Bekijk speciale inhoud

#### Redacteur

- Auteur groep privileges
- Bewerk alle artikelen, inclusief ongepubliceerde

#### Uitgever

- Redacteur groep privileges
- Artikelen publiceren

### Backend Groepen

Deze groepen stellen je in staat om in te loggen op de beheerder via de
*/administrator* URL.

#### Beheerder

- Uitgever Groep privileges
- Toegang tot Administrator Backend

#### Administrator

- Manager groep privileges
- Nieuwe gebruikers aanmaken
- Extensies installeren

#### Supergebruiker

- Administrator privileges
- Wijzig de site template
- Wijzig de globale configuratie

*Vertaald door openai.com*

