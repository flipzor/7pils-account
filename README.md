# 7 Pils — accountpagina

Eén HTML-bestand, gepubliceerd via GitHub Pages op
<https://flipzor.github.io/7pils-account/>. Het hoort bij de Android-app **7 Pils** (die repo
is privé) en doet drie dingen:

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
