# 🍽 Lunchboard

> Einfaches Homeoffice-Tool zur täglichen Koordination von Frühstücks- und Mittagspausen im Team.

---

## Was ist Lunchboard?

Lunchboard ist eine **einzelne HTML-Datei** — kein Backend, keine Installation, keine Abhängigkeiten. Das Tool läuft direkt im Browser und speichert alle Daten lokal auf dem Gerät. Es ist optimiert für die Nutzung auf einem **Tablet im Pausenraum** sowie auf dem **Handy im Homeoffice**.

---

## Features

### ✅ Tägliche Pausenkoordination
- Zwei Pausenblöcke: **Frühstück** und **Mittagessen**
- Jede Person gibt an, ob sie dabei ist oder nicht
- Status: **Dabei** (grün) / **Nein** (rot) / **Offen** (neutral)

### ⏰ Zeitwahl pro Person
- Jede Person wählt ihre eigene Wunschzeit für die Pause
- Zeitslots in **15-Minuten-Schritten**
- Standardzeit voreingestellt (konfigurierbar)
- Frühstück: Standard **09:30**, Bereich **09:00–10:30**
- Mittagessen: Standard **12:30**, Bereich **12:00–14:00**

### ⏱ Pausendauer pro Person
- Jede Person gibt an, wie lange sie für die Pause Zeit hat
- Optionen: **15 / 30 / 45 / 60 Minuten**
- Frühstück: Standard **15 min**
- Mittagessen: Standard **45 min**
- Standard-Dauer je Pause konfigurierbar über die Einstellungen

### 💛 Match-Erkennung
- Sobald alle anwesenden Personen **dieselbe Uhrzeit** gewählt haben, erscheint ein animiertes Match-Banner
- Drei pulsierende Herzen + Konfetti-Effekt beim ersten Match
- Der ausgewählte Zeitchip leuchtet pink hervor
- Karte erhält einen dezenten rosafarbenen Leuchtrahmen

### 🍽 Essenswünsche (Mittagessen)
- Freitextfeld für Restaurantwünsche, Bestellvorschläge etc.
- Wird täglich automatisch zurückgesetzt

### ⚙️ Einstellungen
- **Personen verwalten:** Namen hinzufügen oder entfernen
- **Pausenzeiten konfigurieren:** Start- und Endzeit pro Pause frei wählbar (7:00–20:00, 15-min-Schritte)
- **Standard-Zeit pro Pause** direkt wählbar
- **Standard-Dauer pro Pause** wählbar (15 / 30 / 45 / 60 min)
- Alle Einstellungen werden im Browser gespeichert

### 🔄 Automatischer Tages-Reset
- Beim ersten Öffnen eines neuen Tages werden alle Status automatisch zurückgesetzt
- Einstellungen (Personen, Zeiten) bleiben dauerhaft erhalten
- Manueller Reset jederzeit per Button „Tag zurücksetzen"

### 📱 Mobile-First Design
- Optimiert für Smartphone und Tablet
- Große, fingertaugliche Buttons (min. 44×46 px)
- Sticky Header mit Blur-Effekt
- Automatisches 2-Spalten-Layout ab 680 px Breite (Desktop)

---

## Dateistruktur

Das Tool besteht aus **einer einzigen Datei**:

```
index.html        ← Die gesamte App (HTML + CSS + JavaScript)
README.md         ← Diese Dokumentation
```

Keine weiteren Dateien, Ordner, Node-Module oder Build-Schritte nötig.

---

## Technologie

| Komponente | Details |
|------------|---------|
| **Sprache** | Vanilla HTML, CSS, JavaScript (kein Framework) |
| **Schrift** | Inter via Google Fonts (CDN) |
| **Datenspeicherung** | `localStorage` im Browser |
| **Backend** | Keines — vollständig clientseitig |
| **Abhängigkeiten** | Keine npm-Pakete, keine Build-Tools |

---

## Installation & Deployment

### Lokal ausführen

```bash
# Einfach die Datei im Browser öffnen:
open index.html
```

Kein Server nötig — die Datei funktioniert direkt als `file://`-Pfad.

---

### GitHub Pages (empfohlen)

1. Neues GitHub-Repository anlegen (z.B. `lunchboard`)
2. `index.html` und `README.md` in das Repo hochladen
3. Im Repo: **Settings → Pages → Branch: main → Save**
4. Nach ~1 Minute erreichbar unter:

```
https://DEIN-USERNAME.github.io/lunchboard
```

---

### Netlify Drop (schnellste Option)

1. [app.netlify.com/drop](https://app.netlify.com/drop) öffnen
2. `index.html` per Drag & Drop einwerfen
3. Sofort live unter einer öffentlichen URL

---

## Konfiguration (Einstellungen-Menü)

Alle Einstellungen sind direkt in der App über das **⚙️-Icon** oben rechts erreichbar.

### Personen verwalten

| Aktion | Beschreibung |
|--------|-------------|
| **Hinzufügen** | Name eingeben + Enter oder „+ Hinzufügen" |
| **Entfernen** | „Entfernen"-Button neben dem Namen |
| **Mindestanzahl** | Mindestens 1 Person muss vorhanden sein |

Jede neue Person erhält automatisch eine Farbe aus einer vordefinierten Palette.

### Pausenzeiten konfigurieren

Pro Pause (Frühstück / Mittagessen) konfigurierbar:

| Feld | Beschreibung |
|------|-------------|
| **Von** | Startzeit (Stunde + Minute, je 15-min-Schritte) |
| **Bis** | Endzeit (Stunde + Minute, je 15-min-Schritte) |
| **Standard-Zeit** | Vorausgewählte Uhrzeit beim Tagesstart |
| **Standard-Dauer** | Vorausgewählte Dauer beim Tagesstart (15 / 30 / 45 / 60 min) |

Der Zeitbereich kann frei zwischen **07:00 und 20:00** gewählt werden. Die Zeitchips werden automatisch auf Basis von Start, Ende und 15-min-Schritten generiert.

---

## Datenspeicherung

| Was | Wo | Wie lange |
|-----|----|-----------|
| Tagesstatus (Dabei/Nein/Zeit) | `localStorage` | Bis Ende des Tages |
| Essenswünsche (Notiz) | `localStorage` | Bis Ende des Tages |
| Personen & Einstellungen | `localStorage` | Dauerhaft |

> **Hinweis:** Da `localStorage` gerätebezogen ist, sieht jedes Gerät seinen eigenen Stand. Für geräteübergreifende Synchronisation wäre ein Backend (z.B. Firebase oder Supabase) nötig.

---

## Bekannte Einschränkungen

- **Kein Echtzeit-Sync:** Jedes Gerät/Browser hat seinen eigenen Speicher. Änderungen von Daniel auf seinem Laptop sind auf Lisas Handy nicht sichtbar.
- **Kein Login:** Jede Person kann den Status jeder anderen Person ändern — das Tool basiert auf Vertrauen im Team.
- **Offline-Schrift:** Die Inter-Schrift wird von Google Fonts geladen. Ohne Internetverbindung fällt das System auf den Standard-Browser-Font zurück (Layout bleibt intakt).

---

## Lokale Entwicklung

Da es sich um eine einzelne HTML-Datei handelt, ist kein Build-Prozess nötig:

```bash
# Repository klonen
git clone https://github.com/DEIN-USERNAME/lunchboard.git
cd lunchboard
```

Danach einfach `index.html` per Doppelklick im Browser öffnen — oder die GitHub Pages / Netlify URL aufrufen.

Änderungen können direkt in `index.html` vorgenommen werden — kein Kompilieren nötig.

---

## Roadmap / mögliche Erweiterungen

- [ ] **Firebase-Integration** für geräteübergreifenden Echtzeit-Sync
- [ ] **PWA** (Progressive Web App) — als App auf dem Handy installierbar
- [ ] **Push-Benachrichtigungen** kurz vor der Pausenzeit
- [ ] **Wochen-Übersicht** mit Verlaufsanzeige
- [ ] **Weitere Pausen** (z.B. Kaffeepause) konfigurierbar

---

## Lizenz

MIT — frei verwendbar, anpassbar und weiterzugeben.

---

*Entwickelt mit ❤️ für das Kreis 1 Team — Zürich & Hamburg*
# 🍽 Lunchboard

> Einfaches Homeoffice-Tool zur täglichen Koordination von Frühstücks- und Mittagspausen im Team.

---

## Was ist Lunchboard?

Lunchboard ist eine **einzelne HTML-Datei** — kein Backend, keine Installation, keine Abhängigkeiten. Das Tool läuft direkt im Browser und speichert alle Daten lokal auf dem Gerät. Es ist optimiert für die Nutzung auf einem **Tablet im Pausenraum** sowie auf dem **Handy im Homeoffice**.

---

## Features

### ✅ Tägliche Pausenkoordination
- Zwei Pausenblöcke: **Frühstück** und **Mittagessen**
- Jede Person gibt an, ob sie dabei ist oder nicht
- Status: **Dabei** (grün) / **Nein** (rot) / **Offen** (neutral)

### ⏰ Zeitwahl pro Person
- Jede Person wählt ihre eigene Wunschzeit für die Pause
- Zeitslots in **15-Minuten-Schritten**
- Standardzeit voreingestellt (konfigurierbar)
- Frühstück: Standard **09:30**, Bereich **09:00–10:30**
- Mittagessen: Standard **12:30**, Bereich **12:00–14:00**

### ⏱ Pausendauer pro Person
- Jede Person gibt an, wie lange sie für die Pause Zeit hat
- Optionen: **15 / 30 / 45 / 60 Minuten**
- Frühstück: Standard **15 min**
- Mittagessen: Standard **45 min**
- Standard-Dauer je Pause konfigurierbar über die Einstellungen

### 💛 Match-Erkennung
- Sobald alle anwesenden Personen **dieselbe Uhrzeit** gewählt haben, erscheint ein animiertes Match-Banner
- Drei pulsierende Herzen + Konfetti-Effekt beim ersten Match
- Der ausgewählte Zeitchip leuchtet pink hervor
- Karte erhält einen dezenten rosafarbenen Leuchtrahmen

### 🍽 Essenswünsche (Mittagessen)
- Freitextfeld für Restaurantwünsche, Bestellvorschläge etc.
- Wird täglich automatisch zurückgesetzt

### ⚙️ Einstellungen
- **Personen verwalten:** Namen hinzufügen oder entfernen
- **Pausenzeiten konfigurieren:** Start- und Endzeit pro Pause frei wählbar (7:00–20:00, 15-min-Schritte)
- **Standard-Zeit pro Pause** direkt wählbar
- **Standard-Dauer pro Pause** wählbar (15 / 30 / 45 / 60 min)
- Alle Einstellungen werden im Browser gespeichert

### 🔄 Automatischer Tages-Reset
- Beim ersten Öffnen eines neuen Tages werden alle Status automatisch zurückgesetzt
- Einstellungen (Personen, Zeiten) bleiben dauerhaft erhalten
- Manueller Reset jederzeit per Button „Tag zurücksetzen"

### 📱 Mobile-First Design
- Optimiert für Smartphone und Tablet
- Große, fingertaugliche Buttons (min. 44×46 px)
- Sticky Header mit Blur-Effekt
- Automatisches 2-Spalten-Layout ab 680 px Breite (Desktop)

---

## Dateistruktur

Das Tool besteht aus **einer einzigen Datei**:

```
index.html        ← Die gesamte App (HTML + CSS + JavaScript)
README.md         ← Diese Dokumentation
```

Keine weiteren Dateien, Ordner, Node-Module oder Build-Schritte nötig.

---

## Technologie

| Komponente | Details |
|------------|---------|
| **Sprache** | Vanilla HTML, CSS, JavaScript (kein Framework) |
| **Schrift** | Inter via Google Fonts (CDN) |
| **Datenspeicherung** | `localStorage` im Browser |
| **Backend** | Keines — vollständig clientseitig |
| **Abhängigkeiten** | Keine npm-Pakete, keine Build-Tools |

---

## Installation & Deployment

### Lokal ausführen

```bash
# Einfach die Datei im Browser öffnen:
open index.html
```

Kein Server nötig — die Datei funktioniert direkt als `file://`-Pfad.

---

### GitHub Pages (empfohlen)

1. Neues GitHub-Repository anlegen (z.B. `lunchboard`)
2. `index.html` und `README.md` in das Repo hochladen
3. Im Repo: **Settings → Pages → Branch: main → Save**
4. Nach ~1 Minute erreichbar unter:

```
https://DEIN-USERNAME.github.io/lunchboard
```

---

### Netlify Drop (schnellste Option)

1. [app.netlify.com/drop](https://app.netlify.com/drop) öffnen
2. `index.html` per Drag & Drop einwerfen
3. Sofort live unter einer öffentlichen URL

---

## Konfiguration (Einstellungen-Menü)

Alle Einstellungen sind direkt in der App über das **⚙️-Icon** oben rechts erreichbar.

### Personen verwalten

| Aktion | Beschreibung |
|--------|-------------|
| **Hinzufügen** | Name eingeben + Enter oder „+ Hinzufügen" |
| **Entfernen** | „Entfernen"-Button neben dem Namen |
| **Mindestanzahl** | Mindestens 1 Person muss vorhanden sein |

Jede neue Person erhält automatisch eine Farbe aus einer vordefinierten Palette.

### Pausenzeiten konfigurieren

Pro Pause (Frühstück / Mittagessen) konfigurierbar:

| Feld | Beschreibung |
|------|-------------|
| **Von** | Startzeit (Stunde + Minute, je 15-min-Schritte) |
| **Bis** | Endzeit (Stunde + Minute, je 15-min-Schritte) |
| **Standard-Zeit** | Vorausgewählte Uhrzeit beim Tagesstart |
| **Standard-Dauer** | Vorausgewählte Dauer beim Tagesstart (15 / 30 / 45 / 60 min) |

Der Zeitbereich kann frei zwischen **07:00 und 20:00** gewählt werden. Die Zeitchips werden automatisch auf Basis von Start, Ende und 15-min-Schritten generiert.

---

## Datenspeicherung

| Was | Wo | Wie lange |
|-----|----|-----------|
| Tagesstatus (Dabei/Nein/Zeit) | `localStorage` | Bis Ende des Tages |
| Essenswünsche (Notiz) | `localStorage` | Bis Ende des Tages |
| Personen & Einstellungen | `localStorage` | Dauerhaft |

> **Hinweis:** Da `localStorage` gerätebezogen ist, sieht jedes Gerät seinen eigenen Stand. Für geräteübergreifende Synchronisation wäre ein Backend (z.B. Firebase oder Supabase) nötig.

---

## Bekannte Einschränkungen

- **Kein Echtzeit-Sync:** Jedes Gerät/Browser hat seinen eigenen Speicher. Änderungen von Daniel auf seinem Laptop sind auf Lisas Handy nicht sichtbar.
- **Kein Login:** Jede Person kann den Status jeder anderen Person ändern — das Tool basiert auf Vertrauen im Team.
- **Offline-Schrift:** Die Inter-Schrift wird von Google Fonts geladen. Ohne Internetverbindung fällt das System auf den Standard-Browser-Font zurück (Layout bleibt intakt).

---

## Lokale Entwicklung

Da es sich um eine einzelne HTML-Datei handelt, ist kein Build-Prozess nötig:

```bash
# Repository klonen
git clone https://github.com/DEIN-USERNAME/lunchboard.git
cd lunchboard
```

Danach einfach `index.html` per Doppelklick im Browser öffnen — oder die GitHub Pages / Netlify URL aufrufen.

Änderungen können direkt in `index.html` vorgenommen werden — kein Kompilieren nötig.

---

## Roadmap / mögliche Erweiterungen

- [ ] **Firebase-Integration** für geräteübergreifenden Echtzeit-Sync
- [ ] **PWA** (Progressive Web App) — als App auf dem Handy installierbar
- [ ] **Push-Benachrichtigungen** kurz vor der Pausenzeit
- [ ] **Wochen-Übersicht** mit Verlaufsanzeige
- [ ] **Weitere Pausen** (z.B. Kaffeepause) konfigurierbar

---

## Lizenz

MIT — frei verwendbar, anpassbar und weiterzugeben.

---

*Entwickelt mit ❤️ für das Kreis 1 Team — Zürich & Hamburg*
