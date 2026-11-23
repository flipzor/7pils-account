# 7 Pils — 7pils.nl

De website van de Android-app **7 Pils** (die repo is privé), gepubliceerd via GitHub Pages op
<https://7pils.nl/> (het oude adres `flipzor.github.io/7pils-account/` stuurt daarheen door).
Drie losse HTML-bestanden zonder bouwstap:

| Pagina        | Wat                                                        |
|---------------|------------------------------------------------------------|
| `index.html`  | de voordeur: meekijken zonder app (zie hieronder)          |
| `account.html`| de accountpagina                                           |
| `app.html`    | de app downloaden                                          |
| `kijk.html`   | alleen een doorverwijzing naar de voordeur, voor oude links |

## Accountpagina (`account.html`)

Hij doet drie dingen:

- **de bevestigingsmail** na het registreren landt hier;
- **wachtwoord vergeten**: de link uit de mail komt hier uit en je kiest een nieuw wachtwoord;
- **account verwijderen zonder de app** — dat eist Google zodra een app accounts kent.

Deze repo is publiek omdat GitHub Pages op een gratis account alleen publieke repo's serveert.
Dat kan ook: er staat niets geheims in. De `sb_publishable_...`-sleutel is bedoeld om
uitgedeeld te worden en geeft in zijn eentje niets — alle rechten liggen in de RLS-policies
van het Supabase-project, en verwijderen gaat via een edge function die zelf controleert wie
er belt.

Het verwijderen zelf gebeurt niet hier maar in de edge function `account` van het project:
een account weghalen vraagt de service-sleutel, en die hoort nergens in een browser of op een
telefoon te staan.

Een mail van Supabase die nog naar de voordeur wijst (oudere appversies, al verstuurde mails)
stuurt `index.html` meteen door naar `account.html`, met alles achter de `#` erbij.

## Meekijken zonder app (`index.html`)

Wie van een beheerder een kijkcode krijgt, ziet op
<https://7pils.nl/> de statistieken en de selectie van het
lopende seizoen, zonder account en zonder app. De beheerder deelt de link vanuit de app
(☰ → Account → Meekijken zonder app); de code staat erin achter een `#`.

De pagina rekent niets uit. De app van de beheerder zet een kant-en-klare momentopname op de
server, en de edge function `kijken` geeft die terug bij een geldige code. Er staan alleen
namen, rugnummers, posities en tellingen in, geen geboortedata, notities of foto's.

