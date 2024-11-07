<!-- Filename: J5.x:Enhancing_Password_Security_with_Symbolic_Characters / Display title: Wachtwoordbeveiliging van Gebruikers  -->

## Introductie

In het tabblad *Wachtwoordopties* van het formulier *Gebruikers: Opties* zijn de minimale waarden voor *Cijfers*, *Symbolen*, *Hoofdletters* en *Kleine letters* standaard ingesteld op 0. Voor betere beveiliging moeten deze waarden op 1 worden ingesteld. Nieuwe of gewijzigde wachtwoorden moeten dan een van elk van deze tekens bevatten.

## Symbolen

Het *Open Worldwide Application Security Project* (OWASP) beveelt aan dat alle speciale tekens die beschikbaar zijn op een standaard VS-toetsenbord herkend en geaccepteerd worden bij het instellen van wachtwoordvereisten.

```
 !"#$%&'()*+,-./:;<=>?@[\]^_`{|}~
 ```

Het is niet vanzelfsprekend, maar deze lijst bevat het spatiekarakter.

[OWASP: Wachtwoord Speciale Karakters](https://owasp.org/www-community/password-special-characters)

Voor versie 5.2 konden deze symbolen in wachtwoorden worden gebruikt, maar werden sommigen van hen niet erkend als symbolen voor wachtwoordvalidatiedoeleinden:
```
@[]£^+±~<>/'",.
```

*Vertaald door openai.com*  

