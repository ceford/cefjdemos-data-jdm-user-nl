<!-- Filename: J4.x:Access_Control / Display title: Toegangscontrole -->

## Introductie

Joomla heeft een geavanceerd mechanisme om te bepalen wie inhoud kan bekijken en manipuleren op een Joomla-site. Het **wie**-gedeelte wordt ingesteld in de opties van de Gebruikerscomponent met Gebruikersgroepen en Toegangsniveaus. Het **manipuleren**-gedeelte wordt ingesteld in Actiemachtigingen, hetzij in de Globale Configuratie-instellingen, in de Component-instellingen of in de Item-instellingen. Bijvoorbeeld, standaardwaarden die in Globale Machtigingen zijn ingesteld, kunnen worden overschreven in Artikelenmachtigingen (alle artikelen) en Artikelenmachtigingen kunnen worden overschreven in individuele Artikelmachtigingen.

## Gebruikersgroepen

Gebruikersgroepen worden gebruikt om sitegebruikers op te delen in groepen met verschillende verantwoordelijkheden. Bijvoorbeeld: leden van de groep Schrijvers hebben toestemming om in te loggen op de site, artikelen te maken en hun eigen artikelen te bewerken. Niets meer! Leden van de groep Supergebruikers hebben verantwoordelijkheid voor alle aspecten van sitebeheer en -operatie. Joomla biedt negen standaardgebruikersgroepen en je kunt meer maken als je ze nodig hebt.

![Lijst van gebruikersgroepen](../../../en/images/users/access-control-users-groups-list.png)

De standaardgebruikersgroepen zijn opgezet met ouder-kindrelaties om dubbele toestemmingen te minimaliseren. Voorbeelden van overerving:

- Een lid van de groep Geregistreerd heeft geen toestemmingen voor Administrator Login. Dit geldt ook voor Redacteur of Uitgever.
- Een lid van de groep Schrijvers heeft toestemming om te maken en eigen werk te bewerken. Dit geldt ook voor Redacteur en Uitgever, maar zij hebben aanvullende toestemmingen.

Je kunt nieuwe gebruikersgroepen maken voor speciale doeleinden indien nodig. Je kunt bijvoorbeeld een groep willen maken die wel toestemming heeft voor Administrator Login, maar met toegang beperkt tot een enkel component. Er is een voorbeeld van zo'n aangepaste gebruikersgroep aan het einde van deze tutorial.  

## Toegangsniveaus

Elke keer dat je een object maakt, zoals een artikel, een module of een menu-item, zie je een Toegang-veld, meestal in de rechterkolom van het invoerformulier. Het is een keurvak met keuzes als Openbaar, Gast, Geregistreerd, Speciaal en Supergebruikers. De standaardinstelling is Openbaar. De standaard weergavetoegangsniveaus worden getoond in de volgende schermafbeelding:

![Gebruikers weergavetoegangsniveaus](../../../en/images/users/access-control-users-access-levels.png)

Voorbeelden:

- Als je een sitemodule maakt en de toegang instelt op Geregistreerd, wordt deze alleen gezien door gebruikers die zijn ingelogd op de site.
- Als je een sitemenu-item maakt en de toegang instelt op Supergebruikers, wordt deze alleen gezien door Supergebruikers die zijn ingelogd op de site.

## Machtigingen

De globale configuratiemachtigingen zijn het startpunt waarvandaan de machtigingsinstellingen in componenten of individuele items kunnen erven of worden overschreven. Screenshot:

![globale configuratiemachtigingen](../../../en/images/users/access-control-global-configuration-permissions.png)

De screenshot laat zien dat leden van de Publieke groep geen toestemming hebben om handelingen uit te voeren. Als je elke groep om de beurt selecteert, zie je hoe de machtigingen van groep tot groep veranderen. Merk op dat Manager en Beheerder administratorlogin zijn toegestaan, maar Auteur, Redacteur en Uitgever niet. De laatste zijn in feite Site-rollen in plaats van Beheerrollen.

Alle groepsrechten erven van de Publieke groep. Deze heeft geen toestemming voor enige acties. Echter, standaard kunnen items in de Publieke groep worden bekeken, dus het toekennen van Publieke machtiging aan een item zal ervoor zorgen dat het door alle sitebezoekers kan worden gezien, of ze nu zijn ingelogd of niet.

### Artikel Machtigingen

De acties van Artikelen Machtigingen verschillen van de acties van de Globale Configuratie Machtigingen. Niet aanwezig zijn items gerelateerd aan inloggen en wel aanwezig zijn items gerelateerd aan workflows. Dit is een vrij typisch patroon: een component zal machtigingen hebben die relevant zijn voor het component; een component item (zoals een artikel) zal machtigingen hebben die relevant zijn voor dat ene item.

![Inhoud machtigingen](../../../en/images/users/access-control-global-content-permissions.png)

### Enkel Artikel Machtigingen

De machtigingen voor een enkel artikel hebben slechts drie items: Verwijderen, Bewerken en Bewerken Status:

![enkele artikel machtigingen](../../../en/images/users/access-control-article-permissions.png)

## Voorbeeld Toegangscontrole: Gebruiker met Speciaal Doel

Stel dat je een Gebruikersgroep moet maken voor gebruikers die maar één verantwoordelijkheid hebben, in dit voorbeeld een Artikelbeheerder. Gebruikers in deze groep moeten toestemming hebben voor de beheerderinlog, maar mogen niets anders zien dan de inhoudsitems. Procedure:

### Maak een nieuwe Gebruikersgroep aan

- Selecteer **Gebruikers → Groepen** in het Beheerdersmenu.
- Selecteer de knop `Nieuw` in de Werkbalk.
- Vul het veld Groepstitel in: Artikelbeheerder
- De Groepsouder moet Openbaar zijn - het heeft geen toestemmingen voor iets anders.

![Nieuw gebruikersgroepformulier](../../../en/images/users/access-control-new-group.png)

### Toewijzen aan Speciaal

- Selecteer **Gebruikers → Toegangsniveaus** in het Beheerdersmenu.
- Selecteer het item **Speciaal**.
- Selecteer het selectievakje Artikelbeheerder in het formulier **Gebruikers: Bewerken van BekijkToegangsniveau**.
- Opslaan & Sluiten.

![Selecteer toegang voor groep](../../../en/images/users/access-control-select-access-for-group.png)

### Globale Configuratie Permissies

- Selecteer **Startdashboard → Globale Configuratie** in het
  Beheerdersmenu.
- Selecteer het tabblad **Permissies**.
- Selecteer de groep **Artikelbeheerder**.
- Zet **Beheerder Inloggen** op Toegestaan.
- Opslaan & Sluiten.

![Selecteer toegang voor groep](../../../en/images/users/access-control-article-administrator-global-permissions.png)

### Artikelen Opties Permissies

- Selecteer **Inhoud → Artikelen** in het Beheerdersmenu.
- Selecteer de knop `Opties` in de Werkbalk.
- Selecteer het tabblad **Permissies**.
- Selecteer de groep **Artikelbeheerder**.
- Zet alle items behalve de eerste twee (Configureer ACL & Opties en
  Alleen Opties Configureren) op Toegestaan.
- Opslaan & Sluiten.

![Selecteer toegang voor groep](../../../en/images/users/access-control-article-administrator-content-permissions.png)

### Gebruiker Maken of Bewerken

- Maak een nieuwe gebruiker aan of bewerk een bestaande gebruiker die aan geen groepen is toegewezen.
- Selecteer **Artikelbeheerder** in het tabblad **Toegewezen Gebruikersgroepen**
  van het Gebruiker bewerken formulier.
- Opslaan & Sluiten.
- Log in als een gebruiker in de groep Artikelbeheerder alleen. Het menu
  moet alleen artikelgerelateerde items tonen:

![Selecteer toegang voor groep](../../../en/images/users/access-control-article-administrator-home-dashboard.png)

*Vertaald door openai.com*

