# CONTEXT — Neurodiversiteit op de werkvloer

## Doel van het project

Een interactieve referentiepagina voor gebruik bij werksessies over neurodiversiteit bij ABT. De pagina toont negen veelvoorkomende neurodiverse kenmerken op de werkvloer, met per kenmerk:

- Een profiel (passende beroepen, typische functies en rollen, voordelen, aandachtspunten)
- Een casus: een vergaderverslag-mail geschreven vanuit dat kenmerk
- Een toelichting voor de trainer: waar let je op, welke kracht, welke valkuil
- Een blok "Als collega": eerst wat de samenwerking oplevert, dan waar je op let

Bovenaan staat een neutrale basismail — dezelfde vergadering, zonder uitgesproken kenmerk — als vergelijkingsbasis. Alle negen casusmails vatten hetzelfde ontwerpoverleg samen (project De Werf, verzonnen collega's); alleen de vorm verschilt.

De pagina volgt de ABT-huisstijl (blauw #0076C0, warmgrijze achtergrond, Inter) in een ronde, zachte uitvoering, en heeft een donkere variant die de systeeminstelling volgt. Elke kenmerk-kaart heeft een eigen kleur en motief die bij het kenmerk passen (zie `color`, `tcolor` en `motief` in de JSON).

---

## Bestandsstructuur

```
neurodiversiteit/
├── index.html       # De pagina — HTML, CSS en JavaScript in één bestand; leest kenmerken.json
├── kenmerken.json   # Alle inhoud: titel, categorieën, basismail en negen kenmerken met mail en toelichting
├── PROMPT.md        # De prompt waarmee de casusmails en toelichtingen worden (her)gegenereerd
└── CONTEXT.md       # Dit bestand
```

**`kenmerken.json` is de enige bron van de inhoud.** `index.html` bevat geen teksten van kenmerken; die worden bij het laden uit de JSON gehaald. Teksten aanpassen = de JSON aanpassen, niets aan de HTML.

`index.html` heeft wel een ingesloten kopie van de JSON als terugvaloptie: een browser mag een lokaal geopend bestand (`file://`) geen `kenmerken.json` laten ophalen. Open je `index.html` rechtstreeks vanaf schijf, dan zie je de kopie van de bouwdatum en meldt de pagina dat bovenaan. Op GitHub Pages wordt altijd de actuele JSON geladen.

---

## Huidige stand (laatst bijgewerkt: 28 september 2026)

### Wat werkt

- Negen kenmerk-kaarten in een raster van 3 / 2 / 1 kolommen (3×3 op een computer, één kolom op een telefoon), met categoriefilter (Alle / Aandacht / Sociaal / Executief / Sensorisch / Leren) en aantallen per categorie.
- Elke kaart draagt de kleur en het motief van het kenmerk: `color` (pasteltint), `tcolor` (tekst- en accentkleur) en `motief` uit de JSON. Beschikbare motieven in `index.html`: `vonk`, `raster`, `letters`, `gloed`, `cijfers`, `stippellijn`, `puls`, `lagen`, `sluier`. Ontbreekt `motief`, dan krijgt de kaart alleen de tint. Het detailpaneel neemt de kleur van het geopende kenmerk over; de mailmockup blijft bewust neutraal.
- Aanklikken opent een detailpaneel over de volle breedte direct onder de rij van die kaart (master-detail); Esc of × sluit het. Met ‹ › blader je door de kenmerken zonder terug te hoeven naar het raster — handig tijdens een sessie.
- Drie tabs per kenmerk: **Profiel** (beroepen en functies als doorlopende regel met scheidingstekens, voordelen en aandachtspunten naast elkaar), **Casus: mail** (mailmockup over de volle breedte met de toelichting eronder) en **Als collega** (*Wat brengt het mij* en *Waar let ik op*, drie punten elk, uit het veld `collega` met `helpt` en `letten`). De gekozen tab blijft staan bij het bladeren, zodat je alle mails of alle collega-blokken achter elkaar kunt vergelijken. Ontbreekt `collega`, dan verschijnt de tab niet.
- Neutrale basismail als aparte sectie met toon/verberg-knop; deze blijft staan bij filteren.
- Mailweergave: de eerste regel `Onderwerp: …` uit de JSON wordt de kop, de laatste regel de afzender; de rest wordt letterlijk getoond, inclusief regelafbrekingen en spelfouten (die zijn onderdeel van de casus).
- Toetsenbordbediening: kaarten, filters en tabs zijn knoppen met zichtbare focus.

### Wijzigingen 28 september 2026

- Tab **Als collega** toegevoegd, met de teksten uit het controledocument voor HR ("Neurodiversiteit - inhoud ter controle", 14 september 2026). Die teksten zijn op verzoek van Kobus alvast verwerkt; komt er nog een reactie van HR, dan worden ze in `kenmerken.json` aangepast.

### Wijzigingen 18 september 2026

- Pagina opnieuw opgebouwd op `kenmerken.json` als enige inhoudsbron; de oude `index.html` met inline data (juni 2026) is vervangen.
- Tien casusmails en toelichtingen gegenereerd volgens `PROMPT.md` (16 september 2026) en in de JSON gezet.
- Neutrale basismail toegevoegd aan de JSON als apart object `basismail` (titel, intro, mail, toelichting).
- Veld `functies` (typische functies en rollen) per kenmerk teruggezet in de JSON; dat stond in de juni-versie wel in de pagina maar ontbrak in `kenmerken.json`.
- Donkere variant toegevoegd; navigatie ‹ › in het detailpaneel.
- Dyspraxie (DCD) verwijderd op verzoek van Kobus; negen kenmerken over, de oorspronkelijke id's zijn behouden (6 ontbreekt). De aantallen in kop en intro komen nu uit de data.
- Rondere vormgeving (afgeronde kaarten, panelen en knoppen), kaartstijl per kenmerk in plaats van een categorielabel, en beroepen/functies als doorlopende regel in plaats van losse blokjes. Per kenmerk eigen `color`/`tcolor` in de JSON en een nieuw veld `motief`.

---

## Key decisions

| Beslissing | Reden |
|---|---|
| Inhoud in `kenmerken.json`, opmaak in `index.html` | Teksten zijn los van de code te (her)genereren met `PROMPT.md`, zonder risico voor de pagina |
| Ingesloten kopie van de JSON in `index.html` | Anders is de pagina leeg als je hem lokaal opent; op de website telt alleen de echte JSON |
| Eén vaste vergadering en vaste verzonnen collega's in alle mails | Zo zie je dat het kenmerk in de vorm zit, niet in de inhoud |
| Blok "Als collega" met eerst de opbrengst, dan de aandachtspunten | Collega's lezen eerst wat het oplevert; geen cijfers, geen namen, gedrag in plaats van persoon (keuze Kobus, 14 sep 2026) |
| Neutrale basismail als apart object en aparte sectie | Expliciete vergelijkingsbasis vóór de negen varianten |
| Driebreed raster, detailpaneel over de volle breedte | Compact overzicht; details krijgen de ruimte |
| Geen navigatiebalk | Standalone tool, geen onderdeel van de ABT-website |
| Ronde, zachte uitvoering en een eigen kaartstijl per kenmerk | De vorm van de kaart zegt iets over het kenmerk, net als de vorm van de mail; een kaal raster deed dat niet (keuze Kobus, 18 sep 2026) |

---

## Inhoud aanpassen

1. **Mails opnieuw laten schrijven**: plak de prompt uit `PROMPT.md` samen met `kenmerken.json` in Claude; laat alleen `mail` en `toelichting` invullen. Zet het resultaat terug als `kenmerken.json`.
2. **Losse tekst wijzigen**: pas de tekst in `kenmerken.json` aan. Let op: `\n` is een regelafbreking, aanhalingstekens in de tekst als `\"`. Controleer daarna dat het bestand geldige JSON is (bijvoorbeeld via jsonlint.com).
3. **Kenmerk toevoegen**: kopieer een object in `kenmerken`, geef het een nieuw `id` en een bestaande `cat`, en kies een `color`, `tcolor` en `motief`. De pagina pikt het automatisch op; ontbreekt `functies`, `motief` of `collega`, dan laat de pagina dat gewoon weg.
4. **Reactie van HR verwerken**: de teksten van "Als collega" staan per kenmerk in `collega.helpt` (wat brengt het mij) en `collega.letten` (waar let ik op); de casusmails in `mail` en `toelichting`.

---

## Openstaande taken

- [ ] **ABT-logo** — er staat alleen een tekstregel "ABT · Werksessie neurodiversiteit" in de kop; een logobestand is nog niet in de repo opgenomen.
- [ ] **GitHub Pages controleren** — Settings → Pages → Source `main` / `/ (root)`. De pagina staat dan op `https://kobusvanderzwaal.github.io/neurodiversiteit/`.
- [ ] **Mobiele weergave op een echt toestel bekijken** — de kolommen schakelen bij 900 en 620 px; dat is in een browservenster getest, niet op een telefoon.
- [ ] **Reactie HR** — het controledocument ligt bij een werkgroeplid van HR; de teksten staan alvast op de pagina en worden aangepast als er opmerkingen komen.
- [ ] **Open keuzes uit de toetsing van 14 september** — een zin boven de dyslexie-mail dat de spelfouten bewust zijn; de klinische namen "Executieve disfunctie" en "Angst & sociale fobie"; en de plek van "Hoogsensitiviteit (HSP)" naast erkende diagnoses. Alle drie vragen voor Kobus of HR, niet voor de bouwer.
