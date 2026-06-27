# Trænings Tracker — projektkontekst

## Hvad er dette?
En PWA (Progressive Web App) til at tracke armbøjninger og pull-ups efter løbeture.
Appen er en enkelt HTML-fil (`index.html`) uden eksterne afhængigheder.

## Stack
- **Frontend:** Vanilla HTML/CSS/JS — ingen frameworks, ingen build-step
- **Database:** Google Sheets via Google Apps Script
- **Hosting:** GitHub Pages

## Vigtige URLs
- **Live app:** `https://[dit-github-brugernavn].github.io/traening`
- **Google Apps Script endpoint:** `https://script.google.com/macros/s/AKfycbwa7-PhUsp9jwF1huZvDejumsMW0CkOEkmAQd3WrFqw_4Ads_CByk3CmKVrGsOYrb24/exec`
- **Google Sheet:** `https://docs.google.com/spreadsheets/d/1p2GZPQD-KnubNlxBqoT9rJOD6cTFQbSC72-Urs6Xo1A`

## Struktur i Google Sheet
Fanen hedder `Workouts` med kolonner:
`Dato | Armbøjninger sæt | Armbøjninger total | Pull-ups sæt | Pull-ups total | Følelse`

Sæt gemmes som kommaseparerede tal, fx `10,8,9`.

## Sådan kører du lokalt
Installer **Live Server**-extension i VS Code, højreklik på `index.html` → "Open with Live Server".
For iPhone-visning: F12 i Chrome → mobil-ikon → vælg iPhone-model.

## Arkitektur i index.html
- `state.program` — gemmes i `localStorage` (brugerindstillinger)
- `state.workouts` — hentes fra Google Sheets ved hver besøg på Historik-fanen
- `fetchWorkouts()` — GET til Apps Script, returnerer alle rækker
- `postWorkout()` — POST til Apps Script, tilføjer én række
- `session` — midlertidigt objekt for den aktuelle træning (nulstilles efter gem)

## Øvelser der trackes
- 💪 Armbøjninger
- 🏋️ Pull-ups

## Features
- Log sæt med +/− tæller
- Marker træning som let/passende/hårdt
- Grafer over total reps per session
- Program-side med justerbare mål (reps og antal sæt)
- Automatiske forslag baseret på seneste "følelse"-input

## Deployment
Commit og push til `main` → GitHub Pages opdaterer automatisk inden for ~1 minut.
