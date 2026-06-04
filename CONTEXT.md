# CONTEXT — Neurodiversiteit op de werkvloer

## Doel van het project

Een interactieve referentiepagina voor gebruik bij informatiesessies over neurodiversiteit bij ABT. De pagina geeft een overzicht van de tien meest voorkomende neurodiverse kenmerken op de werkvloer, met per kenmerk:

- Een profiel (passende beroepen, voordelen, aandachtspunten)
- Een realistische casus: een vergaderverslag-mail geschreven vanuit dat kenmerk
- Een trainerstoelichting die de herkenbare patronen duidt

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

## Key decisions

| Beslissing | Reden |
|---|---|
| Alles in één HTML-bestand | Geen server nodig, makkelijk te delen en te hosten via GitHub Pages |
| Twee kolommen (was drie) | Kaarten zijn beter leesbaar als ze openklappen bij meer breedte |
| Neutrale basismail als aparte sectie | Geeft deelnemers een expliciete vergelijkingsbasis vóór de tien varianten |
| ABT huisstijl | Pagina is bedoeld voor gebruik binnen ABT-context |
| Geen navigatiebalk | Pagina is een standalone tool, geen onderdeel van de ABT-website |
| Kaarten zonder afgeronde hoeken | Past bij het strakke, zakelijke ABT-design |
| Tab-indeling per kaart (Profiel / Casus: mail) | Houdt de kaart compact; je kiest zelf wat je wil zien |

---

## Openstaande taken

- [ ] **ABT-logo toevoegen** — het logo-afbeeldingsbestand is nog niet in de repo opgenomen; het navbar-logo is nu puur CSS-tekst
- [ ] **Mobiele weergave testen** — basis responsive CSS zit erin, maar nog niet visueel geverifieerd op klein scherm
- [ ] **Filterwerking controleren** — bij filteren op categorie verdwijnen kaarten correct, maar de basismail-sectie blijft altijd zichtbaar (gewenst gedrag?)
- [ ] **Eventuele uitbreiding** — extra neurodiverse kenmerken of een tweede casus-type toevoegen is eenvoudig via het `data`-array in het script
- [ ] **Hosting** — overweeg GitHub Pages in te schakelen zodat de pagina live bereikbaar is via een URL

---

## Wat te doen als volgende stap

1. **Logo toevoegen**: sla het ABT-logo op als `abt-logo.png` in de projectmap en vervang in `index.html` het stuk `<div class="navbar-logo">...</div>` door `<img src="abt-logo.png" alt="ABT" height="40">` — of geef het bestand mee aan Claude Code.
2. **GitHub Pages aanzetten**: ga naar [github.com/KobusvanderZwaal/neurodiversiteit](https://github.com/KobusvanderZwaal/neurodiversiteit) → Settings → Pages → Source: `main` / `/ (root)`. De pagina is dan live op `https://kobusvandderzwaal.github.io/neurodiversiteit/`.
3. **Inhoud aanpassen**: alle teksten, mails en trainerstoelichtingen staan in het `data`-array in het `<script>`-blok onderaan `index.html`. Je kunt kenmerken toevoegen, wijzigen of verwijderen zonder iets aan de opmaak te veranderen.
