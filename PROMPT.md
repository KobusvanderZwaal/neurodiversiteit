# PROMPT.md — neurodiversiteit

Werkbestand voor het project *Neurodiversiteit op de werkvloer*. De inhoudelijke data staat in `kenmerken.json`. De layout wordt apart gemaakt in Claude Design. Dit bestand bevat de prompt om de casusmails te (her)genereren.

---

## Context

Interactieve, deelbare pagina voor collega's in een ontwerp-/ingenieursbureau. Doel: laten zien hoe een neurodivers kenmerk zich uit in een zakelijke context, en wat daarvan het voordeel en het nadeel is. Wordt gebruikt tijdens trainingssessies en gedeeld via GitHub Pages.

Tien kenmerken, vijf categorieën (aandacht, sociaal, executief, sensorisch, leren). Per kenmerk: beroepen, voordelen, aandachtspunten, één casusmail en een trainerstoelichting. In de UI zit elk kenmerk in een kaart met twee tabs: **Profiel** en **Casus: mail**.

---

## Prompt — casusmails genereren

> Plak dit als één bericht, samen met `kenmerken.json`.

**ROL**
Je bent trainer neurodiversiteit en inclusie.

**DOEL**
Mensen een beeld geven hoe een neurodivers kenmerk zich uit in een zakelijke context en wat daar het voordeel en het nadeel van is.

**CASUS**
Een herkenbare situatie voor een ontwerpbureau. Naar aanleiding van een ontwerpoverleg maakt iemand een mail met het verslag en de acties van de vergadering.

Maak voor elk van de 10 neurodiverse kenmerken in `kenmerken.json` een karakteristieke mail die de positieve kanten **én** de negatieve kanten van dat kenmerk weergeeft.

- De mail is maximaal 6 zinnen en bevat aanvullend 3 actiepunten.
- De volgorde, de lay-out en de informatie van de acties mogen en moeten het neurodiverse kenmerk weergeven. Het kenmerk zit dus niet in de *inhoud* van de mail maar in de *vorm*: toon, structuur, spelling, detailniveau, prioritering, wat wél en niet benoemd wordt.
- Gebruik fictieve collega's en één fictief project, consistent over alle tien de mails, zodat het dezelfde vergadering is die tien keer anders wordt samengevat.
- Schrijf onder elke mail een **trainerstoelichting** van 2–4 zinnen: waar moet de kijker op letten, welke sterke kant zie je terug, welke valkuil. Benoem het gedrag, niet de persoon.

**OUTPUT**
Geef `kenmerken.json` terug met de velden `mail` en `toelichting` per kenmerk ingevuld. Verder niets wijzigen — geen andere velden aanpassen, geen kenmerken toevoegen of weglaten.

Lever het resultaat op als **downloadbaar bestand**, niet als tekst in de chat. Tien mails plus toelichtingen is een lange output; in de chat loopt die kans op afkappen en moet ik hem handmatig overnemen. Controleer vóór oplevering dat het bestand geldige JSON is.

---

## Aandachtspunten uit eerdere iteraties

- Apostrofs (`Jan's`, `collega's`) braken de JavaScript toen de data in single-quoted strings stond. Bij JSON speelt dit niet, maar let erop zodra de data in een `<script>`-blok wordt ingebed.
- De mails zijn karikaturaal genoeg om herkenbaar te zijn, maar mogen niet spottend worden — de trainerstoelichting moet dat expliciet corrigeren.
- Publiceren: repo public, bestand als `index.html`, Settings → Pages → Deploy from a branch → `main` / root.
