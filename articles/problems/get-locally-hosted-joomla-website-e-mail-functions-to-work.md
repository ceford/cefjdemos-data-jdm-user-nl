<!-- Filename: Get_locally_hosted_Joomla!_website_e-mail_functions_to_work / Display title: Lokale Host E-mail  -->

## Lokale Hosting

De meeste ISP's blokkeren poort 25, zodat je geen e-mail kunt verzenden vanuit de SMTP-server van je eigen computer. Dit is om spammers te blokkeren. Als je niet van plan bent te spammen, kun je de mailserver van je ISP gebruiken.

Om de e-mailfunctie van de SMTP-server van je ISP te gebruiken, zelfs als je je eigen Joomla-site op je eigen computer host, meld je aan bij je Joomla-site als een Super User en navigeer je naar het **Server** tabblad van de **Globale Configuratie** pagina. In de **Mail** sectie zou je data er als volgt uit moeten zien:

    Van Email: iemand@voorbeeld.com (meestal jij)
    Van Naam: EenNaam

    Mailer: SMTP
    SMTP Host: smtp.charter.net (Wat je ISP je ook vertelt te gebruiken voor hun SMTP-servers)
    Sendmail-pad: /usr/sbin/sendmail
    SMTP Poort: 25
    SMTP Beveiliging: STARTTLS
    SMTP Verificatie: Ja (of Nee)
    SMTP Gebruikersnaam: johndoe (gebruikersnaam van een van je e-mailaccounts bij je ISP)
    SMTP Wachtwoord: trr33459 (wachtwoord van een van je e-mailaccounts bij je ISP)
Stuur een testbericht om te controleren of het werkt.

De SMTP Gebruikersnaam, Wachtwoord en Host zijn dezelfde velden die je invult bij het toevoegen van een Outlook Express Account, of Eudora, of een e-mailclient die je mogelijk op je computer gebruikt.

Je kunt problemen ondervinden met uitbreidingen die het *Van* adres wijzigen in de e-mails die worden verzonden. Bijvoorbeeld, de ProjectFork extensie stuurt soms e-mails alsof ze afkomstig zijn van de persoon die het project beheert. Dit kan een probleem veroorzaken omdat sommige ISP SMTP-servers geen "van" adres toestaan dat niet overeenkomt met de gebruikersnaam (bijvoorbeeld Rogers in Canada). Je krijgt een bericht als volgt:
"PHPMAILER_FROM_FAILEDnaam@watdanook.com." Een oplossing is ervoor te zorgen dat je altijd een geldig e-mailadres van je ISP gebruikt voor je gebruikers.

*Vertaald door openai.com*

