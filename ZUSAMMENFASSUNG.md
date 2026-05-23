# Website-Zusammenfassung – Luftfahrtversicherung

## Projektübersicht

Einzelne `index.html`-Datei für einen Luftfahrtversicherungs-Spezialisten.  
Design-Anspruch: Privatbank-Ästhetik — ruhig, präzise, hochwertig.  
Zielgruppe: Privatjet-Besitzer, Unternehmer, UHNW-Kunden.

---

## Dateistruktur

```
Website für Herr Grümmer/
└── index.html          (1666 Zeilen — HTML + CSS + JS, alles inline)
```

Keine externen Abhängigkeiten. Kein Framework. Kein Google Fonts.

---

## Seitenstruktur

| # | Sektion | Hintergrund | Besonderheit |
|---|---|---|---|
| 1 | Navigation | Weiß, sticky | Hamburger-Menü (Mobile), Sprachumschalter (5 Sprachen) |
| 2 | Hero | Gradient-Placeholder (navy) | Gold-Tag, zwei CTAs |
| 3 | Trust Bar | `--color-bg-dark` | 3 Kennzahlen, goldene Trennlinien |
| 4 | Versicherungsprodukte | `--color-bg-alt` | Liste mit Trennlinien, kein Icon-Grid |
| 5 | Warum wir | `--color-bg-dark` | Asymmetrisch, 3 Expertise-Punkte |
| 6 | FAQ | Weiß | `<details>`-Accordion, CSS-Pfeil |
| 7 | Kontakt | `--color-bg-alt` | 2 Spalten: Infos + Formular |
| 8 | Footer | `#1A1A1A` | 3 Spalten, BaFin-Pflichtangaben |
| 9 | Impressum / Datenschutz | `--color-bg-dark` | Ausklappbar via `<details>` |

---

## Design-System

### Farben
```
--color-accent:      #185FA5   Hauptakzent, Buttons, Links
--color-accent-dark: #0F3F6E   Hover-States
--color-dark:        #1A1A1A   Navigation, Footer
--color-bg:          #FFFFFF   Haupthintergrund
--color-bg-alt:      #F4F5F7   Alternierende Sections
--color-bg-dark:     #0D1B2A   Premium-Flächen (Hero, Expertise, Footer)
--color-text:        #2C2C2C   Fließtext
--color-text-muted:  #6B7280   Subtext, Labels, Disclaimers
--color-border:      #E5E7EB   Trennlinien
--color-gold:        #C9A84C   Sparsamster Akzent (Linie, Tag)
```

### Schriften
- **Headlines:** `Georgia, Times New Roman, serif` — klassisch, kein AI-Template-Look
- **Fließtext:** System-Font-Stack (`-apple-system, BlinkMacSystemFont, Segoe UI …`)
- Kein Google Fonts-Request

---

## Platzhalter befüllen

Alle Stellen sind mit `[ECKIGEN KLAMMERN]` markiert und mit `<!-- TEXT: … -->`-Kommentaren versehen.

| Platzhalter | Wo |
|---|---|
| `[FIRMENNAME]` | Navigation, Hero, Sections, Footer, JSON-LD |
| `[NAME]` | Impressum |
| `[RECHTSFORM]` | Footer-Disclaimer, Impressum |
| `[STRASSE]`, `[PLZ]`, `[STADT]` | Kontakt, Footer, JSON-LD |
| `[TELEFON]` | Alle `tel:`-Links |
| `[EMAIL]` | Alle `mailto:`-Links |
| `[BAFIN-NR]` | Trust Bar, Footer, Impressum |
| `[JAHR]` | Trust Bar, Expertise-Text, Footer-Copyright |
| `[ZAHL]` | Trust Bar (Jahre Erfahrung) |
| `[REGION]` | Trust Bar, Footer-Tagline |
| `[PRODUKT 1–5]` | Produkte-Section |
| `[FRAGE 1–5]` + `[ANTWORT 1–5]` | FAQ-Section |
| `[ZUSTÄNDIGE IHK]` | Footer-Disclaimer, Impressum |
| `[NUMMER OHNE FÜHRENDE NULL]` | `tel:`-Links (z.B. `+49151...`) |

---

## Rechtliche To-dos vor Launch

- [ ] BaFin-Registrierungsnummer korrekt eintragen (§ 34d GewO)
- [ ] IDD-Pflichtangaben vollständig (EU-Versicherungsvertriebsrichtlinie)
- [ ] Berufshaftpflichtversicherung im Impressum nennen
- [ ] Datenschutzerklärung DSGVO-konform ergänzen
- [ ] Impressum vollständig nach § 5 TMG
- [ ] VVG-Pflichthinweise im Footer prüfen
- [ ] Fachanwalt für Versicherungsrecht oder Compliance-Berater einbinden

---

## Mehrsprachigkeit (i18n)

Der Sprachumschalter befindet sich oben rechts in der Navigation (sichtbar auf Desktop und Mobile).

**Verfügbare Sprachen:**

| Code | Sprache | Flagge |
|---|---|---|
| `de` | Deutsch | 🇩🇪 (Standard) |
| `en` | English | 🇬🇧 |
| `fr` | Français | 🇫🇷 |
| `es` | Español | 🇪🇸 |
| `zh` | 中文 | 🇨🇳 |

**Technische Umsetzung:**
- Reines JavaScript — kein Framework, keine externe Bibliothek
- Übersetzungsobjekt `t` am Ende von `index.html` (letzter `<script>`-Block)
- `window.setLanguage('en')` wechselt alle statischen Texte per `querySelector`/`innerHTML`/`textContent`
- Platzhalter wie `[FIRMENNAME]` bleiben in allen Sprachen erhalten
- Formular-Validierungsmeldungen, Sende-Button-Beschriftungen und Erfolgsnachricht werden ebenfalls übersetzt
- `document.documentElement.lang` wird bei Sprachwechsel aktualisiert (SEO/Accessibility)

**Übersetzte Bereiche:** Navigation · Hero · Trust-Leiste · Produkte-Header · Expertise-Section · FAQ-Header · Kontaktformular · Footer (komplett inkl. Disclaimer)

**Nicht übersetzt (by design):** Produkt-Platzhalter (`[PRODUKT 1–5]`), FAQ-Platzhalter (`[FRAGE/ANTWORT 1–5]`), Impressum & Datenschutz, Developer-Signatur

---

## Kontaktformular

Das Formular validiert clientseitig (Name, E-Mail, Nachricht Pflichtfelder).  
**Der Submit-Handler ist ein Platzhalter** — vor Launch durch echten Endpunkt ersetzen:

```js
// index.html, Zeile ~1270 im <script>-Block
// Empfohlen: Formspree, Netlify Forms oder eigenes Backend
fetch('https://formspree.io/f/XXXX', { method: 'POST', body: new FormData(form) })
```

---

## GitHub

Repository: https://github.com/jotom7-dotcom/herrgr-mmerwebsite

Push-Befehl (nach Authentifizierung):
```bash
cd "/Users/jo/claudecode/Website für Herr Grümmer"
git remote set-url origin https://jotom7-dotcom@github.com/jotom7-dotcom/herrgr-mmerwebsite.git
git push -u origin main
```

---

## Erstellt von

Johannes Ben Toman · [tomandesign7@gmail.com](mailto:tomandesign7@gmail.com)
