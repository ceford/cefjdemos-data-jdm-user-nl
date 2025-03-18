<!-- Filename: J5.x:Managing_Mail_Template_Layout / Display title: E-mailsjablonen -->

## Introductie

E-mailsjablonen worden gebruikt om systeeme-mailberichten te verzenden in **platte tekst** of **HTML** of beide, geselecteerd in het *Mail Templates: Options* formulier. Als slechts één methode is geselecteerd, zal het alternatief niet aanwezig zijn in het berichtbewerkingsformulier.

De volgende screenshot toont een selectie van de 26 standaard Mail Sjablonen die beschikbaar zijn. De lijst is beschikbaar door **Systeem -> Mail Sjablonen** te selecteren in het Beheerdersmenu.

![mail templates list](../../../en/images/templates/mail-templates-list.png)

De e-mailberichten kunnen worden aangepast om de lay-out, verschijning en bewoordingen aan te passen aan de behoeften van uw site. U kunt bijvoorbeeld een site-logo en kleurenschema gebruiken in de e-mails die naar klanten worden gestuurd. Het aanpassen van e-mails die naar beheerders worden gestuurd is minder belangrijk.

Er zijn twee aanpassingsmethoden: via de *Mail Template: Opties* voor alle e-mailsjablonen en via *Per Template Mail-instellingen*.

## Mail Sjabloon: Opties

Selecteer de knop **Opties** in de *Mail Templates*-lijstwerkbalk om toegang te krijgen tot de algemene mailtemplates-instellingen. Selecteer de knop *Inline Help Wisselen* om te zien of een van de formuliervelden extra hulp heeft.

![mail templates options](../../../en/images/templates/mail-templates-options.png)

### E-mailformaat

Wees ervan bewust dat een ontvanger een e-mailclient kan instellen om eenvoudige HTML of platte tekst te gebruiken om het downloaden van afbeeldingen te vermijden. Het kan daarom het beste zijn om het *E-mailformaat* in te stellen op *Platte tekst* of *Beide*.

### Per Sjabloon E-mailinstellingen

Als dit is ingesteld op **Ja**, hebben individuele e-mailsjabloonbewerkingsformulieren een extra *Opties* tabblad waarmee je e-mailinstellingen voor die sjabloon kunt wijzigen en optioneel een kopie (BCC) kunt verzenden naar een specifiek e-mailadres, op voorwaarde dat het **Kopie Verzenden** veld hier ook is ingesteld op **Ingeschakeld**.

## Sjabloon Bewerken Formulier

In de lijst met Mail Sjablonen kun je elk sjabloon selecteren om te bewerken. De Titel link leidt naar het bewerkingsformulier voor het standaard Engelse sjabloon. Elke vlag is een link naar hetzelfde sjabloon in die taal.

### Het tabblad Mail

![edit mail template form](../../../en/images/templates/mail-template-edit.png)

De inhoud van de Subject- en Body-gebieden wordt aanvankelijk in taalstrings opgeslagen. Dit maakt het eenvoudig om te *Herstellen naar standaard Onderwerp* of *Body*. Echter, zodra een specifieke mailtemplate is bewerkt, worden de velden Onderwerp en Body opgeslagen in de `#__mail_templates` tabel.

De items tussen accolades zijn plaatsaanduidingstags die worden vervangen door echte waarden wanneer de e-mail wordt verzonden. In het bovenstaande voorbeeld zou `{SITENAME}` de naam zijn die je voor je site hebt gekozen. `{Method}` zou de geselecteerde e-mailtransportmethode zijn: `PHP Mail`, `Sendmail` of `SMTP`.

De beschikbare placeholder-tags variëren van e-mail tot e-mail. Je zou je eigen aangepaste placeholder-tags kunnen toevoegen, maar dat vereist een aangepaste plugin, zoals beschreven in een [Magazine-artikel](https://magazine.joomla.org/all-issues/february-2025/joomla-5-email-templates-how-to-add-variables-via-plugin) uit februari 2025.

### Het tabblad Opties

Deze tab is alleen aanwezig als de *Per Template Mail Instellingen* is ingesteld op *Ja* in *Mail Templates: Opties*. De onderstaande illustratie toont een screenshot met *Mail Instellingen* ingesteld op *Nee*. Als ingesteld op *Ja* verschijnen er meer formulier velden die de Mail opties overschrijven die zijn ingesteld in de Globale Configuratie, Server tab.

![edit mail template form](../../../en/images/templates/mail-template-edit-options.png)

Als je een blinde kopie van een uitgaande e-mail naar een specifiek e-mailadres wilt sturen, kun je dit invoeren in het veld *Kopie verzenden naar e-mail*.

## E-mailsjabloon Overrides

Om een e-mailsjabloon te overschrijven binnen een aangepast sjabloon:

1. Ga naar Systeem -> Sitetemplates -> Open je template (bijv. Cassiopeia).
2. In het tabblad Overrides maken, selecteer joomla -> mail.
3. Joomla kopieert het `mailtemplate.php` bestand naar de `/html/layouts/joomla/mail/`-map van je template, waar je het naar wens kunt aanpassen.

Zodra de overschrijving is gemaakt, kunt u de indeling en stijlen van uw e-mails aanpassen zonder de basistemplate te beïnvloeden.

## Lijst van E-mailsjablonen

| Titel | Extensie | Beschrijving |
|-------|-----------|-------------|
| Gebruikersacties Log: Notificatie Mail | Gebruikersacties Log | Mail verzonden naar beheerders over nieuwe vermeldingen in het Gebruikersacties Log. |
| Globale Configuratie: Testmail | Configuratie | Verstuurd wanneer u op de knop "Stuur Testmail" klikt in de Globale Configuratie. Het wordt verzonden naar het verzendmailadres dat is ingesteld in de mailinstellingen. |
| Contacten: Contactformulier Mail | Contacten | De "Contactformulier" e-mail. |
| Contacten: Contactformulier Mail Kopie | Contacten | Verstuurd naar de indiener van een mail met het contactformulier als de optionele "Stuur Kopie naar Indiener" is ingeschakeld en geselecteerd. |
| Berichten: Nieuw bericht | Berichten | E-mail met een bericht aangemaakt in de berichten component. |
| Privacy: Verzoek Exporteren van Gegevens (Admin) | Privacy | Mail om de gebruiker te informeren dat een verzoek om de gegevens van deze website te exporteren is aangemaakt door de beheerder. |
| Privacy: Verzoek Verwijderen van Gegevens (Admin) | Privacy | Mail om de gebruiker te informeren dat een verzoek om de gegevens van deze website te verwijderen is aangemaakt door de beheerder. |
| Privacy: Verzoek Exporteren van Gegevens | Privacy | Mail om te verifiëren dat de gegevens van een gebruiker van de website moeten worden geëxporteerd. |
| Privacy: Verzoek Verwijderen van Gegevens | Privacy | Mail om te verifiëren dat de gegevens van een gebruiker van de website moeten worden verwijderd. |
| Privacy: Gebruikersgegevens Export | Privacy | Mail met export van gebruikersgegevens. |
| Gebruikers: Mass Mail Gebruikers | Gebruikers | De "Mass Mail Gebruikers" e-mail. |
| Gebruikers: Wachtwoord Herstel | Gebruikers | Verzonden naar een gebruiker via de link "Wachtwoord vergeten?" bijvoorbeeld in een inlogformulier. |
| Gebruikers: Nieuwe account notificatie aan admin | Gebruikers | Notificatie aan de admin dat een nieuw, geactiveerd account is aangemaakt. |
| Gebruikers: Verzoek aan admin om nieuw account te verifiëren | Gebruikers | Notificatie aan admins om een nieuw, geverifieerd account te verifiëren. |
| Gebruikers: Account geactiveerd door admin | Gebruikers | Notificatie verzonden naar de gebruiker dat het nieuwe account is geactiveerd door een beheerder. |
| Gebruikers: Nieuw account met admin activatie | Gebruikers | Notificatie over nieuw account aan de gebruiker, dat nu door een admin moet worden geactiveerd. |
| Gebruikers: Nieuw account met admin activatie (met WW) | Gebruikers | Notificatie over nieuw account aan de gebruiker, dat nu door een admin moet worden geactiveerd. Het wachtwoord in platte tekst is opgenomen in de mail. |
| Gebruikers: Nieuw account zonder activatie | Gebruikers | Notificatie over nieuw account aan de gebruiker. Het account is al geactiveerd. |
| Gebruikers: Nieuw account zonder activatie (met WW) | Gebruikers | Notificatie over nieuw account aan de gebruiker. Het account is al geactiveerd. Het wachtwoord in platte tekst is opgenomen in de mail. |
| Gebruikers: Nieuw account met zelfactivatie | Gebruikers | Notificatie over nieuw account aan de gebruiker, dat de gebruiker nu zelf moet activeren. |
| Gebruikers: Nieuw account met zelfactivatie (met WW) | Gebruikers | Notificatie over nieuw account aan de gebruiker, dat de gebruiker nu zelf moet activeren. Het wachtwoord in platte tekst is opgenomen in de mail. |
| Gebruikers: Gebruikersnaamherinnering | Gebruikers | Verzonden naar een gebruiker via de link "Gebruikersnaam vergeten?" bijvoorbeeld in een inlogformulier. |
| Code verzonden per e-mail | Multifactor Authenticatie - Authenticatiecode per E-mail | Verzonden naar gebruikers vanaf de Multifactor Authenticatie-pagina bij gebruik van de optie "Authenticatiecode per E-mail". |
| Taak - Privacytoestemming: Vernieuw Toestemming | Taak - Privacytoestemmingen | Herinnering om de privacytoestemming voor deze website te vernieuwen. |
| Joomla: Update Notificatie | Taak - Joomla! Update Notificatie | Verzonden naar de sitebeheerders wanneer de "Joomla! Update Notificatie" taakplugin een update detecteert. |
| Gebruikers: Nieuwe Gebruiker | Gebruiker - Joomla! | Verzonden naar een nieuwe gebruiker wanneer deze in de backend is aangemaakt. |

*Vertaald door openai.com*

