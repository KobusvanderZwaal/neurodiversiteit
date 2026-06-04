# CONTEXT — Neurodiversiteit op de werkvloer

## Doel van het project

Een interactieve referentiepagina voor gebruik bij informatiesessies over neurodiversiteit bij ABT. De pagina geeft een overzicht van de tien meest voorkomende neurodiverse kenmerken op de werkvloer, met per kenmerk:

- Een profiel (passende beroepen, voordelen, aandachtspunten)
- Een realistische casus: een vergaderverslag-mail geschreven vanuit dat kenmerk
- Een toelichting die de herkenbare patronen duidt

Als referentie staat bovenaan een neutrale basismail — dezelfde situatie, zonder uitgesproken neurodiverse kenmerken — zodat deelnemers de varianten direct kunnen vergelijken.

De pagina volgt de ABT huisstijl (blauw #0076C0, warme grijze achtergrond, Inter font).

---

## Bestandsstructuur

```
neurodiversiteit/
├── index.html       # Volledige applicatie — HTML, CSS en JavaScript in één bestand
└── CONTEXT.md       # Dit bestand
```

Alles zit in één `index.html`. Er is geen buildstap, geen framework, geen dependencies behalve Google Fonts (Inter). De pagina werkt direct als je het bestand opent in een browser.

---

## Huidige stand (laatst bijgewerkt: 4 juni 2026)

### Wat werkt

- De pagina draait volledig client-side vanuit één `index.html` — geen server, geen build, geen dependencies behalve Google Fonts.
- Tien kenmerk-kaarten plus de neutrale basismail, volledig in ABT-huisstijl.
- **Categoriefilter** (Alle / Aandacht / Sociaal / Executief / Sensorisch / Leren) toont en verbergt kaarten; de basismail-sectie blijft daarbij altijd staan.
- **Uitklappen over de volle breedte** (master-detail): klik je een tegel aan, dan licht die op en verschijnt het detailpaneel over de volle paginabreedte, direct onder de rij van die tegel — zonder lege gaten in het grid en met behoud van de kaartvolgorde.
- **Twee tabs per detailpaneel:** *Profiel* (passende beroepen, plus voordelen en aandachtspunten in twee kolommen naast elkaar) en *Casus: mail* (de mailmockup over de volle breedte met de toelichting eronder).
- Basismail-sectie met een toon/verberg-knop.
- **Responsief:** 3 kolommen (≥ 901px), 2 kolommen (701–900px), 1 kolom (≤ 700px); het detailpaneel wordt bij resize correct opnieuw onder de juiste rij geplaatst.
- Toetsenbordbediening: tegels zijn met Enter/Spatie te openen.

### Recent gewijzigd (commit `7655306`)

- Uitklappen toont de details nu over de volle paginabreedte (master-detail patroon) — voorheen ingeklemd binnen één kolom.
- Tegelgrid weer driebreed met responsieve tussenstappen (3 / 2 / 1) — was vast tweebreed.
- Profiel-tab: voordelen en aandachtspunten in twee kolommen.
- Mail-casus over de volle breedte met de toelichting eronder, voor betere leesbaarheid.
- Label "Trainerstoelichting" hernoemd naar "Toelichting".
- Wijzigingen zijn gepusht naar `main` op GitHub.

---

## Key decisions

| Beslissing | Reden |
|---|---|
| Alles in één HTML-bestand | Geen server nodig, makkelijk te delen en te hosten via GitHub Pages |
| Driebreed tegelgrid (responsief 3 / 2 / 1) | Compacte overzichtsweergave; de details komen los daaronder, dus de tegels mogen smal blijven |
| Full-width detailpaneel (master-detail) | Uitklappen toont de details onder de rij over de volle breedte i.p.v. ingeklemd in één smalle kolom |
| Profiel in twee kolommen, mail over de volle breedte | Benut de extra breedte; de mail blijft over de volle breedte goed leesbaar, de toelichting staat eronder |
| Neutrale basismail als aparte sectie | Geeft deelnemers een expliciete vergelijkingsbasis vóór de tien varianten |
| ABT huisstijl | Pagina is bedoeld voor gebruik binnen ABT-context |
| Geen navigatiebalk | Pagina is een standalone tool, geen onderdeel van de ABT-website |
| Kaarten zonder afgeronde hoeken | Past bij het strakke, zakelijke ABT-design |
| Tab-indeling per detail (Profiel / Casus: mail) | Houdt het paneel overzichtelijk; je kiest zelf wat je wil zien |

---

## Openstaande taken

- [ ] **ABT-logo toevoegen** — het logo-afbeeldingsbestand is nog niet in de repo opgenomen; het navbar-logo is nu puur CSS-tekst
- [ ] **Mobiele weergave visueel testen** — de responsive CSS (3 / 2 / 1 kolom) zit erin, maar is nog niet visueel geverifieerd op klein scherm
- [ ] **Filterwerking controleren** — bij filteren op categorie verdwijnen kaarten correct, maar de basismail-sectie blijft altijd zichtbaar (gewenst gedrag?)
- [ ] **GitHub Pages controleren** — de code staat op `main`; controleer of Pages aanstaat zodat de pagina live bereikbaar is via een URL
- [ ] **Eventuele uitbreiding** — extra neurodiverse kenmerken of een tweede casus-type toevoegen is eenvoudig via het `data`-array in het script

---

## Wat te doen als volgende stap

1. **Logo toevoegen**: sla het ABT-logo op als `abt-logo.png` in de projectmap en vervang in `index.html` het stuk `<div class="navbar-logo">...</div>` door `<img src="abt-logo.png" alt="ABT" height="40">` — of geef het bestand mee aan Claude Code.
2. **GitHub Pages aanzetten/controleren**: ga naar [github.com/KobusvanderZwaal/neurodiversiteit](https://github.com/KobusvanderZwaal/neurodiversiteit) → Settings → Pages → Source: `main` / `/ (root)`. De pagina is dan live op `https://kobusvanderzwaal.github.io/neurodiversiteit/`.
3. **Inhoud aanpassen**: alle teksten, mails en toelichtingen staan in het `data`-array in het `<script>`-blok onderaan `index.html`. Je kunt kenmerken toevoegen, wijzigen of verwijderen zonder iets aan de opmaak te veranderen.
