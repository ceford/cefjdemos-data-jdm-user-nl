<!-- Filename: J4.x:Workflow / Display title: Publicatie workflow -->

Joomla!  4.x

## Inleiding

De 'Publicatie workflow' component wordt gebruikt om statische statussen
(gedepubliceerd, gepubliceerd, in prullenbak en gearchiveerd) te
vervangen door een meer algemene aanpak. Op deze manier kun je makkelijk
een eigen workflow aanmaken om de artikelen binnen een component te
beheren.

- Het beheergedeelte van artikelen in Joomla 3.x:

<img
src="https://docs.joomla.org/images/thumb/b/bc/Article_view_3-nl.png/800px-Article_view_3-nl.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/b/bc/Article_view_3-nl.png/1200px-Article_view_3-nl.png 1.5x, https://docs.joomla.org/images/b/bc/Article_view_3-nl.png 2x"
data-file-width="1429" data-file-height="406" width="800" height="227"
alt="Article view 3-nl.png" />

- Het beheergedeelte van artikelen in Joomla 4.x:

<img
src="https://docs.joomla.org/images/thumb/9/94/J4_Articles_Backend-en.png/800px-J4_Articles_Backend-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/9/94/J4_Articles_Backend-en.png 1.5x"
data-file-width="1200" data-file-height="332" width="800" height="221"
alt="J4 Articles Backend-en.png" />

Het artikel hulpmiddelen lijstje is nu kleiner en het overzicht in het
algemeen ordelijker. Je kunt eigen statussen voor artikelen aanmaken en
ze in categorieën groeperen.

Er is een handleiding-pagina met stappen voor het aanmaken van je eerste
workflow:
Scenario's.
Je vindt meer informatie over de implementatie van de component op
andere plekken op de pagina van het Google Summer of Code project DOC:
You can disable workflows at any time by visiting "articles" or
"workflows" and clicking "options" in the top right. Switch to the tab
"Integration" and scroll down to "Enable Workflow".

## Voorwaarden & definities

- *Workflows:* Je kunt diverse workflows aanmaken. Iedere workflow bevat
  statussen, mogelijke veranderingen en de condities van de items.
- *Status:* Status kan worden gezien als de stappen in een workflow.
- *Condities:* De conditie van een item kan worden gedepubliceerd,
  gepubliceerd, naar de prullenbak verplaatst of gearchiveerd.
- *Verandering:* Veranderingen bepalen de volgorde van statussen die een
  artikel kan hebben.
- *Categorieën:* Artikelen kunnen aan categorieën worden gekoppeld.

## Workflows

De workflow lijkt op opeenvolgende stappen. Je krijgt toegang via het
bovenste hoofdmenu onder "Inhoud". Je wordt doorgeleid naar de
"Workflowlijst", een overzicht van al je bestaande workflows. Een
workflow bevat diverse statussen met verschillende condities. Items
(bijvoorbeeld artikelen) kunnen deze statussen doorlopen.

<img
src="https://docs.joomla.org/images/thumb/e/e2/Workflows-en.png/800px-Workflows-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/thumb/e/e2/Workflows-en.png/1200px-Workflows-en.png 1.5x, https://docs.joomla.org/images/thumb/e/e2/Workflows-en.png/1600px-Workflows-en.png 2x"
data-file-width="1906" data-file-height="455" width="800" height="191"
alt="Workflows List" />

- Je ziet de status van de workflow (gepubliceerd / gedepubliceerd)
- Naast de status staat de titel. Door op de titel te klikken kun je *de
  workflow bewerken*
  - *Te bewerken*: Titel \| Beschrijving \| Status \| Standaard Optie \|
    Rechten (Rechten beheer)
- Naast de titel vind je de optie om de *Beheer* de workflow status (zie
  voor meer informatie
  Statussen
- Naast de "Status" staat de standaard optie
- Je vind een geel cirkel-icoon naast "standaard", wat het aantal
  bestaande statussen in de workflow aangeeft
- Naast de gele cirkel staat een blauw pijl-icoon welke het aantal
  veranderingen in deze workflow vertegenwoordigt (voor meer informatie
  see
  Veranderingen
- Daarnaast zie je de aanmaakdatum van de workflow, de auteur en de ID.

## Statussen

De status kan bereikt worden via het "Workflow overzicht" door op de
*Beheer* status te klikken. Je kunt een standaard status instellen
(welke de conditie "gepubliceerd" moet hebben). Door op de titel te
klikken kun je de status *Bewerken*.


<img
src="https://docs.joomla.org/images/thumb/a/ac/Stages-en.png/800px-Stages-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/a/ac/Stages-en.png 1.5x"
data-file-width="1200" data-file-height="251" width="800" height="167"
alt="Stages View" />

<img
src="https://docs.joomla.org/images/thumb/7/7f/Stages--edit-en.png/800px-Stages--edit-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/7/7f/Stages--edit-en.png 1.5x"
data-file-width="1200" data-file-height="404" width="800" height="269"
alt="The Edit Stage view" />

- In de tweede afbeelding staat de status optie rechts. Dit is de
  toestand van de status.

## Overgangen

Artikelen kunnen overgaan van de ene status naar de andere. De overgang
kan worden beheerd via het "Workflow overzicht" door op het blauwe pijl
icoon te drukken of via het menu links, na het klikken op *Beheer*
status. Je kunt meerdere overgangen instellen die het item kan
doorlopen. De mogelijke statussen zijn gebaseerd op degene die je
aangemaakt hebt voor deze workflow.

The *current stage* will define where this transition is applied. You
can choose all stages, or a specific stage.

The *target stage* is the stage the workflow will end up at after the
transition has taken place.

<img
src="https://docs.joomla.org/images/thumb/4/45/Transitions--edit--description-en.png/800px-Transitions--edit--description-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/4/45/Transitions--edit--description-en.png 1.5x"
data-file-width="1200" data-file-height="456" width="800" height="304"
alt="Edit Transitions View" />

The *transition actions* tab allows you to define what state the item
will be in after the transition is complete. For example if the item is
an article it could become unpublished, which is exactly what happens in
the *unpublish* transition. You can also define whether the item is
featured or not by the end of the state.

<img
src="https://docs.joomla.org/images/thumb/2/27/Transitions--edit--transition-actions-en.png/800px-Transitions--edit--transition-actions-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/2/27/Transitions--edit--transition-actions-en.png 1.5x"
data-file-width="1200" data-file-height="429" width="800" height="286"
alt="Edit Transition Actions" />

The *transition notifications* tab allows you to define whether a
notification is sent during that state. For example if an article has
been written but needs to be proofread, you could send an email
notification to the editor.

You can also add additional message text. This will also allow you to
use a  language
string
which would make the message text translatable.

The Usergroups option will allow you to define who will receive the
notification. In the example we have chosen we would choose *editor* as
the usergroup. In that example all users within that usergroup would get
a notification.

Finally there is the "more receivers" option. This allows you to choose
individual users to receive this notification.

<img
src="https://docs.joomla.org/images/thumb/5/57/Transitions--edit--notification-en.png/800px-Transitions--edit--notification-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/5/57/Transitions--edit--notification-en.png 1.5x"
data-file-width="1200" data-file-height="481" width="800" height="321"
alt="Edit Transition Notification" />

The final tab is the permissions tab. This allows you to set who can use
this transition.

- *Example:* In the transition "Next Step: Publishing" items are
  originally of the state "unpublished". They are, for example, in need
  of a review. After they have been reviewed, they can transit to the
  state "published".
- All the workflow transition actions are Joomla! workflow plugins. If
  you go to System **→** Plugins. Then change the "type" dropdown to
  "workflow" you will see the plugins. These can be disabled like any
  other plugin.

<img
src="https://docs.joomla.org/images/thumb/9/96/Workflows--plugins--workflows-en.png/800px-Workflows--plugins--workflows-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/9/96/Workflows--plugins--workflows-en.png 1.5x"
data-file-width="1200" data-file-height="358" width="800" height="239"
alt="Workflows Plugins" />

## Categories

Articles can be assigned to categories. They correspond to a certain
workflow and can be customized in various ways. You can set a status,
parent category and also restrict the access as well as the permissions.
This option is not within the workflows screen. For this option you need
to go to Content **→** Categories. Once there open any category and you
will see a "workflows" tab.

- *Example:* You have certain articles that you want to be available
  only for administrators or users of a higher rank. You can call your
  category "Restricted" and set all permissions on "Allowed" for
  administrators or higher. This way you do not have to set those
  permissions for every article concerned but can move them into this
  special category and save time instead.

<img
src="https://docs.joomla.org/images/thumb/d/dd/Workflow-categories-en.png/800px-Workflow-categories-en.png"
decoding="async"
srcset="https://docs.joomla.org/images/d/dd/Workflow-categories-en.png 1.5x"
data-file-width="1200" data-file-height="431" width="800" height="287"
alt="Workflow-categories-en.png" />

## Versioning

When the workflow is enabled fields managed by the workflow are excluded
from the versioning (like "state" and "featured") to avoid permission
conflicts.

## Related Information

See also:

-  Publishing Workflow
  Implementation
- Scenarios
