# RSS — Žan Lah Koštomaj photography site

Statična večstranska spletna predstavitev fotografa, postavljena na **HTML5 + Bootstrap 5**. Predloge so povzete po Figma prototipu (`RSS-Prototip.fig`) — ohranja se postavitev, tipografija (Marcellus / Marcellus SC / Inria Sans) in barvna paleta (črna, bela, siva #d9d9d9, rumena #ffd400).

## Strukture map

```
.
├── index.html        — Domov (hero + carousel + galerija)
├── o-meni.html       — Predstavitev + "Moji Dogodki"
├── storitve.html     — Štiri kartice storitev
├── galerija.html     — Foto galerija + komentarji
├── kontakt.html      — Kontaktni podatki + obrazec + zemljevid
├── 404.html          — Prazna stran
├── assets/           — Slike in ikone iz prototipa
├── css/style.css     — Pred-prevedena stilnica (brand override + utility)
├── scss/             — Izvorni SASS (variables, main, site)
└── partials/         — Skupne HTML komponente za referenco
```

## Bootstrap 5 funkcije, ki so v rabi

- `navbar` z `navbar-expand-lg` in `collapse` (hamburger meni za telefon)
- `carousel` z indikatorji in kontrolami na domači strani
- Mreža (`container` / `row` / `col-*`) z odzivnimi prelomi (`col-6 col-lg-3` ipd.)
- `g-3 g-lg-4` razmiki, `gap-*`, `d-flex`, `align-items-*`, `justify-content-*` utility razredi
- Obrazec (`form-control`, `form-label`, `btn`)
- Pomožni razredi za tipografijo, prikaz in razmike

## SASS / SCSS

Predvideni potek prevoda:

```bash
npm install bootstrap sass
npx sass scss/main.scss css/style.css --watch
```

`scss/_variables.scss` predefinira Bootstrapove spremenljivke (`$primary`, `$font-family-base`, `$border-radius`, …) **pred** `@import "bootstrap"`. `scss/_site.scss` doda lasten brand sloj. Datoteka `css/style.css` v repozitoriju je posnetek prevoda za primere, ko SASS verige ni na voljo (jo pa preglasi tudi živi prevod, če ga zaženete).

## Git / Kanban

- Vsaka stran je razvita na svoji veji (`feature/domov`, `feature/o-meni`, `feature/storitve`, `feature/galerija`, `feature/kontakt`, `feature/404`).
- Po pregledu se vejo zlije nazaj na `main` (`git merge --no-ff`).
- Kanban: `Todo → In progress → Review → Done`, na kartici se zapiše avtor, datum in povezava na PR.

## Kompresija multimedije

Slike v `assets/` so preneseni izrezi iz Figme. Pred objavo je priporočeno:

```bash
# JPEG (mozjpeg) ~80 kakovost
cjpeg -quality 80 -outfile out.jpg in.jpg
# PNG
oxipng -o4 *.png
# SVG
svgo -f assets/
```

