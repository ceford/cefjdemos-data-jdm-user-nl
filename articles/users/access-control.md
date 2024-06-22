<!-- Filename: J4.x:Access_Control / Display title: Toegangsbeheer -->

## Inleiding

Joomla heeft een geavanceerd mechanisme om te bepalen wie inhoud op een
Joomla-site kan zien en aanpassen. Het deel **wie** wordt ingesteld in
de Gebruikerscomponent opties met Gebruikersgroepen en Toegangsniveaus.
Het gedeelte **aanpassen** wordt ingesteld in Actie rechten, of bij de
Algemene instellingen of bij de component instellingen of bij de Item
instellingen. Standaardwaarden die zijn ingesteld in Algemene rechten
kunnen bijvoorbeeld worden overschreven bij de Artikel rechten (alle
artikelen) en Artikel rechten kunnen worden overschreven bij de
individuele artikel rechten.

## Gebruikersgroepen

Gebruikersgroepen worden gebruikt om sitegebruikers op te delen in
groepen met verschillende verantwoordelijkheden. Leden van de
gebruikersgroep Auteur hebben bijvoorbeeld rechten om in te loggen op de
Site, artikelen te maken en hun eigen artikelen te bewerken. Niets
anders! Leden van de Super Users-groep zijn verantwoordelijk voor alle
aspecten van het beheer en de werking van de site. Joomla biedt negen
standaard gebruikersgroepen en men kan er meer aanmaken als dat nodig
is.

<img
src="https://docs.joomla.org/images/thumb/a/ae/J4x-user-groups-nl.png/800px-J4x-user-groups-nl.png.jpeg"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/thumb/a/ae/J4x-user-groups-nl.png/1200px-J4x-user-groups-nl.png.jpeg 1.5x, https://docs.joomla.org/images/a/ae/J4x-user-groups-nl.png 2x"
data-file-width="1278" data-file-height="744" width="800" height="466"
alt="J4x-user-groups-nl.png" />

De standaard gebruikersgroepen zijn opgezet met ouder-kindrelaties om
dubbele rechten te minimaliseren. Voorbeelden van overerving:

- Een lid van de 'geregistreerd' groep heeft geen beheerdersrechten om
  in te loggen in het beheerdeel. Redacteur of Uitgever ook niet.
- Een lid van de auteursgroep heeft rechten om eigen bestanden te maken
  en te bewerken. Dat geldt ook voor Redacteur en Uitgever, maar ze
  hebben extra rechten

Nieuwe gebruikersgroepen kunnen voor speciale doeleinden aangemaakt
worden. Er kan bijvoorbeeld een groep aangemaakt worden die
beheerdersrechten heeft om in te loggen, maar waarvan de toegang beperkt
is tot een enkele component. Er staat een voorbeeld van zo'n eigen
gebruikersgroep aan het eind van deze handleiding.

## Toegangsniveaus

Elke keer als er een object aangemaakt wordt, zoals een artikel, een
module of een menu-item, ziet men een toegang-veld, meestal in de
rechterkolom van het gegevensinvoerformulier. Het is een keuzelijst met
een keuze uit openbaar, gast, geregistreerd, speciaal en supergebruiker.
De standaardwaarde is Openbaar. De standaard weergavetoegangsniveaus
worden getoond in de volgende schermafbeelding:

<img
src="https://docs.joomla.org/images/thumb/0/0e/J4x-user-access-levels-nl.png/800px-J4x-user-access-levels-nl.png.jpeg"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/thumb/0/0e/J4x-user-access-levels-nl.png/1200px-J4x-user-access-levels-nl.png.jpeg 1.5x, https://docs.joomla.org/images/0/0e/J4x-user-access-levels-nl.png 2x"
data-file-width="1271" data-file-height="519" width="800" height="327"
alt="J4x-user-access-levels-nl.png" />

Voorbeelden:

- Als men een sitemodule maakt en Toegang instelt op Geregistreerd,
  wordt deze alleen gezien door gebruikers die zijn aangemeld op de
  website.
- Als men een site menu-item maakt en Toegang instelt op
  Supergebruikers, wordt dit alleen gezien door Supergebruikers die zijn
  ingelogd op de website.

## Rechten

De algemene instellingen rechten zijn het startpunt van waaruit rechten
instellingen in componenten of individuele items kunnen worden
overgenomen of overschreven. Schermafbeelding:

<img
src="https://docs.joomla.org/images/thumb/e/ef/J4x-permissions-global-nl.png/800px-J4x-permissions-global-nl.png.jpeg"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/thumb/e/ef/J4x-permissions-global-nl.png/1200px-J4x-permissions-global-nl.png.jpeg 1.5x, https://docs.joomla.org/images/e/ef/J4x-permissions-global-nl.png 2x"
data-file-width="1285" data-file-height="930" width="800" height="579"
alt="J4x-permissions-global-nl.png" />

The screenshot shows that members of the Public group do not have
permission to take any actions. If you select each group in turn you
will see how the permissions change from group to group. Note that
Manager and Administrator are allowed Administrator Login but Author,
Editor and Publisher are not. The latter are effectively Site roles
rather than Administrator roles.

All group permissions inherit from the Public group. It does not have
permission for any actions. However, by default items in the Public
group can be viewed, so assigning Public permission to an item will
allow it to be seen by all site visitors whether logged in or not.

### Articles Permissions

The Articles Permissions actions differ from the Global Configuration
Permissions actions. Not present are items related to login and present
are items related to workflows. This is a fairly typical pattern: a
component will have permissions relevant to the component; a component
item (such as an article) will have permissions relevant to that one
item.

<img
src="https://docs.joomla.org/images/thumb/7/7f/J4x-permissions-articles-en.png/800px-J4x-permissions-articles-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/7/7f/J4x-permissions-articles-en.png 1.5x"
data-file-width="1000" data-file-height="1037" width="800" height="830"
alt="J4x-permissions-articles-en.png" />

### Single Article Permissions

The single article permissions has just three items: Delete, Edit and
Edit State:

<img
src="https://docs.joomla.org/images/thumb/1/18/J4x-permissions-article-en.png/800px-J4x-permissions-article-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/1/18/J4x-permissions-article-en.png 1.5x"
data-file-width="1000" data-file-height="711" width="800" height="569"
alt="J4x-permissions-article-en.png" />

## Access Control Example: Special Purpose User

Suppose you need to create a User Group for users who have only one
responsibility, in this example an Article Administrator. Users in this
group should have Administrator Login permission but should not see
anything other than the Content items. Procedure:

### Create a new User Group

- Select **Users **→** Groups** from the Administrator menu.
- Select the `New` button in the Toolbar.
- Fill out the Group Title field: Article Administrator
- The Group Parent must be Public - it has no permissions for anything.

<img
src="https://docs.joomla.org/images/thumb/c/c6/J4x-permissions-article-administrator-en.png/800px-J4x-permissions-article-administrator-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/c/c6/J4x-permissions-article-administrator-en.png 1.5x"
data-file-width="1000" data-file-height="249" width="800" height="199"
alt="J4x-permissions-article-administrator-en.png" />

### Assign to Special

- Select **Users **→** Access Levels** from the Administrator menu.
- Select the **Special** item.
- Select the Article Administrator checkbox in the **Users: Edit Viewing
  Access Level** form.
- Save & Close.

<img
src="https://docs.joomla.org/images/thumb/5/59/J4x-permissions-article-administrator-special-en.png/800px-J4x-permissions-article-administrator-special-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/5/59/J4x-permissions-article-administrator-special-en.png 1.5x"
data-file-width="1000" data-file-height="470" width="800" height="376"
alt="J4x-permissions-article-administrator-special-en.png" />

### Global Configuration Permissions

- Select **Home Dashboard **→** Global Configuration** from the
  Administrator menu.
- Select the **Permissions** tab.
- Select the **Article Administrator** group.
- Set **Adminstrator Login** to Allowed.
- Save & Close

<img
src="https://docs.joomla.org/images/thumb/6/66/J4x-permissions-article-administrator-global-en.png/800px-J4x-permissions-article-administrator-global-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/6/66/J4x-permissions-article-administrator-global-en.png 1.5x"
data-file-width="1000" data-file-height="940" width="800" height="752"
alt="J4x-permissions-article-administrator-global-en.png" />

### Articles Options Permissions

- Select **Content **→** Articles** from the Administrator menu.
- Select the `Options` button from the Toolbar.
- Select the **Permissions** tab.
- Select the **Article Administrator** group.
- Set all items except the first two (Configure ACL & Options and
  Configure Options Only) to Allowed.
- Save & Close

<img
src="https://docs.joomla.org/images/thumb/e/ef/J4x-permissions-article-administrator-articles-en.png/800px-J4x-permissions-article-administrator-articles-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/e/ef/J4x-permissions-article-administrator-articles-en.png 1.5x"
data-file-width="1000" data-file-height="930" width="800" height="744"
alt="J4x-permissions-article-administrator-articles-en.png" />

### Create or Edit User

- Create a new user or edit an existing user who is not assigned to any
  groups
- Select **Article Administrator** in the **Assigned User Groups** tab
  of the User edit form.
- Save & Close.
- Login as a user in the Article Administrator Group only. The menu
  should show only article-related items:

<img
src="https://docs.joomla.org/images/thumb/4/40/J4x-permissions-article-administrator-menu-en.png/800px-J4x-permissions-article-administrator-menu-en.png"
class="thumbborder" decoding="async"
srcset="https://docs.joomla.org/images/4/40/J4x-permissions-article-administrator-menu-en.png 1.5x"
data-file-width="1000" data-file-height="451" width="800" height="361"
alt="J4x-permissions-article-administrator-menu-en.png" />
